identify()
{
    read -p "Enter URL:" url
    local filename=$(basename "$url")
    wget -q --show-progress "$url"

    local file_type=$(file -b --mime-type "$filename")

    case "$file_type" in
        audio/*)
            echo "File is an audio file"
            ;;
        video/*)
            echo "File is a video file"
            ;;
        *)
            echo "File type is not supported"
            ;;
    esac
}

identify "$url"

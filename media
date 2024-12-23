var mediaDownloader = {
  init: function() {
    const mediaElements = document.querySelectorAll('video,audio,img');
    if (mediaElements.length === 0) {
      alert('No media elements found on this page.');
      return;
    }
    const popup = document.createElement('div');
    popup.style.position = 'fixed';
    popup.style.bottom = '0';
    popup.style.left = '50%';
    popup.style.transform = 'translateX(-50%)';
    popup.style.width = '90%';
    popup.style.maxWidth = '500px';
    popup.style.backgroundColor = '#f0f0f0';
    popup.style.borderRadius = '15px 15px 0 0';
    popup.style.boxShadow = '0 -5px 15px rgba(0,0,0,0.2)';
    popup.style.padding = '20px';
    popup.style.overflowY = 'auto';
    popup.style.maxHeight = '40vh';
    popup.style.display = 'flex';
    popup.style.flexDirection = 'column';
    popup.style.gap = '10px';
    popup.style.zIndex = '9999';
    popup.style.fontFamily = 'Arial,sans-serif';
    mediaElements.forEach((media, index) => {
      const mediaUrl = media.src || media.currentSrc || media.getAttribute('src');
      if (!mediaUrl) return;
      const card = document.createElement('div');
      card.style.display = 'flex';
      card.style.alignItems = 'center';
      card.style.justifyContent = 'space-between';
      card.style.backgroundColor = '#ffffff';
      card.style.border = '1px solid #ddd';
      card.style.borderRadius = '10px';
      card.style.padding = '10px';
      card.style.boxShadow = '2px 2px 5px rgba(0,0,0,0.1)';
      card.style.cursor = 'pointer';
      const previewImage = document.createElement('img');
      previewImage.style.width = '50px';
      previewImage.style.height = '50px';
      previewImage.style.objectFit = 'cover';
      previewImage.style.marginRight = '10px';
      if (media.tagName === 'IMG') {
        previewImage.src = mediaUrl;
      } else if (media.tagName === 'VIDEO' || media.tagName === 'AUDIO') {
        previewImage.src = mediaUrl;
      } else {
        previewImage.src = 'https://via.placeholder.com/50';
      }
      const downloadText = document.createElement('span');
      downloadText.textContent = `Download ${media.tagName === 'VIDEO' ? 'Video' : media.tagName === 'AUDIO' ? 'Audio' : 'Image'} ${index + 1}`;
      downloadText.style.flexGrow = '1';
      downloadText.style.fontSize = '14px';
      downloadText.style.fontWeight = '600';
      downloadText.style.color = '#333';
      const downloadButton = document.createElement('button');
      downloadButton.textContent = 'Download';
      downloadButton.style.backgroundColor = '#007bff';
      downloadButton.style.color = '#fff';
      downloadButton.style.border = 'none';
      downloadButton.style.padding = '10px 15px';
      downloadButton.style.margin = '0';
      downloadButton.style.borderRadius = '5px';
      downloadButton.style.fontSize = '14px';
      downloadButton.style.cursor = 'pointer';
      downloadButton.style.boxShadow = '0 2px 5px rgba(0,0,0,0.1)';
      downloadButton.addEventListener('mouseover', () => {
        downloadButton.style.backgroundColor = '#0056b3';
      });
      downloadButton.addEventListener('mouseout', () => {
        downloadButton.style.backgroundColor = '#007bff';
      });
      downloadButton.onclick = () => {
        const mediaChunks = media.querySelectorAll('source');
        if (mediaChunks.length > 0) {
          mediaChunks.forEach((chunk) => {
            const a = document.createElement('a');
            a.href = chunk.src;
            a.download = chunk.src.split('/').pop();
            a.click();
          });
        } else {
          const a = document.createElement('a');
          a.href = mediaUrl;
          a.download = mediaUrl.split('/').pop();
          a.click();
        }
      };
      card.appendChild(previewImage);
      card.appendChild(downloadText);
      card.appendChild(downloadButton);
      popup.appendChild(card);
    });
    const closeButton = document.createElement('button');
    closeButton.innerHTML = '&#10005;';
    closeButton.style.position = 'absolute';
    closeButton.style.top = '10px';
    closeButton.style.right = '10px';
    closeButton.style.width = '30px';
    closeButton.style.height = '30px';
    closeButton.style.border = 'none';
    closeButton.style.backgroundColor = '#f0f0f0';
    closeButton.style.color = '#333';
    closeButton.style.borderRadius = '50%';
    closeButton.style.cursor = 'pointer';
    closeButton.style.fontSize = '18px';
    closeButton.style.display = 'flex';
    closeButton.style.alignItems = 'center';
    closeButton.style.justifyContent = 'center';
    closeButton.style.boxShadow = '2px 2px 5px rgba(0,0,0,0.2)';
    closeButton.addEventListener('mouseover', () => {
      closeButton.style.backgroundColor = '#e0e0e0';
    });
    closeButton.addEventListener('mouseout', () => {
      closeButton.style.backgroundColor = '#f0f0f0';
    });
    closeButton.onclick = () => {
      document.body.removeChild(popup);
    };
    popup.appendChild(closeButton);
    document.body.appendChild(popup);
  }
};

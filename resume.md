---
layout: page
title: Resume
---

<div id="pdf-viewer" style="width: 100%; height: 600px;"></div>

<script>
pdfjsLib.GlobalWorkerOptions.workerSrc = '/assets/js/pdfjs/pdf.worker.js';

pdfjsLib.getDocument('/assets/pdf/resume.pdf').promise.then(function(pdf) {
  pdf.getPage(1).then(function(page) {
    var scale = 1.5;
    var viewport = page.getViewport({scale: scale});
    var canvas = document.createElement('canvas');
    var context = canvas.getContext('2d');
    canvas.height = viewport.height;
    canvas.width = viewport.width;
    var renderContext = {
      canvasContext: context,
      viewport: viewport
    };
    page.render(renderContext);
    document.getElementById('pdf-viewer').appendChild(canvas);
  });
});
</script>

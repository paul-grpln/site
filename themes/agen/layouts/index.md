

{{ if .Site.Data.homepage.service.enable }}
<!-- service -->
<section class="section">
  <div class="container">
    <div class="row">
      {{ with .Site.Data.homepage.service }}
      <div class="col-lg-10 mx-auto text-center">
        <h2>{{ .title | markdownify }}</h2>
        <p class="lead">{{ .subtitle | markdownify}}</p>
        <div class="section-border"></div>
      </div>
      {{ end }}
    </div>
    <div class="row">
      {{ range first 3 .Site.Data.service.services }}
      <div class="col-lg-4 mb-4 mb-lg-0">
        <div class="card hover-bg-secondary shadow py-4">
          <div class="card-body text-center">
            <div class="position-relative">
              <i
                class="icon-lg icon-box bg-gradient-primary rounded-circle {{ .icon }} mb-5 d-inline-block text-white"></i>
              <i class="icon-lg icon-watermark text-white {{ .icon }}"></i>
            </div>
            <h4 class="mb-4">{{ .title | markdownify }}</h4>
            <p>{{ .content | markdownify }}</p>
          </div>
        </div>
      </div>
      {{ end }}
    </div>
  </div>
</section>
<!-- /service -->
{{ end }}

{{ if .Site.Data.homepage.feature.enable }}
{{ partial "feature.html" . }}
{{ end }}

{{ if .Site.Data.homepage.promo.enable }}
<!-- promo video -->
{{ with .Site.Data.homepage.promo }}
<section class="section-lg position-relative bg-cover" data-background="'{{ .bgImage | absURL }}'">
  <div class="container">
    <div class="row justify-content-between">
      <div class="col-lg-6 col-md-8 col-sm-7 col-8">
        <h2 class="text-white mb-4">{{ .title  | markdownify }}</h2>
        <p class="text-light mb-4">{{ .content | markdownify }}</p>
        {{ if .button.enable }}
        {{ with .button }}
        <a href="{{ .link | absURL }}" class="btn btn-primary">{{ .label }}</a>
        {{ end }}
        {{ end }}
      </div>
      <div class="col-md-2 col-sm-4 col-4 text-right align-self-end">
        <a class="venobox" data-autoplay="true" data-vbtype="video" href="{{ .videoURL | safeURL }}">
          <i
            class="text-center icon-sm icon-box rounded-circle text-white bg-gradient-primary d-block ti-control-play"></i>
        </a>
      </div>
    </div>
  </div>
</section>
{{ end }}
<!-- /promo video -->
{{ end }}

{{ if .Site.Data.homepage.project.enable }}
<!-- project -->
<section class="section pb-0">
  <div class="container-fluid px-0">
    <div class="row">
      {{ with .Site.Data.homepage.project }}
      <div class="col-lg-10 mx-auto text-center">
        <h2>{{ .title | markdownify }}</h2>
        {{ if ne .title "" }}
        <div class="section-border"></div>
        {{ end }}
      </div>
      {{ end }}
    </div>

    <div class="row no-gutters shuffle-wrapper">
      {{ range first 5 .Site.Data.project.projects }}

      {{ $column := .column }}
      {{ if eq $column 1 }}
      {{ $column = "col-lg-4 col-md-6" }}
      {{ else if eq $column 2 }}
      {{ $column = "col-lg-8" }}
      {{ else }}
      {{ $column = "col-lg-4 col-md-6" }}
      {{ end }}
      <div class="{{$column}} shuffle-item">
        <div class="project-item">
          <img src="{{ .image | absURL }}" alt="project-image" class="img-fluid w-100">
          <div class="project-hover bg-secondary px-4 py-3">
            {{ if and ( ne .link "" ) ( ne .link "#" ) }}
            <a href="{{ .link | safeURL }}" target="_blank" class="text-white h4">{{ .title | markdownify}}</a>
            <a href="{{ .link | safeURL }}"><i class="ti-link icon-xs text-white"></i></a>
            {{ else }}
            <h4 class="text-white">{{ .title | markdownify }}</h4>
            {{ end }}
          </div>
        </div>
      </div>
      {{ end }}
    </div>
  </div>
</section>
<!-- /project -->
{{ end }}

{{ if .Site.Data.homepage.pricing.enable }}
<!-- pricing -->
<section class="section pb-0">
  <div class="container">
    <div class="row">
      {{ with .Site.Data.homepage.pricing }}
      <div class="col-lg-10 mx-auto text-center">
        <h2>{{ .title | markdownify }}</h2>
        <div class="section-border"></div>
      </div>
      {{ end }}
    </div>
    <div class="row">
      {{ range .Site.Data.pricing.pricingTable }}
      <div class="col-lg-4 col-sm-6 mb-4 mb-lg-0">
        <div class="card bottom-shape bg-secondary pt-4 pb-5">
          <div class="card-body text-center">
            <h4 class="text-white">{{ .title }}</h4>
            <p class="text-light mb-4">{{ .subtitle | markdownify }}</p>
            <p class="text-white mb-4">$ <span
                class="display-3 font-weight-bold vertical-align-middle">{{ .price }}</span></p>
            <ul class="list-unstyled mb-5">
              {{ range .serviceList }}
              <li class="text-white mb-3">{{ .service | markdownify }}</li>
              {{ end }}
            </ul>
            {{ with .button }}
            <a href="{{ .link | safeURL }}" class="btn btn-outline-light">{{ .label }}</a>
            {{ end }}
          </div>
        </div>
      </div>
      {{ end }}
    </div>
  </div>
</section>
<!-- /pricing -->
{{ end }}

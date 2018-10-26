guard 'shell' do
  watch(%r{.+\.uml}) do |m|
    `java -jar lib/plantuml.jar -tpng #{m[0]}`
    `sed "s/%src%/#{File.basename(m[0], '.uml') + '.png'}/g" < livereload.tmpl > #{File.basename(m[0], '.uml')}.html`
  end
end

guard 'livereload' do
  watch(%r{.+\.html})
end

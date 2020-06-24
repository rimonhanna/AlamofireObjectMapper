workspace 'AlamofireObjectMapper.xcworkspace'
inhibit_all_warnings!
use_frameworks!

##
## Define Pod dependencies
##
def app_pods
    pod 'Alamofire'
    pod 'ObjectMapper'

end

target :'AlamofireObjectMapper iOS' do
    platform :ios, '10.0'
    app_pods
    target 'AlamofireObjectMapperTests iOS' do
      inherit! :search_paths
    end
end

target :'AlamofireObjectMapper macOS' do
    platform :osx, '10.12'
    app_pods
    target 'AlamofireObjectMapperTests macOS' do
      inherit! :search_paths
    end
end


post_install do |installer_representation|
    installer_representation.pods_project.targets.each do |target|
        target.build_configurations.each do |config|
            config.build_settings['SWIFT_VERSION'] = "5.0"
            config.build_settings['GCC_WARN_INHIBIT_ALL_WARNINGS'] = "YES"
            config.build_settings.delete('CODE_SIGNING_ALLOWED')
            config.build_settings.delete('CODE_SIGNING_REQUIRED')
            if config.name == 'Release'
                config.build_settings['SWIFT_COMPILATION_MODE'] = 'wholemodule'
            end   
        end
    end
end

# Podfile

source 'https://github.com/CocoaPods/Specs.git'

# Select the appropriate platform below
platform :ios, '8.0'

#
# Some other entries might already exist in the file
# ...
#

# ignore all warnings from all pods
inhibit_all_warnings!

use_frameworks!

target "Pegasus" do
  pod 'VIMNetworking', :git => 'https://github.com/FastSociety/VIMNetworking.git',  :branch => 'cocoapod_framework', :submodules => true
end

target "PegasusExtension" do
  pod 'VIMNetworking', :git => 'https://github.com/FastSociety/VIMNetworking.git',  :branch => 'cocoapod_framework', :submodules => true
end

post_install do |installer_representation|
  installer_representation.project.targets.each do |target|
    if target.name == 'Pods-PegasusExtension-AFNetworking' || target.name == 'Pods-PegasusExtension-VIMNetworking'
      target.build_configurations.each do |config|
        config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= ['$(inherited)']
        config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] << 'AF_APP_EXTENSIONS=1'
        config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] << 'UPLOAD_EXTENSION=1'
      end
    end
  end
end




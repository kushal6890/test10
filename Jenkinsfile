node {
  deleteDir()
  checkout scm
  echo 'beginnning workflow...'

  stage 'install gems'
  sh '''#!/bin/bash
  source /home/jenkins/.bashrc
  export PUPPET_GEM_VERSION="~> 5.5.0"
  /usr/local/rvm/bin/rvm ruby-2.4.4 do bundle install --path=.bundle/gems/ --without system_tests
  '''


  stage 'validation'
  sh '''#!/bin/bash
  source /home/jenkins/.bashrc
  /usr/local/rvm/bin/rvm ruby-2.4.4 do bundle exec rake validate
  '''

  stage 'lint'
  sh '''#!/bin/bash
  source /home/jenkins/.bashrc
  /usr/local/rvm/bin/rvm ruby-2.4.4 do bundle exec rake lint
  '''


  stage 'spec'
  sh '''#!/bin/bash
  source /home/jenkins/.bashrc
  /usr/local/rvm/bin/rvm ruby-2.4.4 do bundle exec rake spec
  '''


  stage'build'
  sh '''#!/bin/bash
  source /home/jenkins/.bashrc
  /usr/local/rvm/bin/rvm ruby-2.4.4 do bundle exec rake build
  '''
}

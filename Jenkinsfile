pipeline {
   agent any
   environment {
       PATH = "C:\\Program Files\\MATLAB\\R2023b\\bin;${PATH}"   // Windows agent 
   }
    stages {
        stage('First_Step') {
            steps {
               runMATLABCommand(command: 'disp("The building just started!")')
            }       
        }
        stage('Simulation') {
            steps {
                runMATLABCommand(command: 'simulation_check')
            }       
        }
       stage('Testcases') {
            steps {
                runMATLABTests(testResultsJUnit: 'test-results/results.xml',
                               codeCoverageCobertura: 'code-coverage/coverage.xml', 
                                 testResultsPDF: 'test-results/testreport.pdf')
            }
        }
       stage('Jmaab_check') {
            steps {
                runMATLABCommand(command: 'jmaab_check')
            }       
        }
       stage('Code_Generation') {
            steps {
                runMATLABCommand(command: 'code_generation')
            }       
        }
       stage('Finish') {
            steps {
               runMATLABCommand(command: 'disp("This is the last step.")')
            } 
       }
   }

}

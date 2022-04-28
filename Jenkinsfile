@Library('cmsdevopscorelib')_
if ("$buildordeploy" == 'build'){ 
build "$branch_name"
}
else
{
 if ("$branch_name" == 'develop'){ 
 deploy "$branch_name"
 }
 else
 {
 echo "deployment to $branch_name ENV is not allowed"
  sh 'exit 1'
 }
 
}

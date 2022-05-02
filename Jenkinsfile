@Library('cmsdevopscorelib')_
if ("$buildordeploy" == 'build'){
 if ("$branch_name" == 'develop'){ 
 build "$branch_name"
 }
 else
 {
 echo "__________Build not allowed on $branch_name ____________"
 exit 1
   }
}
else
{
 if ("$branch_name" == 'develop'){ 
 deploy "$branch_name"
 }
 else
 {
 echo "__________deployment to $branch_name ENV is not allowed____________"
 exit 1
   }
 
}
/* @Library('cmsdevopscorelib')_
if ("$buildordeploy" == 'build'){
  build "$branch_name"
 }
 else
 {
  deploy "$branch_name"
 } */

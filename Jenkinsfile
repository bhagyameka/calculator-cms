@Library('cmsdevopscorelib')_
if ("$buildordeploy" == 'build'){
 if ("$branch_name" == 'develop'){ 
 build "$branch_name"
 }
 else
 {
 echo "__________Build not allowed on $branch_name____________"
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
   }
 
}

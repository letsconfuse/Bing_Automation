# Bing_Automation

# Define the path to Microsoft Edge executable
$edgePath = "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe"

# Define profiles and actions
$profiles = @(
    @{
        ProfileName = "Profile 10"
        SleepDuration = 600  # seconds
    },
    @{
        ProfileName = "Profile 11"
        SleepDuration = 600  # seconds
    },
    @{
        ProfileName = "Profile 2"
        SleepDuration = 600  # seconds
    },
    @{
        ProfileName = "Profile 12"
        SleepDuration = 600  # seconds
    },
    @{
        ProfileName = "Profile 13"
        SleepDuration = 600  # seconds
    }

)

# Loop through each profile
foreach ($profile in $profiles) {
    $profileName = $profile.ProfileName

    # Start Microsoft Edge with the specified profile
    Start-Process -FilePath $edgePath -ArgumentList "--profile-directory=`"$profileName`"" 
    Start-Sleep -Seconds 3
    $randomWord = Get-Random -InputObject @("apple", "banana", "cherry", "orange", "grape")
    $searchUrl = "https://www.bing.com/search?q=$randomWord"
    Start-Process -FilePath $edgePath -ArgumentList "--profile-directory=`"$profileName`" --new-tab $searchUrl"
    Start-Sleep -Seconds 5

    # Wait for the specified duration before terminating Edge
    Start-Sleep -Seconds $profile.SleepDuration

    # Terminate Microsoft Edge processes associated with the specified profile
    Stop-Process -Name msedge -Force
    Start-Sleep -Seconds 20  # Give some time before starting the next profile
}

# Clean up screen awake job
Get-Job | Remove-Job -Force

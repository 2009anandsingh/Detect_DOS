# Detect_DOS
this program will help invidivual machines to detect possible DOS or DDOS attempts and remote machines. Currently few values are static.




***///


$a = (Get-NetTCPConnection | Where-Object { $_.State -eq 'SynReceived' }).count
$b = "DOS Attempted - TCP SYN-Establishing at  "
$c = "  per second"
if ($a -lt 1000)
 {  
    
 }
    else 
 {
    $a = (Get-NetTCPConnection | Where-Object { $_.State -eq 'SynReceived' }).count
    $b = "DOS Attempted - TCP SYN-Establishing at  "
    $c = "  per second"
    $e = Get-NetTCPConnection -State SynReceived | select remoteaddress -Unique
    $d = $b + $a.ToString() + $c + $e
    Write-EventLog -LogName "Application" -Source "Alienvault" -EventID 5148 -EntryType Warning -Message $d -Category 1 -RawData 9
 }
 
 
 ***///

<div align="center">

## vb\.net Ping Function


</div>

### Description

Allows you to ping a remote host using vb.net
 
### More Info
 
Public Function Ping(ByVal host As String) As String

a string with the response


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Dain Axel Muller](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/dain-axel-muller.md)
**Level**          |Intermediate
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |VB\.NET
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__10-1.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/dain-axel-muller-vb-net-ping-function__10-4311/archive/master.zip)





### Source Code

```
Public Function Ping(ByVal host As String) As String
    Try
      Dim a As New System.Net.NetworkInformation.Ping
      Dim b As System.Net.NetworkInformation.PingReply
      Dim txtlog As String = ""
      Dim c As New System.Net.NetworkInformation.PingOptions
      c.DontFragment = True
      c.Ttl = 64
      Dim data As String = "aaaaaaaaaaaaaaaa"
      Dim bt As Byte() = System.Text.Encoding.ASCII.GetBytes(data)
      Dim i As Int16
      For i = 1 To 4
        b = a.Send(host, 2000, bt, c)
        If b.Status = Net.NetworkInformation.IPStatus.Success Then
          txtlog += "Reply from " & host & " in " & b.RoundtripTime & " ms, ttl " & b.Options.Ttl & vbCrLf
        End If
        If b.Status = Net.NetworkInformation.IPStatus.DestinationHostUnreachable Then
          txtlog += "Destination Host Unreachable" & vbCrLf
        End If
        If b.Status = Net.NetworkInformation.IPStatus.TimedOut Then
          txtlog += "Reply timed out" & vbCrLf
        End If
      Next i
      Return txtlog
    Catch ex As Exception
      Return "Ping error"
    End Try
  End Function
```


---
title: OracleDataReader’da REF CURSOR Parametreleri
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 801dff0f-2508-45aa-9416-f45d6887740c
ms.openlocfilehash: 32285c78bfe8e8c24e70109cbf82a63a4d42848e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166475"
---
# <a name="ref-cursor-parameters-in-an-oracledatareader"></a><span data-ttu-id="053ca-102">OracleDataReader’da REF CURSOR Parametreleri</span><span class="sxs-lookup"><span data-stu-id="053ca-102">REF CURSOR Parameters in an OracleDataReader</span></span>

<span data-ttu-id="053ca-103">Bu Microsoft Visual Basic örneği, bir REF CURSOR parametresi döndüren bir PL/SQL saklı yordamını yürütür ve değeri bir olarak okur <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="053ca-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
```vb  
Private Sub Button1_Click(ByVal sender As Object, _  
  ByVal e As System.EventArgs) Handles Button1.Click  
  
  Dim connString As New String(_  
      "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
    Dim rdr As OracleDataReader  
  
    conn.Open()  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_ONE_CURSOR"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter(  
      "N_EMPNO", OracleType.Number)).Value = 7369  
    cmd.Parameters.Add(New OracleParameter(  
      "IO_CURSOR", OracleType.Cursor)).Direction = ParameterDirection.Output  
  
    rdr = cmd.ExecuteReader()  
    While (rdr.Read())  
        REM do something with the values  
    End While  
  
    rdr.Close()  
  End Using  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="053ca-104">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="053ca-104">See also</span></span>

- [<span data-ttu-id="053ca-105">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="053ca-105">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="053ca-106">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="053ca-106">ADO.NET Overview</span></span>](ado-net-overview.md)

---
description: 'Daha fazla bilgi edinin: bir OracleDataReader kullanarak birden çok REF Imleçten veri alma'
title: OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
ms.openlocfilehash: 855373bd8307adbdf771ec9caf61c685a82d1108
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663436"
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a>OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma

Bu Microsoft Visual Basic örneği, iki REF CURSOR parametresi döndüren bir PL/SQL saklı yordamı yürütür ve kullanarak değerleri okur <xref:System.Data.OracleClient.OracleDataReader> .

```vb
Private Sub Button1_Click( _
  ByVal sender As Object, ByVal e As System.EventArgs)  _
  Handles Button1.Click

  Dim connString As New String( _
      "Data Source=Oracle9i;User ID=scott;Password=[PLACEHOLDER];")
  Using conn As New OracleConnection(connString)
    Dim cmd As New OracleCommand()
    Dim rdr As OracleDataReader

    conn.Open()
    cmd.Connection = conn
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"
    cmd.CommandType = CommandType.StoredProcedure
    cmd.Parameters.Add(New OracleParameter( _
      "EMPCURSOR", OracleType.Cursor)).Direction = _
      ParameterDirection.Output
    cmd.Parameters.Add(New OracleParameter(_
      "DEPTCURSOR", OracleType.Cursor)).Direction = _
      ParameterDirection.Output

    rdr = cmd.ExecuteReader(CommandBehavior.CloseConnection)
    While (rdr.Read())
        REM do something with the values from the EMP table
    End While

    rdr.NextResult()
    While (rdr.Read())
        REM do something with the values from the DEPT table
    End While
    rdr.Close()
  End Using
End Sub
```

## <a name="see-also"></a>Ayrıca bkz.

- [Oracle REF CURSOR](oracle-ref-cursors.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)

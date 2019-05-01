---
title: Katalog İşlemleri Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: beb5d2db898df1c98662d53190ac1432acc746e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878234"
---
# <a name="performing-catalog-operations"></a>Katalog İşlemleri Gerçekleştirme
Bir veritabanı veya katalog, CREATE TABLE veya CREATE PROCEDURE deyimi gibi değiştirmek için bir komut çalıştırmak için oluşturma bir **komut** uygun SQL deyimlerini kullanarak nesne ve **bağlantı** nesne. Komutu ile yürütme **ExecuteNonQuery** yöntemi **komut** nesne.  
  
 Aşağıdaki kod örneği, bir Microsoft SQL Server veritabanında bir saklı yordam oluşturur.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +   
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +   
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +   
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Verileri Değiştirmek için Komutları Kullanma](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)
- [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

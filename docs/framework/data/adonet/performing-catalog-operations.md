---
title: Katalog İşlemleri Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: beb5d2db898df1c98662d53190ac1432acc746e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141459"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="7c1e5-102">Katalog İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="7c1e5-102">Performing Catalog Operations</span></span>
<span data-ttu-id="7c1e5-103">Bir veritabanı veya katalog, CREATE TABLE veya CREATE PROCEDURE deyimi gibi değiştirmek için bir komut çalıştırmak için oluşturma bir **komut** uygun SQL deyimlerini kullanarak nesne ve **bağlantı** nesne.</span><span class="sxs-lookup"><span data-stu-id="7c1e5-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="7c1e5-104">Komutu ile yürütme **ExecuteNonQuery** yöntemi **komut** nesne.</span><span class="sxs-lookup"><span data-stu-id="7c1e5-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="7c1e5-105">Aşağıdaki kod örneği, bir Microsoft SQL Server veritabanında bir saklı yordam oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c1e5-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c1e5-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c1e5-106">See also</span></span>

- [<span data-ttu-id="7c1e5-107">Verileri Değiştirmek için Komutları Kullanma</span><span class="sxs-lookup"><span data-stu-id="7c1e5-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)
- [<span data-ttu-id="7c1e5-108">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c1e5-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="7c1e5-109">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="7c1e5-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

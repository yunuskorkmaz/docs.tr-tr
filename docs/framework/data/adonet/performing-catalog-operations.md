---
title: Katalog İşlemleri Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 802762592a63a2046abcde8ed83ac67be47faf96
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161652"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="fca05-102">Katalog İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="fca05-102">Performing Catalog Operations</span></span>

<span data-ttu-id="fca05-103">CREATE TABLE veya yordam oluşturma deyimi gibi bir veritabanını veya kataloğu değiştirmek üzere bir komut yürütmek için, uygun SQL deyimlerini ve bir **bağlantı** nesnesini kullanarak bir **komut** nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fca05-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="fca05-104">**Komut nesnesinin** **ExecuteNonQuery** yöntemiyle komutunu yürütün.</span><span class="sxs-lookup"><span data-stu-id="fca05-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="fca05-105">Aşağıdaki kod örneği Microsoft SQL Server veritabanında bir saklı yordam oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fca05-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fca05-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fca05-106">See also</span></span>

- [<span data-ttu-id="fca05-107">Verileri Değiştirmek için Komutları Kullanma</span><span class="sxs-lookup"><span data-stu-id="fca05-107">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="fca05-108">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="fca05-108">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="fca05-109">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fca05-109">ADO.NET Overview</span></span>](ado-net-overview.md)

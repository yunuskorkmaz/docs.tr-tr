---
title: Veritabanından Tek Değer Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794740"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="5bcf8-102">Veritabanından Tek Değer Alma</span><span class="sxs-lookup"><span data-stu-id="5bcf8-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="5bcf8-103">Tablo veya veri akışı biçiminde değil, yalnızca tek bir değer olan veritabanı bilgilerini döndürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5bcf8-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="5bcf8-104">Örneğin, Count (\*), Sum (price) veya AVG (Quantity) gibi bir toplama işlevinin sonucunu döndürmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bcf8-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="5bcf8-105">**Komut** nesnesi, **ExecuteReader metodunu** yöntemini kullanarak tek değerler döndürme yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="5bcf8-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="5bcf8-106">**ExecuteReader metodunu** yöntemi, bir skaler değer olarak sonuç kümesinin ilk satırının ilk sütununun değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="5bcf8-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="5bcf8-107">Aşağıdaki kod örneği, kullanarak <xref:System.Data.SqlClient.SqlCommand>veritabanına yeni bir değer ekler.</span><span class="sxs-lookup"><span data-stu-id="5bcf8-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="5bcf8-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Yöntemi, ekli kaydın kimlik sütunu değerini döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5bcf8-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5bcf8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bcf8-109">See also</span></span>

- [<span data-ttu-id="5bcf8-110">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bcf8-110">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="5bcf8-111">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="5bcf8-111">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="5bcf8-112">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="5bcf8-112">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="5bcf8-113">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5bcf8-113">ADO.NET Overview</span></span>](ado-net-overview.md)

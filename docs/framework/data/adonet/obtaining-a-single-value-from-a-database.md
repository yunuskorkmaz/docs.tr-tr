---
title: Veritabanından Tek Değer Alma
description: ADO.NET içinde tek bir değer döndürmeyi öğrenin. Bu örnek kod, ekli bir kayıt için kimlik sütunu değerini döndürür.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 9ce29bc1321814bd60cfaacd222fc55a3fbf12ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150732"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="0fb75-104">Veritabanından Tek Değer Alma</span><span class="sxs-lookup"><span data-stu-id="0fb75-104">Obtaining a Single Value from a Database</span></span>

<span data-ttu-id="0fb75-105">Tablo veya veri akışı biçiminde değil, yalnızca tek bir değer olan veritabanı bilgilerini döndürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0fb75-105">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="0fb75-106">Örneğin, COUNT ( \* ), Sum (price) veya AVG (Quantity) gibi bir toplama işlevinin sonucunu döndürmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fb75-106">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="0fb75-107">**Komut** nesnesi, **ExecuteReader metodunu** yöntemini kullanarak tek değerler döndürme yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fb75-107">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="0fb75-108">**ExecuteReader metodunu** yöntemi, bir skaler değer olarak sonuç kümesinin ilk satırının ilk sütununun değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="0fb75-108">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="0fb75-109">Aşağıdaki kod örneği, kullanarak veritabanına yeni bir değer ekler <xref:System.Data.SqlClient.SqlCommand> .</span><span class="sxs-lookup"><span data-stu-id="0fb75-109">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="0fb75-110"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>Yöntemi, ekli kaydın kimlik sütunu değerini döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0fb75-110">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0fb75-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fb75-111">See also</span></span>

- [<span data-ttu-id="0fb75-112">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="0fb75-112">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="0fb75-113">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="0fb75-113">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="0fb75-114">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="0fb75-114">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="0fb75-115">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0fb75-115">ADO.NET Overview</span></span>](ado-net-overview.md)

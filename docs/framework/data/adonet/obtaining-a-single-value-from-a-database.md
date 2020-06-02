---
title: Veritabanından Tek Değer Alma
description: ADO.NET içinde tek bir değer döndürmeyi öğrenin. Bu örnek kod, ekli bir kayıt için kimlik sütunu değerini döndürür.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: a6f268f72f8b8a09ae48ba3cad6254323cb95a20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286708"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="c0241-104">Veritabanından Tek Değer Alma</span><span class="sxs-lookup"><span data-stu-id="c0241-104">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="c0241-105">Tablo veya veri akışı biçiminde değil, yalnızca tek bir değer olan veritabanı bilgilerini döndürmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c0241-105">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="c0241-106">Örneğin, COUNT ( \* ), Sum (price) veya AVG (Quantity) gibi bir toplama işlevinin sonucunu döndürmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0241-106">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="c0241-107">**Komut** nesnesi, **ExecuteReader metodunu** yöntemini kullanarak tek değerler döndürme yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0241-107">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="c0241-108">**ExecuteReader metodunu** yöntemi, bir skaler değer olarak sonuç kümesinin ilk satırının ilk sütununun değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0241-108">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="c0241-109">Aşağıdaki kod örneği, kullanarak veritabanına yeni bir değer ekler <xref:System.Data.SqlClient.SqlCommand> .</span><span class="sxs-lookup"><span data-stu-id="c0241-109">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="c0241-110"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>Yöntemi, ekli kaydın kimlik sütunu değerini döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0241-110">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c0241-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0241-111">See also</span></span>

- [<span data-ttu-id="c0241-112">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0241-112">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="c0241-113">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="c0241-113">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="c0241-114">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="c0241-114">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="c0241-115">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c0241-115">ADO.NET Overview</span></span>](ado-net-overview.md)

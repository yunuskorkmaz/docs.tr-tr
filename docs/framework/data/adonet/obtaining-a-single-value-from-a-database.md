---
title: Bir veritabanından tek değer alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: e362a71f902739663961099cf2f43dff90b4743c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711466"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="bd6f1-102">Bir veritabanından tek değer alma</span><span class="sxs-lookup"><span data-stu-id="bd6f1-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="bd6f1-103">Yalnızca tek bir değer dönüş veritabanı bilgileri yerine bir tablo veya veri akışını biçiminde gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bd6f1-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="bd6f1-104">Örneğin, sonuç sayısı gibi bir toplama işlevinin isteyebilirsiniz (\*), SUM(Price) veya AVG(Quantity).</span><span class="sxs-lookup"><span data-stu-id="bd6f1-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="bd6f1-105">**Komut** nesnesi kullanarak tek değerler döndürülecek yeteneği sağlar **ExecuteScalar** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bd6f1-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="bd6f1-106">**ExecuteScalar** yöntemi döndürür, skaler değer olarak, sonuç kümesi ilk satırının ilk sütununu değeri.</span><span class="sxs-lookup"><span data-stu-id="bd6f1-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="bd6f1-107">Aşağıdaki kod örneği kullanarak veritabanını yeni bir değer ekler. bir <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="bd6f1-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="bd6f1-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Yöntemi eklenen kaydın Kimlik sütununda değer döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bd6f1-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bd6f1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd6f1-109">See also</span></span>
- [<span data-ttu-id="bd6f1-110">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd6f1-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="bd6f1-111">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="bd6f1-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)
- [<span data-ttu-id="bd6f1-112">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="bd6f1-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="bd6f1-113">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="bd6f1-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

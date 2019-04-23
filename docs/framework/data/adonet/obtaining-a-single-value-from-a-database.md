---
title: Veritabanından Tek Değer Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 5eb81fd2a64f06f1252f71e251e58df568e7407c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120685"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="5487e-102">Veritabanından Tek Değer Alma</span><span class="sxs-lookup"><span data-stu-id="5487e-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="5487e-103">Yalnızca tek bir değer dönüş veritabanı bilgileri yerine bir tablo veya veri akışını biçiminde gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5487e-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="5487e-104">Örneğin, sonuç sayısı gibi bir toplama işlevinin isteyebilirsiniz (\*), SUM(Price) veya AVG(Quantity).</span><span class="sxs-lookup"><span data-stu-id="5487e-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="5487e-105">**Komut** nesnesi kullanarak tek değerler döndürülecek yeteneği sağlar **ExecuteScalar** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5487e-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="5487e-106">**ExecuteScalar** yöntemi döndürür, skaler değer olarak, sonuç kümesi ilk satırının ilk sütununu değeri.</span><span class="sxs-lookup"><span data-stu-id="5487e-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="5487e-107">Aşağıdaki kod örneği kullanarak veritabanını yeni bir değer ekler. bir <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="5487e-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="5487e-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Yöntemi eklenen kaydın Kimlik sütununda değer döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5487e-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5487e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5487e-109">See also</span></span>

- [<span data-ttu-id="5487e-110">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="5487e-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="5487e-111">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="5487e-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)
- [<span data-ttu-id="5487e-112">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="5487e-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="5487e-113">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="5487e-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

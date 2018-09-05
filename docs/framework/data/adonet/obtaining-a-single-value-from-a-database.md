---
title: Bir veritabanından tek değer alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 1a0d92c7acad58d3618c3f50b7463022352cf542
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560863"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="652df-102">Bir veritabanından tek değer alma</span><span class="sxs-lookup"><span data-stu-id="652df-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="652df-103">Yalnızca tek bir değer dönüş veritabanı bilgileri yerine bir tablo veya veri akışını biçiminde gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="652df-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="652df-104">Örneğin, sonuç sayısı gibi bir toplama işlevinin isteyebilirsiniz (\*), SUM(Price) veya AVG(Quantity).</span><span class="sxs-lookup"><span data-stu-id="652df-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="652df-105">**Komut** nesnesi kullanarak tek değerler döndürülecek yeteneği sağlar **ExecuteScalar** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="652df-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="652df-106">**ExecuteScalar** yöntemi döndürür, skaler değer olarak, sonuç kümesi ilk satırının ilk sütununu değeri.</span><span class="sxs-lookup"><span data-stu-id="652df-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="652df-107">Aşağıdaki kod örneği kullanarak veritabanını yeni bir değer ekler. bir <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="652df-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="652df-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Yöntemi eklenen kaydın Kimlik sütununda değer döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="652df-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="652df-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="652df-109">See Also</span></span>  
 [<span data-ttu-id="652df-110">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="652df-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="652df-111">Komut Yürütme</span><span class="sxs-lookup"><span data-stu-id="652df-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="652df-112">DbConnection, DbCommand ve DbException</span><span class="sxs-lookup"><span data-stu-id="652df-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="652df-113">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="652df-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

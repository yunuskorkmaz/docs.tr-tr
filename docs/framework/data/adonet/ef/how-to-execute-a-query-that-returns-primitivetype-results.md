---
title: 'Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: 4805a9f959096b87e2ed3e35b02fbd8c04d45fbc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251479"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a><span data-ttu-id="3c7f2-102">Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="3c7f2-102">How to: Execute a Query that Returns PrimitiveType Results</span></span>
<span data-ttu-id="3c7f2-103">Bu konu <xref:System.Data.EntityClient.EntityCommand>, kullanarak bir kavramsal modele karşı bir komutun nasıl yürütüleceğini ve bir <xref:System.Data.EntityClient.EntityDataReader>kullanarak <xref:System.Data.Metadata.Edm.PrimitiveType> sonuçların nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c7f2-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand>, and how to retrieve the <xref:System.Data.Metadata.Edm.PrimitiveType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="3c7f2-104">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3c7f2-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="3c7f2-105">Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi kullanmak [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="3c7f2-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="3c7f2-106">Daha fazla bilgi için [nasıl yapılır: Varlık Veri Modeli Sihirbazı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c7f2-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="3c7f2-107">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin (`Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="3c7f2-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="3c7f2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c7f2-108">Example</span></span>  
 <span data-ttu-id="3c7f2-109">Bu örnek, <xref:System.Data.Metadata.Edm.PrimitiveType> sonuç döndüren bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="3c7f2-109">This example executes a query that returns a <xref:System.Data.Metadata.Edm.PrimitiveType> result.</span></span> <span data-ttu-id="3c7f2-110">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` işleve bağımsız değişken olarak geçirirseniz, işlev, tümünün `Products`ortalama liste fiyatını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="3c7f2-110">If you pass the following query as an argument to the `ExecutePrimitiveTypeQuery` function, the function displays the average list price of all `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 <span data-ttu-id="3c7f2-111">Aşağıdaki <xref:System.Data.EntityClient.EntityParameter> gibiparametreli<xref:System.Data.EntityClient.EntityCommand> bir sorgu geçirirseniz, nesne üzerindeki özelliği.<xref:System.Data.EntityClient.EntityCommand.Parameters%2A></span><span class="sxs-lookup"><span data-stu-id="3c7f2-111">If you pass a parameterized query, like the following, <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a><span data-ttu-id="3c7f2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c7f2-112">See also</span></span>

- [<span data-ttu-id="3c7f2-113">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3c7f2-113">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="3c7f2-114">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="3c7f2-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)

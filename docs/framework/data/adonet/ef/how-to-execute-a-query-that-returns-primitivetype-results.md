---
title: 'Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: ef212b31e9a7eda5adb037ff2b91f298ae6e948e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546763"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a><span data-ttu-id="65f5a-102">Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="65f5a-102">How to: Execute a Query that Returns PrimitiveType Results</span></span>
<span data-ttu-id="65f5a-103">Bu konu, kullanarak bir kavramsal modele karşı bir komutun nasıl yürütüleceğini <xref:System.Data.EntityClient.EntityCommand> ve <xref:System.Data.Metadata.Edm.PrimitiveType> bir kullanarak sonuçların nasıl alınacağını gösterir <xref:System.Data.EntityClient.EntityDataReader> .</span><span class="sxs-lookup"><span data-stu-id="65f5a-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand>, and how to retrieve the <xref:System.Data.Metadata.Edm.PrimitiveType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="65f5a-104">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="65f5a-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="65f5a-105">Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="65f5a-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="65f5a-106">Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="65f5a-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="65f5a-107">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="65f5a-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="65f5a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="65f5a-108">Example</span></span>  
 <span data-ttu-id="65f5a-109">Bu örnek, sonuç döndüren bir sorgu yürütür <xref:System.Data.Metadata.Edm.PrimitiveType> .</span><span class="sxs-lookup"><span data-stu-id="65f5a-109">This example executes a query that returns a <xref:System.Data.Metadata.Edm.PrimitiveType> result.</span></span> <span data-ttu-id="65f5a-110">Aşağıdaki sorguyu işleve bağımsız değişken olarak geçirirseniz `ExecutePrimitiveTypeQuery` , işlev, tümünün ortalama liste fiyatını görüntüler `Products` :</span><span class="sxs-lookup"><span data-stu-id="65f5a-110">If you pass the following query as an argument to the `ExecutePrimitiveTypeQuery` function, the function displays the average list price of all `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 <span data-ttu-id="65f5a-111">Aşağıdaki gibi parametreli bir sorgu geçirirseniz, <xref:System.Data.EntityClient.EntityParameter> <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> nesne üzerindeki özelliği <xref:System.Data.EntityClient.EntityCommand> .</span><span class="sxs-lookup"><span data-stu-id="65f5a-111">If you pass a parameterized query, like the following, <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a><span data-ttu-id="65f5a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65f5a-112">See also</span></span>

- [<span data-ttu-id="65f5a-113">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="65f5a-113">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="65f5a-114">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="65f5a-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)

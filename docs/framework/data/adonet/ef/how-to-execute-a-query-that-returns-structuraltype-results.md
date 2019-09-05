---
title: 'Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: 635fb20757f359520d292b850b2d554d4972aaab
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251462"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a><span data-ttu-id="031b6-102">Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="031b6-102">How to: Execute a Query that Returns StructuralType Results</span></span>
<span data-ttu-id="031b6-103">Bu konu, bir <xref:System.Data.EntityClient.EntityCommand> nesne kullanarak bir kavramsal modele karşı bir komutun nasıl yürütüleceğini ve bir <xref:System.Data.EntityClient.EntityDataReader>kullanarak <xref:System.Data.Metadata.Edm.StructuralType> sonuçların nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="031b6-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.StructuralType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="031b6-104"><xref:System.Data.Metadata.Edm.EntityType>, Ve<xref:System.Data.Metadata.Edm.RowType> sınıfları sınıfındantüretilir.<xref:System.Data.Metadata.Edm.ComplexType> <xref:System.Data.Metadata.Edm.StructuralType></span><span class="sxs-lookup"><span data-stu-id="031b6-104">The <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> and <xref:System.Data.Metadata.Edm.ComplexType> classes derive from the <xref:System.Data.Metadata.Edm.StructuralType> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="031b6-105">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="031b6-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="031b6-106">Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi kullanmak [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="031b6-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="031b6-107">Daha fazla bilgi için [nasıl yapılır: Varlık Veri Modeli Sihirbazı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="031b6-107">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="031b6-108">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin (`Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="031b6-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="031b6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="031b6-109">Example</span></span>  
 <span data-ttu-id="031b6-110">Bu örnek, sonuçları döndüren <xref:System.Data.Metadata.Edm.EntityType> bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="031b6-110">This example executes a query that returns <xref:System.Data.Metadata.Edm.EntityType> results.</span></span> <span data-ttu-id="031b6-111">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` işleve bağımsız değişken olarak geçirirseniz, işlevi ile `Products`ilgili ayrıntıları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="031b6-111">If you pass the following query as an argument to the `ExecuteStructuralTypeQuery` function, the function displays details about the `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 <span data-ttu-id="031b6-112">Parametreli bir sorgu geçirirseniz, aşağıdaki gibi, <xref:System.Data.EntityClient.EntityParameter> <xref:System.Data.EntityClient.EntityCommand> nesne üzerindeki <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> özelliğine nesneleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="031b6-112">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a><span data-ttu-id="031b6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="031b6-113">See also</span></span>

- [<span data-ttu-id="031b6-114">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="031b6-114">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="031b6-115">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="031b6-115">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)

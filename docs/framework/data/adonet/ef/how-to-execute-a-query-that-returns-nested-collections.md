---
title: 'Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: b3319d3b833ab50ec426c8059bccf818b1407a60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115303"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="027a0-102">Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="027a0-102">How to: Execute a Query that Returns Nested Collections</span></span>
<span data-ttu-id="027a0-103">Bu komut kavramsal modeline karşı kullanarak yürütme gösterilmektedir bir <xref:System.Data.EntityClient.EntityCommand> nesne ve kullanarak iç içe toplama sonuçları almak nasıl bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="027a0-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="027a0-104">Bu örnekte, kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="027a0-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="027a0-105">Ekleme [AdventureWorks satışları modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="027a0-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="027a0-106">Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="027a0-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="027a0-107">Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="027a0-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="027a0-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="027a0-108">Example</span></span>  
 <span data-ttu-id="027a0-109">A *koleksiyon iç içe geçmiş* başka bir koleksiyon içinde olan bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="027a0-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="027a0-110">Aşağıdaki kod bir koleksiyonunu alır `Contacts` ve iç içe geçmiş koleksiyonlarının `SalesOrderHeaders` her ile ilişkili olan `Contact`.</span><span class="sxs-lookup"><span data-stu-id="027a0-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="027a0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="027a0-111">See also</span></span>

- [<span data-ttu-id="027a0-112">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="027a0-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

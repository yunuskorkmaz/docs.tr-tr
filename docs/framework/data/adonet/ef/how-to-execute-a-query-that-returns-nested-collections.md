---
title: 'Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: accbf44c20e52fbce5104721b50bc1650d7fd565
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251492"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="b4a89-102">Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="b4a89-102">How to: Execute a Query that Returns Nested Collections</span></span>
<span data-ttu-id="b4a89-103">Bu, bir <xref:System.Data.EntityClient.EntityCommand> nesne kullanarak bir kavramsal modele karşı bir komutun nasıl yürütüleceğini ve <xref:System.Data.EntityClient.EntityDataReader>kullanarak iç içe geçmiş koleksiyon sonuçlarının nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4a89-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="b4a89-104">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b4a89-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="b4a89-105">Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi kullanmak [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b4a89-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="b4a89-106">Daha fazla bilgi için [nasıl yapılır: Varlık Veri Modeli Sihirbazı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b4a89-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="b4a89-107">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin (`Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="b4a89-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="b4a89-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4a89-108">Example</span></span>  
 <span data-ttu-id="b4a89-109">*İç içe geçmiş koleksiyon* , başka bir koleksiyon içinde olan bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="b4a89-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="b4a89-110">Aşağıdaki kod, bir koleksiyonunu `Contacts` ve her `Contact`biriyle ilişkili iç içe geçmiş `SalesOrderHeaders` koleksiyonları alır.</span><span class="sxs-lookup"><span data-stu-id="b4a89-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="b4a89-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4a89-111">See also</span></span>

- [<span data-ttu-id="b4a89-112">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="b4a89-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)

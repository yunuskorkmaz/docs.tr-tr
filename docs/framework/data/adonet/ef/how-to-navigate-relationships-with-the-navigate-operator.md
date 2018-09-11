---
title: 'Nasıl yapılır: ile ilişkilerde gezinme işleci gidin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: 4327aacf4cb7ec8b30c2f46696e2a19b1b3ae18c
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44352543"
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="e9bf7-102">Nasıl yapılır: ile ilişkilerde gezinme işleci gidin</span><span class="sxs-lookup"><span data-stu-id="e9bf7-102">How to: Navigate Relationships with the Navigate Operator</span></span>
<span data-ttu-id="e9bf7-103">Bu konuda kullanarak kavramsal modeline karşı komut yürütme işlemi gösterilmektedir bir <xref:System.Data.EntityClient.EntityCommand> nesne ve nasıl alınacağını <xref:System.Data.Metadata.Edm.RefType> kullanarak sonuçları bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="e9bf7-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="e9bf7-104">Bu örnekte, kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e9bf7-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="e9bf7-105">Ekleme [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9bf7-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="e9bf7-106">Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="e9bf7-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="e9bf7-107">Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="e9bf7-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="e9bf7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9bf7-108">Example</span></span>  
 <span data-ttu-id="e9bf7-109">Aşağıdaki örnek ilişkilerinde gezinme gösterilmiştir [!INCLUDE[esql](../../../../../includes/esql-md.md)] kullanarak [NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="e9bf7-109">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="e9bf7-110">`Navigate` İşleci aşağıdaki parametreleri alır: bir varlık, ilişki türü, ilişki sonu ile ilişki başına örneği.</span><span class="sxs-lookup"><span data-stu-id="e9bf7-110">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="e9bf7-111">İsteğe bağlı olarak, varlık ve ilişki türü için yalnızca bir örneğini geçirebilirsiniz `Navigate` işleci.</span><span class="sxs-lookup"><span data-stu-id="e9bf7-111">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="e9bf7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9bf7-112">See Also</span></span>  
 [<span data-ttu-id="e9bf7-113">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="e9bf7-113">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [<span data-ttu-id="e9bf7-114">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="e9bf7-114">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)

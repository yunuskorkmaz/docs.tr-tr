---
title: 'Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
ms.openlocfilehash: c9f3b7e19770c89bbb200913bf7fcf44f901ea99
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854583"
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a><span data-ttu-id="3e571-102">Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="3e571-102">How to: Execute a Query that Returns RefType Results</span></span>
<span data-ttu-id="3e571-103">Bu konu, bir <xref:System.Data.EntityClient.EntityCommand> nesne kullanarak bir kavramsal modele karşı bir komutun nasıl yürütüleceğini ve bir <xref:System.Data.EntityClient.EntityDataReader>kullanarak <xref:System.Data.Metadata.Edm.RefType> sonuçların nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e571-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="3e571-104">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3e571-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="3e571-105">Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="3e571-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="3e571-106">Daha fazla bilgi için [nasıl yapılır: Varlık Veri Modeli Sihirbazı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e571-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="3e571-107">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin (`Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="3e571-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="3e571-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e571-108">Example</span></span>  
 <span data-ttu-id="3e571-109">Bu örnek, sonuçları döndüren <xref:System.Data.Metadata.Edm.RefType> bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="3e571-109">This example executes a query that returns <xref:System.Data.Metadata.Edm.RefType> results.</span></span> <span data-ttu-id="3e571-110">Aşağıdaki sorguyu `ExecuteRefTypeQuery` işleve bir bağımsız değişken olarak geçirirseniz, işlev varlığa bir başvuru döndürür:</span><span class="sxs-lookup"><span data-stu-id="3e571-110">If you pass the following query as an argument to the `ExecuteRefTypeQuery` function, the function returns a reference to the entity:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 <span data-ttu-id="3e571-111">Parametreli bir sorgu geçirirseniz, aşağıdaki gibi, <xref:System.Data.EntityClient.EntityParameter> <xref:System.Data.EntityClient.EntityCommand> nesne üzerindeki <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> özelliğine nesneleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3e571-111">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a><span data-ttu-id="3e571-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e571-112">See also</span></span>

- [<span data-ttu-id="3e571-113">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3e571-113">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="3e571-114">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="3e571-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)

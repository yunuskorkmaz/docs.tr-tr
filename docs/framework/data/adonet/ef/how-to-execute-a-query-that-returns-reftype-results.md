---
title: 'Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
ms.openlocfilehash: f3f1e11d3211140abb02733de4b5b46ac93cf769
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317174"
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a><span data-ttu-id="9441e-102">Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="9441e-102">How to: Execute a Query that Returns RefType Results</span></span>
<span data-ttu-id="9441e-103">Bu konuda kullanarak kavramsal modeline karşı komut yürütme işlemi gösterilmektedir bir <xref:System.Data.EntityClient.EntityCommand> nesne ve nasıl alınacağını <xref:System.Data.Metadata.Edm.RefType> kullanarak sonuçları bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="9441e-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="9441e-104">Bu örnekte, kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9441e-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="9441e-105">Ekleme [AdventureWorks satışları modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) projenize ve projenizi kullanmak üzere yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9441e-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="9441e-106">Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9441e-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="9441e-107">Uygulamanız için kod sayfasında, aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="9441e-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="9441e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9441e-108">Example</span></span>  
 <span data-ttu-id="9441e-109">Bu örnek döndüren bir sorgu yürütür <xref:System.Data.Metadata.Edm.RefType> sonuçları.</span><span class="sxs-lookup"><span data-stu-id="9441e-109">This example executes a query that returns <xref:System.Data.Metadata.Edm.RefType> results.</span></span> <span data-ttu-id="9441e-110">Bağımsız değişken olarak aşağıdaki sorguyu geçirirseniz `ExectueRefTypeQuery` işlevi, işlev, varlığa bir başvuru döndürür:</span><span class="sxs-lookup"><span data-stu-id="9441e-110">If you pass the following query as an argument to the `ExectueRefTypeQuery` function, the function returns a reference to the entity:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 <span data-ttu-id="9441e-111">Aşağıdaki gibi parametreli bir sorgu başarılı olursa ekleme <xref:System.Data.EntityClient.EntityParameter> nesneleri için <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> özelliği <xref:System.Data.EntityClient.EntityCommand> nesne.</span><span class="sxs-lookup"><span data-stu-id="9441e-111">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a><span data-ttu-id="9441e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9441e-112">See also</span></span>

- [<span data-ttu-id="9441e-113">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9441e-113">Entity SQL Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="9441e-114">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="9441e-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

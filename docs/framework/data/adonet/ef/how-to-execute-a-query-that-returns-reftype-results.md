---
title: "Nasıl yapılır: RefType sonuçları döndüren bir sorgu yürütme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4e5bb3a3f6cba2cbc9799825e7f608f4c0e636f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a><span data-ttu-id="b71e9-102">Nasıl yapılır: RefType sonuçları döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="b71e9-102">How to: Execute a Query that Returns RefType Results</span></span>
<span data-ttu-id="b71e9-103">Bu konuda kullanarak kavramsal model karşı komut yürütme gösterilmiştir bir <xref:System.Data.EntityClient.EntityCommand> nesne ve nasıl alınacağını <xref:System.Data.Metadata.Edm.RefType> kullanarak sonuçları bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b71e9-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="b71e9-104">Bu örnekte kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b71e9-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="b71e9-105">Ekleme [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) projenize ve kullanmak için projenizin yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b71e9-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="b71e9-106">Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="b71e9-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="b71e9-107">Uygulamanız için kod sayfasında aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="b71e9-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="b71e9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="b71e9-108">Example</span></span>  
 <span data-ttu-id="b71e9-109">Bu örnek döndüren bir sorgu yürütür <xref:System.Data.Metadata.Edm.RefType> sonuçları.</span><span class="sxs-lookup"><span data-stu-id="b71e9-109">This example executes a query that returns <xref:System.Data.Metadata.Edm.RefType> results.</span></span> <span data-ttu-id="b71e9-110">Bağımsız değişken olarak aşağıdaki sorguyu geçirdiğiniz `ExectueRefTypeQuery` işlevi, işlevi varlığa bir başvuru döndürür:</span><span class="sxs-lookup"><span data-stu-id="b71e9-110">If you pass the following query as an argument to the `ExectueRefTypeQuery` function, the function returns a reference to the entity:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 <span data-ttu-id="b71e9-111">Aşağıdaki gibi parametreli bir sorgu başarılı olursa eklemek <xref:System.Data.EntityClient.EntityParameter> nesneleri <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> özellikte <xref:System.Data.EntityClient.EntityCommand> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b71e9-111">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a><span data-ttu-id="b71e9-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b71e9-112">See Also</span></span>  
 [<span data-ttu-id="b71e9-113">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b71e9-113">Entity SQL Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="b71e9-114">Entity Framework için EntityClient sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="b71e9-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

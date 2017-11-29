---
title: "Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme"
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
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b786fb54d8e588173cf79a5020f96c6a68ddecf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a><span data-ttu-id="cb8b9-102">Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="cb8b9-102">How to: Execute a Query that Returns StructuralType Results</span></span>
<span data-ttu-id="cb8b9-103">Bu konuda kullanarak kavramsal model karşı komut yürütme gösterilmiştir bir <xref:System.Data.EntityClient.EntityCommand> nesne ve nasıl alınacağını <xref:System.Data.Metadata.Edm.StructuralType> kullanarak sonuçları bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="cb8b9-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.StructuralType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="cb8b9-104"><xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> Ve <xref:System.Data.Metadata.Edm.ComplexType> sınıfları türetilen <xref:System.Data.Metadata.Edm.StructuralType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cb8b9-104">The <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> and <xref:System.Data.Metadata.Edm.ComplexType> classes derive from the <xref:System.Data.Metadata.Edm.StructuralType> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="cb8b9-105">Bu örnekte kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cb8b9-105">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="cb8b9-106">Ekleme [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) projenize ve kullanmak için projenizin yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb8b9-106">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="cb8b9-107">Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="cb8b9-107">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="cb8b9-108">Uygulamanız için kod sayfasında aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="cb8b9-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="cb8b9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb8b9-109">Example</span></span>  
 <span data-ttu-id="cb8b9-110">Bu örnek döndüren bir sorgu yürütür <xref:System.Data.Metadata.Edm.EntityType> sonuçları.</span><span class="sxs-lookup"><span data-stu-id="cb8b9-110">This example executes a query that returns <xref:System.Data.Metadata.Edm.EntityType> results.</span></span> <span data-ttu-id="cb8b9-111">Bağımsız değişken olarak aşağıdaki sorguyu geçirdiğiniz `ExecuteStructuralTypeQuery` işlevi, işlevi görüntüler ayrıntılar hakkında `Products`:</span><span class="sxs-lookup"><span data-stu-id="cb8b9-111">If you pass the following query as an argument to the `ExecuteStructuralTypeQuery` function, the function displays details about the `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 <span data-ttu-id="cb8b9-112">Aşağıdaki gibi parametreli bir sorgu başarılı olursa eklemek <xref:System.Data.EntityClient.EntityParameter> nesneleri <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> özellikte <xref:System.Data.EntityClient.EntityCommand> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cb8b9-112">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a><span data-ttu-id="cb8b9-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb8b9-113">See Also</span></span>  
 [<span data-ttu-id="cb8b9-114">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cb8b9-114">Entity SQL Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="cb8b9-115">Entity Framework için EntityClient sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="cb8b9-115">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

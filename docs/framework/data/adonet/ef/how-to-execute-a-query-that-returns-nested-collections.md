---
title: "Nasıl yapılır: iç içe geçmiş koleksiyonları döndüren bir sorgu yürütme"
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
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cb299566678b19194b3144c6a9f1f3a288fd67ba
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="d674c-102">Nasıl yapılır: iç içe geçmiş koleksiyonları döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="d674c-102">How to: Execute a Query that Returns Nested Collections</span></span>
<span data-ttu-id="d674c-103">Bu komut kavramsal model karşı kullanarak yürütme gösterilmiştir bir <xref:System.Data.EntityClient.EntityCommand> nesne ve kullanarak iç içe toplama sonuçları almak nasıl bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d674c-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="d674c-104">Bu örnekte kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d674c-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="d674c-105">Ekleme [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) projenize ve kullanmak için projenizin yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d674c-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="d674c-106">Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="d674c-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="d674c-107">Uygulamanız için kod sayfasında aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="d674c-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="d674c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d674c-108">Example</span></span>  
 <span data-ttu-id="d674c-109">A *iç içe toplama* içinde başka bir koleksiyonu bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="d674c-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="d674c-110">Aşağıdaki kod bir koleksiyonunu alır `Contacts` ve iç içe geçmiş koleksiyonları `SalesOrderHeaders` her ile ilişkili olan `Contact`.</span><span class="sxs-lookup"><span data-stu-id="d674c-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="d674c-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d674c-111">See Also</span></span>  
 [<span data-ttu-id="d674c-112">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="d674c-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)

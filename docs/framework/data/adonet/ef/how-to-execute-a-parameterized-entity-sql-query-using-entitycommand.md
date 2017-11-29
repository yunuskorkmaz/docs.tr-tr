---
title: "Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme"
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
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1531e18a6be3e7ab5c0cec4f19f33692fd04383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="0ba5c-102">Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme</span><span class="sxs-lookup"><span data-stu-id="0ba5c-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="0ba5c-103">Bu konuda nasıl yürütüleceği gösterilmektedir bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] kullanarak parametreye sahip sorgu bir <xref:System.Data.EntityClient.EntityCommand> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0ba5c-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="0ba5c-104">Bu örnekte kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0ba5c-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="0ba5c-105">Ekleme [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) projenize ve kullanmak için projenizin yapılandırma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0ba5c-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="0ba5c-106">Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="0ba5c-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="0ba5c-107">Uygulamanız için kod sayfasında aşağıdakileri ekleyin `using` deyimleri (`Imports` Visual Basic'te):</span><span class="sxs-lookup"><span data-stu-id="0ba5c-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="0ba5c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ba5c-108">Example</span></span>  
 <span data-ttu-id="0ba5c-109">Aşağıdaki örnekte, iki parametreli bir sorgu dizesi oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0ba5c-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="0ba5c-110">Daha sonra oluşturur bir <xref:System.Data.EntityClient.EntityCommand>, iki parametreyi ekler <xref:System.Data.EntityClient.EntityParameter> , koleksiyonunu <xref:System.Data.EntityClient.EntityCommand>ve toplulukta tekrarlanan `Contact` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0ba5c-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="0ba5c-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba5c-111">See Also</span></span>  
 [<span data-ttu-id="0ba5c-112">Nasıl yapılır: parametreleştirilmiş sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="0ba5c-112">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
 [<span data-ttu-id="0ba5c-113">Varlık SQL dili</span><span class="sxs-lookup"><span data-stu-id="0ba5c-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)

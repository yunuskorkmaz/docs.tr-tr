---
title: 'Nasıl yapılır: EntityCommand Kullanarak Parametreli Entity SQL Sorgusu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: 24b24e4c35c85edb1f960ae18a58cbc5893690d0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536229"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="b028d-102">Nasıl yapılır: EntityCommand Kullanarak Parametreli Entity SQL Sorgusu Yürütme</span><span class="sxs-lookup"><span data-stu-id="b028d-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="b028d-103">Bu konu [!INCLUDE[esql](../../../../../includes/esql-md.md)] , bir nesnesi kullanarak parametreleri olan bir sorgunun nasıl yürütüleceğini gösterir <xref:System.Data.EntityClient.EntityCommand> .</span><span class="sxs-lookup"><span data-stu-id="b028d-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="b028d-104">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b028d-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="b028d-105">Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b028d-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="b028d-106">Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b028d-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="b028d-107">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="b028d-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="b028d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="b028d-108">Example</span></span>  
 <span data-ttu-id="b028d-109">Aşağıdaki örnek, iki parametreli bir sorgu dizesi oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b028d-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="b028d-110">Daha sonra bir oluşturur <xref:System.Data.EntityClient.EntityCommand> , bunun koleksiyonuna iki parametre ekler <xref:System.Data.EntityClient.EntityParameter> <xref:System.Data.EntityClient.EntityCommand> ve öğe koleksiyonunda yinelenir `Contact` .</span><span class="sxs-lookup"><span data-stu-id="b028d-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="b028d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b028d-111">See also</span></span>

- <span data-ttu-id="b028d-112">[Nasıl yapılır: Parametreli sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b028d-112">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- [<span data-ttu-id="b028d-113">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="b028d-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)

---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme'
title: 'Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: a5666fd84ed7253b58cc49babdfa5f5e4614146c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697549"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a><span data-ttu-id="f67d9-103">Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="f67d9-103">How to: Execute a Query that Returns StructuralType Results</span></span>

<span data-ttu-id="f67d9-104">Bu konu, bir nesne kullanarak bir kavramsal modele karşı bir komutun nasıl yürütüleceğini <xref:System.Data.EntityClient.EntityCommand> ve <xref:System.Data.Metadata.Edm.StructuralType> bir kullanarak sonuçların nasıl alınacağını gösterir <xref:System.Data.EntityClient.EntityDataReader> .</span><span class="sxs-lookup"><span data-stu-id="f67d9-104">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.StructuralType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="f67d9-105"><xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> Ve <xref:System.Data.Metadata.Edm.ComplexType> sınıfları sınıfından türetilir <xref:System.Data.Metadata.Edm.StructuralType> .</span><span class="sxs-lookup"><span data-stu-id="f67d9-105">The <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> and <xref:System.Data.Metadata.Edm.ComplexType> classes derive from the <xref:System.Data.Metadata.Edm.StructuralType> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="f67d9-106">Bu örnekteki kodu çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f67d9-106">To run the code in this example</span></span>  
  
1. <span data-ttu-id="f67d9-107">Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f67d9-107">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="f67d9-108">Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f67d9-108">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="f67d9-109">Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="f67d9-109">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="f67d9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f67d9-110">Example</span></span>  

 <span data-ttu-id="f67d9-111">Bu örnek, sonuçları döndüren bir sorgu yürütür <xref:System.Data.Metadata.Edm.EntityType> .</span><span class="sxs-lookup"><span data-stu-id="f67d9-111">This example executes a query that returns <xref:System.Data.Metadata.Edm.EntityType> results.</span></span> <span data-ttu-id="f67d9-112">Aşağıdaki sorguyu işleve bağımsız değişken olarak geçirirseniz `ExecuteStructuralTypeQuery` , işlevi ile ilgili ayrıntıları görüntüler `Products` :</span><span class="sxs-lookup"><span data-stu-id="f67d9-112">If you pass the following query as an argument to the `ExecuteStructuralTypeQuery` function, the function displays details about the `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 <span data-ttu-id="f67d9-113">Parametreli bir sorgu geçirirseniz, aşağıdaki gibi, <xref:System.Data.EntityClient.EntityParameter> <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> nesne üzerindeki özelliğine nesneleri ekleyin <xref:System.Data.EntityClient.EntityCommand> .</span><span class="sxs-lookup"><span data-stu-id="f67d9-113">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a><span data-ttu-id="f67d9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f67d9-114">See also</span></span>

- [<span data-ttu-id="f67d9-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f67d9-115">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="f67d9-116">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="f67d9-116">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)

---
title: "Nasıl yapılır: Model tarafından tanımlanan işlevler sorgularda çağırın"
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
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ec20542ad452bcefbe2b6d286e68ad8bbfb5adb9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="a0573-102">Nasıl yapılır: Model tarafından tanımlanan işlevler sorgularda çağırın</span><span class="sxs-lookup"><span data-stu-id="a0573-102">How to: Call Model-Defined Functions in Queries</span></span>
<span data-ttu-id="a0573-103">Bu konuda içinden kavramsal modelde tanımlanan işlevleri çağırmak nasıl açıklanmaktadır [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="a0573-103">This topic describes how to call functions that are defined in the conceptual model from within [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="a0573-104">Model tanımlı bir işlevin içinden çağırmak için aşağıdaki yordamı İleri düzey bir özeti sağlayan bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="a0573-104">The procedure below provides a high-level outline for calling a model-defined function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="a0573-105">Aşağıdaki örnek yordamdaki adımları hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0573-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="a0573-106">Yordam, kavramsal modelde tanımlanan bir işlev varsayar.</span><span class="sxs-lookup"><span data-stu-id="a0573-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="a0573-107">Daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span><span class="sxs-lookup"><span data-stu-id="a0573-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="a0573-108">Kavramsal modelde tanımlanan bir işlev çağrısı için</span><span class="sxs-lookup"><span data-stu-id="a0573-108">To call a function defined in the conceptual model</span></span>  
  
1.  <span data-ttu-id="a0573-109">Kavramsal modelde tanımlanmış işlevi eşlendiği uygulamanız için bir ortak dil çalışma zamanı (CLR) yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a0573-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="a0573-110">Map yöntemi için uygulamanız gereken bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a0573-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="a0573-111">Unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> öznitelik parametrelerinin kavramsal model ad alanı adını ve kavramsal modelde işlev adı sırasıyla verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a0573-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="a0573-112">İşlevi ad çözümlemesi LINQ için büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="a0573-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2.  <span data-ttu-id="a0573-113">İşlev çağrısı bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="a0573-113">Call the function in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0573-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0573-114">Example</span></span>  
 <span data-ttu-id="a0573-115">Aşağıdaki örnek içinden kavramsal modelde tanımlanan bir işlev nasıl çağırılacağını bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="a0573-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="a0573-116">Örneğin Okul modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0573-116">The example uses the School model.</span></span> <span data-ttu-id="a0573-117">Okul modeli hakkında daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) ve [Okul .edmx dosyasının oluşturma](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="a0573-117">For information about the School model, see [Creating the School Sample Database](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="a0573-118">Bir eğitmen işe beri aşağıdaki kavramsal model işlevi yıl sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0573-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="a0573-119">Kavramsal bir model işlevi ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span><span class="sxs-lookup"><span data-stu-id="a0573-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="a0573-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0573-120">Example</span></span>  
 <span data-ttu-id="a0573-121">Ardından, uygulama ve kullanmak için aşağıdaki yöntemi ekleyin bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> kavramsal model işlevi eşlemek için:</span><span class="sxs-lookup"><span data-stu-id="a0573-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="a0573-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0573-122">Example</span></span>  
 <span data-ttu-id="a0573-123">Kavramsal model işlevi içinden çağırabilirsiniz artık bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="a0573-123">Now you can call the conceptual model function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="a0573-124">Aşağıdaki kod, on yıldan fazla önce işe alınan tüm Eğitmen görüntülenecek yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="a0573-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a0573-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0573-125">See Also</span></span>  
 [<span data-ttu-id="a0573-126">.edmx dosyasının genel bakış</span><span class="sxs-lookup"><span data-stu-id="a0573-126">.edmx File Overview</span></span>](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="a0573-127">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="a0573-127">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="a0573-128">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a0573-128">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="a0573-129">Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="a0573-129">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)

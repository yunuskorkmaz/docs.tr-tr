---
title: 'Nasıl Yapılır: Sorgularda Model Tanımlı İşlevler Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: b142ef820e964eaf5f1afed53a6b12a9344c7dda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189337"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="92d2a-102">Nasıl Yapılır: Sorgularda Model Tanımlı İşlevler Çağırma</span><span class="sxs-lookup"><span data-stu-id="92d2a-102">How to: Call Model-Defined Functions in Queries</span></span>

<span data-ttu-id="92d2a-103">Bu konu, LINQ to Entities sorguları içinden kavramsal modelde tanımlanan işlevlerin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="92d2a-103">This topic describes how to call functions that are defined in the conceptual model from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="92d2a-104">Aşağıdaki yordam, bir LINQ to Entities sorgusunun içinden model tanımlı bir işlevi çağırmak için üst düzey bir ana hat sağlar.</span><span class="sxs-lookup"><span data-stu-id="92d2a-104">The procedure below provides a high-level outline for calling a model-defined function from within a LINQ to Entities query.</span></span> <span data-ttu-id="92d2a-105">Aşağıdaki örnek, yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="92d2a-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="92d2a-106">Yordam, kavramsal modelde bir işlevi tanımladığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="92d2a-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="92d2a-107">Daha fazla bilgi için bkz. [nasıl yapılır: kavramsal modelde özel Işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="92d2a-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="92d2a-108">Kavramsal modelde tanımlanan bir işlevi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="92d2a-108">To call a function defined in the conceptual model</span></span>  
  
1. <span data-ttu-id="92d2a-109">Uygulamanıza, kavramsal modelde tanımlanan işlevle eşlenen bir ortak dil çalışma zamanı (CLR) yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92d2a-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="92d2a-110">Yöntemi eşlemek için bir yöntemine uygulamanız gerekir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="92d2a-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="92d2a-111"><xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A>Özniteliğin ve parametrelerinin, kavramsal modelin <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> ad alanı adı ve kavramsal modeldeki işlev adı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="92d2a-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="92d2a-112">LINQ için işlev adı çözümlemesi büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="92d2a-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2. <span data-ttu-id="92d2a-113">İşlevi bir LINQ to Entities sorgusunda çağırın.</span><span class="sxs-lookup"><span data-stu-id="92d2a-113">Call the function in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92d2a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="92d2a-114">Example</span></span>  

 <span data-ttu-id="92d2a-115">Aşağıdaki örnek, LINQ to Entities sorgusunun içinde kavramsal modelde tanımlanan bir işlevin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92d2a-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a LINQ to Entities query.</span></span> <span data-ttu-id="92d2a-116">Örnek, okul modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="92d2a-116">The example uses the School model.</span></span> <span data-ttu-id="92d2a-117">Okul modeli hakkında daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) ve [okul. edmx dosyası](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))oluşturma.</span><span class="sxs-lookup"><span data-stu-id="92d2a-117">For information about the School model, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="92d2a-118">Aşağıdaki kavramsal model işlevi, bir eğitmenin işe başlamasından bu yana yıl sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="92d2a-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="92d2a-119">Bir kavramsal modele işlev ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: kavramsal modelde özel Işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span><span class="sxs-lookup"><span data-stu-id="92d2a-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="92d2a-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="92d2a-120">Example</span></span>  

 <span data-ttu-id="92d2a-121">Ardından, uygulamanıza aşağıdaki yöntemi ekleyin ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> bunu kavramsal model işleviyle eşlemek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="92d2a-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="92d2a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="92d2a-122">Example</span></span>  

 <span data-ttu-id="92d2a-123">Artık kavramsal model işlevini bir LINQ to Entities sorgusunun içinden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92d2a-123">Now you can call the conceptual model function from within a LINQ to Entities query.</span></span> <span data-ttu-id="92d2a-124">Aşağıdaki kod, on yıldan daha önce işe alınan tüm eğitmenleri göstermek için yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="92d2a-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="92d2a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92d2a-125">See also</span></span>

- <span data-ttu-id="92d2a-126">[. edmx dosyasına genel bakış](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="92d2a-126">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="92d2a-127">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="92d2a-127">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="92d2a-128">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="92d2a-128">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="92d2a-129">Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="92d2a-129">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)

---
title: "Nasıl yapılır: çağrı nesne yöntemleri olarak modeli tarafından tanımlanan İşlevler"
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
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a934cd8c122a1564c034f8578e8bad680ba919a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a><span data-ttu-id="801ce-102">Nasıl yapılır: çağrı nesne yöntemleri olarak modeli tarafından tanımlanan İşlevler</span><span class="sxs-lookup"><span data-stu-id="801ce-102">How to: Call Model-Defined Functions as Object Methods</span></span>
<span data-ttu-id="801ce-103">Bu konu, bir yöntem olarak model tanımlı bir işlevi çağırmak açıklar bir <xref:System.Data.Objects.ObjectContext> nesne veya özel bir sınıf bir statik yöntem olarak.</span><span class="sxs-lookup"><span data-stu-id="801ce-103">This topic describes how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object or as a static method on a custom class.</span></span> <span data-ttu-id="801ce-104">A *modeli tanımlı işlev* kavramsal modelde tanımlanan bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="801ce-104">A *model-defined function* is a function that is defined in the conceptual model.</span></span> <span data-ttu-id="801ce-105">Konudaki yordamlar, bunları Entities sorgularında LINQ çağırmak yerine doğrudan bu işlevleri çağırmak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="801ce-105">The procedures in the topic describe how to call these functions directly instead of calling them from LINQ to Entities queries.</span></span> <span data-ttu-id="801ce-106">Model tanımlı işlevler LINQ to Entities sorgularında çağırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: sorgularda Call Model-Defined işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).</span><span class="sxs-lookup"><span data-stu-id="801ce-106">For information about calling model-defined functions in LINQ to Entities queries, see [How to: Call Model-Defined Functions in Queries](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).</span></span>  
  
 <span data-ttu-id="801ce-107">Model tanımlı bir işlev olarak çağrısı bir <xref:System.Data.Objects.ObjectContext> yöntemi veya özel bir sınıf bir statik yöntem, ilk yöntemi modeli tanımlı işlev eşleme yapmalısınız bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="801ce-107">Whether you call a model-defined function as an <xref:System.Data.Objects.ObjectContext> method or as a static method on a custom class, you must first map the method to the model-defined function with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="801ce-108">Ancak, tanımladığınızda bir yöntem üzerinde <xref:System.Data.Objects.ObjectContext> sınıfı kullanmanız gerekir <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> ancak bir statik yöntem özel bir sınıf tanımladığınızda, kullanmalıdır LINQ sağlayıcıyı gösterme özelliği <xref:System.Linq.IQueryable.Provider%2A> özelliği LINQ sağlayıcıyı gösterme.</span><span class="sxs-lookup"><span data-stu-id="801ce-108">However, when you define a method on the <xref:System.Data.Objects.ObjectContext> class, you must use the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property to expose the LINQ provider, whereas when you define a static method on a custom class, you must use the <xref:System.Linq.IQueryable.Provider%2A> property to expose the LINQ provider.</span></span> <span data-ttu-id="801ce-109">Daha fazla bilgi için aşağıdaki yordamları izleyin örneklere bakın.</span><span class="sxs-lookup"><span data-stu-id="801ce-109">For more information, see the examples that follow the procedures below.</span></span>  
  
 <span data-ttu-id="801ce-110">Model tanımlı bir işlev üzerinde bir yöntem olarak çağırmak için aşağıdaki yordamları üst düzey ana hatlarını sağlamak bir <xref:System.Data.Objects.ObjectContext> nesne ve özel bir sınıf bir statik yöntem olarak.</span><span class="sxs-lookup"><span data-stu-id="801ce-110">The procedures below provide high-level outlines for calling a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object and as a static method on a custom class.</span></span> <span data-ttu-id="801ce-111">Aşağıdaki örnekler yordamlarda bulunan adımları hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="801ce-111">The examples that follow provide more detail about the steps in the procedures.</span></span> <span data-ttu-id="801ce-112">Yordamlar, kavramsal modelde tanımlanan bir işlev varsayar.</span><span class="sxs-lookup"><span data-stu-id="801ce-112">The procedures assume that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="801ce-113">Daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span><span class="sxs-lookup"><span data-stu-id="801ce-113">For more information, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a><span data-ttu-id="801ce-114">Bir ObjectContext nesnesinde bir yöntem olarak model tanımlı bir işlevi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="801ce-114">To call a model-defined function as a method on an ObjectContext object</span></span>  
  
1.  <span data-ttu-id="801ce-115">Türetilen parçalı sınıf genişletmek için kaynak dosyası ekleme <xref:System.Data.Objects.ObjectContext> Entity Framework araçları tarafından otomatik olarak oluşturulan sınıf.</span><span class="sxs-lookup"><span data-stu-id="801ce-115">Add a source file to extend the partial class derived from the <xref:System.Data.Objects.ObjectContext> class, auto-generated by the Entity Framework tools.</span></span> <span data-ttu-id="801ce-116">CLR saplama ayrı bir kaynak dosyasında tanımlama değişiklikleri dosyayı yeniden üretildiğinde kaybolur engeller.</span><span class="sxs-lookup"><span data-stu-id="801ce-116">Defining the CLR stub in a separate source file will prevent the changes from being lost when the file is regenerated.</span></span>  
  
2.  <span data-ttu-id="801ce-117">Ortak dil çalışma zamanı (CLR) yöntemine ekleyin, <xref:System.Data.Objects.ObjectContext> sınıfı şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="801ce-117">Add a common language runtime (CLR) method to your <xref:System.Data.Objects.ObjectContext> class that does the following:</span></span>  
  
    -   <span data-ttu-id="801ce-118">Kavramsal modelde tanımlanmış işlevi eşlenir.</span><span class="sxs-lookup"><span data-stu-id="801ce-118">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="801ce-119">Map yöntemi için uygulamanız gereken bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="801ce-119">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="801ce-120">Unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> özniteliğinin parametreleridir kavramsal model ad alanı adını ve kavramsal modelde işlev adı sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="801ce-120">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span> <span data-ttu-id="801ce-121">İşlevi ad çözümlemesi LINQ için büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="801ce-121">Function name resolution for LINQ is case sensitive.</span></span>  
  
    -   <span data-ttu-id="801ce-122">Sonuçlarını döndürür <xref:System.Linq.IQueryProvider.Execute%2A> tarafından döndürülen yöntemi <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="801ce-122">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property.</span></span>  
  
3.  <span data-ttu-id="801ce-123">Örneğindeki bir üye olarak yöntemi çağırma <xref:System.Data.Objects.ObjectContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="801ce-123">Call the method as a member on an instance of the <xref:System.Data.Objects.ObjectContext> class.</span></span>  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a><span data-ttu-id="801ce-124">Özel bir sınıf üzerinde statik yöntemi olarak model tanımlı bir işlevi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="801ce-124">To call a model-defined function as static method on a custom class</span></span>  
  
1.  <span data-ttu-id="801ce-125">Bir sınıf uygulamanız için şunları yapar için statik bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="801ce-125">Add a class to your application with a static method that does the following:</span></span>  
  
    -   <span data-ttu-id="801ce-126">Kavramsal modelde tanımlanmış işlevi eşlenir.</span><span class="sxs-lookup"><span data-stu-id="801ce-126">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="801ce-127">Map yöntemi için uygulamanız gereken bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="801ce-127">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="801ce-128">Unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> özniteliğinin parametreleridir kavramsal model ad alanı adını ve kavramsal modelde işlev adı sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="801ce-128">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span>  
  
    -   <span data-ttu-id="801ce-129">Kabul eden bir <xref:System.Linq.IQueryable> bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="801ce-129">Accepts an <xref:System.Linq.IQueryable> argument.</span></span>  
  
    -   <span data-ttu-id="801ce-130">Sonuçlarını döndürür <xref:System.Linq.IQueryProvider.Execute%2A> tarafından döndürülen yöntemi <xref:System.Linq.IQueryable.Provider%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="801ce-130">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Linq.IQueryable.Provider%2A> property.</span></span>  
  
2.  <span data-ttu-id="801ce-131">Yöntemi bir üye olarak bir statik yöntem çağrı üzerinde özel sınıfı</span><span class="sxs-lookup"><span data-stu-id="801ce-131">Call the method as a member a static method on the custom class</span></span>  
  
## <a name="example"></a><span data-ttu-id="801ce-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="801ce-132">Example</span></span>  
 <span data-ttu-id="801ce-133">**Bir ObjectContext nesnesinde bir yöntem olarak Model tanımlı bir işlev çağırma**</span><span class="sxs-lookup"><span data-stu-id="801ce-133">**Calling a Model-Defined Function as a Method on an ObjectContext Object**</span></span>  
  
 <span data-ttu-id="801ce-134">Aşağıdaki örnek, bir yöntem olarak model tanımlı bir işlevi çağırmak gösterilmiştir bir <xref:System.Data.Objects.ObjectContext> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="801ce-134">The following example demonstrates how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object.</span></span> <span data-ttu-id="801ce-135">Örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="801ce-135">The example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span>  
  
 <span data-ttu-id="801ce-136">Belirtilen ürün için ürün geliri aşağıdan kavramsal model işlevi döndürür göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="801ce-136">Consider the conceptual model function below that returns product revenue for a specified product.</span></span> <span data-ttu-id="801ce-137">(Kavramsal modelinizi işlevi ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span><span class="sxs-lookup"><span data-stu-id="801ce-137">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a><span data-ttu-id="801ce-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="801ce-138">Example</span></span>  
 <span data-ttu-id="801ce-139">Aşağıdaki kod, bir yönteme ekler `AdventureWorksEntities` kavramsal model işlevi yukarıdaki eşleyen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="801ce-139">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="801ce-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="801ce-140">Example</span></span>  
 <span data-ttu-id="801ce-141">Aşağıdaki kod, belirtilen ürün için ürün geliri görüntülemek için yukarıdaki yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="801ce-141">The following code calls the method above to display the product revenue for a specified product:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="801ce-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="801ce-142">Example</span></span>  
 <span data-ttu-id="801ce-143">Aşağıdaki örnek bir koleksiyon döndürür modeli tanımlı bir işlevi çağırmak nasıl gösterir (olarak bir <xref:System.Linq.IQueryable%601> nesnesi).</span><span class="sxs-lookup"><span data-stu-id="801ce-143">The following example demonstrates how to call a model-defined function that returns a collection (as an <xref:System.Linq.IQueryable%601> object).</span></span> <span data-ttu-id="801ce-144">Tüm döndüren kavramsal model işlevi aşağıdaki göz önünde bulundurun `SalesOrderDetails` verilen ürün kimliği için</span><span class="sxs-lookup"><span data-stu-id="801ce-144">Consider the conceptual model function below that returns all the `SalesOrderDetails` for a given product ID.</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a><span data-ttu-id="801ce-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="801ce-145">Example</span></span>  
 <span data-ttu-id="801ce-146">Aşağıdaki kod, bir yönteme ekler `AdventureWorksEntities` kavramsal model işlevi yukarıdaki eşleyen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="801ce-146">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="801ce-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="801ce-147">Example</span></span>  
 <span data-ttu-id="801ce-148">Aşağıdaki kod yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="801ce-148">The following code calls the method.</span></span> <span data-ttu-id="801ce-149">Unutmayın döndürülen <xref:System.Linq.IQueryable%601> sorgu satır toplamları her biri için döndürmek için iyileştirilmiştir daha fazla `SalesOrderDetail`.</span><span class="sxs-lookup"><span data-stu-id="801ce-149">Note that the returned <xref:System.Linq.IQueryable%601> query is further refined to return line totals for each `SalesOrderDetail`.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="801ce-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="801ce-150">Example</span></span>  
 <span data-ttu-id="801ce-151">**Özel bir sınıf bir statik yöntem olarak Model tanımlı bir işlev çağırma**</span><span class="sxs-lookup"><span data-stu-id="801ce-151">**Calling a Model-Defined Function as a Static Method on a Custom Class**</span></span>  
  
 <span data-ttu-id="801ce-152">Sonraki örnek, bir statik yöntem özel bir sınıf olarak model tanımlı bir işlevi çağırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="801ce-152">The next example demonstrates how to call a model-defined function as a static method on a custom class.</span></span> <span data-ttu-id="801ce-153">Örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="801ce-153">The example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="801ce-154">Özel bir sınıf bir statik yöntem olarak model tanımlı bir işlev çağırdığınızda, model tanımlı işlevi bir koleksiyon kabul edip değerlerin bir toplama koleksiyonda dönün gerekir.</span><span class="sxs-lookup"><span data-stu-id="801ce-154">When you call a model-defined function as a static method on a custom class, the model-defined function must accept a collection and return an aggregation of values in the collection.</span></span>  
  
 <span data-ttu-id="801ce-155">Bir satış siparişi ayrıntısını koleksiyon için ürün geliri aşağıdan kavramsal model işlevi döndürür göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="801ce-155">Consider the conceptual model function below that returns product revenue for a SalesOrderDetail collection.</span></span> <span data-ttu-id="801ce-156">(Kavramsal modelinizi işlevi ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).).</span><span class="sxs-lookup"><span data-stu-id="801ce-156">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).).</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="801ce-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="801ce-157">Example</span></span>  
 <span data-ttu-id="801ce-158">Aşağıdaki kod, kavramsal model işlevi yukarıdaki eşleyen bir statik yöntem içerir ve uygulamanıza bir sınıf ekler.</span><span class="sxs-lookup"><span data-stu-id="801ce-158">The following code adds a class to your application that contains a static method that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="801ce-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="801ce-159">Example</span></span>  
 <span data-ttu-id="801ce-160">Aşağıdaki kod, bir satış siparişi ayrıntısını koleksiyon için ürün geliri görüntülemek için yukarıdaki yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="801ce-160">The following code calls the method above to display the product revenue for a SalesOrderDetail collection:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="801ce-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="801ce-161">See Also</span></span>  
 [<span data-ttu-id="801ce-162">.edmx dosyasının genel bakış</span><span class="sxs-lookup"><span data-stu-id="801ce-162">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="801ce-163">LINQ to Entities sorguları</span><span class="sxs-lookup"><span data-stu-id="801ce-163">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="801ce-164">LINQ to Entities sorgularında işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="801ce-164">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)

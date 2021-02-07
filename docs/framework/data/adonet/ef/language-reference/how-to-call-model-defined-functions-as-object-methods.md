---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Model-Defined Işlevlerini nesne yöntemleri olarak çağırma'
title: 'Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 46f171d5785bf715382e87c3fb7dae932db0bb65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748680"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a><span data-ttu-id="0898b-103">Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="0898b-103">How to: Call Model-Defined Functions as Object Methods</span></span>

<span data-ttu-id="0898b-104">Bu konu, model tanımlı bir işlevin bir <xref:System.Data.Objects.ObjectContext> nesne veya özel bir sınıfta statik bir yöntem olarak nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0898b-104">This topic describes how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object or as a static method on a custom class.</span></span> <span data-ttu-id="0898b-105">*Model tanımlı bir işlev* , kavramsal modelde tanımlanan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="0898b-105">A *model-defined function* is a function that is defined in the conceptual model.</span></span> <span data-ttu-id="0898b-106">Konusundaki yordamlar, LINQ to Entities sorgulardan onları çağırmak yerine, bu işlevlerin doğrudan nasıl çağrılacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="0898b-106">The procedures in the topic describe how to call these functions directly instead of calling them from LINQ to Entities queries.</span></span> <span data-ttu-id="0898b-107">LINQ to Entities sorgularda model tanımlı işlevleri çağırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: sorgularda Model-Defined Işlevleri çağırma](how-to-call-model-defined-functions-in-queries.md).</span><span class="sxs-lookup"><span data-stu-id="0898b-107">For information about calling model-defined functions in LINQ to Entities queries, see [How to: Call Model-Defined Functions in Queries](how-to-call-model-defined-functions-in-queries.md).</span></span>  
  
 <span data-ttu-id="0898b-108">Model tanımlı bir işlevi bir <xref:System.Data.Objects.ObjectContext> Yöntem olarak veya özel bir sınıfta statik bir yöntem olarak çağırdığınıza göre, öncelikle yöntemi ile model tanımlı işlev ile eşlemeniz gerekir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0898b-108">Whether you call a model-defined function as an <xref:System.Data.Objects.ObjectContext> method or as a static method on a custom class, you must first map the method to the model-defined function with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="0898b-109">Ancak, sınıfında bir yöntemi tanımladığınızda <xref:System.Data.Objects.ObjectContext> , <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> LINQ sağlayıcısını göstermek için özelliğini kullanmanız gerekir, ancak özel bir sınıfta statik bir yöntem TANıMLADıĞıNıZDA, <xref:System.Linq.IQueryable.Provider%2A> LINQ sağlayıcısını göstermek için özelliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0898b-109">However, when you define a method on the <xref:System.Data.Objects.ObjectContext> class, you must use the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property to expose the LINQ provider, whereas when you define a static method on a custom class, you must use the <xref:System.Linq.IQueryable.Provider%2A> property to expose the LINQ provider.</span></span> <span data-ttu-id="0898b-110">Daha fazla bilgi için aşağıdaki yordamları izleyen örneklere bakın.</span><span class="sxs-lookup"><span data-stu-id="0898b-110">For more information, see the examples that follow the procedures below.</span></span>  
  
 <span data-ttu-id="0898b-111">Aşağıdaki yordamlar, model tanımlı bir işlevi bir nesne üzerinde yöntem olarak <xref:System.Data.Objects.ObjectContext> ve özel bir sınıfta statik bir yöntem olarak çağırmak için üst düzey anahatlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0898b-111">The procedures below provide high-level outlines for calling a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object and as a static method on a custom class.</span></span> <span data-ttu-id="0898b-112">Aşağıdaki örneklerde, yordamlardaki adımlar hakkında daha fazla ayrıntı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0898b-112">The examples that follow provide more detail about the steps in the procedures.</span></span> <span data-ttu-id="0898b-113">Yordamlar, kavramsal modelde bir işlevi tanımladığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="0898b-113">The procedures assume that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="0898b-114">Daha fazla bilgi için bkz. [nasıl yapılır: kavramsal modelde özel Işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0898b-114">For more information, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a><span data-ttu-id="0898b-115">Bir ObjectContext nesnesinde model tanımlı bir işlevi bir yöntem olarak çağırmak için</span><span class="sxs-lookup"><span data-stu-id="0898b-115">To call a model-defined function as a method on an ObjectContext object</span></span>  
  
1. <span data-ttu-id="0898b-116"><xref:System.Data.Objects.ObjectContext>Entity Framework araçları tarafından otomatik olarak oluşturulan sınıftan türetilmiş kısmi sınıfı genişletmek için bir kaynak dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0898b-116">Add a source file to extend the partial class derived from the <xref:System.Data.Objects.ObjectContext> class, auto-generated by the Entity Framework tools.</span></span> <span data-ttu-id="0898b-117">CLR Saplamasının ayrı bir kaynak dosyasında tanımlanması, dosyanın yeniden üretildiğinde değişikliklerin kaybolmasına engel olur.</span><span class="sxs-lookup"><span data-stu-id="0898b-117">Defining the CLR stub in a separate source file will prevent the changes from being lost when the file is regenerated.</span></span>  
  
2. <span data-ttu-id="0898b-118">Aşağıdaki gibi, sınıfınıza bir ortak dil çalışma zamanı (CLR) yöntemi ekleyin <xref:System.Data.Objects.ObjectContext> :</span><span class="sxs-lookup"><span data-stu-id="0898b-118">Add a common language runtime (CLR) method to your <xref:System.Data.Objects.ObjectContext> class that does the following:</span></span>  
  
    - <span data-ttu-id="0898b-119">Kavramsal modelde tanımlanan işlevle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="0898b-119">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="0898b-120">Yöntemi eşlemek için bir yöntemine uygulamanız gerekir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0898b-120">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="0898b-121"><xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A>Özniteliğinin ve parametrelerinin, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> kavramsal modelin ad alanı adı ve kavramsal modelde işlev adı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0898b-121">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span> <span data-ttu-id="0898b-122">LINQ için işlev adı çözümlemesi büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="0898b-122">Function name resolution for LINQ is case sensitive.</span></span>  
  
    - <span data-ttu-id="0898b-123"><xref:System.Linq.IQueryProvider.Execute%2A>Özelliği tarafından döndürülen yöntemin sonuçlarını döndürür <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> .</span><span class="sxs-lookup"><span data-stu-id="0898b-123">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property.</span></span>  
  
3. <span data-ttu-id="0898b-124">Yöntemi, sınıfının bir örneğinde üye olarak çağırın <xref:System.Data.Objects.ObjectContext> .</span><span class="sxs-lookup"><span data-stu-id="0898b-124">Call the method as a member on an instance of the <xref:System.Data.Objects.ObjectContext> class.</span></span>  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a><span data-ttu-id="0898b-125">Model tanımlı bir işlevi özel bir sınıfta statik yöntem olarak çağırmak için</span><span class="sxs-lookup"><span data-stu-id="0898b-125">To call a model-defined function as static method on a custom class</span></span>  
  
1. <span data-ttu-id="0898b-126">Aşağıdaki gibi bir statik yöntemle uygulamanıza bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0898b-126">Add a class to your application with a static method that does the following:</span></span>  
  
    - <span data-ttu-id="0898b-127">Kavramsal modelde tanımlanan işlevle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="0898b-127">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="0898b-128">Yöntemi eşlemek için bir yöntemine uygulamanız gerekir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0898b-128">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="0898b-129"><xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A>Özniteliğinin ve parametrelerinin, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> kavramsal modelin ad alanı adı ve kavramsal modelde işlev adı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0898b-129">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span>  
  
    - <span data-ttu-id="0898b-130">Bir <xref:System.Linq.IQueryable> bağımsız değişkeni kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0898b-130">Accepts an <xref:System.Linq.IQueryable> argument.</span></span>  
  
    - <span data-ttu-id="0898b-131"><xref:System.Linq.IQueryProvider.Execute%2A>Özelliği tarafından döndürülen yöntemin sonuçlarını döndürür <xref:System.Linq.IQueryable.Provider%2A> .</span><span class="sxs-lookup"><span data-stu-id="0898b-131">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Linq.IQueryable.Provider%2A> property.</span></span>  
  
2. <span data-ttu-id="0898b-132">Yöntemi, özel sınıfta bir statik yöntem olarak çağırın</span><span class="sxs-lookup"><span data-stu-id="0898b-132">Call the method as a member a static method on the custom class</span></span>  
  
## <a name="example"></a><span data-ttu-id="0898b-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="0898b-133">Example</span></span>  

 <span data-ttu-id="0898b-134">**Bir Model-Defined Işlevini bir ObjectContext nesnesi üzerinde yöntem olarak çağırma**</span><span class="sxs-lookup"><span data-stu-id="0898b-134">**Calling a Model-Defined Function as a Method on an ObjectContext Object**</span></span>  
  
 <span data-ttu-id="0898b-135">Aşağıdaki örnek, model tanımlı bir işlevin bir nesne üzerinde yöntem olarak nasıl çağrılacağını gösterir <xref:System.Data.Objects.ObjectContext> .</span><span class="sxs-lookup"><span data-stu-id="0898b-135">The following example demonstrates how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object.</span></span> <span data-ttu-id="0898b-136">Örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır.</span><span class="sxs-lookup"><span data-stu-id="0898b-136">The example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
 <span data-ttu-id="0898b-137">Belirtilen ürün için ürün gelirini döndüren aşağıdaki kavramsal model işlevini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0898b-137">Consider the conceptual model function below that returns product revenue for a specified product.</span></span> <span data-ttu-id="0898b-138">(Kavramsal modelinize işlev ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: kavramsal modelde özel Işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span><span class="sxs-lookup"><span data-stu-id="0898b-138">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a><span data-ttu-id="0898b-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="0898b-139">Example</span></span>  

 <span data-ttu-id="0898b-140">Aşağıdaki kod, `AdventureWorksEntities` Yukarıdaki kavramsal model işlevi ile eşleşen sınıfa bir yöntem ekler.</span><span class="sxs-lookup"><span data-stu-id="0898b-140">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="0898b-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="0898b-141">Example</span></span>  

 <span data-ttu-id="0898b-142">Aşağıdaki kod, belirtilen bir ürün için ürün gelirini göstermek üzere yukarıdaki yöntemi çağırır:</span><span class="sxs-lookup"><span data-stu-id="0898b-142">The following code calls the method above to display the product revenue for a specified product:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="0898b-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="0898b-143">Example</span></span>  

 <span data-ttu-id="0898b-144">Aşağıdaki örnek, bir koleksiyon (nesne olarak) döndüren model tanımlı bir işlevin nasıl çağrılacağını gösterir <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="0898b-144">The following example demonstrates how to call a model-defined function that returns a collection (as an <xref:System.Linq.IQueryable%601> object).</span></span> <span data-ttu-id="0898b-145">Belirtilen ürün KIMLIĞI için tüm ' i döndüren kavramsal model işlevini göz önünde bulundurun `SalesOrderDetails` .</span><span class="sxs-lookup"><span data-stu-id="0898b-145">Consider the conceptual model function below that returns all the `SalesOrderDetails` for a given product ID.</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a><span data-ttu-id="0898b-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="0898b-146">Example</span></span>  

 <span data-ttu-id="0898b-147">Aşağıdaki kod, `AdventureWorksEntities` Yukarıdaki kavramsal model işlevi ile eşleşen sınıfa bir yöntem ekler.</span><span class="sxs-lookup"><span data-stu-id="0898b-147">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="0898b-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="0898b-148">Example</span></span>  

 <span data-ttu-id="0898b-149">Aşağıdaki kod yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0898b-149">The following code calls the method.</span></span> <span data-ttu-id="0898b-150">Döndürülen <xref:System.Linq.IQueryable%601> sorgunun her biri için satır toplamlarını döndürecek şekilde daha iyi bir şekilde iyileştirdiğini unutmayın `SalesOrderDetail` .</span><span class="sxs-lookup"><span data-stu-id="0898b-150">Note that the returned <xref:System.Linq.IQueryable%601> query is further refined to return line totals for each `SalesOrderDetail`.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="0898b-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="0898b-151">Example</span></span>  

 <span data-ttu-id="0898b-152">**Bir Model-Defined Işlevi özel bir sınıfta statik yöntem olarak çağırma**</span><span class="sxs-lookup"><span data-stu-id="0898b-152">**Calling a Model-Defined Function as a Static Method on a Custom Class**</span></span>  
  
 <span data-ttu-id="0898b-153">Sonraki örnek, model tanımlı bir işlevin özel bir sınıfta statik bir yöntem olarak nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0898b-153">The next example demonstrates how to call a model-defined function as a static method on a custom class.</span></span> <span data-ttu-id="0898b-154">Örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır.</span><span class="sxs-lookup"><span data-stu-id="0898b-154">The example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0898b-155">Model tanımlı bir işlevi özel bir sınıfta statik bir yöntem olarak çağırdığınızda, model tanımlı işlev bir koleksiyonu kabul etmeli ve koleksiyondaki değerlerin toplanmasını döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="0898b-155">When you call a model-defined function as a static method on a custom class, the model-defined function must accept a collection and return an aggregation of values in the collection.</span></span>  
  
 <span data-ttu-id="0898b-156">Bir SalesOrderDetail koleksiyonu için ürün gelirini döndüren aşağıdaki kavramsal model işlevini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0898b-156">Consider the conceptual model function below that returns product revenue for a SalesOrderDetail collection.</span></span> <span data-ttu-id="0898b-157">(Kavramsal modelinize işlev ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: kavramsal modelde özel Işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).).</span><span class="sxs-lookup"><span data-stu-id="0898b-157">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).).</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="0898b-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="0898b-158">Example</span></span>  

 <span data-ttu-id="0898b-159">Aşağıdaki kod, uygulamanıza, yukarıdaki kavramsal model işlevine eşleyen statik bir yöntem içeren bir sınıf ekler.</span><span class="sxs-lookup"><span data-stu-id="0898b-159">The following code adds a class to your application that contains a static method that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="0898b-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="0898b-160">Example</span></span>  

 <span data-ttu-id="0898b-161">Aşağıdaki kod, bir SalesOrderDetail koleksiyonu için ürün gelirini göstermek üzere yukarıdaki yöntemi çağırır:</span><span class="sxs-lookup"><span data-stu-id="0898b-161">The following code calls the method above to display the product revenue for a SalesOrderDetail collection:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0898b-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0898b-162">See also</span></span>

- <span data-ttu-id="0898b-163">[. edmx dosyasına genel bakış](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0898b-163">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="0898b-164">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="0898b-164">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="0898b-165">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0898b-165">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)

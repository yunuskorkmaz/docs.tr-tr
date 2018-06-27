---
title: Desen dispose
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7bb9420d6439cff36c5cfa997152773503fbd9a
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948556"
---
# <a name="dispose-pattern"></a><span data-ttu-id="cf065-102">Desen dispose</span><span class="sxs-lookup"><span data-stu-id="cf065-102">Dispose Pattern</span></span>
<span data-ttu-id="cf065-103">Tüm Programlar bir veya daha fazla sistem kaynakları, bellek, sistem tanıtıcıları veya veritabanı bağlantıları gibi kendi yürütme sürecinde alın.</span><span class="sxs-lookup"><span data-stu-id="cf065-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="cf065-104">Geliştiriciler alınan ve kullanılan sonra bunlar serbest gerekir çünkü bu tür sistem kaynaklarını kullanırken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf065-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="cf065-105">CLR otomatik bellek yönetimi için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf065-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="cf065-106">Yönetilen bellek (C# işleci kullanılarak ayrılmış bellek `new`) açıkça serbest bırakılacak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cf065-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="cf065-107">Ayrıca, atık toplayıcı (GC) tarafından otomatik olarak yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="cf065-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="cf065-108">Bu bellek yayınlama yorucu ve zor görev geliştiricilerden boşaltır ve .NET Framework tarafından karşılanan eşi görülmemiş üretkenlik ana nedenlerinden biri olmuştur.</span><span class="sxs-lookup"><span data-stu-id="cf065-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="cf065-109">Ne yazık ki, yönetilen bellek yalnızca sistem kaynaklarını birçok türdeki biridir.</span><span class="sxs-lookup"><span data-stu-id="cf065-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="cf065-110">Yönetilen bellek dışındaki kaynaklar hala açıkça yayımlanması gerekir ve yönetilmeyen kaynaklar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="cf065-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="cf065-111">GC yönetilmeyen gibi kaynakları yönetmek için yönetilmeyen kaynakları yönetmek için sorumluluk geliştiriciler elinizde arasındadır yani tasarlanmamıştır özellikle.</span><span class="sxs-lookup"><span data-stu-id="cf065-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="cf065-112">CLR yönetilmeyen kaynakları serbest bırakma bazı Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf065-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="cf065-113"><xref:System.Object?displayProperty=nameWithType> sanal bir yöntem bildirir <xref:System.Object.Finalize%2A> (sonlandırıcıyı olarak da bilinir) çağrılan tarafından GC önce nesnenin bellek tarafından GC iadesi ve yönetilmeyen kaynakları serbest bırakmak için geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="cf065-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="cf065-114">Sonlandırıcıyı geçersiz türleri sonlandırılabilir türleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="cf065-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="cf065-115">Sonlandırıcılar bazı temizleme senaryolarda etkili olsa da, bunlar iki önemli sakıncaları vardır:</span><span class="sxs-lookup"><span data-stu-id="cf065-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="cf065-116">GC bir nesne koleksiyonu için uygun olduğunu algıladığında sonlandırıcıyı adı verilir.</span><span class="sxs-lookup"><span data-stu-id="cf065-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="cf065-117">Bu, belirli belirlenmemiş bir süre sonra kaynak artık gerekli değildir gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="cf065-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="cf065-118">Olduğunda Geliştirici verebilir veya kaynak ve kaynak sonlandırıcıyı tarafından gerçekten zaman yayımlanan saat serbest bırakmak istediğiniz arasındaki gecikme birçok olması kaynakları (kolayca tükendi kaynakları) almayı programlarda veya olarak kabul edilebilir Kaynakları (örneğin, büyük yönetilmeyen bellek arabellek) kullanımda tutmak maliyetli durumları.</span><span class="sxs-lookup"><span data-stu-id="cf065-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="cf065-119">CLR bir sonlandırıcı çağırmak gerektiğinde sonraki yuvarlamak atık toplama (koleksiyonları arasında çalıştırmak sonlandırıcılar) kadar nesnenin bellek koleksiyonunu erteleyin gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf065-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="cf065-120">Bu nesnenin bellek (ve başvurduğu tüm nesneler) daha uzun bir süre için serbest bırakılacak değil, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cf065-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="cf065-121">Bu nedenle, özel olarak sonlandırıcılar üzerinde bağlı olan yönetilmeyen kaynakları olması kaynaklarla ilgilenirken mümkün olan en kısa sürede geri kazanmak önemli olduğu durumlarda birçok senaryo ya da yüksek oranda kullanıcı senaryoları uygun olmayabilir eklenen GC ek yükü sonlandırma kabul edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="cf065-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="cf065-122">Bir çerçeve sağlar <xref:System.IDisposable?displayProperty=nameWithType> Geliştirici gerekli olmadığında hemen yönetilmeyen kaynakları serbest bırakmak için el ile bir yol sağlamak üzere uygulanmalıdır arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cf065-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="cf065-123">Ayrıca sağlar <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> GC, anlayabilirsiniz yöntemi bir nesne, el ile bırakıldı ve artık, sonlandırılır ve bu durumda nesnenin bellek önceki istenemiyor gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cf065-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="cf065-124">Türleri uygulayan `IDisposable` arabirimi atılabilir türler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="cf065-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="cf065-125">Dispose düzeni kullanım ve sonlandırıcılar uyarlamasını standart hale getirmek için tasarlanmıştır ve `IDisposable` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cf065-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="cf065-126">Uygulaması karmaşıklığını azaltmak için desen ana gerekçesi olan <xref:System.Object.Finalize%2A> ve <xref:System.IDisposable.Dispose%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="cf065-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="cf065-127">Yöntemler (farklar sonraki bölümde açıklanmıştır) bazı ancak tüm kod yollarının paylaşmak olgu gelen karmaşıklık kaynaklandığını.</span><span class="sxs-lookup"><span data-stu-id="cf065-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="cf065-128">Ayrıca, bazı öğeler belirleyici kaynak yönetimi için dil desteği evrimi ilgili deseninin geçmiş nedenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="cf065-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="cf065-129">**✓ YAPMAK** atılabilir türler örneklerini içeren türlerinde temel Dispose desenini uygular.</span><span class="sxs-lookup"><span data-stu-id="cf065-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="cf065-130">Bkz: [temel Dispose düzeni](#basic_pattern) temel düzeni hakkında ayrıntılı bilgi için bölüm.</span><span class="sxs-lookup"><span data-stu-id="cf065-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="cf065-131">Bir tür atılabilir diğer nesnelerin ömrü boyunca sorumlu ise, geliştiriciler bunlarla ilgili çok silmek için bir yönteme ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="cf065-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="cf065-132">Kapsayıcının kullanarak `Dispose` yöntemi bu mümkün kılmak için uygun bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="cf065-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="cf065-133">**✓ YAPMAK** temel Dispose desen uygulamak ve bir sonlandırıcı türlerinde, açıkça boşaltılması gerekiyor ve sonlandırıcılar sahip değil tutan kaynakları sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf065-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="cf065-134">Örneğin, yönetilmeyen bellek arabelleği depolama türlerinde düzeni uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf065-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="cf065-135">[Sonlandırılabilir türleri](#finalizable_types) bölüm sonlandırıcılar uygulama için ilgili yönergeleri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf065-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="cf065-136">**✓ DÜŞÜNÜN** temel Dispose düzeni uygulama sınıflarında kendilerini tutmayın yönetilmeyen kaynakları veya tek kullanımlık nesneleri ancak yapmak subtypes etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="cf065-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="cf065-137">Bu harika bir örneği <xref:System.IO.Stream?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cf065-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="cf065-138">Herhangi bir kaynağa sahip olmayan bir Özet temel sınıf olmasına rağmen kendi alt sınıfların çoğunu ve bu nedenle, bu deseni uygular.</span><span class="sxs-lookup"><span data-stu-id="cf065-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="cf065-139">Temel Dispose düzeni</span><span class="sxs-lookup"><span data-stu-id="cf065-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="cf065-140">Uygulama deseni temel uyarlamasını içerir `System.IDisposable` arabirimi ve bildirme `Dispose(bool)` arasında paylaşılması için tüm kaynak temizleme mantığını uygulayan yöntemi `Dispose` yöntemi ve isteğe bağlı Sonlandırıcı.</span><span class="sxs-lookup"><span data-stu-id="cf065-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="cf065-141">Aşağıdaki örnekte basit bir uygulama temel deseninin gösterir:</span><span class="sxs-lookup"><span data-stu-id="cf065-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder() {  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposing) {  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cf065-142">Boole parametresi `disposing` yöntemi gelen çağrıldı olup olmadığını gösteren `IDisposable.Dispose` uygulaması veya sonlandırıcıyı.</span><span class="sxs-lookup"><span data-stu-id="cf065-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="cf065-143">`Dispose(bool)` Diğer başvuru nesneleri (örneğin, yukarıdaki örnekteki kaynak alanı) erişmeden önce uygulama parametresi denetlemelidir.</span><span class="sxs-lookup"><span data-stu-id="cf065-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="cf065-144">Gelen yöntem çağrıldığında bu tür nesneler yalnızca erişilen `IDisposable.Dispose` uygulaması (zaman `disposing` parametresi true değerine eşittir).</span><span class="sxs-lookup"><span data-stu-id="cf065-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="cf065-145">Sonlandırıcıyı yöntemi çağrıldıysa (`disposing` false), diğer nesneleri değil erişilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cf065-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="cf065-146">, Nesneler öngörülemeyen bir sırada sonlandırılır ve bu nedenle bunlar veya onların bağımlılıkları hiçbirini zaten sonlandırılan nedenidir.</span><span class="sxs-lookup"><span data-stu-id="cf065-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="cf065-147">Ayrıca, bu bölümde, zaten Dispose düzeni uygulamıyor bir taban sınıflarıyla uygular.</span><span class="sxs-lookup"><span data-stu-id="cf065-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="cf065-148">Zaten deseni uygulayan bir sınıftan devralmayı, yalnızca geçersiz kılma `Dispose(bool)` yöntemi ek kaynak temizleme mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf065-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="cf065-149">**✓ YAPMAK** bildirme bir `protected virtual void Dispose(bool disposing)` tüm mantığı merkezileştirmek yöntemi ilgili yönetilmeyen kaynakları serbest bırakma için.</span><span class="sxs-lookup"><span data-stu-id="cf065-149">**✓ DO** declare a `protected virtual void Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="cf065-150">Tüm kaynak temizleme Bu yöntemde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf065-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="cf065-151">Yöntem sonlandırıcıyı çağrılır ve `IDisposable.Dispose` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf065-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="cf065-152">Parametre bir sonlandırıcı içinde çağrılan varsa false olur.</span><span class="sxs-lookup"><span data-stu-id="cf065-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="cf065-153">Sonlandırma sırasında çalıştıran herhangi bir kod sonlandırılabilir diğer nesneleri erişilmemesi emin olmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf065-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="cf065-154">Sonlandırıcılar uygulama ayrıntılarını sonraki bölümde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf065-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="cf065-155">**✓ YAPMAK** uygulamak `IDisposable` yalnızca çağırarak arabirim `Dispose(true)` arkasından `GC.SuppressFinalize(this)`.</span><span class="sxs-lookup"><span data-stu-id="cf065-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="cf065-156">Çağrı `SuppressFinalize` varsa yalnızca gerçekleşeceğini `Dispose(true)` başarıyla yürütür.</span><span class="sxs-lookup"><span data-stu-id="cf065-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="cf065-157">**X yok** parametresiz olun `Dispose` sanal yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf065-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="cf065-158">`Dispose(bool)` Alt sınıflar tarafından geçersiz kılınması gereken bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="cf065-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
```csharp
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
```  
  
 <span data-ttu-id="cf065-159">**X yok** hiçbir aşırı bildirme `Dispose` yöntemi dışında `Dispose()` ve `Dispose(bool)`.</span><span class="sxs-lookup"><span data-stu-id="cf065-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="cf065-160">`Dispose` Bu desen kod oluşturma ve uygulayıcılar, kullanıcılar ve derleyicileri arasında Karışıklığı önlemek için ayrılmış bir sözcük dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf065-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="cf065-161">Bazı diller belirli türlerinde bu deseni otomatik olarak uygulamak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf065-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="cf065-162">**✓ YAPMAK** izin `Dispose(bool)` birden çok kez çağrılacak yöntem.</span><span class="sxs-lookup"><span data-stu-id="cf065-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="cf065-163">Yöntemi, hiçbir şey ilk çağrısından sonra yapmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf065-163">The method might choose to do nothing after the first call.</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="cf065-164">**KAÇININ x** içinden bir özel durum atma `Dispose(bool)` dışındaki burada içeren işlem bozulmuş Kritik durumları altında (sızıntılarını, paylaşılan durumu tutarsız, vs.).</span><span class="sxs-lookup"><span data-stu-id="cf065-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="cf065-165">Kullanıcıların beklediğiniz yapılan bir çağrı `Dispose` bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="cf065-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="cf065-166">Varsa `Dispose` bir özel durum oluşturabilen, daha fazla finally bloğu temizleme mantığı değil yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="cf065-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="cf065-167">Bu sorunu çözmek için kullanıcının her çağrı için Kaydır gerekir `Dispose` (içinde finally bloğunda!) bir try bloğunda, müşteri adayları çok karmaşık temizleme işleyicilerine.</span><span class="sxs-lookup"><span data-stu-id="cf065-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="cf065-168">Çalıştırıldığında bir `Dispose(bool disposing)` yöntemi, hiçbir zaman throw bir atma false ise özel durumu.</span><span class="sxs-lookup"><span data-stu-id="cf065-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="cf065-169">Bunun yapılması bir Sonlandırıcısı bağlamı içinde çalıştırıldığında işlemini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="cf065-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="cf065-170">**✓ YAPMAK** throw bir <xref:System.ObjectDisposedException> , nesne atıldı sonra kullanılamayan üyeden.</span><span class="sxs-lookup"><span data-stu-id="cf065-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething() {  
        if (disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
        ...  
    }  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="cf065-171">**✓ DÜŞÜNÜN** yöntemi sağlama `Close()`, ek olarak `Dispose()`, yakın alan standart terminolojisinde olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="cf065-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="cf065-172">Bunu yaparken, yaptığınız önemli `Close` uygulaması aynı `Dispose` ve uygulayın `IDisposable.Dispose` yöntemi açıkça.</span><span class="sxs-lookup"><span data-stu-id="cf065-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
```csharp
public class Stream : IDisposable {  
    IDisposable.Dispose() {  
        Close();  
    }  
    public void Close() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a><span data-ttu-id="cf065-173">Sonlandırılabilir türleri</span><span class="sxs-lookup"><span data-stu-id="cf065-173">Finalizable Types</span></span>  
 <span data-ttu-id="cf065-174">Sonlandırılabilir türler sonlandırıcıyı geçersiz kılma ve bir sonlandırma kod yolunda sağlayarak temel Dispose düzeni genişleten türleridir `Dispose(bool)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf065-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="cf065-175">Öncelikle, yürütme sırasında sistem durumuyla ilgili (normalde geçerli) bazı varsayımlarda yapılamıyor çünkü sonlandırıcılar doğru uygulamak notoriously zordur.</span><span class="sxs-lookup"><span data-stu-id="cf065-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="cf065-176">Aşağıdaki yönergeler dikkatli dikkate almanız.</span><span class="sxs-lookup"><span data-stu-id="cf065-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="cf065-177">Bazı yönergeler için değil yalnızca geçerli olduğunu unutmayın `Finalize` yöntemi, ancak herhangi bir kod için bir sonlandırıcı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cf065-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="cf065-178">Temel Dispose önceden tanımlanmış düzeni söz konusu olduğunda, yani içinde yürütür mantığı `Dispose(bool disposing)` zaman `disposing` parametre değer false.</span><span class="sxs-lookup"><span data-stu-id="cf065-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="cf065-179">Taban sınıf zaten sonlandırılabilir ise ve temel Dispose deseni uygular, değil kılmanız `Finalize` yeniden.</span><span class="sxs-lookup"><span data-stu-id="cf065-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="cf065-180">Bunun yerine yalnızca kılmalıdır `Dispose(bool)` yöntemi ek kaynak temizleme mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf065-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="cf065-181">Aşağıdaki kod bir sonlandırılabilir türünün bir örneği gösterir:</span><span class="sxs-lookup"><span data-stu-id="cf065-181">The following code shows an example of a finalizable type:</span></span>  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder() {  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing) {  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing) { // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    public void Dispose() {
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 <span data-ttu-id="cf065-182">**KAÇININ x** türleri sonlandırılabilir yapma.</span><span class="sxs-lookup"><span data-stu-id="cf065-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="cf065-183">Bir sonlandırıcı gerekli düşündüğünüz herhangi bir durumu dikkatlice düşünün.</span><span class="sxs-lookup"><span data-stu-id="cf065-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="cf065-184">Gerçek yoktur hem performans hem de kod karmaşıklık açısından sonlandırıcılar örnekleriyle ilişkili maliyeti.</span><span class="sxs-lookup"><span data-stu-id="cf065-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="cf065-185">Kaynak sarmalayıcıları gibi kullanmayı tercih <xref:System.Runtime.InteropServices.SafeHandle> mümkün olduğunda yönetilmeyen kaynakları kapsüllemek için; bu durumda bir sonlandırıcı hale gereksiz sarmalayıcı kendi kaynak Temizleme için sorumlu olduğu için.</span><span class="sxs-lookup"><span data-stu-id="cf065-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="cf065-186">**X yok** değer türleri sonlandırılabilir olun.</span><span class="sxs-lookup"><span data-stu-id="cf065-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="cf065-187">Yalnızca başvuru türleri gerçekte CLR tarafından sonlandırılır ve bu nedenle değer türünde bir sonlandırıcı yerleştirmek için her türlü girişim yok sayılacak.</span><span class="sxs-lookup"><span data-stu-id="cf065-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="cf065-188">Bu kural, C# ve C++ Derleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="cf065-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="cf065-189">**✓ YAPMAK** tür kendi Sonlandırıcı olmayan bir yönetilmeyen kaynak serbest bırakma için sorumlu ise bir türü sonlandırılabilir olun.</span><span class="sxs-lookup"><span data-stu-id="cf065-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="cf065-190">Sonlandırıcıyı uygularken, yalnızca çağrısı `Dispose(false)` ve içindeki tüm kaynak temizleme mantığını yerleştirin `Dispose(bool disposing)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf065-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing) {
        ...  
    }  
}  
```  
  
 <span data-ttu-id="cf065-191">**✓ YAPMAK** her sonlandırılabilir türüne temel Dispose desenini uygular.</span><span class="sxs-lookup"><span data-stu-id="cf065-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="cf065-192">Bu türdeki kullanıcıların açıkça belirleyici temizleme sonlandırıcıyı sorumlu olduğu kaynaklarla işlemini gerçekleştirmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf065-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="cf065-193">**X yok** önemli riski Bunlar zaten sonlandırılan, çünkü sonlandırıcıyı kod yolunda sonlandırılabilir tüm nesnelere erişme.</span><span class="sxs-lookup"><span data-stu-id="cf065-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="cf065-194">Örneğin, başka bir sonlandırılabilir nesne B başvuruyor sonlandırılabilir bir nesne A güvenilir bir şekilde B A'ın kullanamazsınız sonlandırıcıyı, veya tam tersi.</span><span class="sxs-lookup"><span data-stu-id="cf065-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="cf065-195">Sonlandırıcılar (eksikliği kritik sonlandırma için zayıf bir sıralama garanti) rastgele sırayla denir.</span><span class="sxs-lookup"><span data-stu-id="cf065-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="cf065-196">Ayrıca, bir uygulama etki alanı kaldırma sırasında veya işlem sonlandırma sırasında bazı noktalarda statik değişkenler depolanan nesneler da toplanan olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cf065-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="cf065-197">Sonlandırılabilir nesne (veya statik değişkenler depolanan değerleri kullanabilecek statik bir yöntemini çağırmadan) başvurduğu statik bir değişken olabilir erişme güvenli IF <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf065-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="cf065-198">**✓ YAPMAK** olun, `Finalize` korumalı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf065-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="cf065-199">Çünkü bu kılavuz zorlamak için derleyicileri yardımcı C#, C++ ve VB.NET geliştiriciler bu hakkında endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cf065-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="cf065-200">**X yok** let özel durumlar kaçış sistem kritik hataları dışında Sonlandırıcısı mantığı gelen.</span><span class="sxs-lookup"><span data-stu-id="cf065-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="cf065-201">Sonlandırıcı bir özel durum, CLR (itibariyle .NET Framework sürüm 2.0), tüm işlem kapatılır yürütme ve denetimli bir şekilde yayımlanan kaynakları diğer sonlandırıcılar engelleyen.</span><span class="sxs-lookup"><span data-stu-id="cf065-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="cf065-202">**✓ DÜŞÜNÜN** oluşturma ve kritik sonlandırılabilir nesnesini kullanarak (içeren bir tür hiyerarşisinde bir türüyle <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) içinde bir sonlandırıcı kesinlikle gerekir yürütme zorlanmış uygulama etki alanı kaldırır ve iş parçacığı karşısında bile durumlar için durdurur.</span><span class="sxs-lookup"><span data-stu-id="cf065-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="cf065-203">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="cf065-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cf065-204">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="cf065-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf065-205">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf065-205">See Also</span></span>  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="cf065-206">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="cf065-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="cf065-207">Ortak Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="cf065-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [<span data-ttu-id="cf065-208">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="cf065-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)

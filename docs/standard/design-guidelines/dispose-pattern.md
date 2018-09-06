---
title: Dispose deseni
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
ms.openlocfilehash: ff52e17cfe4a4236e4d165c0961ca3a23fed9a72
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864650"
---
# <a name="dispose-pattern"></a><span data-ttu-id="40863-102">Dispose deseni</span><span class="sxs-lookup"><span data-stu-id="40863-102">Dispose Pattern</span></span>
<span data-ttu-id="40863-103">Tüm Programlar kursu, yürütme sırasında bir veya daha fazla sistem kaynakları, bellek, sistemi işleyicilerini veya veritabanı bağlantıları gibi edinin.</span><span class="sxs-lookup"><span data-stu-id="40863-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="40863-104">Geliştiriciler alınan ve kullanılan sonra bunlar serbest bırakılması gerekir çünkü bu tür sistem kaynakları kullanırken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40863-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="40863-105">CLR'nin otomatik bellek yönetimi için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="40863-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="40863-106">Yönetilen bellek (C# işleci kullanılarak ayrılmış bellek `new`) açıkça serbest bırakılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="40863-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="40863-107">Atık toplayıcı (GC) tarafından otomatik olarak yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="40863-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="40863-108">Bu işlem, bellek serbest zor ve yorucu bir görev geliştiricilerden serbest bırakır ve .NET Framework tarafından gösterilen eşi görülmemiş bir üretkenlik için temel nedenlerinden biri olmuştur.</span><span class="sxs-lookup"><span data-stu-id="40863-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="40863-109">Ne yazık ki, yönetilen bellek yalnızca sistem kaynakları birçok türde biridir.</span><span class="sxs-lookup"><span data-stu-id="40863-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="40863-110">Yönetilen bellek haricinde kaynaklar yine de açıkça serbest bırakılması gerektiği ve yönetilmeyen kaynaklar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="40863-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="40863-111">GC yönetilmeyen gibi kaynakları yönetmek için yönetilmeyen kaynaklarını yönetme sorumluluğunu geliştiricilere elinizde kaynaklandığını anlamına gelir tasarlanmamıştır özellikle.</span><span class="sxs-lookup"><span data-stu-id="40863-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="40863-112">CLR yönetilmeyen kaynakları serbest bırakmak bazı Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="40863-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="40863-113"><xref:System.Object?displayProperty=nameWithType> sanal yöntem <xref:System.Object.Finalize%2A> (Sonlandırıcı olarak da bilinir) adlı atık toplama tarafından önce nesnenin bellek atık toplama tarafından geri kazanılır ve yönetilmeyen kaynakları serbest bırakmak için geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="40863-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="40863-114">Sonlandırıcıyı geçersiz kılın türleri sonlandırılabilir türleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="40863-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="40863-115">Sonlandırıcılar bazı temizleme senaryolarda etkili olsa da, bunlar iki önemli engelleri vardır:</span><span class="sxs-lookup"><span data-stu-id="40863-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="40863-116">Atık toplama bir nesne koleksiyonu için uygun olduğunu algıladığında, sonlandırıcı adı verilir.</span><span class="sxs-lookup"><span data-stu-id="40863-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="40863-117">Bu, belirli belirsiz bir süre sonra kaynak artık gerekli değildir gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="40863-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="40863-118">Olduğunda Geliştirici olabilir veya kaynak ve zaman Sonlandırıcı tarafından kaynak gerçekten yayınlandığında serbest bırakmak istediğiniz arasında gecikme çok nadir kaynakları (kolayca bitti kaynaklar) elde ettiğiniz programlar ya da kabul edilemez olabilir. Kaynakları (örneğin, büyük bir yönetilmeyen bellek arabellek) kullanımda tutmak pahalı olduğu durumlarda.</span><span class="sxs-lookup"><span data-stu-id="40863-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="40863-119">CLR bir sonlandırıcı çağrısı gerektiğinde, sonraki yuvarlak çöp toplama (koleksiyonları arasında çalıştırma sonlandırıcılar) kadar nesnenizin belleğini koleksiyonunu erteleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="40863-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="40863-120">Bu, nesnenizin belleğini (ve başvurduğu tüm nesneler) daha uzun bir süre için kullanıma sunulacağını yok anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="40863-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="40863-121">Bu nedenle, bağlı olan özel sonlandırıcılar üzerinde yönetilmeyen kaynakları nadir kaynakları ile ilgilenirken, mümkün olan en kısa sürede geri kazanmak önemli olduğu durumlarda birçok senaryoda ya da yüksek performanslı senaryolarında, uygun olmayabilir eklenen GC ek yükü sonlandırma kabul edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="40863-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="40863-122">Bir çerçeve sağlar <xref:System.IDisposable?displayProperty=nameWithType> Geliştirici gerekli olmayan hemen sonra yönetilmeyen kaynaklar serbest bırakılacaksa el ile bir yol sağlamak için uygulanması gereken Arabirimi.</span><span class="sxs-lookup"><span data-stu-id="40863-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="40863-123">Ayrıca sağlar <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> GC, söyleyebilirsiniz yöntemi bir nesne, el ile bırakıldı ve artık sonlandırılmayı nesnenizin belleğini daha önce bu durumda kazanılabilir gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="40863-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="40863-124">Türleri uygulayan `IDisposable` arabirimi atılabilir türler adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="40863-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="40863-125">Dispose deseni kullanım ve sonlandırıcılar uygulaması standart hale getirmek için tasarlanmıştır ve `IDisposable` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="40863-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="40863-126">Desen ana hacktivism yürütmesinin karmaşıklığını azaltmaktır <xref:System.Object.Finalize%2A> ve <xref:System.IDisposable.Dispose%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="40863-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="40863-127">Gelen yöntemleri (farklar, sonraki bölümde açıklanmıştır) ancak tüm kod yolları paylaşmak olgu karmaşıklığı kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="40863-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="40863-128">Ayrıca, bazı öğeler evrimi belirleyici kaynak yönetimi için dil desteği, ilgili Düzen geçmiş nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="40863-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="40863-129">**✓ DO** atılabilir türler örneklerini içeren türlerinde temel Dispose desenini uygular.</span><span class="sxs-lookup"><span data-stu-id="40863-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="40863-130">Bkz: [temel Dispose deseni](#basic_pattern) bölümde temel düzeni hakkında ayrıntılı bilgi için.</span><span class="sxs-lookup"><span data-stu-id="40863-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="40863-131">Bir tür atılabilen diğer nesnelerin ömrü boyunca sorumlu geliştiriciler, çok silmek için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="40863-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="40863-132">Kapsayıcının kullanarak `Dispose` bunu mümkün hale getirmek için kullanışlı bir yol yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="40863-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="40863-133">**✓ DO** temel Dispose desen uygulamak ve bir sonlandırıcı türlerinde, açıkça boşaltılması gerekiyor ve sonlandırıcılar sahip değil tutan kaynakları sağlar.</span><span class="sxs-lookup"><span data-stu-id="40863-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="40863-134">Örneğin, deseni, yönetilmeyen bellek arabelleği depolama türlerinde uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40863-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="40863-135">[Sonlandırılabilir türleri](#finalizable_types) bölümde, bir sonlandırıcı uygulamak için ilgili yönergeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40863-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="40863-136">**✓ CONSIDER** temel Dispose düzeni uygulama sınıflarında kendilerini tutmayın yönetilmeyen kaynakları veya tek kullanımlık nesneleri ancak yapmak subtypes etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="40863-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="40863-137">Bu harika bir örneği <xref:System.IO.Stream?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="40863-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="40863-138">Tüm kaynakları tutan değil Özet temel sınıf olmasına rağmen alt sınıflara çoğunu ve bu nedenle, bu deseni uygular.</span><span class="sxs-lookup"><span data-stu-id="40863-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="40863-139">Temel Dispose deseni</span><span class="sxs-lookup"><span data-stu-id="40863-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="40863-140">Uygulama düzeninin basit uygulaması içerir `System.IDisposable` arabirimi ve bildirme `Dispose(bool)` arasında paylaşılması için tüm kaynak temizleme mantığını uygulayan yöntemi `Dispose` yöntemi ve isteğe bağlı bir sonlandırıcı.</span><span class="sxs-lookup"><span data-stu-id="40863-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="40863-141">Aşağıdaki örnek, basit bir uygulama temel deseni gösterir:</span><span class="sxs-lookup"><span data-stu-id="40863-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
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
  
 <span data-ttu-id="40863-142">Boole parametresi `disposing` gelen yöntemi çağrıldı olup olmadığını gösteren `IDisposable.Dispose` uygulama veya Sonlandırıcı.</span><span class="sxs-lookup"><span data-stu-id="40863-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="40863-143">`Dispose(bool)` Diğer başvuru nesneleri (örneğin, yukarıdaki örnekte kaynak alan) erişmeden önce uygulama parametresi denetlemelidir.</span><span class="sxs-lookup"><span data-stu-id="40863-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="40863-144">Gelen yöntem çağrıldığında bu tür nesneler yalnızca erişilen `IDisposable.Dispose` uygulama (zaman `disposing` parametresi true olarak eşittir).</span><span class="sxs-lookup"><span data-stu-id="40863-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="40863-145">Yöntemin Sonlandırıcı çağrılması durumunda (`disposing` false), diğer nesnelerin erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="40863-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="40863-146">Nesneler beklenmedik bir sırada olan sonlandırılır ve bu nedenle bunlar ve bunların bağımlılıklarını hiçbirini zaten sonlandırılan nedenidir.</span><span class="sxs-lookup"><span data-stu-id="40863-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="40863-147">Ayrıca, bu bölüm, zaten Dispose desenini uygulamaz tabana sahip sınıflar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="40863-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="40863-148">Desen uygulayan bir sınıftan devraldığını ise yalnızca geçersiz kılma `Dispose(bool)` ek kaynak temizleme mantığını sağlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40863-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="40863-149">**✓ DO** bildirme bir `protected virtual void Dispose(bool disposing)` tüm mantığı merkezileştirmek yöntemi ilgili yönetilmeyen kaynakları serbest bırakma için.</span><span class="sxs-lookup"><span data-stu-id="40863-149">**✓ DO** declare a `protected virtual void Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="40863-150">Bu yöntemde tüm kaynak temizleme gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="40863-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="40863-151">Yöntem sonlandırıcıyı çağrılır ve `IDisposable.Dispose` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40863-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="40863-152">Parametre bir sonlandırıcı içinde çağrılan yanlış olur.</span><span class="sxs-lookup"><span data-stu-id="40863-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="40863-153">Sonlandırma sırasında çalışan herhangi bir kod sonlandırılabilir diğer nesnelerin erişilmemesi emin olmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40863-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="40863-154">Sonlandırıcılar uygulama ayrıntılarını, sonraki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="40863-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="40863-155">**✓ DO** uygulamak `IDisposable` yalnızca çağırarak arabirim `Dispose(true)` arkasından `GC.SuppressFinalize(this)`.</span><span class="sxs-lookup"><span data-stu-id="40863-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="40863-156">Çağrı `SuppressFinalize` yalnızca durumunda gerçekleşmesi gereken `Dispose(true)` başarılı bir şekilde yürütür.</span><span class="sxs-lookup"><span data-stu-id="40863-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="40863-157">**X DO NOT** parametresiz olun `Dispose` sanal yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40863-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="40863-158">`Dispose(bool)` Alt sınıflar tarafından geçersiz kılınması gereken bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="40863-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
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
  
 <span data-ttu-id="40863-159">**X DO NOT** hiçbir aşırı bildirme `Dispose` yöntemi dışında `Dispose()` ve `Dispose(bool)`.</span><span class="sxs-lookup"><span data-stu-id="40863-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="40863-160">`Dispose` Bu düzen kod oluşturma ve uygulayıcılar, kullanıcılar ve derleyiciler arasındaki Karışıklığı önlemek için ayrılmış bir sözcük düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="40863-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="40863-161">Bazı diller, otomatik olarak bu deseni belirli türlerde uygulamak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40863-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="40863-162">**✓ DO** izin `Dispose(bool)` birden çok kez çağrılacak yöntem.</span><span class="sxs-lookup"><span data-stu-id="40863-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="40863-163">Yöntemi, hiçbir şey yapma ilk çağrıdan sonra da tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40863-163">The method might choose to do nothing after the first call.</span></span>  
  
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
  
 <span data-ttu-id="40863-164">**X AVOID** içinden bir özel durum atma `Dispose(bool)` dışındaki burada içeren işlem bozulmuş Kritik durumları altında (sızıntılarını, paylaşılan durumu tutarsız, vs.).</span><span class="sxs-lookup"><span data-stu-id="40863-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="40863-165">Kullanıcıların beklediğiniz bir çağrı `Dispose` bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="40863-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="40863-166">Varsa `Dispose` bir özel durum oluşturabilen, daha fazla finally bloğu temizleme mantıksal değil yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="40863-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="40863-167">Bu sorunu çözmek için kullanıcının yapılan her çağrı kaydırma gerekir `Dispose` (içinde finally bloğunda!) bir try bloğunda, müşteri adayları için çok karmaşık temizleme işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="40863-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="40863-168">Çalıştırıldığında bir `Dispose(bool disposing)` yöntemi, hiçbir zaman throw disposing false ise özel durumu.</span><span class="sxs-lookup"><span data-stu-id="40863-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="40863-169">Bunun yapılması bir sonlandırıcı bağlamı içinde çalıştırıldığında işlemini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="40863-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="40863-170">**✓ DO** throw bir <xref:System.ObjectDisposedException> , nesne atıldı sonra kullanılamayan üyeden.</span><span class="sxs-lookup"><span data-stu-id="40863-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
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
  
 <span data-ttu-id="40863-171">**✓ CONSIDER** yöntemi sağlama `Close()`, ek olarak `Dispose()`, yakın alan standart terminolojisinde olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="40863-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="40863-172">Bunun yapılması, yaptığınız önemli olduğu `Close` aynı uygulama `Dispose` ve uygulamayı düşünün `IDisposable.Dispose` yöntemi açıkça.</span><span class="sxs-lookup"><span data-stu-id="40863-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
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
## <a name="finalizable-types"></a><span data-ttu-id="40863-173">Sonlandırılabilir türleri</span><span class="sxs-lookup"><span data-stu-id="40863-173">Finalizable Types</span></span>  
 <span data-ttu-id="40863-174">Sonlandırılabilir türler sonlandırıcıyı geçersiz kılma ve sonlandırma kod yolunda sağlayarak temel Dispose desenini genişleten türler `Dispose(bool)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40863-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="40863-175">Öncelikle, belirli (normalde geçerli) sistem durumu hakkında yürütülmesi sırasında varsayımlar yapamazsınız çünkü sonlandırıcılar doğru uygulamak öğesinin zordur.</span><span class="sxs-lookup"><span data-stu-id="40863-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="40863-176">Aşağıdaki yönergeleri dikkatle dikkate alınması.</span><span class="sxs-lookup"><span data-stu-id="40863-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="40863-177">Bazı yönergeler için değil yalnızca geçerli olduğunu unutmayın `Finalize` yöntemi, ancak herhangi bir kod için bir sonlandırıcı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="40863-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="40863-178">İçinde yürüten mantığı temel Dispose önceden tanımlanmış düzeni söz konusu olduğunda, yani `Dispose(bool disposing)` olduğunda `disposing` parametre değer false.</span><span class="sxs-lookup"><span data-stu-id="40863-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="40863-179">Temel sınıf zaten sonlandırılabilir ve temel Dispose desenini uygular, değil'ı geçersiz kılmalıdır `Finalize` yeniden.</span><span class="sxs-lookup"><span data-stu-id="40863-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="40863-180">Yalnızca kılmanız gereken `Dispose(bool)` ek kaynak temizleme mantığını sağlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40863-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="40863-181">Aşağıdaki kod örneği sonlandırılabilir türü gösterir:</span><span class="sxs-lookup"><span data-stu-id="40863-181">The following code shows an example of a finalizable type:</span></span>  
  
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
  
 <span data-ttu-id="40863-182">**X AVOID** türleri sonlandırılabilir yapma.</span><span class="sxs-lookup"><span data-stu-id="40863-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="40863-183">Bir sonlandırıcı gerekli düşündüğünüz herhangi bir durumu dikkatlice düşünün.</span><span class="sxs-lookup"><span data-stu-id="40863-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="40863-184">Gerçek yoktur, hem performans hem de kod karmaşıklık açısından sonlandırıcılar örnekleriyle ilişkili maliyeti.</span><span class="sxs-lookup"><span data-stu-id="40863-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="40863-185">Kaynak sarmalayıcıları gibi kullanmayı tercih <xref:System.Runtime.InteropServices.SafeHandle> mümkün olduğunda yönetilmeyen kaynakları kapsüllemek üzere bu durumda bir sonlandırıcı olur gereksiz sarmalayıcı kendi kaynak Temizleme için sorumlu olduğu için.</span><span class="sxs-lookup"><span data-stu-id="40863-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="40863-186">**X DO NOT** değer türleri sonlandırılabilir olun.</span><span class="sxs-lookup"><span data-stu-id="40863-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="40863-187">Yalnızca başvuru türleri CLR tarafından gerçekten kesin ve bu nedenle bir değer türü üzerinde bir sonlandırıcı yerleştirmek için her türlü girişim yok sayılacak.</span><span class="sxs-lookup"><span data-stu-id="40863-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="40863-188">C# ve C++ Derleyicileri, bu kuralı uygular.</span><span class="sxs-lookup"><span data-stu-id="40863-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="40863-189">**✓ DO** tür kendi Sonlandırıcı olmayan bir yönetilmeyen kaynak serbest bırakma için sorumlu ise bir türü sonlandırılabilir olun.</span><span class="sxs-lookup"><span data-stu-id="40863-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="40863-190">Bir sonlandırıcı uygulamak, yalnızca çağrı `Dispose(false)` ve içindeki tüm kaynak temizleme mantığını yerleştirin `Dispose(bool disposing)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40863-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
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
  
 <span data-ttu-id="40863-191">**✓ DO** her sonlandırılabilir türüne temel Dispose desenini uygular.</span><span class="sxs-lookup"><span data-stu-id="40863-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="40863-192">Bu kullanıcıların türü açıkça Sonlandırıcı sorumlu olduğu aynı bu kaynakların belirlenimci temizleme gerçekleştirmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="40863-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="40863-193">**X DO NOT** önemli riski Bunlar zaten sonlandırılan, çünkü sonlandırıcıyı kod yolunda sonlandırılabilir tüm nesnelere erişme.</span><span class="sxs-lookup"><span data-stu-id="40863-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="40863-194">Örneğin, bir başvuru yapan başka bir nesneye sonlandırılabilir B sonlandırılabilir bir nesnenin bir güvenilir bir şekilde B A içinde kullanamazsınız, sonlandırıcı ya da tam tersi.</span><span class="sxs-lookup"><span data-stu-id="40863-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="40863-195">Sonlandırıcılar (kısıtlıysa, kritik sonlandırma bir zayıf sıralama garantisi) rastgele sırayla çağrılır.</span><span class="sxs-lookup"><span data-stu-id="40863-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="40863-196">Ayrıca, bir uygulama etki alanı kaldırma sırasında veya işlem sonlandırma sırasında bazı noktalarda statik değişkenlerinde depolanan nesnelerin da toplanan olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="40863-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="40863-197">Sonlandırılabilir bir nesnenin (veya statik değişkenlerinde depolanan değerleri kullanabilecek statik bir yöntemi) başvurduğu bir statik değişken olmayabilir erişme güvenli if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="40863-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="40863-198">**✓ DO** olun, `Finalize` korumalı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40863-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="40863-199">Derleyiciler bu anlayışın zorlamak için yardımcı olduğundan geliştiricilerin C#, C++ ve VB.NET bu konuda endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="40863-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="40863-200">**X DO NOT** let özel durumlar kaçış sistem kritik hataları dışında Sonlandırıcısı mantığı gelen.</span><span class="sxs-lookup"><span data-stu-id="40863-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="40863-201">Bir sonlandırıcı bir özel durum, CLR (itibariyle .NET Framework sürüm 2.0), tüm işlem kapatır yürütme ve denetimli bir biçimde yayımlanan kaynakları diğer sonlandırıcılar engelleyen.</span><span class="sxs-lookup"><span data-stu-id="40863-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="40863-202">**✓ CONSIDER** oluşturma ve kritik sonlandırılabilir nesnesini kullanarak (içeren bir tür hiyerarşisinde bir türüyle <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) içinde bir sonlandırıcı kesinlikle gerekir yürütme zorlanmış uygulama etki alanı kaldırır ve iş parçacığı karşısında bile durumlar için durdurur.</span><span class="sxs-lookup"><span data-stu-id="40863-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="40863-203">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="40863-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="40863-204">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="40863-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40863-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40863-205">See also</span></span>

- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="40863-206">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="40863-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="40863-207">Ortak Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="40863-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
- [<span data-ttu-id="40863-208">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="40863-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)

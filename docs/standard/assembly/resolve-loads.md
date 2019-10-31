---
title: Derleme yüklerini çözme
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 6a49c070bd7d2e3819044c6bb653671a2fc8199f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106991"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="5d8ad-102">Derleme yüklerini çözme</span><span class="sxs-lookup"><span data-stu-id="5d8ad-102">Resolve assembly loads</span></span>
<span data-ttu-id="5d8ad-103">.NET, derleme yüklemesi üzerinde daha fazla denetim gerektiren uygulamalar için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-103">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="5d8ad-104">Uygulamanız, bu olayı işleyerek, yük bağlamına normal yoklama yollarının dışından bir derleme yükleyebilir, kaç tane derleme sürümünden hangilerinin yükleneceğini seçebilir, dinamik bir derlemeyi yayarak ve bu şekilde devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-104">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="5d8ad-105">Bu konu, <xref:System.AppDomain.AssemblyResolve> olayını işlemeye yönelik rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-105">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d8ad-106">Yalnızca yansıma bağlamındaki derleme yüklerini çözümlemek için bunun yerine <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> olayını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-106">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="5d8ad-107">AssemblyResolve olayı nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="5d8ad-107">How the AssemblyResolve event works</span></span>  
 <span data-ttu-id="5d8ad-108"><xref:System.AppDomain.AssemblyResolve> olayı için bir işleyici kaydettiğinizde, çalışma zamanı bir derlemeye ada göre bağlama başarısız olduğunda işleyici çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-108">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="5d8ad-109">Örneğin, kullanıcı kodundan aşağıdaki yöntemleri çağırmak <xref:System.AppDomain.AssemblyResolve> olayının oluşturulmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="5d8ad-109">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="5d8ad-110">İlk bağımsız değişkeni, yüklenecek derlemenin görünen adını temsil eden bir dize olan (yani <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özelliği tarafından döndürülen dize) bir <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntem aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-110">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="5d8ad-111">İlk bağımsız değişkeni yüklenecek derlemeyi tanımlayan bir <xref:System.Reflection.AssemblyName> nesnesi olan bir <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-111">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="5d8ad-112"><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-112">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="5d8ad-113">Başka bir uygulama etki alanındaki bir nesneyi örnekleyen bir <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-113">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="5d8ad-114">Olay işleyicisinin yaptığı</span><span class="sxs-lookup"><span data-stu-id="5d8ad-114">What the event handler does</span></span>  
 <span data-ttu-id="5d8ad-115"><xref:System.AppDomain.AssemblyResolve> olayının işleyicisi, yüklenecek derlemenin görünen adını <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özelliğinde alır.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-115">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5d8ad-116">İşleyici derleme adını tanımıyorsa, `null` (C#), `Nothing` (Visual Basic) veya `nullptr` (görsel C++) döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-116">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="5d8ad-117">İşleyici derleme adını tanırsa, isteği karşılayan bir derlemeyi yükleyebilir ve döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-117">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="5d8ad-118">Aşağıdaki listede bazı örnek senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-118">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="5d8ad-119">İşleyici derlemenin bir sürümünün konumunu biliyorsa, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> yöntemini kullanarak derlemeyi yükleyebilir ve başarılı olursa yüklenen derlemeyi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-119">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="5d8ad-120">İşleyicinin bayt dizileri olarak depolanan derlemelerin bir veritabanına erişimi varsa, bayt dizisi alan <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemelerinin birini kullanarak bir bayt dizisi yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-120">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="5d8ad-121">İşleyici dinamik bir derleme üretebilir ve döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-121">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d8ad-122">İşleyici, derlemeyi yük bağlamı içine, yük bağlamına veya Bağlamsız olarak yüklemesi gerekir. İşleyici derlemeyi yalnızca yansıma bağlamına <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> yöntemini kullanarak yüklerse, <xref:System.AppDomain.AssemblyResolve> olayını oluşturan yük girişimi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-122">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="5d8ad-123">Bu, uygun bir derlemeyi döndürecek olay işleyicisinin sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-123">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="5d8ad-124">İşleyici, <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özellik değerini <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> oluşturucusuna geçirerek istenen derlemenin görünen adını ayrıştırabilirler.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-124">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="5d8ad-125">.NET Framework 4 ' ten başlayarak, işleyici, geçerli isteğin başka bir derlemenin bağımlılığı olup olmadığını anlamak için <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliğini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-125">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="5d8ad-126">Bu bilgiler, bağımlılığı karşılayan bir derlemeyi belirlemesine yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-126">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="5d8ad-127">Olay işleyicisi derlemenin farklı bir sürümünü istenen sürümden döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-127">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="5d8ad-128">Çoğu durumda, işleyici tarafından döndürülen derleme, işleyicinin onu içine yüklediği bağlamdan bağımsız olarak yükleme bağlamında görünür.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-128">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="5d8ad-129">Örneğin, işleyici bir derlemeyi yük-from bağlamına yüklemek için <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemini kullanıyorsa, işleyici onu döndürdüğünde, derleme yükleme bağlamında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-129">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="5d8ad-130">Ancak, aşağıdaki örnekte, işleyici onu döndürdüğünde derleme bağlam olmadan görünür:</span><span class="sxs-lookup"><span data-stu-id="5d8ad-130">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="5d8ad-131">İşleyici bağlamı olmayan bir derlemeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-131">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="5d8ad-132"><xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliği null değil.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-132">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="5d8ad-133">İstekte bulunan derleme (yani, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliği tarafından döndürülen derleme), bağlam olmadan yükleniydi.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-133">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="5d8ad-134">Bağlamlar hakkında bilgi için <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> yöntemi aşırı yüklemesi ' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-134">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="5d8ad-135">Aynı derlemenin birden çok sürümü aynı uygulama etki alanına yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-135">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="5d8ad-136">Tür atama sorunlarına yol açabildiğinden bu uygulama önerilmez.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-136">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="5d8ad-137">Bkz. [derleme yüklemesi Için en iyi uygulamalar](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="5d8ad-137">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="5d8ad-138">Olay işleyicisinin yapması gereken</span><span class="sxs-lookup"><span data-stu-id="5d8ad-138">What the event handler should not do</span></span>  
<span data-ttu-id="5d8ad-139"><xref:System.AppDomain.AssemblyResolve> olayını işlemeye yönelik birincil kural, tanımadığınız bir derlemeyi döndürmeye çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-139">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="5d8ad-140">İşleyiciyi yazdığınızda hangi derlemelerin olay oluşturulmasına neden olabileceğini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-140">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="5d8ad-141">İşleyiciniz diğer derlemeler için null değer döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-141">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="5d8ad-142">.NET Framework 4 ' ten başlayarak, <xref:System.AppDomain.AssemblyResolve> olayı uydu derlemeleri için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-142">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="5d8ad-143">Bu değişiklik, işleyici tüm derleme yükleme isteklerini çözümlemeye çalışırsa .NET Framework önceki bir sürümü için yazılmış bir olay işleyicisini etkiler.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-143">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="5d8ad-144">Tanımadığı derlemeleri yoksaymayan olay işleyicileri bu değişiklikten etkilenmez: null döndürür ve normal geri dönüş mekanizmaları izlenir.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-144">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="5d8ad-145">Bir derlemeyi yüklerken, olay işleyicisi bir yığın taşmasına yol açabileceğinden, <xref:System.AppDomain.AssemblyResolve> olayının yinelemeli olarak oluşturulmasına neden olabilecek <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemelerinin hiçbirini kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-145">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="5d8ad-146">(Bu konunun önceki kısımlarında sunulan listeye bakın.) Tüm olay işleyicileri döndürülünceye kadar hiçbir özel durum oluşturulmadığından, yükleme isteği için özel durum işleme sağlıyorsanız bile bu durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="5d8ad-147">Bu nedenle, `MyAssembly` bulunamazsa aşağıdaki kod yığın taşmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="5d8ad-147">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e) 
    {
        Console::WriteLine("Resolving {0}", e->Name);
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    } 
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        } 
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e) 
    {
        Console.WriteLine("Resolving {0}", e.Name);
        return Assembly.Load(e.Name);
    }
} 

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System
Imports System.Reflection

Class BadExample

    Shared Sub Main()
    
        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

## <a name="see-also"></a><span data-ttu-id="5d8ad-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-148">See also</span></span>

- [<span data-ttu-id="5d8ad-149">Derleme yükleme için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="5d8ad-149">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="5d8ad-150">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="5d8ad-150">Use application domains</span></span>](../../framework/app-domains/use.md)

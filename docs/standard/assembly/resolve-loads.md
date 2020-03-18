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
ms.openlocfilehash: d6314fae266505fbb4410aaaa351973070ab3811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156445"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="89909-102">Derleme yüklerini çözme</span><span class="sxs-lookup"><span data-stu-id="89909-102">Resolve assembly loads</span></span>
<span data-ttu-id="89909-103">.NET, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> montaj yüklemesi üzerinde daha fazla denetim gerektiren uygulamalar için olay sağlar.</span><span class="sxs-lookup"><span data-stu-id="89909-103">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="89909-104">Bu olayı işleyerek, uygulamanız normal sondalama yollarının dışından bir derlemeyi yükleyebilir, yüklemek için birkaç montaj sürümünden hangisini seçebilir, dinamik bir derleme yontabilir ve döndürebilir ve böylece devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="89909-104">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="89909-105">Bu <xref:System.AppDomain.AssemblyResolve> konu, olayı işlemek için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="89909-105">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89909-106">Yalnızca yansıma bağlamında montaj yüklerini çözmek için <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> olayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="89909-106">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="89909-107">AssemblyResolve olayı nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="89909-107">How the AssemblyResolve event works</span></span>  
 <span data-ttu-id="89909-108"><xref:System.AppDomain.AssemblyResolve> Olay için bir işleyici kaydettiğinizde, çalışma zamanı ada göre derlemeye bağlanamayınca işleyici çağrılır.</span><span class="sxs-lookup"><span data-stu-id="89909-108">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="89909-109">Örneğin, kullanıcı kodundan aşağıdaki yöntemleri çağırmak <xref:System.AppDomain.AssemblyResolve> olayın yükseltilmesine neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="89909-109">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="89909-110">İlk <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> bağımsız değişkeni yüklemek için derlemenin görüntü adını temsil eden bir dize olan bir yöntem aşırı yükleme (diğer <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> bir şekilde, <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özellik tarafından döndürülen dize).</span><span class="sxs-lookup"><span data-stu-id="89909-110">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="89909-111">İlk <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> bağımsız değişkeni yüklenmesi için derlemeyi tanımlayan bir nesne olan bir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.AssemblyName> yöntem aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="89909-111">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="89909-112">Aşırı <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="89909-112">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="89909-113">Başka <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> bir uygulama etki alanında bir nesneyi anında alan bir veya yöntem aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="89909-113">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="89909-114">Olay işleyicisi ne yapar</span><span class="sxs-lookup"><span data-stu-id="89909-114">What the event handler does</span></span>  
 <span data-ttu-id="89909-115">Olayın işleyicisi, <xref:System.AppDomain.AssemblyResolve> <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özellikte yüklenecek derlemenin görüntü adını alır.</span><span class="sxs-lookup"><span data-stu-id="89909-115">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="89909-116">İşleyici derleme adını tanımıyorsa, (C#), `null` `Nothing` (Visual Basic) `nullptr` veya (Visual C++) döndürür.</span><span class="sxs-lookup"><span data-stu-id="89909-116">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="89909-117">İşleyici montaj adını tanırsa, isteği karşılayan bir derleme yükleyebilir ve döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="89909-117">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="89909-118">Aşağıdaki listede bazı örnek senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89909-118">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="89909-119">İşleyici, derlemenin bir sürümünün konumunu biliyorsa, veya <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> yöntemi kullanarak derlemeyi yükleyebilir ve başarılı olursa yüklenen derlemeyi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="89909-119">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="89909-120">İşleyici, bayt dizileri olarak depolanan derlemeler veritabanına erişebiliyorsa, bayt dizisini alan <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemin aşırı yüklenmesi yönteminden birini kullanarak bir bayt dizisini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="89909-120">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="89909-121">İşleyici dinamik bir derleme oluşturabilir ve döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="89909-121">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89909-122">Işleyici, derlemeyi yük bağlamına, yük bağlamına veya bağlam olmadan yüklemelidir. Işleyici, derlemeyi <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> yalnızca yansıma bağlamına, <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> yöntemi veya yöntemi kullanarak yüklerse, <xref:System.AppDomain.AssemblyResolve> olayı yükselten yük girişimi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="89909-122">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="89909-123">Uygun bir derlemeyi döndürmek olay işleyicisinin sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="89909-123">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="89909-124">İşleyici, <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özellik değerini <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> oluşturucuya geçirerek istenen derlemenin görüntü adını ayrıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="89909-124">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="89909-125">.NET Framework 4'ten başlayarak, işleyici geçerli isteğin başka bir derlemenin bağımlılığı olup olmadığını belirlemek için <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliği kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="89909-125">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="89909-126">Bu bilgiler, bağımlılığı karşılayacak bir derleme belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="89909-126">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="89909-127">Olay işleyicisi, derlemenin istenen sürümden farklı bir sürümünü döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="89909-127">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="89909-128">Çoğu durumda, işleyici tarafından döndürülen derleme, işleyicinin yükettiği bağlamdan bağımsız olarak yük bağlamında görünür.</span><span class="sxs-lookup"><span data-stu-id="89909-128">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="89909-129">Örneğin, işleyici bir derlemeyi yük ten bağlamına yüklemek için <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi kullanırsa, işleyici onu döndürdüğünde derleme yük bağlamında görünür.</span><span class="sxs-lookup"><span data-stu-id="89909-129">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="89909-130">Ancak, aşağıdaki durumda işleyici döndürdüğünde derleme bağlamsız görünür:</span><span class="sxs-lookup"><span data-stu-id="89909-130">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="89909-131">Işleyici bağlam olmadan bir derleme yükler.</span><span class="sxs-lookup"><span data-stu-id="89909-131">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="89909-132">Mülk <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> hükümsüz değil.</span><span class="sxs-lookup"><span data-stu-id="89909-132">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="89909-133">İstenen derleme (diğer bir şekilde, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özellik tarafından döndürülen derleme) bağlam olmadan yüklendi.</span><span class="sxs-lookup"><span data-stu-id="89909-133">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="89909-134">Bağlamlar hakkında bilgi için <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> aşırı yükleme yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="89909-134">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="89909-135">Aynı derlemenin birden çok sürümü aynı uygulama etki alanına yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="89909-135">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="89909-136">Tür atama sorunlarına yol açabileceğinden, bu uygulama önerilmez.</span><span class="sxs-lookup"><span data-stu-id="89909-136">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="89909-137">[Montaj yüklemesi için en iyi uygulamalara](../../framework/deployment/best-practices-for-assembly-loading.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="89909-137">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="89909-138">Olay işleyicisinin yapmaması gerekenler</span><span class="sxs-lookup"><span data-stu-id="89909-138">What the event handler should not do</span></span>  
<span data-ttu-id="89909-139"><xref:System.AppDomain.AssemblyResolve> Olayı işlemek için birincil kural, tanımadığınız bir derlemeyi döndürmeye çalışmamanız gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="89909-139">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="89909-140">Işleyiciyi yazarken, hangi derlemelerin olayın yükseltilmesine neden olabileceğini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89909-140">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="89909-141">Amiriniz diğer derlemeler için null döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="89909-141">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="89909-142">.NET Framework 4'ten <xref:System.AppDomain.AssemblyResolve> başlayarak, uydu meclisleri için etkinlik yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="89909-142">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="89909-143">İşleyici tüm derleme yük isteklerini çözmeye çalışırsa, bu değişiklik .NET Framework'ün önceki bir sürümü için yazılmış bir olay işleyicisini etkiler.</span><span class="sxs-lookup"><span data-stu-id="89909-143">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="89909-144">Tanımadıkları derlemeleri yok sayan olay işleyicileri bu değişiklikten etkilenmez: Null döndürürler ve normal geri dönüş mekanizmaları izlenir.</span><span class="sxs-lookup"><span data-stu-id="89909-144">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="89909-145">Bir derleme yüklerken, <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.AppDomain.AssemblyResolve> olay işleyicisi olayın yinelemeli olarak yükseltilmesine neden olabilecek aşırı yüklemeleri kullanmamalıdır, çünkü bu bir yığın taşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="89909-145">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="89909-146">(Bu konuda daha önce verilen listeye bakın.) Tüm olay işleyicileri döndürülene kadar özel durum atılmadığından, yük isteği için özel durum işleme yi sağlasanız bile bu durum gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="89909-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="89909-147">Böylece, aşağıdaki kod bulunamazsa bir `MyAssembly` yığın taşması ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="89909-147">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="89909-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89909-148">See also</span></span>

- [<span data-ttu-id="89909-149">Montaj yüklemesi için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="89909-149">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="89909-150">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="89909-150">Use application domains</span></span>](../../framework/app-domains/use.md)

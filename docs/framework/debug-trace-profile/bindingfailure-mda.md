---
title: bindingFailure MDA
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e904d452b9f4a1b172d35984b752c0d97228338
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480956"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="862cc-102">bindingFailure MDA</span><span class="sxs-lookup"><span data-stu-id="862cc-102">bindingFailure MDA</span></span>

<span data-ttu-id="862cc-103">`bindingFailure` Yönetilen hata ayıklama Yardımcısı (MDA) yüklemek bir derleme başarısız olduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="862cc-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>

## <a name="symptoms"></a><span data-ttu-id="862cc-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="862cc-104">Symptoms</span></span>

<span data-ttu-id="862cc-105">Kod gibi statik başvuru veya yükleyici yöntemlerden birini kullanarak bir derlemeyi yüklemek denediğini <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="862cc-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="862cc-106">Derleme yüklü değil ve bir <xref:System.IO.FileNotFoundException> veya <xref:System.IO.FileLoadException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="862cc-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>

## <a name="cause"></a><span data-ttu-id="862cc-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="862cc-107">Cause</span></span>

<span data-ttu-id="862cc-108">Çalışma zamanının bir derlemeyi yükleyemedi bağlama hatası gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="862cc-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="862cc-109">Bağlama hatası sonucu aşağıdaki durumlardan biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="862cc-109">A binding failure might be the result of one of the following situations:</span></span>

- <span data-ttu-id="862cc-110">Ortak dil çalışma zamanı (CLR), istenen derlemesi bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="862cc-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="862cc-111">Bu, yüklü derleme veya derleme bulmak için düzgün yapılandırılmamış uygulama gibi oluşabilir birçok neden vardır.</span><span class="sxs-lookup"><span data-stu-id="862cc-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>

- <span data-ttu-id="862cc-112">Ortak bir sorunu senaryosu, diğer uygulama etki alanında bu türü içeren derlemenin yüklenecek CLR gerektiren başka bir uygulama etki alanına bir tür geçiyor.</span><span class="sxs-lookup"><span data-stu-id="862cc-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="862cc-113">Bu, diğer uygulama etki alanı özgün uygulama etki alanından farklı şekilde yapılandırılmışsa, derlemeyi yüklemeye çalışma zamanı için mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="862cc-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="862cc-114">Örneğin, iki uygulama etki alanları farklı olabilir <xref:System.AppDomain.BaseDirectory%2A> özellik değerleri.</span><span class="sxs-lookup"><span data-stu-id="862cc-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>

- <span data-ttu-id="862cc-115">İstenen derleme bozuk veya bir derleme değil.</span><span class="sxs-lookup"><span data-stu-id="862cc-115">The requested assembly is corrupted or is not an assembly.</span></span>

- <span data-ttu-id="862cc-116">Bütünleştirilmiş kod yüklemeye çalışan kod derlemeleri yüklemek için doğru kod erişimi güvenliği izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="862cc-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>

- <span data-ttu-id="862cc-117">Kullanıcı kimlik bilgileri, dosyayı okumak için gerekli izinlere sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="862cc-117">The user credentials do not provide the required permissions to read the file.</span></span>

## <a name="resolution"></a><span data-ttu-id="862cc-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="862cc-118">Resolution</span></span>

<span data-ttu-id="862cc-119">İlk adım, neden CLR istenen derlemeye bağlanamadı belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="862cc-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="862cc-120">Neden çalışma zamanı bulunamadı veya olabilirsiniz senaryoları gibi istenen derleme nedeni bölümünde listelenen mümkün yük olan birçok neden vardır.</span><span class="sxs-lookup"><span data-stu-id="862cc-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="862cc-121">Bağlama hatanın nedenini ortadan kaldırmak için aşağıdaki eylemleri önerilir:</span><span class="sxs-lookup"><span data-stu-id="862cc-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>

- <span data-ttu-id="862cc-122">Tarafından sağlanan verileri kullanarak nedenini `bindingFailure` MDA:</span><span class="sxs-lookup"><span data-stu-id="862cc-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>

  - <span data-ttu-id="862cc-123">Çalıştırma [Fuslogvw.exe (Derleme bağlaması Günlük Görüntüleyici)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) derleme cildiyle üretilen hata günlüklerini okumak için.</span><span class="sxs-lookup"><span data-stu-id="862cc-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>

  - <span data-ttu-id="862cc-124">Derleme için istenen konumu olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="862cc-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="862cc-125">Durumunda, <xref:System.Reflection.Assembly.LoadFrom%2A> ve <xref:System.Reflection.Assembly.LoadFile%2A> yöntemleri, istenen konumu kolayca belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="862cc-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="862cc-126">Durumunda, <xref:System.Reflection.Assembly.Load%2A> derleme kimliği kullanarak bağlanan, yöntem, gerekir arayın uygulama etki alanının içinde bu kimlikle eşleşen derlemeleri <xref:System.AppDomain.BaseDirectory%2A> özellik araştırma yolu ve genel derleme önbelleği.</span><span class="sxs-lookup"><span data-stu-id="862cc-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>

- <span data-ttu-id="862cc-127">Önceki belirlemeye dayalı nedenini çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="862cc-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="862cc-128">Olası çözüm seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="862cc-128">Possible resolution options are the following:</span></span>

  - <span data-ttu-id="862cc-129">İstenen derlemeyi genel bütünleştirilmiş kod önbelleğine ve çağrı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="862cc-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="862cc-130"><xref:System.Reflection.Assembly.Load%2A> derleme kimliği tarafından yükleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="862cc-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="862cc-131">İstenen derleme arama ve uygulama dizini kopyalamak <xref:System.Reflection.Assembly.Load%2A> yöntemi tarafından kimlik derlemesi yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="862cc-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="862cc-132">Uygulama etki bağlama hatası oluştuğu derleme yolu ya da değiştirerek içerecek şekilde yeniden <xref:System.AppDomain.BaseDirectory%2A> özelliği veya özel bir yoklama yolu ekleme.</span><span class="sxs-lookup"><span data-stu-id="862cc-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>

  - <span data-ttu-id="862cc-133">Dosyayı okumak oturum açan kullanıcının izin vermek bir dosya için erişim denetim listesini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="862cc-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="862cc-134">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="862cc-134">Effect on the Runtime</span></span>

<span data-ttu-id="862cc-135">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="862cc-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="862cc-136">Yalnızca hataları bağlama hakkında veri bildirir.</span><span class="sxs-lookup"><span data-stu-id="862cc-136">It only reports data about binding failures.</span></span>

## <a name="output"></a><span data-ttu-id="862cc-137">Çıkış</span><span class="sxs-lookup"><span data-stu-id="862cc-137">Output</span></span>

<span data-ttu-id="862cc-138">İstenen yol dahil olmak üzere, yük ve/veya görünen adı, bağlama bağlamı, yükü istenen uygulama etki alanı için başarısız olan derlemenin ve hatanın nedenini MDA bildirir.</span><span class="sxs-lookup"><span data-stu-id="862cc-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>

<span data-ttu-id="862cc-139">Görünen ad veya istenen yol verileri CLR için kullanılabilir değilse boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="862cc-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="862cc-140">Başarısız olan çağrı ise <xref:System.Reflection.Assembly.Load%2A> yöntemi, bu büyük olasılıkla çalışma zamanı derlemenin görünen adı belirleyemedi.</span><span class="sxs-lookup"><span data-stu-id="862cc-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>

## <a name="configuration"></a><span data-ttu-id="862cc-141">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="862cc-141">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="862cc-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="862cc-142">Example</span></span>

<span data-ttu-id="862cc-143">Aşağıdaki kod örneği, bu mda'nın etkinleştirebilmek için bir durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="862cc-143">The following code example demonstrates a situation that can activate this MDA:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            // This call attempts to load a nonexistent assembly.
            // The call will throw a System.IO.FileNotFound exception
            // and cause the activation of the bindingFailure MDA
            // if it is registered.
            Assembly.Load("NonExistentAssembly");
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="862cc-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="862cc-144">See also</span></span>

- [<span data-ttu-id="862cc-145">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="862cc-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

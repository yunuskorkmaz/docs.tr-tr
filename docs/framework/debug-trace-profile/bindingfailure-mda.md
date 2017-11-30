---
title: bindingFailure MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 89c1ce4b39379aeae80240750cdbcd2e61b6ec11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="61fe4-102">bindingFailure MDA</span><span class="sxs-lookup"><span data-stu-id="61fe4-102">bindingFailure MDA</span></span>
<span data-ttu-id="61fe4-103">`bindingFailure` Yönetilen hata ayıklama Yardımcısı (MDA), bir derlemeyi yüklemek başarısız olduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="61fe4-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="61fe4-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="61fe4-104">Symptoms</span></span>  
 <span data-ttu-id="61fe4-105">Kod gibi statik başvuru veya yükleyici yöntemlerden birini kullanarak bir derlemeyi yüklemeye çalıştı <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="61fe4-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="61fe4-106">Derleme yüklü değil ve bir <xref:System.IO.FileNotFoundException> veya <xref:System.IO.FileLoadException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="61fe4-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="61fe4-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="61fe4-107">Cause</span></span>  
 <span data-ttu-id="61fe4-108">Çalışma zamanı bütünleştirilmiş yükleyemiyor bağlama hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="61fe4-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="61fe4-109">Bağlama hatası nedeni aşağıdaki durumlardan biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="61fe4-109">A binding failure might be the result of one of the following situations:</span></span>  
  
-   <span data-ttu-id="61fe4-110">Ortak dil çalışma zamanı (CLR) istenen derlemesi bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="61fe4-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="61fe4-111">Bu, yüklenmiyor derleme veya derleme bulmak için düzgün yapılandırılmamış uygulama gibi oluşabilir pek çok neden vardır.</span><span class="sxs-lookup"><span data-stu-id="61fe4-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>  
  
-   <span data-ttu-id="61fe4-112">Yaygın bir sorun senaryo, başka bir uygulama etki alanında o türünü içeren bütünleştirilmiş CLR gerektiren başka bir uygulama etki alanına bir türü geçiyor.</span><span class="sxs-lookup"><span data-stu-id="61fe4-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="61fe4-113">Bu, başka bir uygulama etki alanı özgün uygulama etki alanından farklı şekilde yapılandırılmışsa derlemeyi yüklemeye çalışma zamanı için mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="61fe4-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="61fe4-114">Örneğin, iki uygulama etki alanları farklı olabilir <xref:System.AppDomain.BaseDirectory%2A> özellik değerleri.</span><span class="sxs-lookup"><span data-stu-id="61fe4-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>  
  
-   <span data-ttu-id="61fe4-115">İstenen derlemeyi bozuk veya bir derleme değil.</span><span class="sxs-lookup"><span data-stu-id="61fe4-115">The requested assembly is corrupted or is not an assembly.</span></span>  
  
-   <span data-ttu-id="61fe4-116">Derleme yüklenmeye çalışılıyor kod derlemelerini yüklemek için doğru kod erişim güvenliği izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="61fe4-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>  
  
-   <span data-ttu-id="61fe4-117">Kullanıcı kimlik bilgileri dosyasını okumak için gerekli izinleri sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="61fe4-117">The user credentials do not provide the required permissions to read the file.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="61fe4-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="61fe4-118">Resolution</span></span>  
 <span data-ttu-id="61fe4-119">İlk adım, neden CLR istenen derlemeye bağlanamadı belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="61fe4-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="61fe4-120">Neden çalışma zamanı bulunamadı veya olabilirsiniz senaryoları gibi istenen derlemeyi neden bölümünde listelenen mümkün yük edilmiş pek çok neden vardır.</span><span class="sxs-lookup"><span data-stu-id="61fe4-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="61fe4-121">Aşağıdaki eylemleri bağlama hatanın nedenini ortadan kaldırmak için önerilir:</span><span class="sxs-lookup"><span data-stu-id="61fe4-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>  
  
-   <span data-ttu-id="61fe4-122">Tarafından sağlanan verileri kullanarak nedenini `bindingFailure` MDA:</span><span class="sxs-lookup"><span data-stu-id="61fe4-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>  
  
    -   <span data-ttu-id="61fe4-123">Çalıştırma [Fuslogvw.exe (Derleme bağlaması Günlük Görüntüleyici)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) derleme bağlayıcı tarafından üretilen hata günlüklerini okumak için.</span><span class="sxs-lookup"><span data-stu-id="61fe4-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>  
  
    -   <span data-ttu-id="61fe4-124">Derleme istenen konumda olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="61fe4-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="61fe4-125">Durumunda <xref:System.Reflection.Assembly.LoadFrom%2A> ve <xref:System.Reflection.Assembly.LoadFile%2A> yöntemleri, istenilen konuma kolayca belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="61fe4-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="61fe4-126">Durumunda <xref:System.Reflection.Assembly.Load%2A> derleme kimliğini kullanarak bağlar, yöntem, gerekir Ara uygulama etki alanı içinde bu kimliğiyle eşleşmesi derlemeleri <xref:System.AppDomain.BaseDirectory%2A> özellik araştırma yolu ve genel derleme önbelleği.</span><span class="sxs-lookup"><span data-stu-id="61fe4-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>  
  
-   <span data-ttu-id="61fe4-127">Önceki belirleme temel nedenini çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="61fe4-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="61fe4-128">Olası bir çözüm seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="61fe4-128">Possible resolution options are the following:</span></span>  
  
    -   <span data-ttu-id="61fe4-129">İstenen derlemeyi genel derleme önbelleği ve çağrı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="61fe4-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="61fe4-130"><xref:System.Reflection.Assembly.Load%2A>derleme kimliği tarafından yükleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61fe4-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="61fe4-131">İstenen derlemeyi uygulama dizini ve çağrı kopyalamak <xref:System.Reflection.Assembly.Load%2A> yöntemi kimliği tarafından derlemesi yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="61fe4-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="61fe4-132">Bağlama hatası oluştuğu ya da değiştirerek derleme yolu eklemek için uygulama etki alanı yeniden <xref:System.AppDomain.BaseDirectory%2A> özelliği veya özel araştırma yollar ekleme.</span><span class="sxs-lookup"><span data-stu-id="61fe4-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>  
  
    -   <span data-ttu-id="61fe4-133">Oturum açmış kullanıcının dosyayı okuma izni dosya için erişim denetim listesini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="61fe4-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="61fe4-134">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="61fe4-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="61fe4-135">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="61fe4-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="61fe4-136">Yalnızca hataları bağlama hakkında verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="61fe4-136">It only reports data about binding failures.</span></span>  
  
## <a name="output"></a><span data-ttu-id="61fe4-137">Çıkış</span><span class="sxs-lookup"><span data-stu-id="61fe4-137">Output</span></span>  
 <span data-ttu-id="61fe4-138">İstenen yol dahil olmak üzere, yükleme ve/veya görüntüleme adı, bağlama bağlamı, yükleme istendi uygulama etki alanı için başarısız olan derlemenin ve hatanın nedenini MDA raporlar.</span><span class="sxs-lookup"><span data-stu-id="61fe4-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>  
  
 <span data-ttu-id="61fe4-139">Görünen adı ya da istenen yol verileri CLR kullanılabilir değilse boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="61fe4-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="61fe4-140">Başarısız olan çağrı yapmak ise <xref:System.Reflection.Assembly.Load%2A> yöntemi, bu olası çalışma zamanı derlemesi için görünen ad belirleyemedi.</span><span class="sxs-lookup"><span data-stu-id="61fe4-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="61fe4-141">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="61fe4-141">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="61fe4-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="61fe4-142">Example</span></span>  
 <span data-ttu-id="61fe4-143">Aşağıdaki kod örneği, bu MDA etkinleştirebilirsiniz bir durumu gösterir:</span><span class="sxs-lookup"><span data-stu-id="61fe4-143">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="61fe4-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61fe4-144">See Also</span></span>  
 [<span data-ttu-id="61fe4-145">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="61fe4-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

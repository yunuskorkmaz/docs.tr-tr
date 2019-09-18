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
ms.openlocfilehash: 93c426cce792c8f30a3551e2d4626736dd67278f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052952"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="df472-102">bindingFailure MDA</span><span class="sxs-lookup"><span data-stu-id="df472-102">bindingFailure MDA</span></span>

<span data-ttu-id="df472-103">Yönetilen `bindingFailure` hata ayıklama Yardımcısı (MDA), bir derleme yükleme başarısız olduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="df472-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>

## <a name="symptoms"></a><span data-ttu-id="df472-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="df472-104">Symptoms</span></span>

<span data-ttu-id="df472-105">Kod, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> statik başvuru veya ya <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>da gibi Loader yöntemlerinden birini kullanarak bir derlemeyi yüklemeyi denedi.</span><span class="sxs-lookup"><span data-stu-id="df472-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="df472-106">Derleme yüklü değil ve bir <xref:System.IO.FileNotFoundException> veya <xref:System.IO.FileLoadException> özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="df472-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>

## <a name="cause"></a><span data-ttu-id="df472-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="df472-107">Cause</span></span>

<span data-ttu-id="df472-108">Çalışma zamanı bir derlemeyi yükleyemediğinde bağlama hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="df472-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="df472-109">Bir bağlama hatası, aşağıdaki durumlardan birinin sonucu olabilir:</span><span class="sxs-lookup"><span data-stu-id="df472-109">A binding failure might be the result of one of the following situations:</span></span>

- <span data-ttu-id="df472-110">Ortak dil çalışma zamanı (CLR) istenen derlemeyi bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="df472-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="df472-111">Bunun gerçekleşebileceği, derlemenin yüklü olmadığı veya uygulamanın derlemeyi bulmak için doğru şekilde yapılandırılmadığı birçok nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="df472-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>

- <span data-ttu-id="df472-112">Yaygın bir sorun senaryosu başka bir uygulama etki alanına bir tür geçirilerek, CLR 'nin diğer uygulama etki alanında bu türü içeren derlemeyi yüklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="df472-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="df472-113">Diğer uygulama etki alanı orijinal uygulama etki alanından farklı yapılandırılmışsa, çalışma zamanının derlemeyi yüklemesi mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="df472-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="df472-114">Örneğin, iki uygulama etki alanı farklı <xref:System.AppDomain.BaseDirectory%2A> özellik değerlerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="df472-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>

- <span data-ttu-id="df472-115">İstenen derleme bozuk veya bir derleme değil.</span><span class="sxs-lookup"><span data-stu-id="df472-115">The requested assembly is corrupted or is not an assembly.</span></span>

- <span data-ttu-id="df472-116">Derlemeyi yüklemeye çalışan kodun, derlemeleri yüklemek için doğru kod erişimi güvenlik izinleri yok.</span><span class="sxs-lookup"><span data-stu-id="df472-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>

- <span data-ttu-id="df472-117">Kullanıcı kimlik bilgileri, dosyayı okumak için gerekli izinleri sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="df472-117">The user credentials do not provide the required permissions to read the file.</span></span>

## <a name="resolution"></a><span data-ttu-id="df472-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="df472-118">Resolution</span></span>

<span data-ttu-id="df472-119">İlk adım, CLR 'nin istenen derlemeye neden bağlanmadığını belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="df472-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="df472-120">Çalışma zamanının istenen derlemeyi (nedeni bölümünde listelenen senaryolar gibi) bulmamasının pek çok nedeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="df472-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="df472-121">Bağlama hatasının nedenini ortadan kaldırmak için aşağıdaki eylemler önerilir:</span><span class="sxs-lookup"><span data-stu-id="df472-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>

- <span data-ttu-id="df472-122">`bindingFailure` Mda tarafından belirtilen verileri kullanarak nedenini belirleme:</span><span class="sxs-lookup"><span data-stu-id="df472-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>

  - <span data-ttu-id="df472-123">Derleme cildi tarafından üretilen hata günlüklerini okumak için [Fuslogvw. exe ' yi (derleme bağlama günlük Görüntüleyici)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df472-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>

  - <span data-ttu-id="df472-124">Derlemenin istenen konumda olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="df472-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="df472-125"><xref:System.Reflection.Assembly.LoadFrom%2A> Ve<xref:System.Reflection.Assembly.LoadFile%2A> yöntemleri söz konusu olduğunda, istenen konum kolayca belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="df472-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="df472-126">Derleme kimliğini kullanarak bağlanan <xref:System.Reflection.Assembly.Load%2A> yöntemi söz konusu olduğunda, uygulama <xref:System.AppDomain.BaseDirectory%2A> etki alanının özellik araştırma yolu ve genel derleme önbelleğinde bu kimlikle eşleşen derlemeler için arama yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="df472-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>

- <span data-ttu-id="df472-127">Önceki belirleme temelinde nedeni çözün.</span><span class="sxs-lookup"><span data-stu-id="df472-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="df472-128">Olası çözüm seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="df472-128">Possible resolution options are the following:</span></span>

  - <span data-ttu-id="df472-129">İstenen derlemeyi genel derleme önbelleğine yükleyip öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="df472-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="df472-130"><xref:System.Reflection.Assembly.Load%2A>derlemeyi kimliğe göre yükleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df472-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="df472-131">İstenen derlemeyi uygulama dizinine kopyalayın ve derlemeyi kimliğe göre yüklemek için <xref:System.Reflection.Assembly.Load%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="df472-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="df472-132"><xref:System.AppDomain.BaseDirectory%2A> Özelliği değiştirerek ya da özel yoklama yolları ekleyerek, derleme yolunu dahil etmek için bağlama hatasının oluştuğu uygulama etki alanını yeniden yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="df472-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>

  - <span data-ttu-id="df472-133">Oturum açan kullanıcının dosyayı okumasına izin vermek için dosya için erişim denetim listesini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="df472-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="df472-134">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="df472-134">Effect on the Runtime</span></span>

<span data-ttu-id="df472-135">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="df472-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="df472-136">Yalnızca bağlama hatalarıyla ilgili verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="df472-136">It only reports data about binding failures.</span></span>

## <a name="output"></a><span data-ttu-id="df472-137">Çıkış</span><span class="sxs-lookup"><span data-stu-id="df472-137">Output</span></span>

<span data-ttu-id="df472-138">MDA, istenen yol ve/veya görünen ad, bağlama bağlamı, yükün istendiği uygulama etki alanı ve hatanın nedeni dahil olmak üzere, yükleme başarısız olan derlemeyi rapor ediyor.</span><span class="sxs-lookup"><span data-stu-id="df472-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>

<span data-ttu-id="df472-139">Görünen ad veya istenen yol, verilerin CLR tarafından kullanılamadığı durumlarda boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="df472-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="df472-140">Başarısız olan çağrı <xref:System.Reflection.Assembly.Load%2A> yöntemi ise, çalışma zamanının derleme için görünen adı belirleyememe olasıdır.</span><span class="sxs-lookup"><span data-stu-id="df472-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>

## <a name="configuration"></a><span data-ttu-id="df472-141">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="df472-141">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="df472-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="df472-142">Example</span></span>

<span data-ttu-id="df472-143">Aşağıdaki kod örneğinde, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="df472-143">The following code example demonstrates a situation that can activate this MDA:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="df472-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df472-144">See also</span></span>

- [<span data-ttu-id="df472-145">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="df472-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)

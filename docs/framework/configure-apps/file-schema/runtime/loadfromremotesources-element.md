---
title: <loadFromRemoteSources> Öğesi
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8e8663bf9d119007eb7d3771d16d55b1aa54856
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663601"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="c4511-102">\<loadFromRemoteSources > öğesi</span><span class="sxs-lookup"><span data-stu-id="c4511-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="c4511-103">.NET Framework 4 ve üzeri sürümlerde uzak kaynaklardan yüklenen derlemelerin tam güven verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4511-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="c4511-104">Visual Studio proje hata listesindeki bir hata iletisi veya bir derleme hatası nedeniyle bu makaleye yönlendirilmiş olmanız durumunda bkz [. nasıl yapılır: Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))'da Web 'Den bir bütünleştirilmiş kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4511-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
 <span data-ttu-id="c4511-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c4511-105">\<configuration></span></span>  
<span data-ttu-id="c4511-106">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="c4511-106">\<runtime></span></span>  
<span data-ttu-id="c4511-107">\<loadFromRemoteSources ></span><span class="sxs-lookup"><span data-stu-id="c4511-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4511-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4511-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4511-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c4511-109">Attributes and elements</span></span>
 <span data-ttu-id="c4511-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4511-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4511-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4511-111">Attributes</span></span>  
  
|<span data-ttu-id="c4511-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c4511-112">Attribute</span></span>|<span data-ttu-id="c4511-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4511-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c4511-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c4511-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="c4511-115">Uzak bir kaynaktan yüklenen bir derlemeye tam güven verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4511-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c4511-116">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="c4511-116">enabled attribute</span></span>  
  
|<span data-ttu-id="c4511-117">Değer</span><span class="sxs-lookup"><span data-stu-id="c4511-117">Value</span></span>|<span data-ttu-id="c4511-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4511-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c4511-119">Uzak kaynaklardaki uygulamalara tam güven vermeyin.</span><span class="sxs-lookup"><span data-stu-id="c4511-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="c4511-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c4511-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c4511-121">Uzak kaynaklardaki uygulamalara tam güven verme.</span><span class="sxs-lookup"><span data-stu-id="c4511-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4511-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c4511-122">Child elements</span></span>  
 <span data-ttu-id="c4511-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4511-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4511-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c4511-124">Parent elements</span></span>  
  
|<span data-ttu-id="c4511-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4511-125">Element</span></span>|<span data-ttu-id="c4511-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4511-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c4511-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c4511-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c4511-128">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c4511-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4511-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4511-129">Remarks</span></span>

<span data-ttu-id="c4511-130">.NET Framework 3,5 ve önceki sürümlerde, uzak bir konumdan bir derlemeyi yüklerseniz, derlemedeki kod, yüklendiği bölgeye bağlı bir izin kümesiyle kısmi güvende çalışır.</span><span class="sxs-lookup"><span data-stu-id="c4511-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="c4511-131">Örneğin, bir Web sitesinden derleme yüklerseniz Internet bölgesine yüklenir ve Internet izin kümesi verilir.</span><span class="sxs-lookup"><span data-stu-id="c4511-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="c4511-132">Diğer bir deyişle, bir Internet korumalı alanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c4511-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="c4511-133">Kod erişim güvenliği (CAS) ilkesi, .NET Framework 4 ile başlayarak devre dışıdır ve derlemeler tam güvende yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c4511-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="c4511-134">Normalde, bu, daha önce korumalı olan <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemle yüklenen derlemelere tam güven verir.</span><span class="sxs-lookup"><span data-stu-id="c4511-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="c4511-135">Bunu engellemek için, uzak bir kaynaktan yüklenen derlemelerde kod çalıştırma özelliği varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c4511-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="c4511-136">Varsayılan olarak, uzak bir derlemeyi yüklemeye çalışırsanız, aşağıdakine benzer bir <xref:System.IO.FileLoadException> özel durum iletisi ile oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="c4511-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="c4511-137">Derlemeyi yüklemek ve kodunu yürütmek için şunlardan birini yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c4511-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="c4511-138">Derleme için açık bir korumalı alan oluşturun (bkz [. nasıl yapılır: Bir korumalı alana](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)kısmen güvenilen kod çalıştırın).</span><span class="sxs-lookup"><span data-stu-id="c4511-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="c4511-139">Derlemenin kodunu tam güvende çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c4511-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="c4511-140">Bunu, `<loadFromRemoteSources>` öğesini yapılandırarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4511-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="c4511-141">.NET Framework önceki sürümlerinde bulunan kısmi güvende çalışan derlemelerin artık .NET Framework 4 ve sonraki sürümlerde tam güvende çalıştığını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c4511-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4511-142">Derlemenin tam güvende çalıştırılmamalıdır, bu yapılandırma öğesini ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="c4511-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="c4511-143">Bunun yerine, derlemenin yükleneceği <xref:System.AppDomain> bir korumalı alan oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4511-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="c4511-144">Öğesi için özniteliği yalnızca kod erişim güvenliği (CAS) devre dışı bırakıldığında etkilidir. `enabled` `<loadFromRemoteSources>`</span><span class="sxs-lookup"><span data-stu-id="c4511-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="c4511-145">Varsayılan olarak, CA ilkesi .NET Framework 4 ve sonraki sürümlerde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c4511-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="c4511-146">`enabled` Olarak`true`ayarlarsanız, uzak derlemelere tam güven verilir.</span><span class="sxs-lookup"><span data-stu-id="c4511-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="c4511-147">, Olarak `true`ayarlanmamışsa, aşağıdaki koşullardan biri <xref:System.IO.FileLoadException> altında bir oluşturulur: `enabled`</span><span class="sxs-lookup"><span data-stu-id="c4511-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="c4511-148">Geçerli etki alanının korumalı alana alma davranışı, .NET Framework 3,5 ' deki davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c4511-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="c4511-149">Bu, CAS ilkesinin devre dışı bırakılması ve geçerli etki alanının korumalı olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4511-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="c4511-150">Yüklenen derleme `MyComputer` bölgeden değil.</span><span class="sxs-lookup"><span data-stu-id="c4511-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="c4511-151">Öğesi için `<loadFromRemoteSources>` `true` ayarı, bu özel durumun oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="c4511-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="c4511-152">Ortak dil çalışma zamanına bağlı olarak, güvenlik için yüklenmiş derlemeleri korumalı hale getirmenizi ve tam güvende yürütülmesine izin verilip verilmeyeceğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4511-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="c4511-153">Notlar</span><span class="sxs-lookup"><span data-stu-id="c4511-153">Notes</span></span>

- <span data-ttu-id="c4511-154">.NET Framework 4,5 ve sonraki sürümlerinde, yerel ağ paylaşımlarında derlemeler varsayılan olarak tam güvende çalışır; `<loadFromRemoteSources>` öğesini etkinleştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c4511-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="c4511-155">Bir uygulama Web 'den kopyalanmışsa, bu, yerel bilgisayarda bulunsa bile, Windows tarafından bir Web uygulaması olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="c4511-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="c4511-156">Dosya özelliklerini değiştirerek bu belirtimi değiştirebilir veya derlemeye tam güven sağlamak için `<loadFromRemoteSources>` öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4511-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="c4511-157">Alternatif olarak, işletim sisteminin Web 'den yüklenmiş olarak işaretlediğini belirten yerel bir derlemeyi yüklemek için <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4511-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="c4511-158">Bir Windows sanal bilgisayar uygulamasında çalışan bir uygulama içindealabilirsiniz.<xref:System.IO.FileLoadException></span><span class="sxs-lookup"><span data-stu-id="c4511-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="c4511-159">Bu, barındırma bilgisayarındaki bağlantılı klasörlerden bir dosya yüklemeye çalıştığınızda meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="c4511-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="c4511-160">Ayrıca, [Uzak Masaüstü Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Hizmetleri) üzerinden bağlanmış bir klasörden dosya yüklemeye çalıştığınızda da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="c4511-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="c4511-161">Özel durumdan kaçınmak için, olarak `enabled` `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c4511-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="c4511-162">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="c4511-162">Configuration file</span></span>

<span data-ttu-id="c4511-163">Bu öğe genellikle uygulama yapılandırma dosyasında kullanılır, ancak bağlama göre diğer yapılandırma dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4511-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="c4511-164">Daha fazla bilgi için, .NET güvenlik bloguna [AIT CA 'Ların daha örtük kullanımları: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="c4511-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="c4511-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4511-165">Example</span></span>

<span data-ttu-id="c4511-166">Aşağıdaki örnek, uzak kaynaklardan yüklenen derlemelere nasıl tam güven verildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4511-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="c4511-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4511-167">See also</span></span>

- [<span data-ttu-id="c4511-168">CAS Ilkesinin daha örtük kullanımları: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="c4511-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [<span data-ttu-id="c4511-169">Nasıl yapılır: Bir korumalı alanda kısmen güvenilen kod Çalıştır</span><span class="sxs-lookup"><span data-stu-id="c4511-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="c4511-170">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c4511-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c4511-171">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="c4511-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

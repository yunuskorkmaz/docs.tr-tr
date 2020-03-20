---
title: <loadFromRemoteSources> Öğesi
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154068"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="57aa8-102">\<loadFromRemoteSources> elemanı</span><span class="sxs-lookup"><span data-stu-id="57aa8-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="57aa8-103">Uzak kaynaklardan yüklenen derlemelerin .NET Framework 4 ve sonraki lerine tam güven verilip verilmemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="57aa8-104">Visual Studio proje hata listesindeki bir hata iletisi veya yapı hatası nedeniyle bu makaleye yönlendirildiyseniz, [bkz.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="57aa8-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="57aa8-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="57aa8-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="57aa8-106">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="57aa8-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="57aa8-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span><span class="sxs-lookup"><span data-stu-id="57aa8-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57aa8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57aa8-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57aa8-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="57aa8-109">Attributes and elements</span></span>
 <span data-ttu-id="57aa8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57aa8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57aa8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57aa8-111">Attributes</span></span>  
  
|<span data-ttu-id="57aa8-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="57aa8-112">Attribute</span></span>|<span data-ttu-id="57aa8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57aa8-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="57aa8-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="57aa8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="57aa8-115">Uzak bir kaynaktan yüklenen bir derlemeye tam güven verilip verilmemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="57aa8-116">etkin öznitelik</span><span class="sxs-lookup"><span data-stu-id="57aa8-116">enabled attribute</span></span>  
  
|<span data-ttu-id="57aa8-117">Değer</span><span class="sxs-lookup"><span data-stu-id="57aa8-117">Value</span></span>|<span data-ttu-id="57aa8-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57aa8-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="57aa8-119">Uzak kaynaklardan gelen uygulamalara tam güven vermeyin.</span><span class="sxs-lookup"><span data-stu-id="57aa8-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="57aa8-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="57aa8-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="57aa8-121">Uzak kaynaklardan gelen uygulamalara tam güven tanıyın.</span><span class="sxs-lookup"><span data-stu-id="57aa8-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57aa8-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="57aa8-122">Child elements</span></span>  
 <span data-ttu-id="57aa8-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="57aa8-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57aa8-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="57aa8-124">Parent elements</span></span>  
  
|<span data-ttu-id="57aa8-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="57aa8-125">Element</span></span>|<span data-ttu-id="57aa8-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57aa8-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="57aa8-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="57aa8-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="57aa8-128">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57aa8-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57aa8-129">Remarks</span></span>

<span data-ttu-id="57aa8-130">.NET Framework 3.5 ve önceki sürümlerinde, bir derlemeyi uzak bir konumdan yüklerseniz, derlemedeki kod, yüklendiği bölgeye bağlı bir hibe kümesiyle kısmi güven içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="57aa8-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="57aa8-131">Örneğin, bir web sitesinden bir derleme yüklerseniz, internet bölgesine yüklenir ve Internet izin kümesi verilir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="57aa8-132">Başka bir deyişle, bir Internet sandbox yürütülür.</span><span class="sxs-lookup"><span data-stu-id="57aa8-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="57aa8-133">.NET Framework 4'ten başlayarak, kod erişim güvenliği (CAS) ilkesi devre dışı bırakılır ve derlemeler tam güven içinde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="57aa8-134">Normalde, bu daha önce kumlanmış olan <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemle yüklenen derlemelere tam güven verir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="57aa8-135">Bunu önlemek için, uzak bir kaynaktan yüklenen derlemelerde kod çalıştırma yeteneği varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="57aa8-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="57aa8-136">Varsayılan olarak, uzak bir derleme yüklemeyi <xref:System.IO.FileLoadException> denerseniz, aşağıdaki gibi bir özel durum iletisi atılır:</span><span class="sxs-lookup"><span data-stu-id="57aa8-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

<span data-ttu-id="57aa8-137">Derlemeyi yüklemek ve kodunu yürütmek için aşağıdakilerden birini gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="57aa8-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="57aa8-138">Montaj için açıkça bir kum havuzu oluşturun [(bkz.](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)</span><span class="sxs-lookup"><span data-stu-id="57aa8-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="57aa8-139">Derlemenin kodunu tam güven içinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="57aa8-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="57aa8-140">Bunu öğeyi `<loadFromRemoteSources>` yapılandırarak yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="57aa8-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="57aa8-141">.NET Framework'ün önceki sürümlerinde kısmi güven içinde çalışan derlemelerin artık .NET Framework 4 ve sonraki sürümlerde tam güven içinde çalışmasını belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="57aa8-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57aa8-142">Derleme tam güven içinde çalışmazise, bu yapılandırma öğesini ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="57aa8-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="57aa8-143">Bunun yerine, montaj yüklemek <xref:System.AppDomain> için bir kum lu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="57aa8-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="57aa8-144">Öğenin `enabled` `<loadFromRemoteSources>` özniteliği yalnızca kod erişim güvenliği (CAS) devre dışı bırakıldığında etkilidir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="57aa8-145">Varsayılan olarak, CAS ilkesi .NET Framework 4 ve sonraki sürümlerde devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="57aa8-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="57aa8-146">Eğer `enabled` `true`ayarlarsanız, uzak derlemeler tam güven verilir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="57aa8-147">Ayarlanmadıysa, `enabled` aşağıdaki <xref:System.IO.FileLoadException> koşullardan biri altında a atılır: `true`</span><span class="sxs-lookup"><span data-stu-id="57aa8-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="57aa8-148">Geçerli etki alanının kum kutulama davranışı .NET Framework 3.5'teki davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="57aa8-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="57aa8-149">Bu, CAS ilkesinin devre dışı bırakılmasını ve geçerli etki alanının sandboxed olmamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="57aa8-150">Yüklenen montaj `MyComputer` bölgeden değil.</span><span class="sxs-lookup"><span data-stu-id="57aa8-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="57aa8-151">Öğeyi `<loadFromRemoteSources>` bu `true` özel durum atılmasını önlemek için ayarlama.</span><span class="sxs-lookup"><span data-stu-id="57aa8-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="57aa8-152">Güvenlik için yüklenen derlemeleri kumlamak için ortak dil çalışma süresine güvenmediğinizi ve bunların tam güven içinde yürütülmesine izin verilebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="57aa8-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="57aa8-153">Notlar</span><span class="sxs-lookup"><span data-stu-id="57aa8-153">Notes</span></span>

- <span data-ttu-id="57aa8-154">.NET Framework 4.5 ve sonraki sürümlerinde, yerel ağ hisselerindeki derlemeler varsayılan olarak tam güven içinde çalışır; öğeyi `<loadFromRemoteSources>` etkinleştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="57aa8-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="57aa8-155">Bir uygulama web'den kopyalanmışsa, yerel bilgisayarda olsa bile Windows tarafından bir web uygulaması olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="57aa8-156">Bu atamayı dosya özelliklerini değiştirerek değiştirebilir veya `<loadFromRemoteSources>` derlemeye tam güven vermek için öğeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57aa8-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="57aa8-157">Alternatif olarak, işletim sisteminin <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> web'den yüklenmiş olarak işaretlediği yerel bir derlemeyi yüklemek için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57aa8-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="57aa8-158">Windows Virtual <xref:System.IO.FileLoadException> PC uygulamasında çalışan bir uygulamada a alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57aa8-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="57aa8-159">Bu, barındırma bilgisayarındaki bağlantılı klasörlerden bir dosya yüklemeyi denediğinizde olabilir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="57aa8-160">Uzak [Masaüstü Hizmetleri](/windows/win32/termserv/terminal-services-portal) (Terminal Hizmetleri) üzerinden bağlı bir klasörden dosya yüklemeyi denediğinizde de oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](/windows/win32/termserv/terminal-services-portal) (Terminal Services).</span></span> <span data-ttu-id="57aa8-161">Özel durum lardan `enabled` kaçınmak `true`için, '' olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="57aa8-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="57aa8-162">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="57aa8-162">Configuration file</span></span>

<span data-ttu-id="57aa8-163">Bu öğe genellikle uygulama yapılandırma dosyasında kullanılır, ancak içeriğe bağlı olarak diğer yapılandırma dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="57aa8-164">Daha fazla bilgi için CAS [İlkesinin Daha Örtülü Kullanımları makalesine bakın: .NET](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) Security blogundaki loadFromRemoteSources.</span><span class="sxs-lookup"><span data-stu-id="57aa8-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="57aa8-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="57aa8-165">Example</span></span>

<span data-ttu-id="57aa8-166">Aşağıdaki örnek, uzak kaynaklardan yüklenen derlemelere tam güvenin nasıl verilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="57aa8-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="57aa8-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57aa8-167">See also</span></span>

- [<span data-ttu-id="57aa8-168">CAS İlkesinin Daha Örtülü Kullanımı: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="57aa8-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [<span data-ttu-id="57aa8-169">Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="57aa8-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="57aa8-170">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="57aa8-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="57aa8-171">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="57aa8-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

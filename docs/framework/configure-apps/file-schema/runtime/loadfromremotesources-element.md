---
title: <loadFromRemoteSources> Öğesi
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: 568c0c814dcc57be0f5be435bb7750c970ffec19
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192457"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="8eaa5-102">\<loadFromRemoteSources> öğesi</span><span class="sxs-lookup"><span data-stu-id="8eaa5-102">\<loadFromRemoteSources> element</span></span>

<span data-ttu-id="8eaa5-103">.NET Framework 4 ve üzeri sürümlerde uzak kaynaklardan yüklenen derlemelerin tam güven verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8eaa5-104">Visual Studio proje hata listesi veya bir derleme hatası nedeniyle bu makaleye yönlendirilmiş olmanız halinde, bkz. [nasıl yapılır: Visual Studio 'Da Web 'Den derleme kullanma](/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8eaa5-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**  
  
## <a name="syntax"></a><span data-ttu-id="8eaa5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8eaa5-105">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8eaa5-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="8eaa5-106">Attributes and elements</span></span>

 <span data-ttu-id="8eaa5-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8eaa5-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8eaa5-108">Attributes</span></span>  
  
|<span data-ttu-id="8eaa5-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8eaa5-109">Attribute</span></span>|<span data-ttu-id="8eaa5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eaa5-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8eaa5-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="8eaa5-112">Uzak bir kaynaktan yüklenen bir derlemeye tam güven verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-112">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8eaa5-113">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="8eaa5-113">enabled attribute</span></span>  
  
|<span data-ttu-id="8eaa5-114">Değer</span><span class="sxs-lookup"><span data-stu-id="8eaa5-114">Value</span></span>|<span data-ttu-id="8eaa5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eaa5-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8eaa5-116">Uzak kaynaklardaki uygulamalara tam güven vermeyin.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-116">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="8eaa5-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="8eaa5-118">Uzak kaynaklardaki uygulamalara tam güven verme.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-118">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8eaa5-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="8eaa5-119">Child elements</span></span>  

 <span data-ttu-id="8eaa5-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8eaa5-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="8eaa5-121">Parent elements</span></span>  
  
|<span data-ttu-id="8eaa5-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8eaa5-122">Element</span></span>|<span data-ttu-id="8eaa5-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eaa5-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8eaa5-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8eaa5-125">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eaa5-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8eaa5-126">Remarks</span></span>

<span data-ttu-id="8eaa5-127">.NET Framework 3,5 ve önceki sürümlerde, uzak bir konumdan bir derlemeyi yüklerseniz, derlemedeki kod, yüklendiği bölgeye bağlı bir izin kümesiyle kısmi güvende çalışır.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-127">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="8eaa5-128">Örneğin, bir Web sitesinden derleme yüklerseniz Internet bölgesine yüklenir ve Internet izin kümesi verilir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-128">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="8eaa5-129">Diğer bir deyişle, bir Internet korumalı alanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-129">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="8eaa5-130">Kod erişim güvenliği (CAS) ilkesi, .NET Framework 4 ile başlayarak devre dışıdır ve derlemeler tam güvende yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-130">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="8eaa5-131">Normalde, bu, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> daha önce korumalı olan yöntemle yüklenen derlemelere tam güven verir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-131">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="8eaa5-132">Bunu engellemek için, uzak bir kaynaktan yüklenen derlemelerde kod çalıştırma özelliği varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-132">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="8eaa5-133">Varsayılan olarak, uzak bir derlemeyi yüklemeye çalışırsanız, aşağıdakine <xref:System.IO.FileLoadException> benzer bir özel durum iletisi ile oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="8eaa5-133">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

<span data-ttu-id="8eaa5-134">Derlemeyi yüklemek ve kodunu yürütmek için şunlardan birini yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8eaa5-134">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="8eaa5-135">Derleme için açık bir korumalı alan oluşturun (bkz. [nasıl yapılır: bir korumalı alana kısmen güvenilen kod çalıştırma](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span><span class="sxs-lookup"><span data-stu-id="8eaa5-135">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="8eaa5-136">Derlemenin kodunu tam güvende çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-136">Run the assembly's code in full trust.</span></span> <span data-ttu-id="8eaa5-137">Bunu, öğesini yapılandırarak yapabilirsiniz `<loadFromRemoteSources>` .</span><span class="sxs-lookup"><span data-stu-id="8eaa5-137">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="8eaa5-138">.NET Framework önceki sürümlerinde bulunan kısmi güvende çalışan derlemelerin artık .NET Framework 4 ve sonraki sürümlerde tam güvende çalıştığını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-138">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8eaa5-139">Derlemenin tam güvende çalıştırılmamalıdır, bu yapılandırma öğesini ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-139">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="8eaa5-140">Bunun yerine, derlemenin yükleneceği bir korumalı alan oluşturun <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="8eaa5-140">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="8eaa5-141">`enabled`Öğesi için özniteliği `<loadFromRemoteSources>` yalnızca kod erişim GÜVENLIĞI (CAS) devre dışı bırakıldığında etkilidir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-141">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="8eaa5-142">Varsayılan olarak, CA ilkesi .NET Framework 4 ve sonraki sürümlerde devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-142">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="8eaa5-143">`enabled`Olarak ayarlarsanız `true` , uzak derlemelere tam güven verilir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-143">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="8eaa5-144">`enabled`, Olarak ayarlanmamışsa `true` , <xref:System.IO.FileLoadException> aşağıdaki koşullardan biri altında bir oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="8eaa5-144">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="8eaa5-145">Geçerli etki alanının korumalı alana alma davranışı, .NET Framework 3,5 ' deki davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-145">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="8eaa5-146">Bu, CAS ilkesinin devre dışı bırakılması ve geçerli etki alanının korumalı olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-146">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="8eaa5-147">Yüklenen derleme `MyComputer` bölgeden değil.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-147">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="8eaa5-148">`<loadFromRemoteSources>`Öğesi için ayarı, `true` Bu özel durumun oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-148">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="8eaa5-149">Ortak dil çalışma zamanına bağlı olarak, güvenlik için yüklenmiş derlemeleri korumalı hale getirmenizi ve tam güvende yürütülmesine izin verilip verilmeyeceğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-149">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="8eaa5-150">Notlar</span><span class="sxs-lookup"><span data-stu-id="8eaa5-150">Notes</span></span>

- <span data-ttu-id="8eaa5-151">.NET Framework 4,5 ve sonraki sürümlerinde, yerel ağ paylaşımlarında derlemeler varsayılan olarak tam güvende çalışır; öğesini etkinleştirmeniz gerekmez `<loadFromRemoteSources>` .</span><span class="sxs-lookup"><span data-stu-id="8eaa5-151">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="8eaa5-152">Bir uygulama Web 'den kopyalanmışsa, bu, yerel bilgisayarda bulunsa bile, Windows tarafından bir Web uygulaması olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-152">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="8eaa5-153">Dosya özelliklerini değiştirerek bu belirtimi değiştirebilir veya `<loadFromRemoteSources>` derlemeye tam güven sağlamak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-153">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="8eaa5-154">Alternatif olarak, <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> işletim sisteminin Web 'den yüklenmiş olarak işaretlediğini belirten yerel bir derlemeyi yüklemek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-154">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="8eaa5-155">Bir <xref:System.IO.FileLoadException> Windows sanal bilgisayar uygulamasında çalışan bir uygulama içinde alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-155">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="8eaa5-156">Bu, barındırma bilgisayarındaki bağlantılı klasörlerden bir dosya yüklemeye çalıştığınızda meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-156">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="8eaa5-157">Ayrıca, [Uzak Masaüstü Hizmetleri](/windows/win32/termserv/terminal-services-portal) (Terminal Hizmetleri) üzerinden bağlanmış bir klasörden dosya yüklemeye çalıştığınızda da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-157">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](/windows/win32/termserv/terminal-services-portal) (Terminal Services).</span></span> <span data-ttu-id="8eaa5-158">Özel durumdan kaçınmak için, `enabled` olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="8eaa5-158">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="8eaa5-159">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="8eaa5-159">Configuration file</span></span>

<span data-ttu-id="8eaa5-160">Bu öğe genellikle uygulama yapılandırma dosyasında kullanılır, ancak bağlama göre diğer yapılandırma dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-160">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="8eaa5-161">Daha fazla bilgi için, .NET güvenlik bloguna [AIT CA 'Ların daha örtük kullanımları: loadFromRemoteSources](/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-161">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="8eaa5-162">Örnek</span><span class="sxs-lookup"><span data-stu-id="8eaa5-162">Example</span></span>

<span data-ttu-id="8eaa5-163">Aşağıdaki örnek, uzak kaynaklardan yüklenen derlemelere nasıl tam güven verildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-163">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="8eaa5-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eaa5-164">See also</span></span>

- [<span data-ttu-id="8eaa5-165">CAS Ilkesinin daha örtük kullanımları: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="8eaa5-165">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [<span data-ttu-id="8eaa5-166">Nasıl yapılır: bir korumalı alanda kısmen güvenilen kod çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8eaa5-166">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="8eaa5-167">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="8eaa5-167">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8eaa5-168">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="8eaa5-168">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

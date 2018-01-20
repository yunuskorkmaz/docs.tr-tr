---
title: '&lt;loadFromRemoteSources&gt; Element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13b42405a0faf721c46476aadaa0cff8163883c1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a><span data-ttu-id="0c639-102">&lt;loadFromRemoteSources&gt; Element</span><span class="sxs-lookup"><span data-stu-id="0c639-102">&lt;loadFromRemoteSources&gt; Element</span></span>
<span data-ttu-id="0c639-103">Uzak kaynaklardan derlemeler tam güven verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c639-103">Specifies whether assemblies from remote sources should be granted full trust.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c639-104">Hata iletisinde Visual Studio Proje hata listesi veya bir derleme hatası nedeniyle bu konuya yönelik olup [nasıl yapılır: Visual Studio'da Web bir derleme kullanma](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span><span class="sxs-lookup"><span data-stu-id="0c639-104">If you were directed to this topic because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span></span>  
  
 <span data-ttu-id="0c639-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0c639-105">\<configuration></span></span>  
<span data-ttu-id="0c639-106">\<runtime></span><span class="sxs-lookup"><span data-stu-id="0c639-106">\<runtime></span></span>  
<span data-ttu-id="0c639-107">\<loadFromRemoteSources></span><span class="sxs-lookup"><span data-stu-id="0c639-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c639-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c639-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c639-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c639-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0c639-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c639-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c639-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c639-111">Attributes</span></span>  
  
|<span data-ttu-id="0c639-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0c639-112">Attribute</span></span>|<span data-ttu-id="0c639-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c639-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0c639-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0c639-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0c639-115">Uzak kaynaktan yüklenen bir derlemeyi tam güven verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c639-115">Specifies whether an assembly that is loaded from remote sources should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0c639-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0c639-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="0c639-117">Değer</span><span class="sxs-lookup"><span data-stu-id="0c639-117">Value</span></span>|<span data-ttu-id="0c639-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c639-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0c639-119">Tam güven uzak kaynaklardan gelen uygulamalara vermeyin.</span><span class="sxs-lookup"><span data-stu-id="0c639-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="0c639-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0c639-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0c639-121">Tam güven uzak kaynaklardan gelen uygulamalara verin.</span><span class="sxs-lookup"><span data-stu-id="0c639-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c639-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c639-122">Child Elements</span></span>  
 <span data-ttu-id="0c639-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="0c639-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c639-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c639-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0c639-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c639-125">Element</span></span>|<span data-ttu-id="0c639-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c639-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0c639-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0c639-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0c639-128">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="0c639-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c639-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c639-129">Remarks</span></span>  
 <span data-ttu-id="0c639-130">Uzak bir konumdan bir derlemeyi yüklenen .NET Framework sürüm 3.5 ve önceki sürümlerinde derleme kısmen güvenilen yüklü değildi bölgenin bağlı verme kümesi ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="0c639-130">In the .NET Framework version 3.5 and earlier versions, if you loaded an assembly from a remote location, the assembly would run partially trusted with a grant set that depended on the zone in which it was loaded.</span></span> <span data-ttu-id="0c639-131">Örneğin, bir Web sitesinden bir derlemeyi yüklerse Internet bölgeye yüklendi ve Internet izin kümesi verildi.</span><span class="sxs-lookup"><span data-stu-id="0c639-131">For example, if you loaded an assembly from a website, it was loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="0c639-132">Diğer bir deyişle, bir Internet korumalı alanda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0c639-132">In other words, it executed in an Internet sandbox.</span></span> <span data-ttu-id="0c639-133">Bu derleme çalıştırmayı denerseniz [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve sonraki sürümlerinde, bir özel durum; bir korumalı alan açıkça derleme için oluşturmalısınız (bkz [nasıl yapılır: çalıştırma kısmen güvenilen kod içinde bir korumalı alan](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), ya da tam güvende çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="0c639-133">If you try to run that assembly in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later versions, an exception is thrown; you must either explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), or run it in full trust.</span></span>  
  
 <span data-ttu-id="0c639-134">`<loadFromRemoteSources>` Belirtmenizi .NET Framework'ün kısmen güvenilen olarak önceki sürümlerinde çalışır derlemeler tam olarak çalıştırılacak olan öğesi sağlar güvenilen [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="0c639-134">The `<loadFromRemoteSources>` element lets you specify that the assemblies that would have run partially trusted in earlier versions of the .NET Framework are to be run fully trusted in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="0c639-135">Varsayılan olarak, uzaktan derlemeleri çalıştırmayın [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="0c639-135">By default, remote assemblies do not run in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span> <span data-ttu-id="0c639-136">Uzak bir derleme çalıştırmak için ya da tam olarak güvenilir olarak çalıştırmak veya bir korumalı oluşturmanız gerekir <xref:System.AppDomain> çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="0c639-136">To run a remote assembly, you must either run it as fully trusted or create a sandboxed <xref:System.AppDomain> in which to run it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c639-137">İçinde [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], yerel ağ paylaşımlarında derlemeler, varsayılan tam güven çalıştırılır; etkinleştirmeniz gerekmez `<loadFromRemoteSources>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0c639-137">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblies on local network shares are run as full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c639-138">Bir uygulamanın web sunucusundan kopyalanan, yerel bilgisayarda bulunsa bile, Windows tarafından bir web uygulaması olacak şekilde işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="0c639-138">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="0c639-139">Dosya özelliklerini değiştirerek bu ataması değiştirebilir veya kullanabilirsiniz `<loadFromRemoteSources>` öğesi derleme vermek için tam güven.</span><span class="sxs-lookup"><span data-stu-id="0c639-139">You can change that designation by changing the file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="0c639-140">Alternatif olarak, kullandığınız <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> işletim sistemi Web'den yüklenen olarak işaretlenmiş yerel bir derlemeyi yüklemeye yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0c639-140">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>  
  
 <span data-ttu-id="0c639-141">`enabled` Yalnızca kod erişim güvenliği (CAS) devre dışı bırakıldığında bu öğe etkilidir için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0c639-141">The `enabled` attribute for this element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="0c639-142">Varsayılan olarak, CAS ilkesini devre dışı durumda [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="0c639-142">By default, CAS policy is disabled in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="0c639-143">Ayarlarsanız `enabled` için `true`, uzak uygulamalarını tam güven verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0c639-143">If you set `enabled` to `true`, remote applications are granted full trust.</span></span>  
  
 <span data-ttu-id="0c639-144">Varsa `<loadFromRemoteSources>``enabled` ayarlanmazsa `true`, aşağıdaki koşullar altında bir özel durum:</span><span class="sxs-lookup"><span data-stu-id="0c639-144">If `<loadFromRemoteSources>``enabled` is not set to `true`, an exception is thrown under the following conditions:</span></span>  
  
-   <span data-ttu-id="0c639-145">Korumalı alan geçerli etki alanının içinde davranışını öğesinden farklı bir davranıştır [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0c639-145">The sandboxing behavior of the current domain is different from its behavior in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span> <span data-ttu-id="0c639-146">Bu, CA ilke devre dışı bırakılması ve korumalı olmaması için geçerli etki alanı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0c639-146">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>  
  
-   <span data-ttu-id="0c639-147">Yüklenmekte olan derleme gelen değil `MyComputer` bölgesi.</span><span class="sxs-lookup"><span data-stu-id="0c639-147">The assembly being loaded is not from the `MyComputer` zone.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c639-148">Alabilirsiniz bir <xref:System.IO.FileLoadException> bağlantılı klasörlerden barındıran bilgisayarda bir dosyayı yüklemeye çalıştığınızda Windows Virtual PC uygulamasında.</span><span class="sxs-lookup"><span data-stu-id="0c639-148">You may get a <xref:System.IO.FileLoadException> in a Windows Virtual PC application when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="0c639-149">Bir dosya üzerinden bağlı bir klasörden yüklemeye çalıştığınızda bu hatayı da oluşabilir [Uzak Masaüstü Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Hizmetleri).</span><span class="sxs-lookup"><span data-stu-id="0c639-149">This error may also occur when you try to load a file from a folder linked over [Remote Desktop Services](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="0c639-150">Özel durum önlemek için ayarlandığından `enabled` için `true`.</span><span class="sxs-lookup"><span data-stu-id="0c639-150">To avoid the exception, set `enabled` to `true`.</span></span>  
  
 <span data-ttu-id="0c639-151">Ayarı `<loadFromRemoteSources>` öğesine `true` bu özel durumlar gelen engeller.</span><span class="sxs-lookup"><span data-stu-id="0c639-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="0c639-152">Ortak dil çalışma zamanı için korumalı alan güvenlik için yüklenen derlemeleri güvenmek değil, belirtmenize olanak sağlar ve bunlar olarak yürütün olmasına izin verilmesi gerektiğini tam güven.</span><span class="sxs-lookup"><span data-stu-id="0c639-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute as full trust.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0c639-153">Derleme tam güvende çalıştırmamanız gerekir, bu yapılandırma öğesi ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="0c639-153">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="0c639-154">Bunun yerine, bir korumalı oluşturun <xref:System.AppDomain> , derlemesi yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="0c639-154">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0c639-155">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="0c639-155">Configuration File</span></span>  
 <span data-ttu-id="0c639-156">Bu öğe uygulama yapılandırma dosyasında genellikle kullanılır, ancak bağlam bağlı olarak diğer yapılandırma dosyalarını, kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c639-156">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="0c639-157">Daha fazla bilgi için bkz: [daha fazla örtük kullanan CA ilke: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) .NET güvenlik günlüğündeki.</span><span class="sxs-lookup"><span data-stu-id="0c639-157">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c639-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c639-158">Example</span></span>  
 <span data-ttu-id="0c639-159">Aşağıdaki örnek uygulamaları için tam güven uzak kaynaktan nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c639-159">The following example shows how to grant full trust to applications from remote sources.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c639-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c639-160">See Also</span></span>  
 [<span data-ttu-id="0c639-161">CA ilke daha örtük kullanır: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="0c639-161">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [<span data-ttu-id="0c639-162">Nasıl yapılır: korumalı alanda kısmen güvenilen kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0c639-162">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [<span data-ttu-id="0c639-163">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0c639-163">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="0c639-164">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="0c639-164">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)

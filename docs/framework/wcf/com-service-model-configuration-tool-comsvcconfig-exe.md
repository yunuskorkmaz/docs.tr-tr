---
title: "COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 322268f5b11a5078545ae120440f91d327d6a615
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="e3d62-102">COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="e3d62-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="e3d62-103">COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe), Web Hizmetleri olarak açığa çıkarılması COM + arabirimleri yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3d62-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3d62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3d62-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="e3d62-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3d62-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3d62-106">ComSvcConfig.exe kullanmak için yerel bilgisayarda yönetici olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3d62-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="e3d62-107">Aracı şu konumda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e3d62-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="e3d62-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows iletişim Foundation\\</span><span class="sxs-lookup"><span data-stu-id="e3d62-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="e3d62-109">ComSvcConfig.exe hakkında daha fazla bilgi için bkz: [nasıl yapılır: COM + hizmet modeli yapılandırma aracını kullanma](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e3d62-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="e3d62-110">Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilen modları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e3d62-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="e3d62-111">Seçenek</span><span class="sxs-lookup"><span data-stu-id="e3d62-111">Option</span></span>|<span data-ttu-id="e3d62-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3d62-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="e3d62-113">Arabirimin bir COM + hizmet modeli tümleştirmesi için yapılandırma yükler.</span><span class="sxs-lookup"><span data-stu-id="e3d62-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="e3d62-114">Kısa form `/i`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="e3d62-115">COM + arabirimi için bir yapılandırma hizmet modeli entegrasyonunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e3d62-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="e3d62-116">Kısa form `/u`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="e3d62-117">COM + uygulamaları ve hizmet modeli tümleştirmesi için yapılandırılmış arabirimine sahip bileşenleri hakkında bilgileri listeler.</span><span class="sxs-lookup"><span data-stu-id="e3d62-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="e3d62-118">Kısa form `/l`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="e3d62-119">Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilir bayrakları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3d62-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="e3d62-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="e3d62-120">Option</span></span>|<span data-ttu-id="e3d62-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3d62-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e3d62-122">`/application:`\< *ApplicationId* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="e3d62-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="e3d62-123">Yapılandırmak için COM + uygulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3d62-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="e3d62-124">Kısa form `/a`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="e3d62-125">`/contract:`\< *ClassID* &#124; *ProgID* &#124; \*,*InterfaceId* &#124; *InterfaceName* &#124;\*\></span><span class="sxs-lookup"><span data-stu-id="e3d62-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="e3d62-126">COM + bileşeni ve hizmet sözleşmesini olarak yapılandırılacak arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3d62-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="e3d62-127">Kısa form `/c`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="e3d62-128">While joker karakter (\*) bileşeni ve arabirim adlarını belirttiğinizde kullanılabilir, istemediğiniz arabirimleri doğurabilir, kullanmamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="e3d62-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="e3d62-129">`/hosting:`\< *complus* &#124; *edildi*\></span><span class="sxs-lookup"><span data-stu-id="e3d62-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="e3d62-130">COM + modu veya Web barındırma modu barındırma kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3d62-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="e3d62-131">Kısa form `/h`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="e3d62-132">COM + kullanma modu barındırma COM + uygulamasının açık etkinleştirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e3d62-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="e3d62-133">Web barındırma modu otomatik olarak etkinleştirilecek COM + uygulaması verir kullanarak gerekli.</span><span class="sxs-lookup"><span data-stu-id="e3d62-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="e3d62-134">COM + uygulaması bir kitaplık uygulaması varsa, Internet Information Services (IIS) işleminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e3d62-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="e3d62-135">COM + uygulaması bir sunucu uygulaması ise, Dllhost.exe işleminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e3d62-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="e3d62-136">`/webSite:`\< *WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="e3d62-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="e3d62-137">Ne zaman modu barındırma Web barındırma için Web sitesi kullanılır belirtir (bkz `/hosting` bayrağı).</span><span class="sxs-lookup"><span data-stu-id="e3d62-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="e3d62-138">Kısa form `/w`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="e3d62-139">Web sitesi belirtilmezse, varsayılan Web sitesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3d62-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="e3d62-140">`/webDirectory:`\< *WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="e3d62-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="e3d62-141">Web barındırma kullanıldığında barındırmak için sanal dizini belirtir (bkz `/hosting` bayrağı).</span><span class="sxs-lookup"><span data-stu-id="e3d62-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="e3d62-142">Kısa form `/d`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="e3d62-143">Bir sözleşme tanımı hizmetinden almak istediğiniz istemcileri desteklemek için varsayılan hizmet yapılandırması için bir meta veri değişimi (MEX) Hizmeti uç noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="e3d62-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="e3d62-144">Kısa form `/x`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="e3d62-145">Uygulama bileşeni ve arabirim bilgilerini kimlikleri olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e3d62-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="e3d62-146">Kısa form `/k`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="e3d62-147">ComSvcConfig.exe kendi logo görüntülemesini engeller.</span><span class="sxs-lookup"><span data-stu-id="e3d62-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="e3d62-148">Kısa form `/n`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="e3d62-149">Tüm uyarı veya bilgilendirme metin karşılaşılan hataları yanı sıra çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e3d62-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="e3d62-150">Kısa form `/v`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="e3d62-151">Kullanım iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e3d62-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="e3d62-152">Kısa form `/?`.</span><span class="sxs-lookup"><span data-stu-id="e3d62-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="e3d62-153">Belirtilen arabirim kullanıma sunulabilecek bir veya daha fazla yöntem imzaları içerdiğinde bir hizmet yapılandırması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e3d62-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="e3d62-154">Hizmeti başlatma sırasında uyumlu yöntemlerini hizmet sözleşmesi işlemler olarak görünür ve uyumlu olmayan yöntemleri göz ardı edilir ve hizmet sözleşmeden yok.</span><span class="sxs-lookup"><span data-stu-id="e3d62-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="e3d62-155">Bu bayrak eksikse, belirtilen arabirimi bir veya daha fazla uyumsuz yöntemleri içerdiğinde aracı bir hizmet yapılandırması oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="e3d62-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="e3d62-156">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e3d62-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="e3d62-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3d62-157">Description</span></span>  
 <span data-ttu-id="e3d62-158">Aşağıdaki örnek, `IFinances` arabiriminin `ItemOrders.IFinancial` bileşeninden (OnlineStore COM + uygulaması) COM + barındırma modunu kullanarak Web hizmetleri sunulan arabirimleri kümesi için.</span><span class="sxs-lookup"><span data-stu-id="e3d62-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="e3d62-159">Tüm uyarıları karşılaşılan hataları yanı sıra çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e3d62-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e3d62-160">Kod</span><span class="sxs-lookup"><span data-stu-id="e3d62-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="e3d62-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3d62-161">Description</span></span>  
 <span data-ttu-id="e3d62-162">Aşağıdaki örnek, `IStockLevels` arabiriminin `ItemInventory.Warehouse` bileşeninden (OnlineWarehouse COM + uygulaması) Web modu barındırma kullanarak Web hizmetleri sunulan arabirimleri kümesi için.</span><span class="sxs-lookup"><span data-stu-id="e3d62-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="e3d62-163">IIS OnlineWarehouse sanal dizinde Web barındırılan Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="e3d62-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e3d62-164">Kod</span><span class="sxs-lookup"><span data-stu-id="e3d62-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="e3d62-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3d62-165">Description</span></span>  
 <span data-ttu-id="e3d62-166">Aşağıdaki örnek kaldırır `IFinances` arabiriminin `ItemOrders.Financial` bileşeninden (OnlineStore COM + uygulaması) Web Hizmetleri olarak sunulan arabirimleri kümesi.</span><span class="sxs-lookup"><span data-stu-id="e3d62-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e3d62-167">Kod</span><span class="sxs-lookup"><span data-stu-id="e3d62-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="e3d62-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3d62-168">Description</span></span>  
 <span data-ttu-id="e3d62-169">Aşağıdaki örnek listeler, COM + barındırılan arabirimi, yerel makinede OnlineStore COM + uygulaması için bağlama ayrıntıları ve karşılık gelen adresi ile şu anda açık.</span><span class="sxs-lookup"><span data-stu-id="e3d62-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e3d62-170">Kod</span><span class="sxs-lookup"><span data-stu-id="e3d62-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3d62-171">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3d62-171">See Also</span></span>  
 [<span data-ttu-id="e3d62-172">Nasıl yapılır: COM + hizmet modeli yapılandırma aracını kullanın</span><span class="sxs-lookup"><span data-stu-id="e3d62-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

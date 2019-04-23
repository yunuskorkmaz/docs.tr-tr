---
title: COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 6d0967355e64640e0fd5c81f04a5bf4f33c7b3f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158671"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="5e9d0-102">COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="5e9d0-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="5e9d0-103">COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe) Web Hizmetleri olarak açığa COM arabirimleri yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e9d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e9d0-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="5e9d0-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e9d0-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e9d0-106">ComSvcConfig.exe kullanmak için yerel bilgisayarda yönetici olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="5e9d0-107">Aracı şu konumda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="5e9d0-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="5e9d0-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="5e9d0-109">ComSvcConfig.exe hakkında daha fazla bilgi için bkz: [nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="5e9d0-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="5e9d0-110">Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilen modları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="5e9d0-111">Seçenek</span><span class="sxs-lookup"><span data-stu-id="5e9d0-111">Option</span></span>|<span data-ttu-id="5e9d0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9d0-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="5e9d0-113">Yapılandırma hizmet modeli tümleştirme için bir COM + arabirimini yükler.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="5e9d0-114">Kısa form `/i`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="5e9d0-115">Bir COM arabirimi için bir yapılandırma hizmet modeli tümleştirmeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="5e9d0-116">Kısa form `/u`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="5e9d0-117">COM + uygulamaları ve hizmet modeli tümleştirmesi için yapılandırılmış arabirimlere sahip bileşenler hakkında bilgi listeler.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="5e9d0-118">Kısa form `/l`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="5e9d0-119">Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilecek bayrakları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="5e9d0-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="5e9d0-120">Option</span></span>|<span data-ttu-id="5e9d0-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9d0-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5e9d0-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="5e9d0-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="5e9d0-123">Yapılandırmak için COM + uygulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="5e9d0-124">Kısa form `/a`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="5e9d0-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="5e9d0-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="5e9d0-126">Hizmet sözleşmesini olarak yapılandırılacak arabirimi ve COM + bileşeni belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="5e9d0-127">Kısa form `/c`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="5e9d0-128">While joker karakter (\*) bileşeni ve arabirim adı belirttiğinizde kullanılabilir siz istediniz olmayan arabirimleri sunabileceğinize olduğundan, kullanmamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="5e9d0-129">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="5e9d0-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="5e9d0-130">COM + modunda veya Web barındırma modunda barındırma kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="5e9d0-131">Kısa form `/h`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="5e9d0-132">COM + kullanarak modu barındırma, COM + uygulamasının açık etkinleştirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="5e9d0-133">Barındırma mod, otomatik olarak etkinleştirilecek COM + uygulaması sağlar. Web kullanarak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="5e9d0-134">COM + uygulaması bir kitaplık uygulaması ise, Internet Information Services (IIS) işleminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="5e9d0-135">Sunucu uygulaması COM + uygulamasını Dllhost.exe işleminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="5e9d0-136">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="5e9d0-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="5e9d0-137">Web sitesi, ne zaman modu barındırma Web barındırma için kullanılan belirtir (bkz `/hosting` bayrağı).</span><span class="sxs-lookup"><span data-stu-id="5e9d0-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="5e9d0-138">Kısa form `/w`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="5e9d0-139">Web sitesi belirtilmezse, varsayılan Web sitesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="5e9d0-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="5e9d0-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="5e9d0-141">Web barındırma kullanıldığında barındırmak için sanal dizin belirtir (bkz `/hosting` bayrağı).</span><span class="sxs-lookup"><span data-stu-id="5e9d0-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="5e9d0-142">Kısa form `/d`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="5e9d0-143">Meta veri değişimi (MEX) hizmet uç noktası, hizmetten bir sözleşme tanımı almak istediğiniz istemcileri desteklemek için varsayılan hizmet yapılandırması ekler.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="5e9d0-144">Kısa form `/x`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="5e9d0-145">Uygulama, bileşen ve arabirim bilgilerini kimlikleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="5e9d0-146">Kısa form `/k`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="5e9d0-147">ComSvcConfig.exe kendi logosu görüntülenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="5e9d0-148">Kısa form `/n`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="5e9d0-149">Tüm uyarıları veya bilgilendirici metin karşılaşılan hataları yanı sıra çıkarır.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="5e9d0-150">Kısa form `/v`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="5e9d0-151">Kullanım iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="5e9d0-152">Kısa form `/?`.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="5e9d0-153">Belirtilen arabirim kullanıma sunulabilecek bir veya daha fazla yöntem imzaları içeren bir hizmet yapılandırması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="5e9d0-154">Hizmet başlatma zaman uyumlu yöntemleri hizmet sözleşmesi işlemleri olarak görünür ve uyumlu olmayan yöntemleri göz ardı edilir ve hizmet sözleşme yok.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="5e9d0-155">Bu bayrak yoksa, belirtilen arabirim bir veya daha fazla uyumsuz yöntemleri içerdiğinde aracı bir hizmet yapılandırması oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="5e9d0-156">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5e9d0-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="5e9d0-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9d0-157">Description</span></span>  
 <span data-ttu-id="5e9d0-158">Aşağıdaki örnek ekler `IFinances` arabiriminin `ItemOrders.IFinancial` bileşeninden (OnlineStore COM + uygulaması) COM + barındırma modunu kullanarak Web Hizmetleri olarak sunulan arabirimler dizi.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="5e9d0-159">Tüm uyarıları karşılaşılan hataları yanı sıra çıkarır.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5e9d0-160">Kod</span><span class="sxs-lookup"><span data-stu-id="5e9d0-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="5e9d0-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9d0-161">Description</span></span>  
 <span data-ttu-id="5e9d0-162">Aşağıdaki örnek ekler `IStockLevels` arabiriminin `ItemInventory.Warehouse` Web barındırma modu kullanarak Web Hizmetleri olarak sunulan arabirimler kümesine (OnlineWarehouse COM + uygulaması) bileşeni.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="5e9d0-163">IIS OnlineWarehouse sanal dizine Web barındırılan Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5e9d0-164">Kod</span><span class="sxs-lookup"><span data-stu-id="5e9d0-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="5e9d0-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9d0-165">Description</span></span>  
 <span data-ttu-id="5e9d0-166">Aşağıdaki örnek kaldırır `IFinances` arabiriminin `ItemOrders.Financial` Web Hizmetleri olarak sunulan arabirimler kümesinden (OnlineStore COM + uygulaması) bileşeni.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5e9d0-167">Kod</span><span class="sxs-lookup"><span data-stu-id="5e9d0-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="5e9d0-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9d0-168">Description</span></span>  
 <span data-ttu-id="5e9d0-169">Aşağıdaki örnekte liste, COM + barındırılan arabirimi, yerel makinede OnlineStore COM + uygulaması bağlama ayrıntıları ve karşılık gelen adresi ile şu anda açık.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5e9d0-170">Kod</span><span class="sxs-lookup"><span data-stu-id="5e9d0-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e9d0-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e9d0-171">See also</span></span>

- [<span data-ttu-id="5e9d0-172">Nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın</span><span class="sxs-lookup"><span data-stu-id="5e9d0-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

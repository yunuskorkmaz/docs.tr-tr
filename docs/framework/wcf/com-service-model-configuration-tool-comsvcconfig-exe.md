---
title: COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 6d0967355e64640e0fd5c81f04a5bf4f33c7b3f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158671"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="84721-102">COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="84721-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="84721-103">COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe) Web Hizmetleri olarak açığa COM arabirimleri yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="84721-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84721-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84721-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="84721-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84721-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84721-106">ComSvcConfig.exe kullanmak için yerel bilgisayarda yönetici olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="84721-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="84721-107">Aracı şu konumda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="84721-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="84721-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="84721-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="84721-109">ComSvcConfig.exe hakkında daha fazla bilgi için bkz: [nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="84721-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="84721-110">Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilen modları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="84721-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="84721-111">Seçenek</span><span class="sxs-lookup"><span data-stu-id="84721-111">Option</span></span>|<span data-ttu-id="84721-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84721-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="84721-113">Yapılandırma hizmet modeli tümleştirme için bir COM + arabirimini yükler.</span><span class="sxs-lookup"><span data-stu-id="84721-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="84721-114">Kısa form `/i`.</span><span class="sxs-lookup"><span data-stu-id="84721-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="84721-115">Bir COM arabirimi için bir yapılandırma hizmet modeli tümleştirmeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="84721-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="84721-116">Kısa form `/u`.</span><span class="sxs-lookup"><span data-stu-id="84721-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="84721-117">COM + uygulamaları ve hizmet modeli tümleştirmesi için yapılandırılmış arabirimlere sahip bileşenler hakkında bilgi listeler.</span><span class="sxs-lookup"><span data-stu-id="84721-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="84721-118">Kısa form `/l`.</span><span class="sxs-lookup"><span data-stu-id="84721-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="84721-119">Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilecek bayrakları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="84721-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="84721-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="84721-120">Option</span></span>|<span data-ttu-id="84721-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84721-121">Description</span></span>|  
|------------|-----------------|  
|`/application:` <span data-ttu-id="84721-122">\<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="84721-122">\<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="84721-123">Yapılandırmak için COM + uygulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="84721-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="84721-124">Kısa form `/a`.</span><span class="sxs-lookup"><span data-stu-id="84721-124">Short form `/a`.</span></span>|  
|`/contract:` <span data-ttu-id="84721-125">\<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="84721-125">\<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="84721-126">Hizmet sözleşmesini olarak yapılandırılacak arabirimi ve COM + bileşeni belirtir.</span><span class="sxs-lookup"><span data-stu-id="84721-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="84721-127">Kısa form `/c`.</span><span class="sxs-lookup"><span data-stu-id="84721-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="84721-128">While joker karakter (\*) bileşeni ve arabirim adı belirttiğinizde kullanılabilir siz istediniz olmayan arabirimleri sunabileceğinize olduğundan, kullanmamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="84721-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|`/hosting:` <span data-ttu-id="84721-129">\<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="84721-129">\<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="84721-130">COM + modunda veya Web barındırma modunda barındırma kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="84721-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="84721-131">Kısa form `/h`.</span><span class="sxs-lookup"><span data-stu-id="84721-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="84721-132">COM + kullanarak modu barındırma, COM + uygulamasının açık etkinleştirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="84721-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="84721-133">Barındırma mod, otomatik olarak etkinleştirilecek COM + uygulaması sağlar. Web kullanarak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="84721-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="84721-134">COM + uygulaması bir kitaplık uygulaması ise, Internet Information Services (IIS) işleminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="84721-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="84721-135">Sunucu uygulaması COM + uygulamasını Dllhost.exe işleminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="84721-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|`/webSite:` <span data-ttu-id="84721-136">\<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="84721-136">\<*WebsiteName*\></span></span>|<span data-ttu-id="84721-137">Web sitesi, ne zaman modu barındırma Web barındırma için kullanılan belirtir (bkz `/hosting` bayrağı).</span><span class="sxs-lookup"><span data-stu-id="84721-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="84721-138">Kısa form `/w`.</span><span class="sxs-lookup"><span data-stu-id="84721-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="84721-139">Web sitesi belirtilmezse, varsayılan Web sitesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84721-139">If no Web site is specified, the default Web site is used.</span></span>|  
|`/webDirectory:` <span data-ttu-id="84721-140">\<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="84721-140">\<*WebDirectoryName*\></span></span>|<span data-ttu-id="84721-141">Web barındırma kullanıldığında barındırmak için sanal dizin belirtir (bkz `/hosting` bayrağı).</span><span class="sxs-lookup"><span data-stu-id="84721-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="84721-142">Kısa form `/d`.</span><span class="sxs-lookup"><span data-stu-id="84721-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="84721-143">Meta veri değişimi (MEX) hizmet uç noktası, hizmetten bir sözleşme tanımı almak istediğiniz istemcileri desteklemek için varsayılan hizmet yapılandırması ekler.</span><span class="sxs-lookup"><span data-stu-id="84721-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="84721-144">Kısa form `/x`.</span><span class="sxs-lookup"><span data-stu-id="84721-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="84721-145">Uygulama, bileşen ve arabirim bilgilerini kimlikleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="84721-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="84721-146">Kısa form `/k`.</span><span class="sxs-lookup"><span data-stu-id="84721-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="84721-147">ComSvcConfig.exe kendi logosu görüntülenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="84721-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="84721-148">Kısa form `/n`.</span><span class="sxs-lookup"><span data-stu-id="84721-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="84721-149">Tüm uyarıları veya bilgilendirici metin karşılaşılan hataları yanı sıra çıkarır.</span><span class="sxs-lookup"><span data-stu-id="84721-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="84721-150">Kısa form `/v`.</span><span class="sxs-lookup"><span data-stu-id="84721-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="84721-151">Kullanım iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="84721-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="84721-152">Kısa form `/?`.</span><span class="sxs-lookup"><span data-stu-id="84721-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="84721-153">Belirtilen arabirim kullanıma sunulabilecek bir veya daha fazla yöntem imzaları içeren bir hizmet yapılandırması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="84721-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="84721-154">Hizmet başlatma zaman uyumlu yöntemleri hizmet sözleşmesi işlemleri olarak görünür ve uyumlu olmayan yöntemleri göz ardı edilir ve hizmet sözleşme yok.</span><span class="sxs-lookup"><span data-stu-id="84721-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="84721-155">Bu bayrak yoksa, belirtilen arabirim bir veya daha fazla uyumsuz yöntemleri içerdiğinde aracı bir hizmet yapılandırması oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="84721-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="84721-156">Örnekler</span><span class="sxs-lookup"><span data-stu-id="84721-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="84721-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84721-157">Description</span></span>  
 <span data-ttu-id="84721-158">Aşağıdaki örnek ekler `IFinances` arabiriminin `ItemOrders.IFinancial` bileşeninden (OnlineStore COM + uygulaması) COM + barındırma modunu kullanarak Web Hizmetleri olarak sunulan arabirimler dizi.</span><span class="sxs-lookup"><span data-stu-id="84721-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="84721-159">Tüm uyarıları karşılaşılan hataları yanı sıra çıkarır.</span><span class="sxs-lookup"><span data-stu-id="84721-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="84721-160">Kod</span><span class="sxs-lookup"><span data-stu-id="84721-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="84721-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84721-161">Description</span></span>  
 <span data-ttu-id="84721-162">Aşağıdaki örnek ekler `IStockLevels` arabiriminin `ItemInventory.Warehouse` Web barındırma modu kullanarak Web Hizmetleri olarak sunulan arabirimler kümesine (OnlineWarehouse COM + uygulaması) bileşeni.</span><span class="sxs-lookup"><span data-stu-id="84721-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="84721-163">IIS OnlineWarehouse sanal dizine Web barındırılan Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="84721-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="84721-164">Kod</span><span class="sxs-lookup"><span data-stu-id="84721-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="84721-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84721-165">Description</span></span>  
 <span data-ttu-id="84721-166">Aşağıdaki örnek kaldırır `IFinances` arabiriminin `ItemOrders.Financial` Web Hizmetleri olarak sunulan arabirimler kümesinden (OnlineStore COM + uygulaması) bileşeni.</span><span class="sxs-lookup"><span data-stu-id="84721-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="84721-167">Kod</span><span class="sxs-lookup"><span data-stu-id="84721-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="84721-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84721-168">Description</span></span>  
 <span data-ttu-id="84721-169">Aşağıdaki örnekte liste, COM + barındırılan arabirimi, yerel makinede OnlineStore COM + uygulaması bağlama ayrıntıları ve karşılık gelen adresi ile şu anda açık.</span><span class="sxs-lookup"><span data-stu-id="84721-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="84721-170">Kod</span><span class="sxs-lookup"><span data-stu-id="84721-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="84721-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84721-171">See also</span></span>

- [<span data-ttu-id="84721-172">Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma</span><span class="sxs-lookup"><span data-stu-id="84721-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

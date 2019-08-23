---
title: COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 89462d05b9da7fc63bda58955517bfa9f0c50ab9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964197"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="18f96-102">COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="18f96-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="18f96-103">COM+ hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig. exe), COM+ arabirimlerini Web Hizmetleri olarak kullanıma sunulacak şekilde yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="18f96-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18f96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18f96-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="18f96-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18f96-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18f96-106">ComSvcConfig. exe ' yi kullanmak için yerel bilgisayarda bir yönetici olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18f96-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="18f96-107">Araç aşağıdaki konumda bulunabilir</span><span class="sxs-lookup"><span data-stu-id="18f96-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="18f96-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="18f96-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="18f96-109">ComSvcConfig. exe hakkında daha fazla bilgi için bkz [. nasıl yapılır: COM+ hizmet modeli yapılandırma aracını](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="18f96-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="18f96-110">Aşağıdaki tabloda ComSvcConfig. exe ile kullanılabilen modlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18f96-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="18f96-111">Seçenek</span><span class="sxs-lookup"><span data-stu-id="18f96-111">Option</span></span>|<span data-ttu-id="18f96-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18f96-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="18f96-113">Hizmet modeli tümleştirmesi için bir COM+ arabirimi yapılandırması kurar.</span><span class="sxs-lookup"><span data-stu-id="18f96-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="18f96-114">Kısa biçim `/i`.</span><span class="sxs-lookup"><span data-stu-id="18f96-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="18f96-115">Bir COM+ arabiriminin yapılandırmasını hizmet modeli tümleştirmesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="18f96-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="18f96-116">Kısa biçim `/u`.</span><span class="sxs-lookup"><span data-stu-id="18f96-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="18f96-117">Hizmet modeli tümleştirmesi için yapılandırılmış arabirimlerin bulunduğu COM+ uygulamaları ve bileşenleriyle ilgili bilgileri listeler.</span><span class="sxs-lookup"><span data-stu-id="18f96-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="18f96-118">Kısa biçim `/l`.</span><span class="sxs-lookup"><span data-stu-id="18f96-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="18f96-119">Aşağıdaki tabloda ComSvcConfig. exe ile kullanılabilen bayraklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18f96-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="18f96-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="18f96-120">Option</span></span>|<span data-ttu-id="18f96-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18f96-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="18f96-122">`/application:`ApplicationId *ApplicationName* \< &#124;\></span><span class="sxs-lookup"><span data-stu-id="18f96-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="18f96-123">Yapılandırılacak COM+ uygulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="18f96-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="18f96-124">Kısa biçim `/a`.</span><span class="sxs-lookup"><span data-stu-id="18f96-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="18f96-125">`/contract:`&#124; &#124; &#124; ClassID ProgID&#124; *, InterfaceID* InterfaceName \< \*    \*\></span><span class="sxs-lookup"><span data-stu-id="18f96-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="18f96-126">Hizmet için sözleşme olarak yapılandırılacak COM+ bileşenini ve arabirimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="18f96-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="18f96-127">Kısa biçim `/c`.</span><span class="sxs-lookup"><span data-stu-id="18f96-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="18f96-128">Bileşen ve arabirim adlarını belirttiğinizde\*joker karakteri () kullanılabilir olsa da, istemediğiniz arabirimleri kullanıma sunabileceğiniz için bunu kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="18f96-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="18f96-129">`/hosting:`&#124; ComPlus \<idi  \></span><span class="sxs-lookup"><span data-stu-id="18f96-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="18f96-130">COM+ barındırma modunun mi yoksa Web barındırma modunun mi kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="18f96-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="18f96-131">Kısa biçim `/h`.</span><span class="sxs-lookup"><span data-stu-id="18f96-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="18f96-132">COM+ barındırma modu ' nu kullanmak, COM+ uygulamasının açık etkinleştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="18f96-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="18f96-133">Web barındırma modunun kullanılması, COM+ uygulamasının gerektiği şekilde otomatik olarak etkinleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="18f96-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="18f96-134">COM+ uygulaması bir kitaplık uygulaması ise, Internet Information Services (IIS) işleminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="18f96-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="18f96-135">COM+ uygulaması bir sunucu uygulaması ise, Dllhost. exe işleminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="18f96-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="18f96-136">`/webSite:`*Web SiteName* değeri \<\></span><span class="sxs-lookup"><span data-stu-id="18f96-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="18f96-137">Web barındırma modu kullanıldığında, barındırma için Web sitesini belirtir ( `/hosting` bayrağa bakın).</span><span class="sxs-lookup"><span data-stu-id="18f96-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="18f96-138">Kısa biçim `/w`.</span><span class="sxs-lookup"><span data-stu-id="18f96-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="18f96-139">Hiçbir Web sitesi belirtilmemişse, varsayılan Web sitesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18f96-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="18f96-140">`/webDirectory:`\< *WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="18f96-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="18f96-141">Web barındırma kullanıldığında, barındırma için sanal dizini belirtir ( `/hosting` bayrağa bakın).</span><span class="sxs-lookup"><span data-stu-id="18f96-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="18f96-142">Kısa biçim `/d`.</span><span class="sxs-lookup"><span data-stu-id="18f96-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="18f96-143">Hizmetten bir sözleşme tanımı almak isteyen istemcileri desteklemek için varsayılan hizmet yapılandırmasına bir meta veri değişimi (MEX) hizmet uç noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="18f96-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="18f96-144">Kısa biçim `/x`.</span><span class="sxs-lookup"><span data-stu-id="18f96-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="18f96-145">Uygulama, bileşen ve arabirim bilgilerini kimlik olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="18f96-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="18f96-146">Kısa biçim `/k`.</span><span class="sxs-lookup"><span data-stu-id="18f96-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="18f96-147">ComSvcConfig. exe ' nin logoyu görüntülemesini önler.</span><span class="sxs-lookup"><span data-stu-id="18f96-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="18f96-148">Kısa biçim `/n`.</span><span class="sxs-lookup"><span data-stu-id="18f96-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="18f96-149">Karşılaşılan hatalara ek olarak tüm uyarıları veya bilgilendirici metinleri çıkışlar.</span><span class="sxs-lookup"><span data-stu-id="18f96-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="18f96-150">Kısa biçim `/v`.</span><span class="sxs-lookup"><span data-stu-id="18f96-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="18f96-151">Kullanım iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="18f96-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="18f96-152">Kısa biçim `/?`.</span><span class="sxs-lookup"><span data-stu-id="18f96-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="18f96-153">Belirtilen arabirim gösterilebilir bir veya daha fazla yöntem imzası içerdiğinde bir hizmet yapılandırması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18f96-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="18f96-154">Hizmet başlatma sırasında, uyumlu yöntemler hizmet sözleşmesinde işlem olarak görünür ve uyumlu olmayan yöntemler, hizmet sözleşmesinde yok sayılır ve yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="18f96-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="18f96-155">Bu bayrak eksikse, belirtilen arabirim bir veya daha fazla uyumsuz yöntem içerdiğinde araç bir hizmet yapılandırması oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="18f96-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="18f96-156">Örnekler</span><span class="sxs-lookup"><span data-stu-id="18f96-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="18f96-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18f96-157">Description</span></span>  
 <span data-ttu-id="18f96-158">Aşağıdaki örnek, `IFinances` `ItemOrders.IFinancial` bileşen arabirimini (onlinesbir com+ uygulamasından) com+ barındırma modu kullanılarak Web Hizmetleri olarak gösterilen arabirimler kümesine ekler.</span><span class="sxs-lookup"><span data-stu-id="18f96-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="18f96-159">Karşılaşılan hatalara ek olarak tüm uyarılar çıktı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="18f96-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="18f96-160">Kod</span><span class="sxs-lookup"><span data-stu-id="18f96-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="18f96-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18f96-161">Description</span></span>  
 <span data-ttu-id="18f96-162">Aşağıdaki örnek, `IStockLevels` `ItemInventory.Warehouse` bileşen arabirimini (OnlineWarehouse com+ uygulamasından) Web barındırma modu kullanılarak Web Hizmetleri olarak gösterilen arabirimler kümesine ekler.</span><span class="sxs-lookup"><span data-stu-id="18f96-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="18f96-163">Web hizmeti, IIS 'nin OnlineWarehouse sanal dizininde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="18f96-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="18f96-164">Kod</span><span class="sxs-lookup"><span data-stu-id="18f96-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="18f96-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18f96-165">Description</span></span>  
 <span data-ttu-id="18f96-166">Aşağıdaki örnek `IFinances` `ItemOrders.Financial` bileşen arabirimini (onlinesbir com+ uygulamasından) Web Hizmetleri olarak kullanıma sunulan arabirimlerin kümesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="18f96-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="18f96-167">Kod</span><span class="sxs-lookup"><span data-stu-id="18f96-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="18f96-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18f96-168">Description</span></span>  
 <span data-ttu-id="18f96-169">Aşağıdaki örnek, yerel makinedeki Onlinescompactcom+ uygulaması için ilgili adres ve bağlama ayrıntılarının yanı sıra, şu anda sunulan COM+ barındırılan arabirimlerini listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="18f96-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="18f96-170">Kod</span><span class="sxs-lookup"><span data-stu-id="18f96-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="18f96-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18f96-171">See also</span></span>

- [<span data-ttu-id="18f96-172">Nasıl yapılır: COM+ hizmet modeli yapılandırma aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="18f96-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

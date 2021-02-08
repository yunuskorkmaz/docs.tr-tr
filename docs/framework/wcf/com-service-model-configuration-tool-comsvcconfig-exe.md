---
description: 'Daha fazla bilgi edinin: COM+ hizmet modeli yapılandırma aracı (ComSvcConfig.exe)'
title: COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 81bfcbd468cb5401646a49967b6381b48e2f7cf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781070"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="d212e-103">COM+ Hizmet Modeli Yapılandırma Aracı (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="d212e-103">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>

<span data-ttu-id="d212e-104">COM+ hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe), COM+ arabirimlerini Web Hizmetleri olarak kullanıma sunulacak şekilde yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d212e-104">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d212e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d212e-105">Syntax</span></span>  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="d212e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d212e-106">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d212e-107">ComSvcConfig.exe kullanmak için yerel bilgisayarda yönetici olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d212e-107">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="d212e-108">Araç aşağıdaki konumda bulunabilir</span><span class="sxs-lookup"><span data-stu-id="d212e-108">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="d212e-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="d212e-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="d212e-110">ComSvcConfig.exe hakkında daha fazla bilgi için bkz. [nasıl yapılır: com+ hizmet modeli yapılandırma aracını kullanma](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d212e-110">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="d212e-111">Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilecek modlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d212e-111">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="d212e-112">Seçenek</span><span class="sxs-lookup"><span data-stu-id="d212e-112">Option</span></span>|<span data-ttu-id="d212e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d212e-113">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="d212e-114">Hizmet modeli tümleştirmesi için bir COM+ arabirimi yapılandırması kurar.</span><span class="sxs-lookup"><span data-stu-id="d212e-114">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="d212e-115">Kısa biçim `/i` .</span><span class="sxs-lookup"><span data-stu-id="d212e-115">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="d212e-116">Bir COM+ arabiriminin yapılandırmasını hizmet modeli tümleştirmesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d212e-116">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="d212e-117">Kısa biçim `/u` .</span><span class="sxs-lookup"><span data-stu-id="d212e-117">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="d212e-118">Hizmet modeli tümleştirmesi için yapılandırılmış arabirimlerin bulunduğu COM+ uygulamaları ve bileşenleriyle ilgili bilgileri listeler.</span><span class="sxs-lookup"><span data-stu-id="d212e-118">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="d212e-119">Kısa biçim `/l` .</span><span class="sxs-lookup"><span data-stu-id="d212e-119">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="d212e-120">Aşağıdaki tabloda ComSvcConfig.exe ile kullanılabilecek bayraklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d212e-120">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="d212e-121">Seçenek</span><span class="sxs-lookup"><span data-stu-id="d212e-121">Option</span></span>|<span data-ttu-id="d212e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d212e-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d212e-123">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="d212e-123">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="d212e-124">Yapılandırılacak COM+ uygulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d212e-124">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="d212e-125">Kısa biçim `/a` .</span><span class="sxs-lookup"><span data-stu-id="d212e-125">Short form `/a`.</span></span>|  
|<span data-ttu-id="d212e-126">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="d212e-126">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="d212e-127">Hizmet için sözleşme olarak yapılandırılacak COM+ bileşenini ve arabirimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d212e-127">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="d212e-128">Kısa biçim `/c` .</span><span class="sxs-lookup"><span data-stu-id="d212e-128">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="d212e-129">\*Bileşen ve arabirim adlarını belirttiğinizde joker karakteri () kullanılabilir olsa da, istemediğiniz arabirimleri kullanıma sunabileceğiniz için bunu kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="d212e-129">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="d212e-130">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="d212e-130">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="d212e-131">COM+ barındırma modunun mi yoksa Web barındırma modunun mi kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d212e-131">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="d212e-132">Kısa biçim `/h` .</span><span class="sxs-lookup"><span data-stu-id="d212e-132">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="d212e-133">COM+ barındırma modu ' nu kullanmak, COM+ uygulamasının açık etkinleştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d212e-133">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="d212e-134">Web barındırma modunun kullanılması, COM+ uygulamasının gerektiği şekilde otomatik olarak etkinleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d212e-134">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="d212e-135">COM+ uygulaması bir kitaplık uygulaması ise, Internet Information Services (IIS) işleminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="d212e-135">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="d212e-136">COM+ uygulaması bir sunucu uygulaması ise, Dllhost.exe sürecinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="d212e-136">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="d212e-137">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="d212e-137">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="d212e-138">Web barındırma modu kullanıldığında, barındırma için Web sitesini belirtir ( `/hosting` bayrağa bakın).</span><span class="sxs-lookup"><span data-stu-id="d212e-138">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="d212e-139">Kısa biçim `/w` .</span><span class="sxs-lookup"><span data-stu-id="d212e-139">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="d212e-140">Hiçbir Web sitesi belirtilmemişse, varsayılan Web sitesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d212e-140">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="d212e-141">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="d212e-141">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="d212e-142">Web barındırma kullanıldığında, barındırma için sanal dizini belirtir ( `/hosting` bayrağa bakın).</span><span class="sxs-lookup"><span data-stu-id="d212e-142">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="d212e-143">Kısa biçim `/d` .</span><span class="sxs-lookup"><span data-stu-id="d212e-143">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="d212e-144">Hizmetten bir sözleşme tanımı almak isteyen istemcileri desteklemek için varsayılan hizmet yapılandırmasına bir meta veri değişimi (MEX) hizmet uç noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="d212e-144">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="d212e-145">Kısa biçim `/x` .</span><span class="sxs-lookup"><span data-stu-id="d212e-145">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="d212e-146">Uygulama, bileşen ve arabirim bilgilerini kimlik olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d212e-146">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="d212e-147">Kısa biçim `/k` .</span><span class="sxs-lookup"><span data-stu-id="d212e-147">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="d212e-148">ComSvcConfig.exe logosunu görüntülemesini engeller.</span><span class="sxs-lookup"><span data-stu-id="d212e-148">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="d212e-149">Kısa biçim `/n` .</span><span class="sxs-lookup"><span data-stu-id="d212e-149">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="d212e-150">Karşılaşılan hatalara ek olarak tüm uyarıları veya bilgilendirici metinleri çıkışlar.</span><span class="sxs-lookup"><span data-stu-id="d212e-150">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="d212e-151">Kısa biçim `/v` .</span><span class="sxs-lookup"><span data-stu-id="d212e-151">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="d212e-152">Kullanım iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d212e-152">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="d212e-153">Kısa biçim `/?` .</span><span class="sxs-lookup"><span data-stu-id="d212e-153">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="d212e-154">Belirtilen arabirim gösterilebilir bir veya daha fazla yöntem imzası içerdiğinde bir hizmet yapılandırması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d212e-154">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="d212e-155">Hizmet başlatma sırasında, uyumlu yöntemler hizmet sözleşmesinde işlem olarak görünür ve uyumlu olmayan yöntemler, hizmet sözleşmesinde yok sayılır ve yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d212e-155">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="d212e-156">Bu bayrak eksikse, belirtilen arabirim bir veya daha fazla uyumsuz yöntem içerdiğinde araç bir hizmet yapılandırması oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d212e-156">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="d212e-157">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d212e-157">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="d212e-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d212e-158">Description</span></span>  

 <span data-ttu-id="d212e-159">Aşağıdaki örnek, `IFinances` `ItemOrders.IFinancial` bileşen arabirimini (ONLINESBIR com+ UYGULAMASıNDAN) com+ barındırma modu kullanılarak Web Hizmetleri olarak gösterilen arabirimler kümesine ekler.</span><span class="sxs-lookup"><span data-stu-id="d212e-159">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="d212e-160">Karşılaşılan hatalara ek olarak tüm uyarılar çıktı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d212e-160">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d212e-161">Kod</span><span class="sxs-lookup"><span data-stu-id="d212e-161">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="d212e-162">Description</span><span class="sxs-lookup"><span data-stu-id="d212e-162">Description</span></span>  

 <span data-ttu-id="d212e-163">Aşağıdaki örnek, `IStockLevels` `ItemInventory.Warehouse` bileşen arabirimini (OnlineWarehouse com+ uygulamasından) Web barındırma modu kullanılarak Web Hizmetleri olarak gösterilen arabirimler kümesine ekler.</span><span class="sxs-lookup"><span data-stu-id="d212e-163">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="d212e-164">Web hizmeti, IIS 'nin OnlineWarehouse sanal dizininde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="d212e-164">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d212e-165">Kod</span><span class="sxs-lookup"><span data-stu-id="d212e-165">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="d212e-166">Description</span><span class="sxs-lookup"><span data-stu-id="d212e-166">Description</span></span>  

 <span data-ttu-id="d212e-167">Aşağıdaki örnek `IFinances` `ItemOrders.Financial` bileşen arabirimini (ONLINESBIR com+ uygulamasından) Web Hizmetleri olarak kullanıma sunulan arabirimlerin kümesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d212e-167">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d212e-168">Kod</span><span class="sxs-lookup"><span data-stu-id="d212e-168">Code</span></span>  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="d212e-169">Description</span><span class="sxs-lookup"><span data-stu-id="d212e-169">Description</span></span>  

 <span data-ttu-id="d212e-170">Aşağıdaki örnek, yerel makinedeki Onlinescompactcom+ uygulaması için ilgili adres ve bağlama ayrıntılarının yanı sıra, şu anda sunulan COM+ barındırılan arabirimlerini listelemektedir.</span><span class="sxs-lookup"><span data-stu-id="d212e-170">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d212e-171">Kod</span><span class="sxs-lookup"><span data-stu-id="d212e-171">Code</span></span>  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="d212e-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d212e-172">See also</span></span>

- [<span data-ttu-id="d212e-173">Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma</span><span class="sxs-lookup"><span data-stu-id="d212e-173">How to: Use the COM+ Service Model Configuration Tool</span></span>](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)

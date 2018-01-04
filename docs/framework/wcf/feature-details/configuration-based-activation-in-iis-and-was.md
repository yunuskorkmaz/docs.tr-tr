---
title: "IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc0e954ae5cadbe7e70cd8a83d3d5841f4e0d142
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="98f1a-102">IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="98f1a-102">Configuration-Based Activation in IIS and WAS</span></span>
<span data-ttu-id="98f1a-103">Normalde barındırdığında bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) altında bir .svc dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="98f1a-103">Normally when hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="98f1a-104">.Svc dosya hizmeti ve isteğe bağlı özel hizmet ana bilgisayar üreteci adını içerir.</span><span class="sxs-lookup"><span data-stu-id="98f1a-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="98f1a-105">Bu ek dosya yönetilebilirlik yükünü ekler.</span><span class="sxs-lookup"><span data-stu-id="98f1a-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="98f1a-106">Yapılandırma temelli etkinleştirme özelliği .svc dosyası ve bu nedenle ilişkili sahip gereksinimini ortadan kaldırır yükü.</span><span class="sxs-lookup"><span data-stu-id="98f1a-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>  
  
## <a name="configuration-based-activation"></a><span data-ttu-id="98f1a-107">Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="98f1a-107">Configuration-Based Activation</span></span>  
 <span data-ttu-id="98f1a-108">Yapılandırma temelli etkinleştirme .svc dosyasında yerleştirilmesi için kullanılır ve Web.config dosyasına yerleştirir meta veriler alır.</span><span class="sxs-lookup"><span data-stu-id="98f1a-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="98f1a-109">İçinde <`serviceHostingEnvironment`> öğesi var. bir <`serviceActivations`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="98f1a-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="98f1a-110">İçinde <`serviceActivations`> öğesi bir veya daha fazla <`add`> öğeleri, her barındırılan hizmeti için bir.</span><span class="sxs-lookup"><span data-stu-id="98f1a-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="98f1a-111"><`add`> Öğesi, hizmet ve hizmet türü veya hizmet ana bilgisayar üreteci için göreli adresi ayarlamanıza olanak tanıyan öznitelikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="98f1a-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="98f1a-112">Aşağıdaki kod yapılandırma örneği, bu bölümde nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98f1a-112">The following configuration example code shows how this section is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98f1a-113">Her <`add`> öğesi, bir hizmet ya da bir Fabrika öznitelik belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="98f1a-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="98f1a-114">Hem hizmet hem de Fabrika öznitelikleri belirtme izin verilir.</span><span class="sxs-lookup"><span data-stu-id="98f1a-114">Specifying both service and factory attributes is allowed.</span></span>  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 <span data-ttu-id="98f1a-115">Bu Web.config dosyasında, hizmet kaynak kodu uygulama veya uygulamanın Bin dizinindeki derlenmiş bir derlemeyi App_Code dizinindeki yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98f1a-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="98f1a-116">Yapılandırma temelli etkinleştirme kullanırken, satır içi kod .svc dosyalarında desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="98f1a-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>  
> -   <span data-ttu-id="98f1a-117">`relativeAddress` Özniteliği ayarlanmalıdır göreli adresine gibi "\<alt dizini > / service.svc" veya "~ /\<alt directory/service.svc".</span><span class="sxs-lookup"><span data-stu-id="98f1a-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>  
> -   <span data-ttu-id="98f1a-118">WCF ile ilgili bilinen bir uzantı göreli bir adres kaydederseniz yapılandırma özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="98f1a-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>  
> -   <span data-ttu-id="98f1a-119">Belirtilen göreli adresi sanal uygulama göreli köküdür.</span><span class="sxs-lookup"><span data-stu-id="98f1a-119">The relative address specified is relative to the root of the virtual application.</span></span>  
> -   <span data-ttu-id="98f1a-120">Hiyerarşik yapılandırma modeli nedeniyle, makine ve site düzeyinde kayıtlı göreli adresleri sanal uygulamalar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="98f1a-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>  
> -   <span data-ttu-id="98f1a-121">Kayıtlar yapılandırma dosyasında bir .svc, .xamlx, .xoml veya başka bir dosya ayarlarında daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="98f1a-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>  
> -   <span data-ttu-id="98f1a-122">Tüm ' \' (ters eğik çizgi) IIS gönderilen bir URI / olan otomatik olarak dönüştürülür bir '/' (eğik çizgi).</span><span class="sxs-lookup"><span data-stu-id="98f1a-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="98f1a-123">Göreli bir adresi eklenirse içeren bir ' \' ve IIS göreli adresini kullanan bir URI göndermek, ters eğik çizgiyi eğik için dönüştürülür ve IIS, göreli adresine eşleşemez.</span><span class="sxs-lookup"><span data-stu-id="98f1a-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="98f1a-124">IIS eşleşme olduğunu gösteren izleme bilgilerini gönderir.</span><span class="sxs-lookup"><span data-stu-id="98f1a-124">IIS sends out trace information that indicates that there are no matches found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f1a-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98f1a-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [<span data-ttu-id="98f1a-126">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="98f1a-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="98f1a-127">İş Akışı Hizmetlerini Barındırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="98f1a-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [<span data-ttu-id="98f1a-128">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="98f1a-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [<span data-ttu-id="98f1a-129">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="98f1a-129">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)

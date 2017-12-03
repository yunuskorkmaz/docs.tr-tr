---
title: '&lt;exposedMethod&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecef8049a980f662cce4c421f62ccd3703400d69
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltexposedmethodgt"></a><span data-ttu-id="7b772-102">&lt;exposedMethod&gt;</span><span class="sxs-lookup"><span data-stu-id="7b772-102">&lt;exposedMethod&gt;</span></span>
<span data-ttu-id="7b772-103">Bir Web hizmeti olarak bir COM bileşeni arabirimde kullanıma sunulduğunda sunulan bir COM + yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b772-103">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="7b772-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7b772-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b772-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="7b772-105">\<comContracts></span></span>  
<span data-ttu-id="7b772-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="7b772-106">\<comContract></span></span>  
<span data-ttu-id="7b772-107">\<yöntemleri ></span><span class="sxs-lookup"><span data-stu-id="7b772-107">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b772-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b772-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b772-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b772-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7b772-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b772-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b772-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7b772-111">Attributes</span></span>  
  
|<span data-ttu-id="7b772-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7b772-112">Attribute</span></span>|<span data-ttu-id="7b772-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b772-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b772-114">name</span><span class="sxs-lookup"><span data-stu-id="7b772-114">name</span></span>|<span data-ttu-id="7b772-115">Bir Web hizmeti olarak bir COM bileşeni arabirimde kullanıma sunulduğunda sunulan COM + yöntemini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="7b772-115">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b772-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b772-116">Child Elements</span></span>  
 <span data-ttu-id="7b772-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7b772-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b772-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b772-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7b772-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7b772-119">Element</span></span>|<span data-ttu-id="7b772-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b772-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b772-121">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="7b772-121">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="7b772-122">Bir koleksiyonu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="7b772-122">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b772-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b772-123">Remarks</span></span>  
 <span data-ttu-id="7b772-124">COM + tümleştirme Yapılandırma Aracı (ComSvcConfig.exe) oluşturulan hizmet sözleşmesini görünmesi bir COM arabirimden belirli yöntemleri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b772-124">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="7b772-125">Örneğin, üç adlandırılmış yöntemleri eklemek için aşağıdaki komutu kullanabilirsiniz `IFinances` COM arabirimde `ItemOrders`. Oluşturulan servis sözleşmesi finansal bileşeni.</span><span class="sxs-lookup"><span data-stu-id="7b772-125">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="7b772-126">Sonra da ComSvcConfig.exe çalıştırdığınızda, yukarıda açıklanan yöntemleri olarak listeleniyor aşağıdaki hizmet sözleşmesini ürettiği [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="7b772-126">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 <span data-ttu-id="7b772-127">Hizmet başlatma zamanında çalışma zamanı hizmet sözleşmesi üzerinden yansıtma ve yalnızca listesinde yer yöntemleri ekleyerek oluşturmaya çalıştığında [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="7b772-127">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="7b772-128">İzleme, hizmet sözleşmesini dahil edilmeyen her arabirim yöntemi için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7b772-128">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b772-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b772-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [<span data-ttu-id="7b772-130">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="7b772-130">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="7b772-131">COM + uygulamaları ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="7b772-131">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="7b772-132">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7b772-132">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

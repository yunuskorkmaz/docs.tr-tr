---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 91eafa46aa73b5e6d359fcbe48f098f9f8a4d0f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644322"
---
# <a name="exposedmethod"></a><span data-ttu-id="39b84-101">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="39b84-101">\<exposedMethod></span></span>
<span data-ttu-id="39b84-102">Bir COM + bileşeni üzerinde arabirim bir Web hizmeti olarak sunulduğunda, sunulan bir COM + metodunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39b84-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="39b84-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39b84-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="39b84-104">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="39b84-104">\<comContracts></span></span>  
<span data-ttu-id="39b84-105">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="39b84-105">\<comContract></span></span>  
<span data-ttu-id="39b84-106">\<yöntemleri ></span><span class="sxs-lookup"><span data-stu-id="39b84-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39b84-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39b84-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39b84-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39b84-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39b84-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39b84-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39b84-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39b84-110">Attributes</span></span>  
  
|<span data-ttu-id="39b84-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39b84-111">Attribute</span></span>|<span data-ttu-id="39b84-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39b84-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39b84-113">name</span><span class="sxs-lookup"><span data-stu-id="39b84-113">name</span></span>|<span data-ttu-id="39b84-114">Bir COM + bileşeni üzerinde arabirim bir Web hizmeti olarak sunulduğunda, sunulan COM + metodunu içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="39b84-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39b84-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39b84-115">Child Elements</span></span>  
 <span data-ttu-id="39b84-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="39b84-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39b84-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39b84-117">Parent Elements</span></span>  
  
|<span data-ttu-id="39b84-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="39b84-118">Element</span></span>|<span data-ttu-id="39b84-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39b84-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39b84-120">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="39b84-120">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="39b84-121">Bir koleksiyonu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="39b84-121">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39b84-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39b84-122">Remarks</span></span>  
 <span data-ttu-id="39b84-123">COM + tümleştirme Yapılandırma Aracı (ComSvcConfig.exe), bir COM arabiriminden oluşturulan hizmet sözleşmesini görünmesini belirli yöntemler eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39b84-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="39b84-124">Örneğin, üç adlandırılmış yöntemleri eklemek için aşağıdaki komutu kullanabilirsiniz `IFinances` COM arabirimi `ItemOrders`. Oluşturulan hizmet sözleşmesi için finansal bileşeni.</span><span class="sxs-lookup"><span data-stu-id="39b84-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="39b84-125">Sonra da ComSvcConfig.exe çalıştırdığınızda, daha önce bahsedilen yöntemler olarak listeleme aşağıdaki hizmet sözleşmesi ürettiği [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="39b84-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="39b84-126">Üzerinden yansıtarak ve yalnızca listesine dahil yöntemleri ekleyerek bir hizmet sözleşmesini oluşturmak çalışma zamanı hizmet başlangıç zamanında çalışır [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="39b84-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="39b84-127">İzleme, hizmet sözleşmesinde yer almayan her arabirim yöntemi için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39b84-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b84-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39b84-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="39b84-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="39b84-129">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="39b84-130">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="39b84-130">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="39b84-131">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="39b84-131">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

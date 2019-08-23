---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 032139b714aa11079c7ee8610c332e404b3981ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918993"
---
# <a name="exposedmethod"></a><span data-ttu-id="80351-101">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="80351-101">\<exposedMethod></span></span>
<span data-ttu-id="80351-102">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan bir COM+ yöntemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="80351-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="80351-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80351-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="80351-104">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="80351-104">\<comContracts></span></span>  
<span data-ttu-id="80351-105">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="80351-105">\<comContract></span></span>  
<span data-ttu-id="80351-106">\<Yöntemler ></span><span class="sxs-lookup"><span data-stu-id="80351-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80351-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80351-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80351-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="80351-108">Attributes and Elements</span></span>  
 <span data-ttu-id="80351-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80351-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80351-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80351-110">Attributes</span></span>  
  
|<span data-ttu-id="80351-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="80351-111">Attribute</span></span>|<span data-ttu-id="80351-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80351-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80351-113">name</span><span class="sxs-lookup"><span data-stu-id="80351-113">name</span></span>|<span data-ttu-id="80351-114">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="80351-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80351-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="80351-115">Child Elements</span></span>  
 <span data-ttu-id="80351-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="80351-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80351-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="80351-117">Parent Elements</span></span>  
  
|<span data-ttu-id="80351-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="80351-118">Element</span></span>|<span data-ttu-id="80351-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80351-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80351-120">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="80351-120">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="80351-121">Bir [ \<ExposedMethod >](exposedmethod.md) öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="80351-121">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80351-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80351-122">Remarks</span></span>  
 <span data-ttu-id="80351-123">COM+ tümleştirme yapılandırma aracı (ComSvcConfig. exe), bir COM arabiriminden oluşturulan hizmet sözleşmesinde görünecek belirli yöntemler eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="80351-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="80351-124">Örneğin, ' `IFinances` `ItemOrders`de com arabiriminden üç adlandırılmış yöntemi eklemek için aşağıdaki komutu kullanabilirsiniz. Finans bileşeni, oluşturulan hizmet sözleşmesine.</span><span class="sxs-lookup"><span data-stu-id="80351-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="80351-125">ComSvcConfig. exe dosyasını da çalıştırdığınızda, daha önce bahsedilen yöntemleri [ \<ExposedMethod >](exposedmethod.md) öğeleri olarak listeleyerek aşağıdaki hizmet sözleşmesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="80351-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="80351-126">Hizmet başlatma sırasında çalışma zamanı, yalnızca [ \<ExposedMethod >](exposedmethod.md) öğeleri listesine dahil edilen yöntemleri inceleyerek ve ekleyerek bir hizmet sözleşmesi oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="80351-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="80351-127">Hizmet sözleşmesine dahil olmayan her arabirim yöntemi için bir izleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="80351-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80351-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80351-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="80351-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="80351-129">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="80351-130">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="80351-130">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="80351-131">Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="80351-131">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855303"
---
# <a name="exposedmethod"></a><span data-ttu-id="85fad-101">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="85fad-101">\<exposedMethod></span></span>
<span data-ttu-id="85fad-102">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan bir COM+ yöntemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="85fad-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
<span data-ttu-id="85fad-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="85fad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="85fad-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="85fad-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="85fad-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="85fad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="85fad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="85fad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="85fad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<exposedMethods >** ](exposedmethods.md)</span><span class="sxs-lookup"><span data-stu-id="85fad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)</span></span>\
<span data-ttu-id="85fad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<exposedMethod >**</span><span class="sxs-lookup"><span data-stu-id="85fad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85fad-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85fad-109">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85fad-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="85fad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="85fad-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85fad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85fad-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85fad-112">Attributes</span></span>  
  
|<span data-ttu-id="85fad-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="85fad-113">Attribute</span></span>|<span data-ttu-id="85fad-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85fad-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85fad-115">name</span><span class="sxs-lookup"><span data-stu-id="85fad-115">name</span></span>|<span data-ttu-id="85fad-116">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="85fad-116">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85fad-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="85fad-117">Child Elements</span></span>  
 <span data-ttu-id="85fad-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="85fad-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85fad-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="85fad-119">Parent Elements</span></span>  
  
|<span data-ttu-id="85fad-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="85fad-120">Element</span></span>|<span data-ttu-id="85fad-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85fad-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85fad-122">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="85fad-122">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="85fad-123">Bir [ \<ExposedMethod >](exposedmethod.md) öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="85fad-123">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85fad-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85fad-124">Remarks</span></span>  
 <span data-ttu-id="85fad-125">COM+ tümleştirme yapılandırma aracı (ComSvcConfig. exe), bir COM arabiriminden oluşturulan hizmet sözleşmesinde görünecek belirli yöntemler eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="85fad-125">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="85fad-126">Örneğin, ' `IFinances` `ItemOrders`de com arabiriminden üç adlandırılmış yöntemi eklemek için aşağıdaki komutu kullanabilirsiniz. Finans bileşeni, oluşturulan hizmet sözleşmesine.</span><span class="sxs-lookup"><span data-stu-id="85fad-126">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="85fad-127">ComSvcConfig. exe dosyasını da çalıştırdığınızda, daha önce bahsedilen yöntemleri [ \<ExposedMethod >](exposedmethod.md) öğeleri olarak listeleyerek aşağıdaki hizmet sözleşmesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85fad-127">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="85fad-128">Hizmet başlatma sırasında çalışma zamanı, yalnızca [ \<ExposedMethod >](exposedmethod.md) öğeleri listesine dahil edilen yöntemleri inceleyerek ve ekleyerek bir hizmet sözleşmesi oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="85fad-128">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="85fad-129">Hizmet sözleşmesine dahil olmayan her arabirim yöntemi için bir izleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="85fad-129">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85fad-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85fad-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="85fad-131">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="85fad-131">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="85fad-132">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="85fad-132">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="85fad-133">Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="85fad-133">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

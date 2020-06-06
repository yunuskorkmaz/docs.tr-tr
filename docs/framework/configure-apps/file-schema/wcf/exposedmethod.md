---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855303"
---
# \<exposedMethod>
<span data-ttu-id="f6ae3-101">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan bir COM+ yöntemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f6ae3-101">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a><span data-ttu-id="f6ae3-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6ae3-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6ae3-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6ae3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f6ae3-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6ae3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6ae3-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6ae3-105">Attributes</span></span>  
  
|<span data-ttu-id="f6ae3-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6ae3-106">Attribute</span></span>|<span data-ttu-id="f6ae3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6ae3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6ae3-108">name</span><span class="sxs-lookup"><span data-stu-id="f6ae3-108">name</span></span>|<span data-ttu-id="f6ae3-109">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f6ae3-109">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6ae3-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6ae3-110">Child Elements</span></span>  
 <span data-ttu-id="f6ae3-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f6ae3-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6ae3-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6ae3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f6ae3-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f6ae3-113">Element</span></span>|<span data-ttu-id="f6ae3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6ae3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|<span data-ttu-id="f6ae3-115">[\<exposedMethod>](exposedmethod.md)Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f6ae3-115">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6ae3-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6ae3-116">Remarks</span></span>  
 <span data-ttu-id="f6ae3-117">COM+ tümleştirme yapılandırma aracı (ComSvcConfig. exe), bir COM arabiriminden oluşturulan hizmet sözleşmesinde görünecek belirli yöntemler eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f6ae3-117">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="f6ae3-118">Örneğin, ' de com arabiriminden üç adlandırılmış yöntemi eklemek için aşağıdaki komutu kullanabilirsiniz `IFinances` `ItemOrders` . Finans bileşeni, oluşturulan hizmet sözleşmesine.</span><span class="sxs-lookup"><span data-stu-id="f6ae3-118">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="f6ae3-119">ComSvcConfig. exe dosyasını da çalıştırdığınızda, daha önce bahsedilen yöntemleri öğe olarak listeleyerek aşağıdaki hizmet sözleşmesini oluşturur [\<exposedMethod>](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="f6ae3-119">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="f6ae3-120">Hizmet başlatma sırasında çalışma zamanı, yalnızca öğe listesine dahil olan yöntemleri inceleyerek ve ekleyerek bir hizmet sözleşmesi oluşturmaya çalışır [\<exposedMethod>](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="f6ae3-120">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="f6ae3-121">Hizmet sözleşmesine dahil olmayan her arabirim yöntemi için bir izleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f6ae3-121">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ae3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6ae3-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="f6ae3-123">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="f6ae3-123">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="f6ae3-124">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f6ae3-124">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

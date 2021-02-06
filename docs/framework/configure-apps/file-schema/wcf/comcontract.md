---
description: 'Hakkında daha fazla bilgi edinin: <comContract>'
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: fde1188a087f13da6629460bcebcea16ceefc0e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638671"
---
# \<comContract>

<span data-ttu-id="9f2ab-102">Bir COM+ tümleştirme hizmeti sözleşmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-102">Specifies a COM+ integration service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a><span data-ttu-id="9f2ab-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="9f2ab-103">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f2ab-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f2ab-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9f2ab-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f2ab-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f2ab-106">Attributes</span></span>  
  
|<span data-ttu-id="9f2ab-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9f2ab-107">Attribute</span></span>|<span data-ttu-id="9f2ab-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f2ab-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f2ab-109">Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="9f2ab-109">contract</span></span>|<span data-ttu-id="9f2ab-110">Sözleşme türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-110">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="9f2ab-111">name</span><span class="sxs-lookup"><span data-stu-id="9f2ab-111">name</span></span>|<span data-ttu-id="9f2ab-112">Sözleşme adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-112">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="9f2ab-113">ad alanı</span><span class="sxs-lookup"><span data-stu-id="9f2ab-113">namespace</span></span>|<span data-ttu-id="9f2ab-114">Sözleşme ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-114">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="9f2ab-115">requiresSession</span><span class="sxs-lookup"><span data-stu-id="9f2ab-115">requiresSession</span></span>|<span data-ttu-id="9f2ab-116">Sözleşmenin yalnızca oturumsuz bağlamalarda kullanılıp kullanılamayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-116">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="9f2ab-117">Hizmet başlatıldığında, tümleştirme çalışma zamanı bu ayarın kullanılacak bağlama türüyle tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-117">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="9f2ab-118">Sözleşme için bir veya daha fazla bağlama çakışırsa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-118">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="9f2ab-119">Bu özellik ise `false` ve tek yönlü bir kanal kullanımda ise ve herhangi bir [out] parametresi varsa, bir özel durum da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-119">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f2ab-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f2ab-120">Child Elements</span></span>  
  
|<span data-ttu-id="9f2ab-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f2ab-121">Element</span></span>|<span data-ttu-id="9f2ab-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f2ab-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f2ab-123">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="9f2ab-123">persistableTypes</span></span>|<span data-ttu-id="9f2ab-124">Tüm kalıcı türleri.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-124">All the persistable types.</span></span>|  
|<span data-ttu-id="9f2ab-125">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="9f2ab-125">userDefinedTypes</span></span>|<span data-ttu-id="9f2ab-126">Hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı türler (UDT) koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-126">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="9f2ab-127">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="9f2ab-127">exposedMethods</span></span>|<span data-ttu-id="9f2ab-128">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemlerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-128">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f2ab-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f2ab-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9f2ab-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f2ab-130">Element</span></span>|<span data-ttu-id="9f2ab-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f2ab-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f2ab-132">comContracts</span><span class="sxs-lookup"><span data-stu-id="9f2ab-132">comContracts</span></span>|<span data-ttu-id="9f2ab-133">Öğe koleksiyonunu içerir `comContract` .</span><span class="sxs-lookup"><span data-stu-id="9f2ab-133">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f2ab-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f2ab-134">Remarks</span></span>  

 <span data-ttu-id="9f2ab-135">COM+ tümleştirme hizmeti sözleşmeleri Şu anda `http://tempuri.org` ad alanıyla kısıtlıdır ve anlaşma adı DESTEKLEYICI com arabiriminden türetilir.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-135">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="9f2ab-136">Ancak, öğesini ve `comContracts` `comContract` yapılandırma dosyasındaki öğesini kullanarak alternatifleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-136">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="9f2ab-137">Örneğin, eklenecek ad alanı, sözleşme adı ve Kullanıcı tanımlı türleri, ayrıca bir hizmet sözleşmesinin diğer ayarlarını belirtmek için aşağıdaki yapılandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-137">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="9f2ab-138">Hizmet başlatıldığında, belirtilen ad alanları ve sözleşme adları oluşturulan hizmet açıklamalarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-138">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f2ab-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f2ab-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="9f2ab-140">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="9f2ab-140">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="9f2ab-141">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f2ab-141">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

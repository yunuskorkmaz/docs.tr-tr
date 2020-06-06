---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850032"
---
# \<comContract>
<span data-ttu-id="31f8d-101">Bir COM+ tümleştirme hizmeti sözleşmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="31f8d-101">Specifies a COM+ integration service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a><span data-ttu-id="31f8d-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31f8d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31f8d-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31f8d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="31f8d-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31f8d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31f8d-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31f8d-105">Attributes</span></span>  
  
|<span data-ttu-id="31f8d-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31f8d-106">Attribute</span></span>|<span data-ttu-id="31f8d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31f8d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31f8d-108">Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="31f8d-108">contract</span></span>|<span data-ttu-id="31f8d-109">Sözleşme türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="31f8d-109">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="31f8d-110">name</span><span class="sxs-lookup"><span data-stu-id="31f8d-110">name</span></span>|<span data-ttu-id="31f8d-111">Sözleşme adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="31f8d-111">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="31f8d-112">ad alanı</span><span class="sxs-lookup"><span data-stu-id="31f8d-112">namespace</span></span>|<span data-ttu-id="31f8d-113">Sözleşme ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="31f8d-113">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="31f8d-114">requiresSession</span><span class="sxs-lookup"><span data-stu-id="31f8d-114">requiresSession</span></span>|<span data-ttu-id="31f8d-115">Sözleşmenin yalnızca oturumsuz bağlamalarda kullanılıp kullanılamayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="31f8d-115">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="31f8d-116">Hizmet başlatıldığında, tümleştirme çalışma zamanı bu ayarın kullanılacak bağlama türüyle tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="31f8d-116">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="31f8d-117">Sözleşme için bir veya daha fazla bağlama çakışırsa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="31f8d-117">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="31f8d-118">Bu özellik ise `false` ve tek yönlü bir kanal kullanımda ise ve herhangi bir [out] parametresi varsa, bir özel durum da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="31f8d-118">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31f8d-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31f8d-119">Child Elements</span></span>  
  
|<span data-ttu-id="31f8d-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="31f8d-120">Element</span></span>|<span data-ttu-id="31f8d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31f8d-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31f8d-122">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="31f8d-122">persistableTypes</span></span>|<span data-ttu-id="31f8d-123">Tüm kalıcı türleri.</span><span class="sxs-lookup"><span data-stu-id="31f8d-123">All the persistable types.</span></span>|  
|<span data-ttu-id="31f8d-124">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="31f8d-124">userDefinedTypes</span></span>|<span data-ttu-id="31f8d-125">Hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı türler (UDT) koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="31f8d-125">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="31f8d-126">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="31f8d-126">exposedMethods</span></span>|<span data-ttu-id="31f8d-127">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemlerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="31f8d-127">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31f8d-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31f8d-128">Parent Elements</span></span>  
  
|<span data-ttu-id="31f8d-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="31f8d-129">Element</span></span>|<span data-ttu-id="31f8d-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31f8d-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31f8d-131">comContracts</span><span class="sxs-lookup"><span data-stu-id="31f8d-131">comContracts</span></span>|<span data-ttu-id="31f8d-132">Öğe koleksiyonunu içerir `comContract` .</span><span class="sxs-lookup"><span data-stu-id="31f8d-132">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31f8d-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31f8d-133">Remarks</span></span>  
 <span data-ttu-id="31f8d-134">COM+ tümleştirme hizmeti sözleşmeleri Şu anda `http://tempuri.org` ad alanıyla kısıtlıdır ve anlaşma adı DESTEKLEYICI com arabiriminden türetilir.</span><span class="sxs-lookup"><span data-stu-id="31f8d-134">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="31f8d-135">Ancak, öğesini ve `comContracts` `comContract` yapılandırma dosyasındaki öğesini kullanarak alternatifleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31f8d-135">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="31f8d-136">Örneğin, eklenecek ad alanı, sözleşme adı ve Kullanıcı tanımlı türleri, ayrıca bir hizmet sözleşmesinin diğer ayarlarını belirtmek için aşağıdaki yapılandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31f8d-136">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="31f8d-137">Hizmet başlatıldığında, belirtilen ad alanları ve sözleşme adları oluşturulan hizmet açıklamalarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="31f8d-137">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f8d-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31f8d-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="31f8d-139">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="31f8d-139">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="31f8d-140">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="31f8d-140">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

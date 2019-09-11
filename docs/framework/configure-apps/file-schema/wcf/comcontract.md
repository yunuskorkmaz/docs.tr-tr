---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850032"
---
# <a name="comcontract"></a><span data-ttu-id="24cee-101">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="24cee-101">\<comContract></span></span>
<span data-ttu-id="24cee-102">Bir COM+ tümleştirme hizmeti sözleşmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="24cee-102">Specifies a COM+ integration service contract.</span></span>  
  
<span data-ttu-id="24cee-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="24cee-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="24cee-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="24cee-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="24cee-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="24cee-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="24cee-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<comContract >**</span><span class="sxs-lookup"><span data-stu-id="24cee-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24cee-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24cee-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24cee-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="24cee-108">Attributes and Elements</span></span>  
 <span data-ttu-id="24cee-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24cee-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24cee-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="24cee-110">Attributes</span></span>  
  
|<span data-ttu-id="24cee-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="24cee-111">Attribute</span></span>|<span data-ttu-id="24cee-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cee-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24cee-113">contract</span><span class="sxs-lookup"><span data-stu-id="24cee-113">contract</span></span>|<span data-ttu-id="24cee-114">Sözleşme türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="24cee-114">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="24cee-115">name</span><span class="sxs-lookup"><span data-stu-id="24cee-115">name</span></span>|<span data-ttu-id="24cee-116">Sözleşme adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="24cee-116">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="24cee-117">ad alanı</span><span class="sxs-lookup"><span data-stu-id="24cee-117">namespace</span></span>|<span data-ttu-id="24cee-118">Sözleşme ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="24cee-118">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="24cee-119">requiresSession</span><span class="sxs-lookup"><span data-stu-id="24cee-119">requiresSession</span></span>|<span data-ttu-id="24cee-120">Sözleşmenin yalnızca oturumsuz bağlamalarda kullanılıp kullanılamayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="24cee-120">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="24cee-121">Hizmet başlatıldığında, tümleştirme çalışma zamanı bu ayarın kullanılacak bağlama türüyle tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="24cee-121">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="24cee-122">Sözleşme için bir veya daha fazla bağlama çakışırsa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24cee-122">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="24cee-123">Bu özellik ise `false`ve tek yönlü bir kanal kullanımda ise ve herhangi bir [out] parametresi varsa, bir özel durum da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24cee-123">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24cee-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="24cee-124">Child Elements</span></span>  
  
|<span data-ttu-id="24cee-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="24cee-125">Element</span></span>|<span data-ttu-id="24cee-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cee-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24cee-127">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="24cee-127">persistableTypes</span></span>|<span data-ttu-id="24cee-128">Tüm kalıcı türleri.</span><span class="sxs-lookup"><span data-stu-id="24cee-128">All the persistable types.</span></span>|  
|<span data-ttu-id="24cee-129">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="24cee-129">userDefinedTypes</span></span>|<span data-ttu-id="24cee-130">Hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı türler (UDT) koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="24cee-130">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="24cee-131">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="24cee-131">exposedMethods</span></span>|<span data-ttu-id="24cee-132">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemlerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="24cee-132">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24cee-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="24cee-133">Parent Elements</span></span>  
  
|<span data-ttu-id="24cee-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="24cee-134">Element</span></span>|<span data-ttu-id="24cee-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24cee-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24cee-136">comContracts</span><span class="sxs-lookup"><span data-stu-id="24cee-136">comContracts</span></span>|<span data-ttu-id="24cee-137">`comContract` Öğe koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="24cee-137">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24cee-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24cee-138">Remarks</span></span>  
 <span data-ttu-id="24cee-139">COM+ tümleştirme hizmeti sözleşmeleri Şu anda `http://tempuri.org` ad alanıyla kısıtlıdır ve anlaşma adı destekleyici com arabiriminden türetilir.</span><span class="sxs-lookup"><span data-stu-id="24cee-139">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="24cee-140">Ancak, öğesini ve yapılandırma dosyasındaki `comContracts` `comContract` öğesini kullanarak alternatifleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24cee-140">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="24cee-141">Örneğin, eklenecek ad alanı, sözleşme adı ve Kullanıcı tanımlı türleri, ayrıca bir hizmet sözleşmesinin diğer ayarlarını belirtmek için aşağıdaki yapılandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24cee-141">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="24cee-142">Hizmet başlatıldığında, belirtilen ad alanları ve sözleşme adları oluşturulan hizmet açıklamalarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="24cee-142">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24cee-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24cee-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="24cee-144">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="24cee-144">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="24cee-145">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="24cee-145">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="24cee-146">Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="24cee-146">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

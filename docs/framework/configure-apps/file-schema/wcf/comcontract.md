---
title: '&lt;comContract&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fa70ba3cf8e66411812b84821e80772c9930f7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcomcontractgt"></a><span data-ttu-id="b0a45-102">&lt;comContract&gt;</span><span class="sxs-lookup"><span data-stu-id="b0a45-102">&lt;comContract&gt;</span></span>
<span data-ttu-id="b0a45-103">COM + tümleştirme hizmet sözleşmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0a45-103">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="b0a45-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b0a45-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b0a45-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="b0a45-105">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a45-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0a45-106">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0a45-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0a45-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b0a45-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0a45-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0a45-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0a45-109">Attributes</span></span>  
  
|<span data-ttu-id="b0a45-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0a45-110">Attribute</span></span>|<span data-ttu-id="b0a45-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0a45-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0a45-112">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="b0a45-112">contract</span></span>|<span data-ttu-id="b0a45-113">Sözleşme türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="b0a45-113">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="b0a45-114">name</span><span class="sxs-lookup"><span data-stu-id="b0a45-114">name</span></span>|<span data-ttu-id="b0a45-115">Sözleşme adı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="b0a45-115">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="b0a45-116">ad alanı</span><span class="sxs-lookup"><span data-stu-id="b0a45-116">namespace</span></span>|<span data-ttu-id="b0a45-117">Sözleşme ad alanı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="b0a45-117">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="b0a45-118">requiresSession</span><span class="sxs-lookup"><span data-stu-id="b0a45-118">requiresSession</span></span>|<span data-ttu-id="b0a45-119">Sözleşme süre sonuyla bağlantılarına yalnızca kullanılabilir olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b0a45-119">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="b0a45-120">Hizmet başlatıldığında tümleştirmesi çalışma zamanı bu ayar kullanılacak bağlama türü ile tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0a45-120">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="b0a45-121">Bir özel durum oluşturulur veya daha fazla sözleşme bağlama çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="b0a45-121">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="b0a45-122">Bu özellik ise `false`, tek yönlü bir kanal kullanımda ve herhangi bir [out] parametreleri, bir özel durum da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b0a45-122">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0a45-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0a45-123">Child Elements</span></span>  
  
|<span data-ttu-id="b0a45-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0a45-124">Element</span></span>|<span data-ttu-id="b0a45-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0a45-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0a45-126">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="b0a45-126">persistableTypes</span></span>|<span data-ttu-id="b0a45-127">Tüm kalıcı türleri.</span><span class="sxs-lookup"><span data-stu-id="b0a45-127">All the persistable types.</span></span>|  
|<span data-ttu-id="b0a45-128">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="b0a45-128">userDefinedTypes</span></span>|<span data-ttu-id="b0a45-129">Bir koleksiyon, kullanıcı tanımlı türler (hizmet sözleşmesinde dahil edilecek olan UDT).</span><span class="sxs-lookup"><span data-stu-id="b0a45-129">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="b0a45-130">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="b0a45-130">exposedMethods</span></span>|<span data-ttu-id="b0a45-131">Bir Web hizmeti olarak bir COM bileşeni arabirimde kullanıma sunulduğunda gösterilen COM + yöntemleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="b0a45-131">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0a45-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0a45-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b0a45-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0a45-133">Element</span></span>|<span data-ttu-id="b0a45-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0a45-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0a45-135">comContracts</span><span class="sxs-lookup"><span data-stu-id="b0a45-135">comContracts</span></span>|<span data-ttu-id="b0a45-136">Bir koleksiyonu içerir `comContract` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b0a45-136">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0a45-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0a45-137">Remarks</span></span>  
 <span data-ttu-id="b0a45-138">COM + tümleştirme Hizmet sözleşmeleri "http://tempuri.org" ad alanına şu anda kısıtlı ve sözleşme adı destek COM arabiriminden türetilir.</span><span class="sxs-lookup"><span data-stu-id="b0a45-138">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="b0a45-139">Bununla birlikte, alternatifleri kullanarak belirleyebilirsiniz `comContracts` bölümünde yanı sıra `comContract` yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="b0a45-139">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="b0a45-140">Örneğin, bir hizmet sözleşmesini için ad alanı, sözleşme adı ve dahil edilecek kullanıcı tanımlı türler belirtmek için aşağıdaki yapılandırma gibi diğer ayarları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0a45-140">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
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
  
 <span data-ttu-id="b0a45-141">Hizmet başlatıldığında belirtilen ad alanları ve sözleşmesi adları için oluşturulan hizmet açıklamaları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b0a45-141">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a45-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0a45-142">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="b0a45-143">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="b0a45-143">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="b0a45-144">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="b0a45-144">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="b0a45-145">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b0a45-145">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

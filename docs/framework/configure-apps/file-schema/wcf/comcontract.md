---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: ef980c86efad4fda86cf62148e50688fd22afe49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926100"
---
# <a name="comcontract"></a><span data-ttu-id="ec22a-101">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="ec22a-101">\<comContract></span></span>
<span data-ttu-id="ec22a-102">Bir COM+ tümleştirme hizmeti sözleşmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec22a-102">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="ec22a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ec22a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ec22a-104">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="ec22a-104">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec22a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec22a-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec22a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec22a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ec22a-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec22a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec22a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ec22a-108">Attributes</span></span>  
  
|<span data-ttu-id="ec22a-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ec22a-109">Attribute</span></span>|<span data-ttu-id="ec22a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec22a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec22a-111">Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="ec22a-111">contract</span></span>|<span data-ttu-id="ec22a-112">Sözleşme türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ec22a-112">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="ec22a-113">name</span><span class="sxs-lookup"><span data-stu-id="ec22a-113">name</span></span>|<span data-ttu-id="ec22a-114">Sözleşme adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ec22a-114">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="ec22a-115">ad alanı</span><span class="sxs-lookup"><span data-stu-id="ec22a-115">namespace</span></span>|<span data-ttu-id="ec22a-116">Sözleşme ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ec22a-116">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="ec22a-117">requiresSession</span><span class="sxs-lookup"><span data-stu-id="ec22a-117">requiresSession</span></span>|<span data-ttu-id="ec22a-118">Sözleşmenin yalnızca oturumsuz bağlamalarda kullanılıp kullanılamayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="ec22a-118">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="ec22a-119">Hizmet başlatıldığında, tümleştirme çalışma zamanı bu ayarın kullanılacak bağlama türüyle tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec22a-119">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="ec22a-120">Sözleşme için bir veya daha fazla bağlama çakışırsa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ec22a-120">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="ec22a-121">Bu özellik ise `false`ve tek yönlü bir kanal kullanımda ise ve herhangi bir [out] parametresi varsa, bir özel durum da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ec22a-121">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec22a-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec22a-122">Child Elements</span></span>  
  
|<span data-ttu-id="ec22a-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="ec22a-123">Element</span></span>|<span data-ttu-id="ec22a-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec22a-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec22a-125">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="ec22a-125">persistableTypes</span></span>|<span data-ttu-id="ec22a-126">Tüm kalıcı türleri.</span><span class="sxs-lookup"><span data-stu-id="ec22a-126">All the persistable types.</span></span>|  
|<span data-ttu-id="ec22a-127">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="ec22a-127">userDefinedTypes</span></span>|<span data-ttu-id="ec22a-128">Hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı türler (UDT) koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ec22a-128">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="ec22a-129">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="ec22a-129">exposedMethods</span></span>|<span data-ttu-id="ec22a-130">Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemlerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ec22a-130">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec22a-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec22a-131">Parent Elements</span></span>  
  
|<span data-ttu-id="ec22a-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="ec22a-132">Element</span></span>|<span data-ttu-id="ec22a-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec22a-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec22a-134">comContracts</span><span class="sxs-lookup"><span data-stu-id="ec22a-134">comContracts</span></span>|<span data-ttu-id="ec22a-135">`comContract` Öğe koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ec22a-135">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec22a-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec22a-136">Remarks</span></span>  
 <span data-ttu-id="ec22a-137">COM+ tümleştirme hizmeti sözleşmeleri Şu anda `http://tempuri.org` ad alanıyla kısıtlıdır ve anlaşma adı destekleyici com arabiriminden türetilir.</span><span class="sxs-lookup"><span data-stu-id="ec22a-137">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="ec22a-138">Ancak, öğesini ve yapılandırma dosyasındaki `comContracts` `comContract` öğesini kullanarak alternatifleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec22a-138">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="ec22a-139">Örneğin, eklenecek ad alanı, sözleşme adı ve Kullanıcı tanımlı türleri, ayrıca bir hizmet sözleşmesinin diğer ayarlarını belirtmek için aşağıdaki yapılandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec22a-139">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="ec22a-140">Hizmet başlatıldığında, belirtilen ad alanları ve sözleşme adları oluşturulan hizmet açıklamalarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ec22a-140">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec22a-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec22a-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="ec22a-142">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="ec22a-142">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="ec22a-143">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="ec22a-143">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="ec22a-144">Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ec22a-144">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

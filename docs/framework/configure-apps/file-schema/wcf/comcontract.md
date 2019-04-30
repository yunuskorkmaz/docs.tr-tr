---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 8694f83a731363f83cb09de43214eb4b211ef5ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704290"
---
# <a name="comcontract"></a><span data-ttu-id="5454d-101">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="5454d-101">\<comContract></span></span>
<span data-ttu-id="5454d-102">Bir COM + tümleştirme hizmet sözleşmesi belirler.</span><span class="sxs-lookup"><span data-stu-id="5454d-102">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="5454d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5454d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5454d-104">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="5454d-104">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5454d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5454d-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5454d-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5454d-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5454d-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5454d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5454d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5454d-108">Attributes</span></span>  
  
|<span data-ttu-id="5454d-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5454d-109">Attribute</span></span>|<span data-ttu-id="5454d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5454d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5454d-111">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="5454d-111">contract</span></span>|<span data-ttu-id="5454d-112">Sözleşme türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5454d-112">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="5454d-113">name</span><span class="sxs-lookup"><span data-stu-id="5454d-113">name</span></span>|<span data-ttu-id="5454d-114">Sözleşme adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5454d-114">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="5454d-115">ad alanı</span><span class="sxs-lookup"><span data-stu-id="5454d-115">namespace</span></span>|<span data-ttu-id="5454d-116">Sözleşme ad uzayını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5454d-116">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="5454d-117">requiresSession</span><span class="sxs-lookup"><span data-stu-id="5454d-117">requiresSession</span></span>|<span data-ttu-id="5454d-118">Sözleşmenin sadece oturumdaki bağlamalarda kulanılıp kullanılıp kullanılamayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5454d-118">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="5454d-119">Hizmet başlatıldığında, tümleştirme çalışma zamanı bu ayar kullanılacak bağlama türünü ile tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5454d-119">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="5454d-120">Bir özel durum oluşturulur veya daha fazla bağlama sözleşmesinin çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="5454d-120">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="5454d-121">Bu özellik ise `false`, tek yönlü bir kanal kullanılır ve herhangi bir [out] parametreleri, bir özel durum da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5454d-121">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5454d-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5454d-122">Child Elements</span></span>  
  
|<span data-ttu-id="5454d-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="5454d-123">Element</span></span>|<span data-ttu-id="5454d-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5454d-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5454d-125">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="5454d-125">persistableTypes</span></span>|<span data-ttu-id="5454d-126">Tüm kalıcı türleri.</span><span class="sxs-lookup"><span data-stu-id="5454d-126">All the persistable types.</span></span>|  
|<span data-ttu-id="5454d-127">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="5454d-127">userDefinedTypes</span></span>|<span data-ttu-id="5454d-128">Bir koleksiyon, kullanıcı tanımlı türleri (hizmet sözleşmesi içerisinde dahil edilecek olan UDT).</span><span class="sxs-lookup"><span data-stu-id="5454d-128">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="5454d-129">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="5454d-129">exposedMethods</span></span>|<span data-ttu-id="5454d-130">Bir COM + bileşeni üzerinde arabirim bir Web hizmeti olarak sunulduğunda, sunulan COM + yöntemleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="5454d-130">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5454d-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5454d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="5454d-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="5454d-132">Element</span></span>|<span data-ttu-id="5454d-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5454d-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5454d-134">comContracts</span><span class="sxs-lookup"><span data-stu-id="5454d-134">comContracts</span></span>|<span data-ttu-id="5454d-135">Bir koleksiyonunu içeren `comContract` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="5454d-135">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5454d-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5454d-136">Remarks</span></span>  
 <span data-ttu-id="5454d-137">COM + tümleştirme Hizmet sözleşmeleri için kısıtlı `http://tempuri.org` ad alanını ve sözleşme adı destekleyici bir COM arabiriminden elde edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5454d-137">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="5454d-138">Ancak, alternatif kullanarak belirtebilirsiniz `comContracts` bölümünde yanı sıra `comContract` öğesi yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="5454d-138">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="5454d-139">Örneğin, ad alanı, sözleşme adı ve kullanıcı tanımlı türler dahil edilecek belirtmek için aşağıdaki yapılandırma yanı sıra diğer ayarlar için bir hizmet sözleşmesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5454d-139">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="5454d-140">Hizmet başlatıldığında sözleşmesi adları ve belirtilen ad alanları için oluşturulan hizmet açıklamaları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5454d-140">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5454d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5454d-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="5454d-142">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="5454d-142">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="5454d-143">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="5454d-143">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="5454d-144">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5454d-144">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

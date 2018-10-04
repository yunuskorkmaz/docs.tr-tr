---
title: '&lt;comContract&gt;'
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: e2addbada7f55076ae919d93c897991a7ec0fcd8
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779211"
---
# <a name="ltcomcontractgt"></a><span data-ttu-id="312fd-102">&lt;comContract&gt;</span><span class="sxs-lookup"><span data-stu-id="312fd-102">&lt;comContract&gt;</span></span>
<span data-ttu-id="312fd-103">Bir COM + tümleştirme hizmet sözleşmesi belirler.</span><span class="sxs-lookup"><span data-stu-id="312fd-103">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="312fd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="312fd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="312fd-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="312fd-105">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="312fd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="312fd-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="312fd-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="312fd-107">Attributes and Elements</span></span>  
 <span data-ttu-id="312fd-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="312fd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="312fd-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="312fd-109">Attributes</span></span>  
  
|<span data-ttu-id="312fd-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="312fd-110">Attribute</span></span>|<span data-ttu-id="312fd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="312fd-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="312fd-112">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="312fd-112">contract</span></span>|<span data-ttu-id="312fd-113">Sözleşme türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="312fd-113">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="312fd-114">name</span><span class="sxs-lookup"><span data-stu-id="312fd-114">name</span></span>|<span data-ttu-id="312fd-115">Sözleşme adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="312fd-115">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="312fd-116">ad alanı</span><span class="sxs-lookup"><span data-stu-id="312fd-116">namespace</span></span>|<span data-ttu-id="312fd-117">Sözleşme ad uzayını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="312fd-117">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="312fd-118">requiresSession</span><span class="sxs-lookup"><span data-stu-id="312fd-118">requiresSession</span></span>|<span data-ttu-id="312fd-119">Sözleşmenin sadece oturumdaki bağlamalarda kulanılıp kullanılıp kullanılamayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="312fd-119">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="312fd-120">Hizmet başlatıldığında, tümleştirme çalışma zamanı bu ayar kullanılacak bağlama türünü ile tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="312fd-120">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="312fd-121">Bir özel durum oluşturulur veya daha fazla bağlama sözleşmesinin çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="312fd-121">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="312fd-122">Bu özellik ise `false`, tek yönlü bir kanal kullanılır ve herhangi bir [out] parametreleri, bir özel durum da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="312fd-122">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="312fd-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="312fd-123">Child Elements</span></span>  
  
|<span data-ttu-id="312fd-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="312fd-124">Element</span></span>|<span data-ttu-id="312fd-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="312fd-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="312fd-126">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="312fd-126">persistableTypes</span></span>|<span data-ttu-id="312fd-127">Tüm kalıcı türleri.</span><span class="sxs-lookup"><span data-stu-id="312fd-127">All the persistable types.</span></span>|  
|<span data-ttu-id="312fd-128">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="312fd-128">userDefinedTypes</span></span>|<span data-ttu-id="312fd-129">Bir koleksiyon, kullanıcı tanımlı türleri (hizmet sözleşmesi içerisinde dahil edilecek olan UDT).</span><span class="sxs-lookup"><span data-stu-id="312fd-129">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="312fd-130">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="312fd-130">exposedMethods</span></span>|<span data-ttu-id="312fd-131">Bir COM + bileşeni üzerinde arabirim bir Web hizmeti olarak sunulduğunda, sunulan COM + yöntemleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="312fd-131">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="312fd-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="312fd-132">Parent Elements</span></span>  
  
|<span data-ttu-id="312fd-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="312fd-133">Element</span></span>|<span data-ttu-id="312fd-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="312fd-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="312fd-135">comContracts</span><span class="sxs-lookup"><span data-stu-id="312fd-135">comContracts</span></span>|<span data-ttu-id="312fd-136">Bir koleksiyonunu içeren `comContract` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="312fd-136">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="312fd-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="312fd-137">Remarks</span></span>  
 <span data-ttu-id="312fd-138">COM + tümleştirme Hizmet sözleşmeleri için kısıtlı `http://tempuri.org` ad alanını ve sözleşme adı destekleyici bir COM arabiriminden elde edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="312fd-138">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="312fd-139">Ancak, alternatif kullanarak belirtebilirsiniz `comContracts` bölümünde yanı sıra `comContract` öğesi yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="312fd-139">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="312fd-140">Örneğin, ad alanı, sözleşme adı ve kullanıcı tanımlı türler dahil edilecek belirtmek için aşağıdaki yapılandırma yanı sıra diğer ayarlar için bir hizmet sözleşmesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="312fd-140">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="312fd-141">Hizmet başlatıldığında sözleşmesi adları ve belirtilen ad alanları için oluşturulan hizmet açıklamaları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="312fd-141">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="312fd-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="312fd-142">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="312fd-143">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="312fd-143">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="312fd-144">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="312fd-144">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="312fd-145">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="312fd-145">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

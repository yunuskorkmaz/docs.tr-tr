---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 297a28181de8ce6ed658afad950f25cced9f9cb7
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46579725"
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="f2ed3-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="f2ed3-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="f2ed3-103">`comContracts` Yapılandırma bölümü bir COM + tümleştirme hizmet sözleşmesinin çeşitli özelliklerini belirtmenize olanak veren öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="f2ed3-104">Namespace ve sözleşme belirtme</span><span class="sxs-lookup"><span data-stu-id="f2ed3-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="f2ed3-105">COM + tümleştirme Hizmet sözleşmeleri için kısıtlı `http://tempuri.org` ad alanını ve sözleşme adı destekleyici bir COM arabiriminden elde edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-105">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="f2ed3-106">Ancak, alternatif kullanarak belirtebilirsiniz `comContracts` yapılandırma dosyasının bir bölümünde.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="f2ed3-107">Örneğin, isteğe bağlı oturumdaki bağlamalarda kulanılıp kullanımı zorlamak için yanı sıra, hizmet sözleşmesi ad alanı ve sözleşme adını belirtmek için şu yapılandırmayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="f2ed3-108">Hizmet başlatıldığında sözleşmesi adları ve belirtilen ad alanları için oluşturulan hizmet açıklamaları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="f2ed3-109">Bu bölümde boş olduğunda, hizmet başlatma destekleyen COM arabirimi kodundan alınan bir varsayılan ad alanı ve sözleşme adı geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="f2ed3-110">Ayrıca, kullanabileceğiniz [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) bir COM + bileşeni üzerinde arabirim bir Web hizmeti olarak sunulduğunda, sunulan COM + yöntemlerini belirtmek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="f2ed3-111">Ayrıca [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) tümleştirmesi kullanılan kalıcı türlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="f2ed3-112">Son olarak, kullanabileceğiniz [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) kullanıcı tanımlı türleri (hizmet sözleşmesi içerisinde dahil edilecek olan UDT) içerecek şekilde öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ed3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2ed3-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="f2ed3-114">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="f2ed3-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="f2ed3-115">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="f2ed3-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="f2ed3-116">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="f2ed3-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="f2ed3-117">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="f2ed3-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="f2ed3-118">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="f2ed3-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="f2ed3-119">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f2ed3-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

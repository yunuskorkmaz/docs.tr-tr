---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 47a7d862cf85254f88373d582169ff421be2b5b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673296"
---
# <a name="comcontracts"></a><span data-ttu-id="c6262-101">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="c6262-101">\<comContracts></span></span>
<span data-ttu-id="c6262-102">`comContracts` Yapılandırma bölümü bir COM + tümleştirme hizmet sözleşmesinin çeşitli özelliklerini belirtmenize olanak veren öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c6262-102">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="c6262-103">Namespace ve sözleşme belirtme</span><span class="sxs-lookup"><span data-stu-id="c6262-103">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="c6262-104">COM + tümleştirme Hizmet sözleşmeleri için kısıtlı `http://tempuri.org` ad alanını ve sözleşme adı destekleyici bir COM arabiriminden elde edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c6262-104">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="c6262-105">Ancak, alternatif kullanarak belirtebilirsiniz `comContracts` yapılandırma dosyasının bir bölümünde.</span><span class="sxs-lookup"><span data-stu-id="c6262-105">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="c6262-106">Örneğin, isteğe bağlı oturumdaki bağlamalarda kulanılıp kullanımı zorlamak için yanı sıra, hizmet sözleşmesi ad alanı ve sözleşme adını belirtmek için şu yapılandırmayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6262-106">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="c6262-107">Hizmet başlatıldığında sözleşmesi adları ve belirtilen ad alanları için oluşturulan hizmet açıklamaları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c6262-107">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="c6262-108">Bu bölümde boş olduğunda, hizmet başlatma destekleyen COM arabirimi kodundan alınan bir varsayılan ad alanı ve sözleşme adı geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c6262-108">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="c6262-109">Ayrıca, kullanabileceğiniz [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) bir COM + bileşeni üzerinde arabirim bir Web hizmeti olarak sunulduğunda, sunulan COM + yöntemlerini belirtmek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="c6262-109">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="c6262-110">Ayrıca [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) tümleştirmesi kullanılan kalıcı türlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="c6262-110">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="c6262-111">Son olarak, kullanabileceğiniz [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) kullanıcı tanımlı türleri (hizmet sözleşmesi içerisinde dahil edilecek olan UDT) içerecek şekilde öğesi.</span><span class="sxs-lookup"><span data-stu-id="c6262-111">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6262-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6262-112">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="c6262-113">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="c6262-113">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)
- [<span data-ttu-id="c6262-114">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="c6262-114">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)
- [<span data-ttu-id="c6262-115">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="c6262-115">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)
- [<span data-ttu-id="c6262-116">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="c6262-116">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)
- [<span data-ttu-id="c6262-117">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="c6262-117">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="c6262-118">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c6262-118">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

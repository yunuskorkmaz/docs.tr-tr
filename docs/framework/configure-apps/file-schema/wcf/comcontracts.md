---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: b44c09e7e32129ba21834f7fbb8dc4699904e46b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746416"
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="6b18d-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="6b18d-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="6b18d-103">`comContracts` Yapılandırma bölümü bir COM + tümleştirme hizmet sözleşmesini çeşitli özelliklerini belirtmenize olanak veren öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6b18d-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="6b18d-104">Namespace ve sözleşme belirtme</span><span class="sxs-lookup"><span data-stu-id="6b18d-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="6b18d-105">COM + tümleştirme Hizmet sözleşmeleri için şu anda kısıtlı "http://tempuri.org" ad alanı, ve sözleşme adı destek COM arabiriminden elde edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6b18d-105">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="6b18d-106">Bununla birlikte, alternatifleri kullanarak belirleyebilirsiniz `comContracts` yapılandırma dosyasındaki bölüm.</span><span class="sxs-lookup"><span data-stu-id="6b18d-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="6b18d-107">Örneğin, aşağıdaki yapılandırma süre sonuyla bağlamaları kullanımı zorlamak için bir seçenek yanı sıra, hizmet sözleşmesi ad alanı ve sözleşme adını belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b18d-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
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
  
 <span data-ttu-id="6b18d-108">Hizmet başlatıldığında belirtilen ad alanları ve sözleşmesi adları için oluşturulan hizmet açıklamaları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6b18d-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="6b18d-109">Bu bölüm boş olduğunda, hizmet başlatma destekleyen COM arabirimi kodundan alınır varsayılan ad alanı ve sözleşme adı geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6b18d-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="6b18d-110">Ayrıca, [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğesi bir COM bileşeni arabirimde bir Web hizmeti olarak kullanıma sunulduğunda gösterilen COM + yöntemleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="6b18d-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="6b18d-111">Aynı zamanda [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) tümleştirme sırasında kullanılan kalıcı türlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6b18d-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="6b18d-112">Son olarak, kullanabileceğiniz [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) kullanıcı tanımlı türler (hizmet sözleşmesinde eklenecek olan UDT) eklenecek öğe.</span><span class="sxs-lookup"><span data-stu-id="6b18d-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b18d-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b18d-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="6b18d-114">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="6b18d-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="6b18d-115">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="6b18d-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="6b18d-116">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="6b18d-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="6b18d-117">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="6b18d-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="6b18d-118">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="6b18d-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="6b18d-119">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6b18d-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

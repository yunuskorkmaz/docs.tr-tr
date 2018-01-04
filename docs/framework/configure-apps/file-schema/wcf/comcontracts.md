---
title: '&lt;comContracts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69fbce3f312833c374a4c2615a15359d9c2db3a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="755d1-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="755d1-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="755d1-103">`comContracts` Yapılandırma bölümü bir COM + tümleştirme hizmet sözleşmesini çeşitli özelliklerini belirtmenize olanak veren öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="755d1-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="755d1-104">Namespace ve sözleşme belirtme</span><span class="sxs-lookup"><span data-stu-id="755d1-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="755d1-105">COM + tümleştirme Hizmet sözleşmeleri "http://tempuri.org" ad alanına şu anda kısıtlı ve sözleşme adı destek COM arabiriminden türetilir.</span><span class="sxs-lookup"><span data-stu-id="755d1-105">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="755d1-106">Bununla birlikte, alternatifleri kullanarak belirleyebilirsiniz `comContracts` yapılandırma dosyasındaki bölüm.</span><span class="sxs-lookup"><span data-stu-id="755d1-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="755d1-107">Örneğin, aşağıdaki yapılandırma süre sonuyla bağlamaları kullanımı zorlamak için bir seçenek yanı sıra, hizmet sözleşmesi ad alanı ve sözleşme adını belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="755d1-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
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
  
 <span data-ttu-id="755d1-108">Hizmet başlatıldığında belirtilen ad alanları ve sözleşmesi adları için oluşturulan hizmet açıklamaları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="755d1-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="755d1-109">Bu bölüm boş olduğunda, hizmet başlatma destekleyen COM arabirimi kodundan alınır varsayılan ad alanı ve sözleşme adı geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="755d1-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="755d1-110">Ayrıca, [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) öğesi bir COM bileşeni arabirimde bir Web hizmeti olarak kullanıma sunulduğunda gösterilen COM + yöntemleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="755d1-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="755d1-111">Aynı zamanda [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) tümleştirme sırasında kullanılan kalıcı türlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="755d1-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="755d1-112">Son olarak, kullanabileceğiniz [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) kullanıcı tanımlı türler (hizmet sözleşmesinde eklenecek olan UDT) eklenecek öğe.</span><span class="sxs-lookup"><span data-stu-id="755d1-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755d1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="755d1-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="755d1-114">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="755d1-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="755d1-115">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="755d1-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="755d1-116">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="755d1-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="755d1-117">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="755d1-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="755d1-118">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="755d1-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="755d1-119">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="755d1-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

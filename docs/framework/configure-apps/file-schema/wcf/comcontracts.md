---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919484"
---
# <a name="comcontracts"></a><span data-ttu-id="82a1e-101">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="82a1e-101">\<comContracts></span></span>
<span data-ttu-id="82a1e-102">Yapılandırma `comContracts` bölümü, bir com+ tümleştirme hizmeti sözleşmesinin çeşitli özelliklerini belirtmenizi sağlayan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="82a1e-102">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="82a1e-103">Ad alanı ve sözleşme belirtme</span><span class="sxs-lookup"><span data-stu-id="82a1e-103">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="82a1e-104">COM+ tümleştirme hizmeti sözleşmeleri Şu anda `http://tempuri.org` ad alanıyla kısıtlıdır ve anlaşma adı destekleyici com arabiriminden türetilir.</span><span class="sxs-lookup"><span data-stu-id="82a1e-104">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="82a1e-105">Ancak, yapılandırma dosyasının `comContracts` bölümünü kullanarak alternatifler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a1e-105">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="82a1e-106">Örneğin, hizmet sözleşmesinin ad alanını ve sözleşme adını ve oturum açma bağlamalarında kullanımı zorlama seçeneğini belirtmek için aşağıdaki yapılandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a1e-106">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="82a1e-107">Hizmet başlatıldığında, belirtilen ad alanları ve sözleşme adları oluşturulan hizmet açıklamalarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="82a1e-107">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="82a1e-108">Bu bölüm boş olduğunda, hizmet başlatma, destekleyici COM arabirim KIMLIĞINDEN alınan bir varsayılan ad alanı ve sözleşme adı uygular.</span><span class="sxs-lookup"><span data-stu-id="82a1e-108">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="82a1e-109">Ayrıca, bir com+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda sunulan com+ yöntemlerini belirtmek için [ \<ExposedMethod >](exposedmethod.md) öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a1e-109">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="82a1e-110">Ayrıca, [ \<](persistabletypes.md) tümleştirmede kullanılan kalıcı tablo türlerini belirtmek için > PersistableTypes da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a1e-110">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="82a1e-111">Son olarak, [ \<UserDefinedType >](userdefinedtype.md) öğesini hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı türler (udt) dahil etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a1e-111">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82a1e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82a1e-112">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="82a1e-113">\<exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="82a1e-113">\<exposedMethod></span></span>](exposedmethod.md)
- [<span data-ttu-id="82a1e-114">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="82a1e-114">\<persistableTypes></span></span>](persistabletypes.md)
- [<span data-ttu-id="82a1e-115">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="82a1e-115">\<userDefinedType></span></span>](userdefinedtype.md)
- [<span data-ttu-id="82a1e-116">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="82a1e-116">\<comContract></span></span>](comcontract.md)
- [<span data-ttu-id="82a1e-117">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="82a1e-117">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="82a1e-118">Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="82a1e-118">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

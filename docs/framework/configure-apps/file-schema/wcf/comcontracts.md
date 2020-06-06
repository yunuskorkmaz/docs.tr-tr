---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69919484"
---
# \<comContracts>
<span data-ttu-id="a74bd-101">`comContracts`Yapılandırma bölümü, BIR COM+ tümleştirme hizmeti sözleşmesinin çeşitli özelliklerini belirtmenizi sağlayan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a74bd-101">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="a74bd-102">Ad alanı ve sözleşme belirtme</span><span class="sxs-lookup"><span data-stu-id="a74bd-102">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="a74bd-103">COM+ tümleştirme hizmeti sözleşmeleri Şu anda `http://tempuri.org` ad alanıyla kısıtlıdır ve anlaşma adı DESTEKLEYICI com arabiriminden türetilir.</span><span class="sxs-lookup"><span data-stu-id="a74bd-103">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="a74bd-104">Ancak, `comContracts` yapılandırma dosyasının bölümünü kullanarak alternatifler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a74bd-104">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="a74bd-105">Örneğin, hizmet sözleşmesinin ad alanını ve sözleşme adını ve oturum açma bağlamalarında kullanımı zorlama seçeneğini belirtmek için aşağıdaki yapılandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a74bd-105">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="a74bd-106">Hizmet başlatıldığında, belirtilen ad alanları ve sözleşme adları oluşturulan hizmet açıklamalarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a74bd-106">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="a74bd-107">Bu bölüm boş olduğunda, hizmet başlatma, destekleyici COM arabirim KIMLIĞINDEN alınan bir varsayılan ad alanı ve sözleşme adı uygular.</span><span class="sxs-lookup"><span data-stu-id="a74bd-107">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="a74bd-108">Ayrıca, [\<exposedMethod>](exposedmethod.md) BIR COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya ÇıKARıLAN com+ yöntemlerini belirtmek için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a74bd-108">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="a74bd-109">Ayrıca, [\<persistableTypes>](persistabletypes.md) tümleştirmede kullanılan kalıcı tablo türlerini belirtmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a74bd-109">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="a74bd-110">Son olarak, [\<userDefinedType>](userdefinedtype.md) öğesini hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı türler (udt) dahil etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a74bd-110">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74bd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a74bd-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [<span data-ttu-id="a74bd-112">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="a74bd-112">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a74bd-113">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a74bd-113">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

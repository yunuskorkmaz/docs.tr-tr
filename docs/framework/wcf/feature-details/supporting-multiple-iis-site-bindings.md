---
title: Birden Fazla IIS Site Bağlamasını Destekleme
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: a1fc2de3a10641dfc1c6181c7258bd4160f900e2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988646"
---
# <a name="supporting-multiple-iis-site-bindings"></a>Birden Fazla IIS Site Bağlamasını Destekleme
Internet Information Services (IIS) 7,0 altında bir Windows Communication Foundation (WCF) hizmeti barındırdığında aynı sitede aynı protokolü kullanan birden fazla temel adres sağlamak isteyebilirsiniz. Bu, aynı hizmetin bir dizi farklı URI 'ye yanıt vermesini sağlar. Bu, ve `http://www.contoso.com` `http://contoso.com`üzerinde dinleme yapan bir hizmeti barındırmak istediğinizde yararlıdır. Ayrıca, iç kullanıcılar için temel adresi ve dış kullanıcılara ayrı bir temel adres olan bir hizmet oluşturmak da yararlıdır. Örneğin: `http://internal.contoso.com` ve `http://www.contoso.com`.  
  
> [!NOTE]
> Bu işlevsellik yalnızca HTTP protokolü kullanılarak kullanılabilir.  
  
## <a name="multiple-base-addresses"></a>Birden çok temel adres  
 Bu özellik yalnızca IIS altında barındırılan WCF Hizmetleri için kullanılabilir. Bu özellik varsayılan olarak etkin değildir. Bunu etkinleştirmek için, aşağıdaki örnekte gösterildiği `multipleSiteBindingsEnabled` gibi `true`, özniteliğini Web`serviceHostingEnvironment`. config dosyanızdaki < > öğesine eklemeniz ve olarak ayarlamanız gerekir.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 IIS altında bir WCF hizmeti barındırırken IIS, uygulamayı içeren sanal dizinin URI 'sini temel alan sizin için bir temel adres oluşturur. Web sitenize bir veya daha fazla bağlama eklemek için Internet Information Services Manager kullanarak aynı protokolü kullanan ek temel adresler ekleyebilirsiniz. Her bağlama için bir protokol (HTTP veya HTTPS), bir IP adresi, bağlantı noktası ve ana bilgisayar adı belirtin. Internet Information Services Manager 'ı kullanma hakkında daha fazla bilgi için bkz. [IIS Yöneticisi (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164057). Bir siteye bağlama ekleme hakkında daha fazla bilgi için bkz. [Web sitesi oluşturma (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Aynı site için birden çok temel adres belirtilmesi, WCF Yardım sayfasının içeriğini, şemayı içeri aktarmayı ve hizmet tarafından oluşturulan WSDL/MEX bilgilerini etkiler. WCF Yardım sayfasında, hizmetle iletişim kurabilen bir WCF istemcisi oluşturmak için kullanılacak komut satırı görüntülenir. Bu komut satırı, Web sitesi için IIS bağlamasında belirtilen ilk adresi içerir. Benzer şekilde, şemayı içeri aktarırken yalnızca IIS bağlamasında belirtilen ilk temel adres kullanılır. WSDL ve MEX verileri, IIS bağlamalarında belirtilen tüm temel adresleri içerir.  
  
> [!WARNING]
> Bu, bir hizmette iki temel adres varsa, biri dahili kullanıcılar ve diğeri harici kullanıcılar için, her ikisi de hizmet tarafından oluşturulan WSDL/MEX bilgilerinde belirtilir.

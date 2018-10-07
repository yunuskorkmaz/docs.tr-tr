---
title: Birden Fazla IIS Site Bağlamasını Destekleme
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 5a8b06d86b505452f9ded808f727343b1453e592
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840875"
---
# <a name="supporting-multiple-iis-site-bindings"></a>Birden Fazla IIS Site Bağlamasını Destekleme
Internet Information Services (IIS) 7.0 altında Windows Communication Foundation (WCF) hizmet barındırma, aynı sitede aynı protokolünü kullanan birden çok taban adresi sağlamak isteyebilirsiniz. Bu, farklı bir URI'leri bir sayıya yanıt vermek aynı hizmet sağlar. Dinlediği bir hizmeti barındırmak istediğiniz gerektiğinde bu faydalıdır `http://www.contoso.com` ve `http://contoso.com`. Temel adres iç kullanıcılar için ve dış kullanıcılar için ayrı bir temel adres olan bir hizmet oluşturmak kullanışlıdır. Örneğin: `http://internal.contoso.com` ve `http://www.contoso.com`.  
  
> [!NOTE]
>  Bu işlev, yalnızca HTTP protokolü kullanılarak erişilebilir.  
  
## <a name="multiple-base-addresses"></a>Birden çok taban adresi  
 Bu özellik, yalnızca IIS altında barındırılan WCF hizmetleri için kullanılabilir. Bu özellik varsayılan olarak etkin değildir. Bunu etkinleştirmek için eklemelisiniz `multipleSiteBindingsEnabled` özniteliğini <`serviceHostingEnvironment`>, Web.config öğesinde ayarlayın ve dosya `true`aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 IIS altında bir WCF Hizmeti barındırma, IIS bir temel adres için uygulamayı içeren sanal dizine URI temel alarak oluşturur. Web sitenize bir veya daha fazla bağlamalar eklemek Internet Information Services Manager'ı kullanarak aynı protokolünü kullanan ek temel adresler ekleyebilirsiniz. Her bağlama için bir protokol (HTTP veya HTTPS), bir IP adresi, bağlantı noktası ve bir ana bilgisayar adı belirtin. Internet Information Services Manager'ı kullanma hakkında daha fazla bilgi için bkz. [IIS Yöneticisi'ni (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164057). Bir siteye bağlama ekleme hakkında daha fazla bilgi için bkz. [(IIS 7) Web sitesi oluşturma](https://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Aynı site için birden çok taban adresini belirten şema ve hizmet tarafından oluşturulan WSDL/MEX bilgileri alma WCF Yardım sayfası içeriği etkiler. Hizmet ile iletişim kurabilen bir WCF istemcisi oluşturmak için kullanılacak komut satırını WCF Yardım sayfasını görüntüler. Bu komut satırı, yalnızca Web sitesi IIS bağlamasında belirtilen ilk adresini içerir. Benzer şekilde, şema, yalnızca IIS bağlamasında belirtilen ilk temel adresi alma kullanılır. WSDL ve MEX veri IIS bağlamaları belirtilen temel adresler bulunur.  
  
> [!WARNING]
>  Bu hizmet, iki temel adresi, bir iç kullanıcılar için ve dış kullanıcılar için bir tane varsa, her ikisi de hizmeti tarafından oluşturulan WSDL/MEX bilgileri belirtildiğinden emin anlamına gelir.

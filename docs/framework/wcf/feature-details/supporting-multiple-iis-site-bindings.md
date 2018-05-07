---
title: Birden Fazla IIS Site Bağlamasını Destekleme
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 9b92243bb7aaea5c8ecf708ce863e6979bc9f17c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="supporting-multiple-iis-site-bindings"></a>Birden Fazla IIS Site Bağlamasını Destekleme
Windows Communication Foundation (WCF) hizmetini Internet Information Services (IIS) 7.0 altında barındıran, aynı sitede aynı protokolünü kullanan birden çok taban adresi sağlamak isteyebilirsiniz. Aynı hizmetin farklı URI'ler sayıya yanıt verir. Üzerinde dinleyen bir hizmet barındırmak istediğiniz gerektiğinde bu faydalıdır http://www.contoso.com ve http://contoso.com. İç kullanıcılar için bir taban adresi ve dış kullanıcılar için ayrı bir taban adresi sahip bir hizmet oluşturmak kullanışlıdır. Örneğin: http://internal.contoso.com ve http://www.contoso.com.  
  
> [!NOTE]
>  Bu işlev, yalnızca HTTP protokolünü kullanarak kullanılabilir.  
  
## <a name="multiple-base-addresses"></a>Birden çok taban adresi  
 Bu özellik yalnızca IIS altında barındırılan WCF hizmetleri için kullanılabilir. Bu özellik varsayılan olarak etkin değildir. Etkinleştirmek için eklemelisiniz `multipleSiteBindingsEnabled` özniteliğini <`serviceHostingEnvironment`> Web.config öğesinde dosya ve ayarlamak `true`, aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 IIS altında bir WCF Hizmeti barındırma, IIS bir temel adres için uygulamayı içeren sanal dizin için URI temel alarak oluşturur. Web siteniz için bir veya daha fazla bağlamalar eklemek için Internet Information Services Yöneticisi kullanarak aynı protokolünü kullanan ek temel adres ekleyebilirsiniz. Her bağlama için bir protokol (HTTP veya HTTPS), bir IP adresi, bağlantı noktası ve bir ana bilgisayar adı belirtin. Internet Information Services Yöneticisi kullanma hakkında daha fazla bilgi için bkz: [IIS Yöneticisi'ni (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057). Bir siteye bağlama ekleme hakkında daha fazla bilgi için bkz: [(IIS 7) Web sitesi oluşturma](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Aynı site için birden çok taban adresi belirtme şema ve hizmeti tarafından oluşturulan WSDL/MEX bilgileri alma WCF Yardım sayfası içeriği etkiler. WCF Yardım sayfası hizmeti ile iletişim kurabilen bir WCF istemcisi oluşturmak için kullanılacak komut satırını görüntüler. Bu komut satırı yalnızca Web sitesi için IIS bağlama belirtilen ilk adresini içerir. Benzer şekilde şeması, yalnızca IIS bağlamada belirtilen ilk taban adresi alma kullanıldığında. WSDL ve MEX verileri IIS bağlamaları belirtilen temel adresler içerir.  
  
> [!WARNING]
>  Bu, iki temel adresi, bir iç kullanıcılar için ve biri dış kullanıcılar için bir hizmet varsa, her ikisi de hizmeti tarafından oluşturulan WSDL/MEX bilgilerinin belirtildiğinden emin anlamına gelir.

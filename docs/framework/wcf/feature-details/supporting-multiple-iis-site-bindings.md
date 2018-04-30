---
title: Birden Fazla IIS Site Bağlamasını Destekleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4b586b4d5c3c37355bf7b05a8a0227565a5b5e5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="supporting-multiple-iis-site-bindings"></a>Birden Fazla IIS Site Bağlamasını Destekleme
Barındırdığında bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti Internet Information Services (IIS altında) 7.0, aynı sitede aynı protokolünü kullanan birden çok taban adresi sağlamak isteyebilirsiniz. Aynı hizmetin farklı URI'ler sayıya yanıt verir. Üzerinde dinleyen bir hizmet barındırmak istediğiniz gerektiğinde bu faydalıdır http://www.contoso.com ve http://contoso.com. İç kullanıcılar için bir taban adresi ve dış kullanıcılar için ayrı bir taban adresi sahip bir hizmet oluşturmak kullanışlıdır. Örneğin: http://internal.contoso.com ve http://www.contoso.com.  
  
> [!NOTE]
>  Bu işlev, yalnızca HTTP protokolünü kullanarak kullanılabilir.  
  
## <a name="multiple-base-addresses"></a>Birden çok taban adresi  
 Bu özellik yalnızca kullanılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS altında barındırılan hizmetlerin. Bu özellik varsayılan olarak etkin değildir. Etkinleştirmek için eklemelisiniz `multipleSiteBindingsEnabled` özniteliğini <`serviceHostingEnvironment`> Web.config öğesinde dosya ve ayarlamak `true`, aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Barındırdığında bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti IIS, IIS altında uygulamayı içeren sanal dizin için URI dayalı için bir temel adres oluşturur. Web siteniz için bir veya daha fazla bağlamalar eklemek için Internet Information Services Yöneticisi kullanarak aynı protokolünü kullanan ek temel adres ekleyebilirsiniz. Her bağlama için bir protokol (HTTP veya HTTPS), bir IP adresi, bağlantı noktası ve bir ana bilgisayar adı belirtin. Internet Information Services Yöneticisi kullanma hakkında daha fazla bilgi için bkz: [IIS Yöneticisi'ni (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057). Bir siteye bağlama ekleme hakkında daha fazla bilgi için bkz: [(IIS 7) Web sitesi oluşturma](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Aynı sitede içeriği etkiler birden çok taban adresi belirtme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yardım sayfası, şema ve hizmeti tarafından oluşturulan WSDL/MEX bilgileri alınıyor. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yardım sayfasını görüntüler oluşturmak için kullanılacak komut satırını bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti ile iletişim kurabildiğini istemci. Bu komut satırı yalnızca Web sitesi için IIS bağlama belirtilen ilk adresini içerir. Benzer şekilde şeması, yalnızca IIS bağlamada belirtilen ilk taban adresi alma kullanıldığında. WSDL ve MEX verileri IIS bağlamaları belirtilen temel adresler içerir.  
  
> [!WARNING]
>  Bu, iki temel adresi, bir iç kullanıcılar için ve biri dış kullanıcılar için bir hizmet varsa, her ikisi de hizmeti tarafından oluşturulan WSDL/MEX bilgilerinin belirtildiğinden emin anlamına gelir.

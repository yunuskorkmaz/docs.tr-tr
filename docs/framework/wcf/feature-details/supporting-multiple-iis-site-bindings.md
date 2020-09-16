---
title: Birden Fazla IIS Site Bağlamasını Destekleme
description: IIS 'de bir WCF hizmeti barındırırken aynı sitede aynı protokolü kullanan birden fazla temel adres sağlamayı öğrenin.
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 6af4d885c7fc3d4dcc12ffb4bf6670f1a9b3d78c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546204"
---
# <a name="supporting-multiple-iis-site-bindings"></a>Birden Fazla IIS Site Bağlamasını Destekleme
Internet Information Services (IIS) 7,0 altında bir Windows Communication Foundation (WCF) hizmeti barındırdığında aynı sitede aynı protokolü kullanan birden fazla temel adres sağlamak isteyebilirsiniz. Bu, aynı hizmetin bir dizi farklı URI 'ye yanıt vermesini sağlar. Bu, ve üzerinde dinleme yapan bir hizmeti barındırmak istediğinizde yararlıdır `http://www.contoso.com` `http://contoso.com` . Ayrıca, iç kullanıcılar için temel adresi ve dış kullanıcılara ayrı bir temel adres olan bir hizmet oluşturmak da yararlıdır. Örneğin: `http://internal.contoso.com` ve `http://www.contoso.com`.  
  
> [!NOTE]
> Bu işlevsellik yalnızca HTTP protokolü kullanılarak kullanılabilir.  
  
## <a name="multiple-base-addresses"></a>Birden çok temel adres  
 Bu özellik yalnızca IIS altında barındırılan WCF Hizmetleri için kullanılabilir. Bu özellik varsayılan olarak etkin değildir. Bunu etkinleştirmek için, `multipleSiteBindingsEnabled` `serviceHostingEnvironment` `true` Aşağıdaki örnekte gösterildiği gibi, özniteliğini Web.config dosyanızdaki <> öğesine eklemeniz ve olarak ayarlamanız gerekir.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 IIS altında bir WCF hizmeti barındırırken IIS, uygulamayı içeren sanal dizinin URI 'sini temel alan sizin için bir temel adres oluşturur. Web sitenize bir veya daha fazla bağlama eklemek için Internet Information Services Manager kullanarak aynı protokolü kullanan ek temel adresler ekleyebilirsiniz. Her bağlama için bir protokol (HTTP veya HTTPS), bir IP adresi, bağlantı noktası ve ana bilgisayar adı belirtin. Internet Information Services Manager 'ı kullanma hakkında daha fazla bilgi için bkz. [IIS Yöneticisi (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753842(v=ws.10)). Bir siteye bağlama ekleme hakkında daha fazla bilgi için bkz. [Web sitesi oluşturma (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772350(v=ws.10))  
  
 Aynı site için birden çok temel adres belirtilmesi, WCF Yardım sayfasının içeriğini, şemayı içeri aktarmayı ve hizmet tarafından oluşturulan WSDL/MEX bilgilerini etkiler. WCF Yardım sayfasında, hizmetle iletişim kurabilen bir WCF istemcisi oluşturmak için kullanılacak komut satırı görüntülenir. Bu komut satırı, Web sitesi için IIS bağlamasında belirtilen ilk adresi içerir. Benzer şekilde, şemayı içeri aktarırken yalnızca IIS bağlamasında belirtilen ilk temel adres kullanılır. WSDL ve MEX verileri, IIS bağlamalarında belirtilen tüm temel adresleri içerir.  
  
> [!WARNING]
> Bu, bir hizmette iki temel adres varsa, biri dahili kullanıcılar ve diğeri harici kullanıcılar için, her ikisi de hizmet tarafından oluşturulan WSDL/MEX bilgilerinde belirtilir.

---
title: COM Uygulamaları ile Tümleştirme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 2be428f0ae83596a4398fc9830af40d05f6ab191
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638659"
---
# <a name="integrating-with-com-applications-overview"></a>COM Uygulamaları ile Tümleştirme Genel Bakış
Windows Communication Foundation (WCF), yönetilen kod geliştiriciye bağlantılı uygulamalar oluşturmaya yönelik zengin bir ortam sağlar. Yönetilmeyen COM tabanlı kodunda önemli bir yatırımınız varsa ve geçirmek istiyor musunuz, ancak hala WCF Web Hizmetleri doğrudan mevcut kodunuza WCF hizmet bilinen adını kullanarak tümleştirebilirsiniz. Hizmet bilinen adı, Office VBA, Visual Basic 6.0 veya Visual C++ 6.0 gibi bir geniş aralığı, COM tabanlı geliştirme ortamlarından kullanılabilir.  
  
> [!NOTE]
>  Hizmet bilinen adı WCF iletişim kanalı tüm iletişimi için kullanır. Bu kanal için güvenlik ve kimlik mekanizmaları, kullanılan standart COM ve DCOM Proxy farklıdır. Ayrıca, hizmet adının varsayılan zaman aşımı süresi bir WCF iletişim kanalı kullandığından tüm çağrıları için bir dakika olur.  
  
 Hizmet bilinen adı ile kullanılan `GetObject` WCF Web hizmetlerini çağırmak için kesin türü belirtilmiş, COM özgü bir yaklaşım ile yönetilmeyen Geliştirici sağlamak için işlevi. Bu yerel, COM görünür tanımı WCF Web hizmeti sözleşmesi ve kullanılacak bağlama gerektirir. İlk yöntem çağrısında COM programcıları bu kanal oluşturma şeffaf bir şekilde gerçekleşir, ancak diğer WCF istemcileri gibi hizmet türü belirtilmiş bir kanala hizmet bilinen adı oluşturmalıdır.  
  
 Bilinen ad kullanırken diğer WCF istemcileri ortak, adresi, bağlama ve hizmet ile iletişim kurmak için sözleşme uygulamaları belirtin. Sözleşme aşağıdaki yollardan birinde belirtilebilir:  
  
- Yazılı Sözleşme – Sözleşme, istemci makinede COM görünür türü olarak kaydedilir.  
  
- WSDL sözleşme – sözleşmenin bir WSDL Belgesi biçiminde sağlanır.  
  
- MEX Sözleşme – Sözleşme, çalışma zamanında bir meta veri değişimi (MEX) uç noktasından alınır.  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Hizmet bilinen adı tarafından desteklenen parametreleri  
 Hizmet bilinen adı tarafından desteklenen parametreleri aşağıdaki tabloda gösterilmektedir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`address`|Hizmet URL'si konumu.|  
|`binding`|Bölüm adı uygulama yapılandırmasından bağlama.|  
|`bindingConfiguration`|Adlandırılmış bağlama bölümü içinde adlandırılmış bağlama örneğinden.|  
|`contract`|Hizmet sözleşmesi ya da sözleşme adı (MEX) temsil eden arabirim tanımlayıcısı (IID).|  
|`wsdl`|WSDL belgesi sözleşme tanımı alternatif bir form sağlar.|  
|`spnIdentity`|Sunucu asıl adı (SPN) kimlik hizmetiyle iletişim kurmak için kullanılacak.|  
|`upnIdentity`|Kullanıcı asıl adı (UPN) hizmetiyle iletişim kurmak için kullanılacak kimlik.|  
|`dnsIdentity`|Hizmetiyle iletişim kurmak için kullanılacak DNS Kimliği'ni kullanın.|  
|`mexAddress`|Hizmet meta veri değişimi (MEX) uç noktası URL konumu.|  
|`mexBinding`|MEX uç noktası ile bağlanmak için uygulama yapılandırmasından bağlama bölüm adı.|  
|`mexBindingConfiguration`|MEX uç noktası ile bağlanmak için adlandırılmış bağlama bölümü içinde adlandırılmış bağlama örneğinden.|  
|`bindingNamespace`|Namespace öğesinden alınan MEX. bağlama bölüm adı|  
|`contractNamespace`|Namespace, alınan MEX. sözleşmeden|  
|`mexSpnIdentity`|Sunucu asıl adı (SPN) kimliğini MEX uç noktası ile iletişim kurmak için kullanılacak.|  
|`mexUpnIdentity`|MEX uç noktası ile iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.|  
|`mexDnsIdentity`|MEX uç noktası ile iletişim kurmak için kullanılacak DNS Kimliği'ni kullanın.|  
|`serializer`|"Xml" veya "datacontract" seri hale getirici kullanımını belirtir.|  
  
> [!NOTE]
>  Hatta tamamen COM tabanlı istemciler ile kullanıldığında, hizmet bilinen adı WCF ve destekleyen .NET Framework 2.0 istemci bilgisayarda yüklü olmasını gerektirir. Hizmet bilinen adı kullanan istemci uygulamaları uygun .NET Framework çalışma zamanı sürümünü yükleme önemlidir. Office uygulamaları içinde ad kullanırken bir yapılandırma dosyası doğru framework sürümünü yüklendiğinden emin olmak için gerekli olabilir. Örneğin, Excel ile Excel.exe dosyasıyla aynı dizinde Excel.exe.config adlı bir dosyada aşağıdaki metni yerleştirilmelidir:  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kaydetme ve hizmet bilinen adı yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)

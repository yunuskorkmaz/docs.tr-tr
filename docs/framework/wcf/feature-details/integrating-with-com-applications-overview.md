---
title: COM Uygulamaları ile Tümleştirme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: c789d4a52da9b2785fb5919a674bf19f23d23509
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493402"
---
# <a name="integrating-with-com-applications-overview"></a>COM Uygulamaları ile Tümleştirme Genel Bakış
Windows Communication Foundation (WCF) yönetilen kod developer ile bağlı uygulamaları oluşturmak için zengin bir ortam sağlar. COM tabanlı yönetilmeyen kodunda önemli ölçüde yatırımınız varsa ve geçirmek istediğiniz değil, ancak, hala WCF Web Hizmetleri doğrudan varolan kodunuza WCF Hizmeti bilinen adını kullanarak tümleştirebilirsiniz. Hizmet adının Office VBA, Visual Basic 6.0 veya Visual C++ 6.0 gibi bir geniş aralığı, COM tabanlı geliştirme ortamlarından kullanılabilir.  
  
> [!NOTE]
>  Hizmet adının tüm iletişimi için bir WCF iletişim kanalı kullanır. Bu kanal için güvenlik ve kimlik mekanizmaları standart COM ve DCOM proxy'leri kullanılanlardan farklı. Ayrıca, hizmet adının varsayılan zaman aşımı süresi bir WCF iletişim kanalı kullandığından bir dakikalık tüm çağrıları için kullanılır.  
  
 Hizmet bilinen adı ile birlikte kullanılan `GetObject` işlevi WCF Web hizmetlerini çağırmak için kesin tür belirtilmiş, COM özgü bir yaklaşım ile yönetilmeyen Geliştirici sağlayın. Bu bir yerel, WCF Web hizmeti sözleşme ve kullanılacak bağlama COM görünür tanımını gerektirir. Bu kanal oluşturma ilk yöntemi çağrıda COM programcıları saydam oluşur ancak diğer WCF istemcileri gibi hizmet adının hizmetine yazılan kanal oluşturmalıdır.  
  
 Ad kullanırken diğer WCF istemciler ortak, adresi, bağlama ve hizmet ile iletişim kurmak için sözleşme uygulamaları belirtin. Sözleşme aşağıdaki yollardan biri belirtilebilir:  
  
-   Yazılı Sözleşme – Sözleşme COM görünebilir tür istemci makinesinde olarak kaydedilir.  
  
-   WSDL Sözleşme – Sözleşme WSDL Belgesi biçiminde sağlanır.  
  
-   Çalışma zamanında meta veri değişimi (MEX) uç noktasından MEX Sözleşme – Sözleşme alınır.  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Hizmet bilinen adı tarafından desteklenen parametreleri  
 Aşağıdaki tabloda hizmet bilinen adı tarafından desteklenen parametreleri gösterir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`address`|Hizmet konumu URL.|  
|`binding`|Bölüm adı uygulama yapılandırmasından bağlama.|  
|`bindingConfiguration`|Adlandırılmış bağlama bölüm içindeki adlandırılmış bağlama örneğinden.|  
|`contract`|Hizmet sözleşmesi veya sözleşme adı (MEX) temsil eden arabirim tanımlayıcısı (IID).|  
|`wsdl`|Sözleşme tanımı alternatif bir biçimidir sağlar WSDL belgesi.|  
|`spnIdentity`|Hizmet ile iletişim kurmak için kullanılacak sunucu asıl adı (SPN) kimliği.|  
|`upnIdentity`|Hizmet ile iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.|  
|`dnsIdentity`|Hizmet ile iletişim kurmak için kullanılacak DNS Kimliği'ni kullanın.|  
|`mexAddress`|Hizmet meta veri değişimi (MEX) uç noktası URL'si konumu.|  
|`mexBinding`|Bölüm adı MEX bitiş noktası ile bağlanmak için uygulama yapılandırmasından bağlama.|  
|`mexBindingConfiguration`|MEX bitiş noktası ile bağlanmak için adlandırılmış bağlama bölüm içindeki adlandırılmış bağlama örneğinden.|  
|`bindingNamespace`|Alınan MEX. bağlama bölüm adından Namespace|  
|`contractNamespace`|Alınan MEX. sözleşmeden Namespace|  
|`mexSpnIdentity`|Sunucu asıl adı (SPN) kimliğini MEX bitiş noktası ile iletişim kurmak için kullanılacak.|  
|`mexUpnIdentity`|MEX bitiş noktası ile iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.|  
|`mexDnsIdentity`|MEX bitiş noktası ile iletişim kurmak için kullanılan DNS Kimliği'ni kullanın.|  
|`serializer`|"Xml" veya "datacontract" seri hale getirici belirtin.|  
  
> [!NOTE]
>  Tamamen COM tabanlı istemcilerle bile kullanıldığında, hizmet adının WCF ve destekleyen .NET Framework 2.0 istemci bilgisayarda yüklü olmasını gerektirir. Hizmet bilinen adı kullanma istemci uygulamaları .NET Framework çalışma zamanının uygun sürümünü yükleme önemlidir. Office uygulamaları içinde ad kullanırken, bir yapılandırma dosyası doğru framework sürümü yüklendiğinden emin olmak için gerekli olabilir. Örneğin, Excel ile Excel.exe dosyası ile aynı dizinde Excel.exe.config adlı bir dosyada aşağıdaki metni yerleştirilmelidir:  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)

---
title: "COM Uygulamaları ile Tümleştirme Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e995fc66a925cb0ebe272c9dceca1ba63b9459d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications-overview"></a>COM Uygulamaları ile Tümleştirme Genel Bakış
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]yönetilen kod Geliştirici bağlı uygulamaları oluşturmak için zengin bir ortam sağlar. Ancak, yönetilmeyen COM tabanlı kodunda önemli ölçüde yatırımınız varsa ve geçirmek istemediğiniz hala tümleştirebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Hizmetleri doğrudan varolan kodunuza kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet bilinen adı. Hizmet adının Office VBA, Visual Basic 6.0 veya Visual C++ 6.0 gibi bir geniş aralığı, COM tabanlı geliştirme ortamlarından kullanılabilir.  
  
> [!NOTE]
>  Hizmet bilinen adı kullanan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tüm iletişimi için iletişim kanalı. Bu kanal için güvenlik ve kimlik mekanizmaları standart COM ve DCOM proxy'leri kullanılanlardan farklı. Ayrıca, hizmet adının kullandığından bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletişim kanalını varsayılan zaman aşımı süresi olan tüm çağrıları için bir dakika.  
  
 Hizmet bilinen adı ile birlikte kullanılan `GetObject` yönetilmeyen Geliştirici kesin türü belirtilmiş, COM özgü bir yaklaşım için arama sağlamak için işlevi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Hizmetleri. Bu yerel, COM görünür tanımının gerektirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web hizmet sözleşmesini ve kullanılacak bağlama. Gibi diğer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bu kanal oluşturma ilk yöntemi çağrıda COM programcıları saydam oluşmamasına rağmen istemciler, hizmet adının hizmetine yazılan bir kanal oluşturmak gerekir.  
  
 Diğer ortak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemciler, ad kullanırken uygulamaları belirtin adresi, bağlama ve hizmet ile iletişim kurmak için sözleşme. Sözleşme aşağıdaki yollardan biri belirtilebilir:  
  
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
>  Tamamen COM tabanlı istemcilerle bile kullanıldığında, hizmet adının gerektirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve istemci bilgisayarda yüklü olmasını destekleyen .NET Framework 2.0. Hizmet bilinen adı kullanma istemci uygulamaları .NET Framework çalışma zamanının uygun sürümünü yükleme önemlidir. Office uygulamaları içinde ad kullanırken, bir yapılandırma dosyası doğru framework sürümü yüklendiğinden emin olmak için gerekli olabilir. Örneğin, Excel ile Excel.exe dosyası ile aynı dizinde Excel.exe.config adlı bir dosyada aşağıdaki metni yerleştirilmelidir:  
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
 [Nasıl yapılır: kaydetmek ve hizmet bilinen adı yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)

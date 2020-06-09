---
title: COM Uygulamaları ile Tümleştirme Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: c283e7cbc4cb4b8bc37dd1313480410df93a93bf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596831"
---
# <a name="integrating-with-com-applications-overview"></a>COM Uygulamaları ile Tümleştirme Genel Bakış

Windows Communication Foundation (WCF), bağlı uygulamalar oluşturmak için zengin bir ortam ile yönetilen kod geliştiricisi sağlar. Ancak, yönetilmeyen COM tabanlı kodda önemli bir yatırımınız varsa ve geçiş yapmak istemiyorsanız, WCF hizmeti bilinen adını kullanarak yine de WCF Web hizmetlerini mevcut kodunuzla tümleştirmeye devam edebilirsiniz. Hizmet bilinen adı, Office VBA, Visual Basic 6,0 veya Visual C++ 6,0 gibi çok çeşitli COM tabanlı geliştirme ortamlarından kullanılabilir.

> [!NOTE]
> Hizmet bilinen adı, tüm iletişimler için bir WCF iletişim kanalı kullanır. Bu kanala yönelik güvenlik ve kimlik mekanizmaları standart COM ve DCOM proxy 'lerinde kullanılanlardan farklıdır. Ayrıca, hizmet bilinen adı bir WCF iletişim kanalı kullandığından, tüm çağrılar için varsayılan zaman aşımı süresi bir dakikadır.

Hizmet bilinen `GetObject` geliştiricisi, WCF Web hizmetlerini çağırmak için kesin olarak belirlenmiş, com 'a özgü bir yaklaşımla birlikte yönetilmeyen geliştiriciyi sağlamak için işleviyle birlikte kullanılır. Bu, WCF Web hizmeti sözleşmesinin yerel, COM görünebilir tanımını ve kullanılacak bağlamayı gerektirir. Diğer WCF istemcileri gibi, hizmet bilinen bir kanal, bu kanal oluşturma ilk yöntem çağrısında COM programcısı tarafından saydam olarak gerçekleşse de, hizmete bir türü belirtilmiş bir kanal oluşturulmalıdır.

Diğer WCF istemcileriyle ortak olarak, bilinen ad kullanıldığında, uygulamalar bir hizmetle iletişim kurmak için adresi, bağlamayı ve sözleşmeyi belirtir. Sözleşme aşağıdaki yollarla belirtilebilir:

- Yazılı sözleşme – sözleşme, istemci makinesinde COM görünebilir bir tür olarak kaydedilir.

- WSDL sözleşmesi – sözleşme, WSDL belgesi biçiminde sağlanır.

- MEX sözleşmesi – sözleşme, meta veri değişimi (MEX) uç noktasından çalışma zamanında alınır.

## <a name="parameters-supported-by-the-service-moniker"></a>Hizmet bilinen parametreleri tarafından desteklenen parametreler

Aşağıdaki tabloda, hizmet bilinen adı tarafından desteklenen parametreler gösterilmektedir.

|Parametre|Açıklama|
|---------------|-----------------|
|`address`|Hizmetin URL konumu.|
|`binding`|Uygulama yapılandırmasından bölüm adı bağlama.|
|`bindingConfiguration`|Adlandırılmış bağlama bölümünün içinden adlandırılmış bağlama örneği.|
|`contract`|Hizmet sözleşmesini veya sözleşme adını (MEX 'dan) temsil eden arabirim tanımlayıcısı (IID).|
|`wsdl`|Farklı bir sözleşme tanımı biçimi sağlayan WSDL belgesi.|
|`spnIdentity`|Hizmetle iletişim kurmak için kullanılacak sunucu asıl adı (SPN) kimliği.|
|`upnIdentity`|Hizmetle iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.|
|`dnsIdentity`|Hizmetle iletişim kurmak için kullanılacak DNS kimliği.|
|`mexAddress`|Hizmetin meta veri değişimi (MEX) uç noktasının URL konumu.|
|`mexBinding`|Uygulama yapılandırmasından, MEX uç noktasına bağlanmak için bölüm adı bağlama.|
|`mexBindingConfiguration`|Adlandırılmış bağlama bölümünün içinden, MEX uç noktasına bağlanmak için adlandırılmış bağlama örneği.|
|`bindingNamespace`|Alınan MEX 'den bağlama bölümü adının ad alanı.|
|`contractNamespace`|Alınan MEX 'deki sözleşmenin ad alanı.|
|`mexSpnIdentity`|MEX uç noktasıyla iletişim kurmak için kullanılacak sunucu asıl adı (SPN) kimliği.|
|`mexUpnIdentity`|MEX uç noktasıyla iletişim kurmak için kullanılacak kullanıcı asıl adı (UPN) kimliği.|
|`mexDnsIdentity`|MEX uç noktasıyla iletişim kurmak için kullanılacak DNS kimliği.|
|`serializer`|"Xml" veya "DataContract" serileştirici kullanımını belirtin.|

> [!NOTE]
> Tamamen COM tabanlı istemcilerle birlikte kullanıldığında, hizmet bilinen adı WCF ve destekleyici .NET Framework 2,0 ' i istemci bilgisayara yüklemek için gerekir. Ayrıca, hizmet bilinen adını kullanan istemci uygulamalarının .NET Framework çalışma zamanının uygun sürümünü yüklemesi de önemlidir. Office uygulamalarında bilinen ad kullanıldığında, doğru çerçeve sürümünün yüklendiğinden emin olmak için bir yapılandırma dosyası gerekebilir. Örneğin, Excel 'de aşağıdaki metin, Excel. exe. config adlı bir dosyaya Excel. exe dosyası ile aynı dizinde yerleştirilmelidir:
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma](how-to-register-and-configure-a-service-moniker.md)

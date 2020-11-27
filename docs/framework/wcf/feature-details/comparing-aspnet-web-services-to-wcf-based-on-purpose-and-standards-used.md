---
title: ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: 62917d7a188d0863f6ebcb7dd3531ef2dd6a5132
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295073"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma

HTTP üzerinden basit nesne erişim Protokolü (SOAP) kullanarak ileti gönderen ve alan uygulamalar oluşturmak için ASP.NET Web Hizmetleri geliştirilmiştir. İletilerin yapısı bir XML şeması kullanılarak tanımlanabilir ve .NET Framework Objects 'e ve onlardan iletileri serileştirmek için bir araç sağlanır. Teknoloji Web Hizmetleri Açıklama Dili (WSDL) Web Hizmetleri 'ni anlatmak için otomatik olarak meta veriler oluşturabilir ve WSDL 'den Web Hizmetleri için istemci oluşturmak için ikinci bir araç sağlanır.  
  
 WCF, .NET Framework uygulamalarının diğer yazılım varlıklarıyla ileti alışverişi için etkinleştirilmesi içindir. SOAP varsayılan olarak kullanılır, ancak iletiler herhangi bir biçimde olabilir ve herhangi bir aktarım protokolü kullanılarak dağıtılabilir. İletilerin yapısı bir XML şeması kullanılarak tanımlanabilir ve .NET Framework nesnelerinden gelen ve olmayan iletileri serileştirmek için çeşitli seçenekler vardır. WCF, WSDL ' de teknoloji kullanılarak oluşturulan uygulamaları ve ayrıca WSDL 'den bu uygulamalar için istemci oluşturmaya yönelik bir araç sağlar.  
  
 ASP.NET Web Hizmetleri tarafından desteklenen standartlar, [ASP.NET kullanılarak oluşturulan XML Web hizmetlerinin avantajları](/previous-versions/dotnet/netframework-4.0/0859ebft(v=vs.100))halinde belgelenmiştir. WCF tarafından desteklenen standartların daha kapsamlı listesi, [System-Provided birlikte çalışabilirlik bağlamaları tarafından desteklenen Web Hizmetleri protokollerinde](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)listelenmiştir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma](comparing-aspnet-web-services-to-wcf-based-on-development.md)

---
title: Desteklenen Dağıtım senaryoları
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 6898ec33564a526d0e444502ebb6ed7f142f1856
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347975"
---
# <a name="supported-deployment-scenarios"></a>Desteklenen Dağıtım senaryoları

Kısmen güvenilen uygulamalarda kullanım için desteklenen Windows Communication Foundation (WCF) özelliklerinin alt kümesi, WCF kullanımı için bazı senaryoların gereksinimlerini karşılayacak şekilde tasarlanmıştır. Sunucuda, WCF, ASP.NET 2,0 Orta güven izninin güvenlik nedenleriyle ayarlanan üçüncü taraf uygulamaları çalıştıran Internet ölçekli paylaşılan barındırma sağlayıcılarının gereksinimlerini karşılar. İstemcide, WCF kısmi güven desteği, güvenilir olmayan sitelerden masaüstü uygulamalarının sorunsuz ve güvenli dağıtımına izin veren [ClickOnce dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment) veya WPF XAML tarayıcı uygulaması teknolojisi gibi dağıtım teknolojilerinin gereksinimlerini karşılamak üzere tasarlanmıştır.

## <a name="minimum-permission-requirements"></a>En düşük izin gereksinimleri

WCF, aşağıdaki standart adlandırılmış izin kümelerinden biri altında çalışan uygulamalardaki özelliklerin bir alt kümesini destekler:

- Orta güven izinleri

- Internet bölgesi izinleri

Daha kısıtlayıcı izinlerle kısmen güvenilen uygulamalarda WCF kullanılmaya çalışılması, çalışma zamanında güvenlik özel durumlarına neden olabilir.

Bu izin kümelerinde desteklenen özellikler hakkında daha fazla bilgi için bkz. [kısmi güven özelliği uyumluluğu](partial-trust-feature-compatibility.md).

## <a name="partial-trust-on-the-server"></a>Sunucuda kısmi güven

Birçok ticari ASP.NET Web uygulaması barındırma hizmeti sağlayıcısı, sunucularında çalışan uygulamaların ASP.NET 2,0 Orta güven izin kümesinde çalıştığını belirten uyumluluğunu doğrulamıştır. WCF Hizmetleri, bu ortamlarda çalıştırılabilir <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>veya aktarım düzeyi güvenlik ile <xref:System.ServiceModel.WSHttpBinding> kullanırlar.

Orta düzeyde güven barındırma ortamlarında çalışan WCF Hizmetleri ayrıca, istemci isteklerine yanıt olarak diğer sunuculara iletiler göndererek orta katman hizmet olarak davranabilir. Barındırma ortamı, istenen sunucuya giden istekleri yapmak üzere uygulamaya uygun <xref:System.Net.WebPermission> verildiyse, sunucuda orta katman senaryolar desteklenir.

Desteklenen SOAP bağlamalarından birini kullanan SOAP mesajlaşma 'ya ek olarak, WCF kısmen güvenilen uygulamalarda Web stili hizmetler oluşturmak için <xref:System.ServiceModel.WebHttpBinding> destekler. WCF [Web http programlama modeli](wcf-web-http-programming-model.md), [WCF dağıtımı](wcf-syndication.md)ve [AJAX Tümleştirme ve WCF 'nin JSON desteği](ajax-integration-and-json-support.md) özellikleri kısmi güvende desteklenir.

İş akışı hizmetleri tam güven izinleri gerektirir ve kısmen güvenilen uygulamalarda kullanılamaz.

Daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET 2,0 'de orta güveni kullanma](https://go.microsoft.com/fwlink/?LinkId=84603).

## <a name="partial-trust-on-the-client"></a>İstemcide kısmi güven

Kodu güvenilmeyen Internet sitelerinden indirirken ve çalıştırırken belirli güvenlik önlemleri alınmalıdır. Hem [ClickOnce dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment) hem de WPF XAML tarayıcı UYGULAMASı (XBAP) teknolojisi, güvenli olmayan koda sınırlı Izinler (Internet bölgesi) vermek için kısmi güvenin kullanılmasını sağlar.

WCF, [ClickOnce dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment) veya XBAP tarafından dağıtılan kısmen güvenilen uygulamaların içinden uzak sunucularla iletişim kurmak için kullanılabilir. Internet bölgesi izin kümesi, kaynak ana bilgisayar için <xref:System.Net.WebPermission> içerir ve bu uygulamalar, [kısmi güven özelliği uyumluluğu](partial-trust-feature-compatibility.md)bölümünde AÇıKLANAN desteklenen WCF bağlamalarından herhangi birini kullanarak kaynak sunucu ile iletişim kurmasına olanak tanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod erişim güvenliği](../../misc/code-access-security.md)
- [Windows Presentation Foundation tarayıcıda barındırılan uygulamalara genel bakış](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [Kısmi Güven](partial-trust.md)
- [ASP.NET güven düzeyleri ve Ilke dosyaları](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))

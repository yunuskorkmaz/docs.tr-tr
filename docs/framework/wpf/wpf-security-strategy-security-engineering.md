---
title: WPF Güvenlik Stratejisi - Güvenlik Mühendisliği
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: d5bcd5b06f6d922b29c2a494f1f63da1217e2b2d
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817867"
---
# <a name="wpf-security-strategy---security-engineering"></a>WPF Güvenlik Stratejisi - Güvenlik Mühendisliği
Güvenilir bilgi Işlem, güvenli kod üretimi sağlamaya yönelik bir Microsoft girişimidir. Güvenilir bilgi Işlem girişiminin [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]anahtar öğesi. , [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Güvenli kod teslimini kolaylaştırmak için standart MÜHENDİSLİK süreçleriyle birlikte kullanılan bir mühendislik uygulamasıdır. , [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] En iyi yöntemleri formalization, measurability ve ek yapıyla birleştiren on aşamadan oluşur; örneğin:  
  
- Güvenlik tasarımı Analizi  
  
- Araç tabanlı kalite denetimleri  
  
- Sızma testi  
  
- Son güvenlik incelemesi  
  
- Yayın sonrası ürün güvenlik yönetimi  
  
## <a name="wpf-specifics"></a>WPF özellikleri  
 Mühendislik ekibinin her ikisi de aşağıdaki ana yönlerini [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]içeren bileşimini uygular ve genişletir: [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]  
  
 [Tehdit modelleme](#threat_modeling)  
  
 [Güvenlik analizi ve Düzen araçları](#tools)  
  
 [Test teknikleri](#techniques)  
  
 [Kritik kod yönetimi](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Tehdit modelleme  
 Tehdit modellemesi, uygulamasının [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]temel bir bileşenidir ve olası güvenlik açıklarını belirlemede bir sistem profili için kullanılır. Güvenlik açıkları tanımlandıktan sonra, tehdit modelleme uygun azaltmaları da sağlar.  
  
 Tehdit modellemesi, yüksek düzeyde bir market mağaza kullanarak bir örnek olarak aşağıdaki temel adımları içerir:  
  
1. **Varlıkları tanımlama**. Market mağazalarının varlıkları çalışanlar, güvenli, nakit kayıtları ve envanter içerebilir.  
  
2. **Giriş noktaları numaralandırılıyor**. Market 'in giriş noktaları, ön ve arka kapılar, pencereler, yükleme rampası ve AIR koşullandırma birimlerini içerebilir.  
  
3. **Giriş noktalarını kullanarak varlıklara karşı saldırıları araştırma**. Olası bir saldırı, bir market giriş noktası aracılığıyla Market 'in *güvenli* varlığını hedefleyebilir; Havalandırma birimi, güvenli bir şekilde ve mağaza 'dan çekilme izni vermek için unvidalı olabilir.  
  
 Tehdit modellemesi, genelinde [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uygulanır ve şunları içerir:  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] Ayrıştırıcı dosyaları okur, metni ilgili nesne modeli sınıflarıyla eşleştirir ve gerçek kodu oluşturur.  
  
- Pencere tanıtıcısının (hWnd) nasıl oluşturulduğu, ileti gönderdiği ve bir pencerenin içeriğini işlemek için kullanılan.  
  
- Veri bağlama, kaynakları nasıl edinir ve sistemle etkileşime girer.  
  
 Bu tehdit modelleri, geliştirme sürecinde güvenlik tasarımı gereksinimlerini ve tehdit azaltmalarını belirlemek için önemlidir.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Kaynak çözümleme ve Düzen araçları  
 [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]'Ninel ile güvenlik kodu İnceleme öğelerine ek olarak, Takım,kaynakanalizineveilişkilidüzenlemelereyönelikçeşitliaraçlarıkullanarak[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] güvenlik açıklarını azaltır. Çok çeşitli kaynak araçları kullanılır ve şunları içerir:  
  
- **FxCop**: Yönetilen koddaki, devralma kurallarından, yönetilmeyen kodla güvenle birlikte çalışma ile kod erişimi güvenlik kullanımı arasında değişen yaygın güvenlik sorunlarını bulur. Bkz. [FxCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Önek/PREfast**: Yönetilmeyen kodda, arabellek aşımları, biçim dizesi sorunları ve hata denetimi gibi güvenlik açıklarını ve genel güvenlik konularını bulur.  
  
- **Yasaklanmış API 'ler**: , Gibi güvenlik sorunlarına neden olmak üzere iyi bilinen işlevlerin yanlışlıkla kullanımını belirlemek için kaynak kodu arar `strcpy`. Tanımlandıktan sonra, bu işlevler daha güvenli olan alternatifler ile değiştirilmiştir.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Test teknikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]aşağıdakileri içeren çeşitli güvenlik testi tekniklerini kullanır:  
  
- **Beyaz kutu testi**: Sınayıcılar kaynak kodunu görüntüler ve ardından Exploit testlerini oluşturur.
  
- **Kara kutu testi**: Test edenler, API ve özellikleri inceleyerek güvenlik açıklarını bulmaya çalışır ve ardından ürüne saldırmayı dener.  
  
- **Diğer ürünlerden güvenlik sorunlarını gerileme**: İlgili ürünlerden ilgili olan güvenlik sorunları test edilir. Örneğin, Internet Explorer için yaklaşık 60 güvenlik sorunlarının uygun türevleri tanımlanmıştır ve uygulanabilirliği [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]için denenmelidir.  
  
- **Dosya belirsizlik aracılığıyla araçlara dayalı sızma testi**: Dosya, çeşitli girişler aracılığıyla bir dosya okuyucusunun giriş aralığından yararlanılması. Bu tekniğin [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kullanıldığı bir örnek, görüntü kod çözme kodunda hata olup olmadığını denetmektir.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Kritik kod yönetimi  
 İçin [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] ,[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ayrıcalıkları destekleyen güvenlik açısından kritik kodu işaretlemek ve izlemek için .NET Framework desteğini kullanarak bir güvenlik korumalı alanı oluşturur (bkz. WPF Güvenlik Stratejisi-Platform içindeki **güvenlik açısından kritik metodolojisi** [ Güvenlik](wpf-security-strategy-platform-security.md)). Güvenlik açısından kritik kodda yüksek güvenlik kalitesi gereksinimleri verilince, bu kod, ek bir kaynak yönetimi denetimi ve güvenlik denetimi düzeyi alır. İçin yaklaşık% 5 ila% 10 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] oranında, özel bir gözden geçirme ekibi tarafından gözden geçirilen güvenlik açısından kritik koddan oluşur. Kaynak kodu ve iade işlemi, güvenlik açısından kritik kodu izleyerek ve her kritik varlıkla (kritik kod içeren bir yöntem) oturum kapatma durumuna eşlenerek yönetilir. Kaydolma durumu, bir veya daha fazla gözden geçiren adını içerir. Her günlük oluşturma [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , onaylanmamış değişiklikleri denetlemek için, önceki Derlemeleriyle ilgili kritik kodu karşılaştırır. Bir mühendis İnceleme ekibinden onay olmadan kritik kodu değiştirirse, bu, hemen belirtilir ve düzeltilir. Bu işlem, korumalı alan kodu üzerinde [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] özellikle yüksek düzeyde bir uygulama ve bakım olanağı sunar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](security-wpf.md)
- [WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](wpf-security-strategy-platform-security.md)
- [Güvenilir bilgi Işlem](https://www.microsoft.com/mscorp/twc/default.mspx)
- [.NET 'te güvenlik](../../standard/security/index.md)

---
title: Güvenlik stratejisi ve Mühendisliği
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
ms.openlocfilehash: 57ee0c8242c0bca1b2c76e7751ed25f6a889c264
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741843"
---
# <a name="wpf-security-strategy---security-engineering"></a>WPF Güvenlik Stratejisi - Güvenlik Mühendisliği
Güvenilir bilgi Işlem, güvenli kod üretimi sağlamaya yönelik bir Microsoft girişimidir. Güvenilir bilgi Işlem girişiminin önemli bir öğesi Microsoft Security Development Lifecycle (SDL). SDL, güvenli kod teslimini kolaylaştırmak için standart MÜHENDİSLİK süreçleriyle birlikte kullanılan bir mühendislik uygulamasıdır. SDL, en iyi yöntemleri formalization, measurability ve ek yapıyla birleştiren on aşamadan oluşur; örneğin:  
  
- Güvenlik tasarımı Analizi  
  
- Araç tabanlı kalite denetimleri  
  
- Sızma testi  
  
- Son güvenlik incelemesi  
  
- Yayın sonrası ürün güvenlik yönetimi  
  
## <a name="wpf-specifics"></a>WPF özellikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] mühendislik ekibinin her ikisi de, aşağıdaki anahtar yönlerini içeren, SDL 'yi uygular ve genişletir:  
  
 [Tehdit modelleme](#threat_modeling)  
  
 [Güvenlik analizi ve Düzen araçları](#tools)  
  
 [Test teknikleri](#techniques)  
  
 [Kritik kod yönetimi](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Tehdit modelleme  
 Tehdit modellemesi, SDL 'nin temel bir bileşenidir ve olası güvenlik açıklarını tespit etmek üzere bir sistemin profilini almak için kullanılır. Güvenlik açıkları tanımlandıktan sonra, tehdit modelleme uygun azaltmaları da sağlar.  
  
 Tehdit modellemesi, yüksek düzeyde bir market mağaza kullanarak bir örnek olarak aşağıdaki temel adımları içerir:  
  
1. **Varlıkları tanımlama**. Market mağazalarının varlıkları çalışanlar, güvenli, nakit kayıtları ve envanter içerebilir.  
  
2. **Giriş noktaları numaralandırılıyor**. Market 'in giriş noktaları, ön ve arka kapılar, pencereler, yükleme rampası ve AIR koşullandırma birimlerini içerebilir.  
  
3. **Giriş noktalarını kullanarak varlıklara karşı saldırıları araştırma**. Olası bir saldırı, bir *Market giriş noktası* aracılığıyla Market 'in *güvenli* varlığını hedefleyebilir; Havalandırma birimi, güvenli bir şekilde ve mağaza 'dan çekilme izni vermek için unvidalı olabilir.  
  
 Tehdit modelleme [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tamamında uygulanır ve şunları içerir:  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ayrıştırıcısı dosyaları okur, metni ilgili nesne modeli sınıflarıyla eşleştirir ve gerçek kodu oluşturur.  
  
- Pencere tanıtıcısının (hWnd) nasıl oluşturulduğu, ileti gönderdiği ve bir pencerenin içeriğini işlemek için kullanılan.  
  
- Veri bağlama, kaynakları nasıl edinir ve sistemle etkileşime girer.  
  
 Bu tehdit modelleri, geliştirme sürecinde güvenlik tasarımı gereksinimlerini ve tehdit azaltmalarını belirlemek için önemlidir.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Kaynak çözümleme ve Düzen araçları  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ekibi, SDL 'nin el ile güvenlik kodu İnceleme öğelerine ek olarak, güvenlik açıklarını azaltmak için kaynak analizine ve ilişkili düzenlemelere yönelik birkaç araç kullanır. Çok çeşitli kaynak araçları kullanılır ve şunları içerir:  
  
- **FxCop**: Yönetilen koddaki, devralma kurallarından, yönetilmeyen kod ile güvenli bir şekilde birlikte çalışma ile kod erişimi güvenlik kullanımı arasındaki yaygın güvenlik sorunlarını bulur. Bkz. [FxCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Önek/PREfast**: arabellek aşımları, biçim dizesi sorunları ve hata denetimi gibi yönetilmeyen koddaki güvenlik açıklarını ve genel güvenlik sorunlarını bulur.  
  
- **Yasaklanmış API 'ler**: `strcpy`gibi güvenlik sorunlarına neden olmak üzere iyi bilinen işlevlerin yanlışlıkla kullanımını belirlemek için kaynak kodu arar. Tanımlandıktan sonra, bu işlevler daha güvenli olan alternatifler ile değiştirilmiştir.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Test teknikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aşağıdakileri içeren çeşitli güvenlik testi tekniklerini kullanır:  
  
- **Beyaz kutu testi**: test ediciler kaynak kodunu görüntüler ve ardından Exploit testlerini oluşturur.
  
- **Kara kutu testi**: test edenler, API ve özellikleri inceleyerek güvenlik açıklarını bulmaya çalışır ve ardından ürüne saldırmayı dener.  
  
- **Diğer ürünlerden güvenlik sorunlarını gerileme**: ilgili ürünlerden ilgili olan güvenlik sorunları test edilir. Örneğin, Internet Explorer için yaklaşık 60 güvenlik sorunlarının uygun çeşitleri tanımlanmıştır ve bunların uygulanabilirlikleri [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]edilmeye çalışıldı.  
  
- **Dosya belirsizlik aracılığıyla araçlara dayalı sızma testi**: dosya bulanık hale getirme, çeşitli girişler aracılığıyla bir dosya okuyucusunun giriş aralığından yararlanılır. Bu tekniğin kullanıldığı [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bir örnek, görüntü kod çözme kodunda hata olup olmadığını denetmektir.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Kritik kod yönetimi  
 XAML tarayıcı uygulamaları (XBAP 'ler) için [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], ayrıcalıkları ( [WPF Güvenlik Stratejisi-Platform güvenliği](wpf-security-strategy-platform-security.md)' nde **güvenlik açısından kritik metodolojisi** ) işaretleme ve izleme için .NET Framework desteğini kullanarak bir güvenlik korumalı alanı oluşturur. Güvenlik açısından kritik kodda yüksek güvenlik kalitesi gereksinimleri verilince, bu kod, ek bir kaynak yönetimi denetimi ve güvenlik denetimi düzeyi alır. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] için yaklaşık %5 ila %10, özel bir gözden geçirme ekibi tarafından gözden geçirilen güvenlik açısından kritik koddan oluşur. Kaynak kodu ve iade işlemi, güvenlik açısından kritik kodu izleyerek ve her kritik varlıkla (kritik kod içeren bir yöntem) oturum kapatma durumuna eşlenerek yönetilir. Kaydolma durumu, bir veya daha fazla gözden geçiren adını içerir. Her günlük [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] derlemesi, onaysız değişiklikleri denetlemek için önceki Derlemeleriyle ilgili kritik kodu karşılaştırır. Bir mühendis İnceleme ekibinden onay olmadan kritik kodu değiştirirse, bu, hemen belirtilir ve düzeltilir. Bu işlem, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] Sandbox kodu üzerinde özellikle yüksek düzeyde bir yönetim düzeyi uygulama ve bakımını yapmanızı mümkün.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](security-wpf.md)
- [WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](wpf-security-strategy-platform-security.md)
- [Güvenilir bilgi Işlem](https://www.microsoft.com/mscorp/twc/default.mspx)
- [.NET 'te güvenlik](../../standard/security/index.md)

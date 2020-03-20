---
title: Güvenlik stratejisi ve mühendisliği
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
ms.openlocfilehash: 970627c5de4964ebd5331c488152022fda55bd74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174569"
---
# <a name="wpf-security-strategy---security-engineering"></a>WPF Güvenlik Stratejisi - Güvenlik Mühendisliği
Güvenilir Bilgi İşlem, güvenli kod üretimini sağlamak için bir Microsoft girişimidir. Güvenilir Bilgi İşlem girişiminin önemli bir unsuru Microsoft Güvenlik Geliştirme Yaşam Döngüsü 'dür (SDL). SDL, güvenli kodun teslimini kolaylaştırmak için standart mühendislik süreçleri ile birlikte kullanılan bir mühendislik uygulamasıdır. SDL, en iyi uygulamaları formalizasyon, ölçülebilirlik ve ek yapı yla birleştiren on aşamadan oluşur:  
  
- Güvenlik tasarım analizi  
  
- Takım tabanlı kalite kontrolleri  
  
- Sızma testi  
  
- Son güvenlik incelemesi  
  
- Yayın sonrası ürün güvenliği yönetimi  
  
## <a name="wpf-specifics"></a>WPF Özellikleri  
 Mühendislik [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ekibi, aşağıdaki temel yönleri içeren SDL'yi hem uygular hem de genişletir:  
  
 [Tehdit Modelleme](#threat_modeling)  
  
 [Güvenlik Analizi ve Düzenleme Araçları](#tools)  
  
 [Test Teknikleri](#techniques)  
  
 [Kritik Kod Yönetimi](#critical_code)  
  
<a name="threat_modeling"></a>
### <a name="threat-modeling"></a>Tehdit Modelleme  
 Tehdit modelleme SDL'nin temel bileşenidir ve olası güvenlik açıklarını belirlemek için bir sistemin profilini çıkarmak için kullanılır. Güvenlik açıkları tanımlandıktan sonra, tehdit modellemesi de uygun azaltıcı etkenlerin yerinde olmasını sağlar.  
  
 Yüksek düzeyde, tehdit modelleme örnek olarak bir bakkal kullanarak aşağıdaki önemli adımları içerir:  
  
1. **Varlıkların Tanımlanması**. Bir marketin varlıkları arasında çalışanlar, kasa, yazar kasalar ve envanter bulunabilir.  
  
2. **Giriş Noktalarını Puanlama**. Bir marketin giriş noktaları ön ve arka kapılar, pencereler, yükleme rıhtımı ve klima ünitelerini içerebilir.  
  
3. **Giriş Noktalarını Kullanarak Varlıklara Yönelik Saldırıları Araştırma**. Olası bir saldırı *klima* giriş noktasından bir marketin *güvenli* varlığını hedef alabilir; klima ünitesi, kasanın içinden ve mağazadan çekilmesine izin verecek şekilde sökülebilir.  
  
 Tehdit modelleme boyunca [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uygulanır ve aşağıdakileri içerir:  
  
- Araleyicinin [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dosyaları nasıl okuduğu, metni karşılık gelen nesne modeli sınıflarına nasıl eşler ve gerçek kodu nasıl oluşturur.  
  
- Nasıl bir pencere tutamacı (hWnd) oluşturulur, iletigönderir ve bir pencerenin içeriğini işlemek için kullanılır.  
  
- Veri bağlamanın kaynakları nasıl elde eder ve sistemle etkileşime girilir.  
  
 Bu tehdit modelleri, geliştirme sürecinde güvenlik tasarım gereksinimlerini ve tehdit azaltımlarını belirlemek için önemlidir.  
  
<a name="tools"></a>
### <a name="source-analysis-and-editing-tools"></a>Kaynak Analizi ve Düzenleme Araçları  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] SDL'nin el ile güvenlik kodu gözden geçirme öğelerine ek olarak, takım güvenlik açıklarını azaltmak için kaynak çözümlemesi ve ilişkili ayarlamalar için çeşitli araçlar kullanır. Çok çeşitli kaynak araçları kullanılır ve aşağıdakileri içerir:  
  
- **FXCop**: Devralma kurallarından kod erişim güvenliği kullanımına ve yönetilmeyen kodla güvenli bir şekilde nasıl birlikte çalışılabilene kadar yönetilen kodda sık karşılaşılan güvenlik sorunlarını bulur. Bkz. [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Önek/Prefast**: Arabellek taşmaları, biçim dize sorunları ve hata denetimi gibi yönetilmeyen kodlarda güvenlik açıklarını ve yaygın güvenlik sorunlarını bulur.  
  
- **Yasaklı API'ler**: Güvenlik sorunlarına neden olduğu bilinen işlevlerin yanlışlıkla kullanımını belirlemek `strcpy`için kaynak kodu arar. Tanımlandıktan sonra, bu işlevler daha güvenli alternatiflerle değiştirilir.  
  
<a name="techniques"></a>
### <a name="testing-techniques"></a>Test Teknikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]çeşitli güvenlik sınama teknikleri kullanır:  
  
- **Whitebox Testi**: Test edenler kaynak kodunu görüntüleyin ve ardından yararlanma testleri oluşturur.
  
- **Blackbox Testing**: Test edenler API ve özellikleri inceleyerek güvenlik açıklarını bulmaya ve ürüne saldırmaya çalışırlar.  
  
- **Diğer Ürünlerden Güvenlik Sorunlarının Gerilemesi**: İlgili ürünlerin güvenlik sorunları nın test edildiği durumlarda. Örneğin, Internet Explorer için yaklaşık altmış güvenlik sorunlarının uygun türevleri tanımlanmış ve [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]uygulanabilirliği için denenmiş.  
  
- **Dosya Fuzzing ile Araçlar Tabanlı Penetrasyon Testi**: Dosya bulanıklığı, dosya okuyucunun giriş aralığının çeşitli girişler yoluyla kullanılmasıdır. Bu tekniğin [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kullanıldığı durumlardan biri, görüntü çözme kodundaki hata olup olmadığını denetlemektir.  
  
<a name="critical_code"></a>
### <a name="critical-code-management"></a>Kritik Kod Yönetimi  
 XAML tarayıcı uygulamaları (XBAP'ler) için, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ayrıcalıkları yükselten güvenlik açısından kritik kodu işaretlemek ve izlemek için .NET Framework desteğini kullanarak bir güvenlik alanı oluşturur (Bkz. [WPF Güvenlik Stratejisinde](wpf-security-strategy-platform-security.md)Güvenlik Açısından Kritik **Metodoloji** - Platform Güvenliği). Güvenlik kritik kodundaki yüksek güvenlik kalitesi gereksinimleri göz önüne alındığında, bu kod ek bir kaynak yönetimi denetimi ve güvenlik denetimi düzeyi alır. Yaklaşık %5 ila [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] %10'u, özel bir inceleme ekibi tarafından gözden geçirilen güvenlik açısından kritik koddan oluşur. Kaynak kodu ve iade işlemi, güvenlik kritik kodunu izleyerek ve her kritik varlığın (örneğin kritik kod içeren bir yöntem) işaretleme durumuna eşleyerek yönetilir. İmza durumu, bir veya daha fazla gözden geçirenin adlarını içerir. Her günlük [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] yapı, onaylanmamış değişiklikleri denetlemek için kritik kodu önceki yapılardakiyle karşılaştırır. Bir mühendis inceleme ekibinin onayı olmadan kritik kodu değiştirirse, hemen tanımlanır ve düzeltilir. Bu işlem, özellikle yüksek düzeyde sandbox kodu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] üzerinde inceleme yapılmasını ve bakımını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](security-wpf.md)
- [WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](wpf-security-strategy-platform-security.md)
- [Güvenilir Bilgi İşlem](https://www.microsoft.com/mscorp/twc/default.mspx)
- [.NET içinde güvenlik](../../standard/security/index.md)

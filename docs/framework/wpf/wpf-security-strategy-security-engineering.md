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
ms.openlocfilehash: 9123d59709b483c72ab49652bda1e547430fa33d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663244"
---
# <a name="wpf-security-strategy---security-engineering"></a>WPF Güvenlik Stratejisi - Güvenlik Mühendisliği
Güvenilir bilgi işlem, güvenli kod üretimini sağlamaya yönelik bir Microsoft girişimidir. Güvenilir bilgi işlem inisiyatifiyle önemli bir öğesidir [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Güvenli kod dağıtımını kolaylaştırmak için standart mühendislik süreçlerine ile birlikte kullanılan bir mühendislik uygulamasıdır. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Formalization measurability ve ek yapı ile en iyi birleştiren on aşamadan oluşan dahil olmak üzere:  
  
- Güvenlik tasarımı analizi  
  
- Aracı tabanlı kalite denetimlerinden  
  
- Sızma testi  
  
- Son güvenlik incelemesi  
  
- POST sürüm ürün güvenlik yönetimi  
  
## <a name="wpf-specifics"></a>WPF özellikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] Mühendislik ekibinin hem geçerli hem de genişletir [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], aşağıdaki önemli noktalar birleşimini içerir:  
  
 [Tehdit modelleme](#threat_modeling)  
  
 [Güvenlik analizi ve düzenleme araçları](#tools)  
  
 [Test teknikleri](#techniques)  
  
 [Kritik kod Yönetimi](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Tehdit modelleme  
 Tehdit modelleme olan temel bir bileşenidir [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]ve olası güvenlik açıklarını belirlemek için bir sistem profilini çıkarmak için kullanılır. Güvenlik açıklarını tanımlandıktan sonra tehdit modelleme de uygun bir risk azaltma işlemleri yerinde olmasını sağlar.  
  
 Yüksek bir düzeyde tehdit modelleme, Market örnek kullanıp aşağıdaki temel adımları içerir:  
  
1. **Varlıklar tanımlayan**. Çalışanların, güvenli, Yazar Kasa ve envanter marketin varlıklar içerebilir.  
  
2. **Giriş noktaları numaralandırma**. Marketin giriş noktaları, ön ve arka kapı, windows, yükleme dock ve havalandırma içerebilir.  
  
3. **Giriş noktaları kullanarak varlıkları saldırıları araştırma**. Olası bir saldırı marketin hedef *güvenli* yoluyla varlık *havalandırma* giriş noktası; havalandırma birimi / ve onu aracılığıyla çekilmesi güvenli izin vermek için unscrewed olabilir Depo.  
  
 Tehdit modelleme boyunca uygulanan [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ve aşağıdakileri içerir:  
  
- Nasıl [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ayrıştırıcı dosyalarını okur, karşılık gelen nesne modeli sınıfları için metin eşleştirir ve gerçek kod oluşturur.  
  
- Nasıl bir pencere tutucu (hWnd) oluşturulur, iletileri gönderir ve bir pencere içeriğini işlemek için kullanılır.  
  
- Nasıl veri bağlama kaynağı alır ve sistemi ile etkileşim kurar.  
  
 Bu tehdit modelleri geliştirme sürecinde tanımlayıcı güvenlik tasarım gereksinimleri ve tehdit risk azaltma işlemleri için önemlidir.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Kaynak analizi ve düzenleme araçları  
 Ek olarak el ile bir güvenlik kodu öğelerini gözden [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] takım, güvenlik açıklarını azaltmak için kaynak analiz ve ilişkili düzenlemeleri için çeşitli araçlar kullanır. Çok çeşitli kaynak araçları kullanılır ve aşağıdakileri içerir:  
  
- **FXCop**: Devralma kuralları nasıl güvenli bir şekilde yönetilmeyen kod ile çalışmak kod erişimi güvenliği kullanımı arasında değişen yönetilen kodda ortak güvenlik sorunlarını bulur. Bkz: [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Önek/Prefast**: Yönetilmeyen kod arabellek taşmaları, biçim dizesi sorunları ve hata denetimi gibi güvenlik açıklarını ve ortak güvenlik sorunlarını bulur.  
  
- **Yasaklanmış API**: Kaynak güvenlik sorunları gibi neden olduğu bilinen işlevleri yanlışlıkla kullanımını belirlemek için kod `strcpy`. Tanımlandıktan sonra bu işlevlerin daha güvenli alternatifler ile değiştirilir.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Test teknikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] çeşitli test teknikleri içeren güvenlik kullanır:  
  
- **Whitebox Sınama**: Sınayıcılar kaynak kodunu görüntüleme ve sonra exploit testler oluşturun  
  
- **Blackbox sınama**: Test ediciler, API ve özelliklerini inceleyerek güvenlik açığından yararlandıktan bulmaya ve ürün saldırılara karşı deneyin.  
  
- **Gerileme güvenlik konuları diğer ürünleri**: Uygun olduğunda, ilgili ürün güvenlik sorunlarını test edilmez. Altmış güvenlik sorunları için yaklaşık çeşitleri gibi uygun [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] tanımlanır ve bunların uygulanabilirliğini için çalıştığınız [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
- **Dosya karıştırma aracılığıyla tabanlı araçlar sızma testi**: Dosya karıştırma aralık boyunca birçok giriş dosyası okuyucu yararlanılması giriş olur. Bir örneği [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] burada bu yöntem resim kod çözme hatası olup olmadığını denetlemek için kullanılır.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Kritik kod Yönetimi  
 İçin [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] işaretleme ve izleme ayrıcalıklara yükseltir güvenlik açısından kritik kod için .NET Framework desteği kullanarak, bir güvenlik korumalı oluşturur (bkz **güvenlik açısından kritik Metodoloji** içinde [WPF Güvenlik stratejisi - Platform güvenliği](wpf-security-strategy-platform-security.md)). Bu tür kod kalitesi yüksek güvenlik gereksinimleri, güvenlik açısından kritik kodu verildiğinde, ek bir kaynak yönetim denetim ve güvenlik denetim düzeyi alır. Yaklaşık 5 %10 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] gözden geçirme ekibi tarafından gözden geçirilir güvenlik açısından kritik kod oluşur. Kaynak kodu ve iade etme işlemi, güvenlik açısından kritik kodu izleme ve kritik her varlık (yani kritik kod içeren bir yöntem), oturum durumu devre dışı eşleme tarafından yönetilir. Oturum durumu devre dışı bir veya daha fazla Gözden Geçiren adlarını içerir. Her günlük derlemesi [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kritik kod için onaylanmamış değişiklikleri denetlemek için önceki yapıları karşılaştırır. Bir mühendis kritik kod gözden geçirme ekibinin onayı olmadan değiştirirse, tanımlanır ve hemen düzeltildi. Bu işlem üzerinden scrutiny özellikle yüksek bir düzeyde Bakım ve uygulama tanır [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] korumalı alan kodu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](security-wpf.md)
- [WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Platform Güvenliği](wpf-security-strategy-platform-security.md)
- [Güvenilir bilgi işlem](https://www.microsoft.com/mscorp/twc/default.mspx)
- [.NET içinde güvenlik](../../standard/security/index.md)

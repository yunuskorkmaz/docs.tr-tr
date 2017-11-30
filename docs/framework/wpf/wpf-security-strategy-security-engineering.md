---
title: "WPF Güvenlik Stratejisi - Güvenlik Mühendisliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9237ed7467e87cd3e6ba72418c6964ce918751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="wpf-security-strategy---security-engineering"></a>WPF Güvenlik Stratejisi - Güvenlik Mühendisliği
Güvenilir bilgi işlem, güvenli kod üretim sağlamaya yönelik bir Microsoft girişimidir. Güvenilir bilgi işlem Initiative önemli bir unsurdur [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Standart mühendislik işlemler ile birlikte güvenli kod teslimini kolaylaştırmak için kullanılan bir mühendislik uygulamasıdır. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Formalization, measurability ve ek yapı ile en iyi yöntemler birleştiren on aşamadan oluşur dahil olmak üzere:  
  
-   Güvenlik tasarım çözümlemesi  
  
-   Aracı tabanlı kalite denetimleri  
  
-   Sızma test etme  
  
-   Son güvenlik incelemesi  
  
-   POST yayın ürün güvenlik yönetimi  
  
## <a name="wpf-specifics"></a>WPF özellikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] Mühendislik ekibi hem uygular ve genişleten [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], aşağıdaki unsur birleşimini içerir:  
  
 [Tehdit modelleme](#threat_modeling)  
  
 [Güvenlik analizi ve düzenleme araçları](#tools)  
  
 [Sınama teknikleri](#techniques)  
  
 [Kritik kod Yönetimi](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Tehdit modelleme  
 Tehdit modelleme bir bileşenidir çekirdek [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]ve olası güvenlik açıklarını belirlemek için sistemin profilini için kullanılır. Güvenlik açıkları tanımlandıktan sonra tehdit modelleme ayrıca uygun Azaltıcı Etkenler yerinde olmasını sağlar.  
  
 Yüksek bir düzeyde tehdit modelleme market örnek olarak kullanarak aşağıdaki anahtar adımları içerir:  
  
1.  **Varlıklar tanımlayan**. Marketin varlıklar çalışanlar, güvenli, Yazar Kasa ve stok içerebilir.  
  
2.  **Giriş noktaları numaralandırma**. Marketin giriş noktalarını ön ve arka kapı, windows, yükleme noktası ve havalandırma içerebilir.  
  
3.  **Giriş noktaları kullanarak varlıklar saldırıları araştırma**. Olası bir saldırı marketin hedef *güvenli* aracılığıyla varlığını *klima* klima; giriş noktası birimi aracılığıyla ve işyeri dışında çekebilir güvenli izin vermek için unscrewed olabilir Depo.  
  
 Tehdit modelleme boyunca uygulanır [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ve aşağıdakileri içerir:  
  
-   Nasıl [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ayrıştırıcı dosyalarını okur, karşılık gelen nesne modeli sınıfları ile metni eşleştirir ve fiili kodu oluşturur.  
  
-   Nasıl pencere işleyicisi (hWnd) oluşturulur, iletileri gönderir ve bir pencere içeriğini çizmek için kullanılır.  
  
-   Nasıl veri bağlama kaynakları alır ve sistemi ile etkileşim kurar.  
  
 Bu tehdit modelleri geliştirme sürecinde tanımlayıcı güvenlik tasarım gereksinimleri ve tehdit Azaltıcı için önemlidir.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Kaynak çözümleme ve düzenleme araçları  
 Ek olarak el ile güvenlik kodu öğelerini gözden geçirmeniz [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] takım güvenlik açıklarını azaltmak için kaynak çözümleme ve ilişkili düzenlemeleri için çeşitli araçlar kullanır. Çok çeşitli kaynak araçları kullanılır ve şunları içerir:  
  
-   **FXCop**: yönetilen kod devralma kurallarından güvenle yönetilmeyen kod ile birlikte çalışmak nasıl kod erişimi güvenliği kullanımı arasında değişen ortak güvenlik sorunlarını bulur. Bkz: [FXCop](http://www.gotdotnet.com/team/fxcop/).  
  
-   **Önek/Prefast**: bulur Güvenlik Açıkları ve ortak güvenlik sorunlarını arabellek taşmaları gibi yönetilmeyen kodunda biçim dizesi sorunları ve hata denetimi.  
  
-   **API yasaklanan**: aramaları kaynak güvenlik sorunları gibi neden olduğu bilinen işlevleri yanlışlıkla kullanımını belirlemek için kodu `strcpy`. Tanımlandıktan sonra bu işlevler daha güvenli alternatifler ile değiştirilir.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Sınama teknikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]çeşitli güvenlik sınama dahil teknikleri kullanır:  
  
-   **Whitebox Sınama**: Sınayıcılar kaynak kodu görüntüleme ve yararlanma testleri oluşturma  
  
-   **Blackbox sınama**: sınayıcılar güvenlik yararlanan API ve özelliklerini inceleyerek bulmaya ve ürün saldırı deneyin.  
  
-   **Güvenlik sorunlarını gerileme diğer ürünleri**: uygun yerlerde ilgili ürünlerden güvenlik sorunları sınanır. Örneğin, yaklaşık altmış güvenlik sorunlarını çeşitlemelerini uygun [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] tanımlanır ve bunların uygulanabilirliğini çalıştı [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
-   **Dosya karıştırma aracılığıyla sızma testi tabanlı Araçları**: Dosya karıştırma olan bir dosya okuyucu yararlanılması girişleri çeşitli aralığı girdisini. Bir örnekte [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] burada bu yöntem resim kod çözme hatası olup olmadığını denetlemek için kullanılır.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Kritik kod Yönetimi  
 İçin [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kullanarak, bir güvenlik sandbox oluşturur [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] işaretleme ve ayrıcalıkları artırılan güvenlik açısından kritik kod izleme desteği (bkz **güvenlik açısından kritik Metodoloji** içinde [ WPF güvenlik stratejisi - Platform güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Güvenlik açısından kritik koda yüksek güvenlik kalite gereksinimlerini verildiğinde, bu tür kod ek bir kaynak yönetimi denetim ve güvenlik denetim düzeyi alır. Yaklaşık 5 ile % 10, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] adanmış bir gözden geçirme ekibi tarafından gözden güvenlik açısından kritik kod oluşur. Kaynak kodu ve iade etme işlemi, güvenlik açısından kritik kodu izleme ve kritik her varlık (yani kritik kod içeren bir yöntem), oturum durumu devre dışı eşleme tarafından yönetilir. Oturum durumu devre dışı bir veya daha fazla gözden geçirenlerin adlarını içerir. Her günlük yapılandırmanın [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kritik kod onaylanmamış değişiklikleri denetlemek için önceki derlemelerinde karşılaştırır. Mühendisin kritik kod gözden geçirme ekibinin onayı olmadan değiştirirse, tanımlanır ve hemen düzeltilir. Bu işlem üzerinden uygulama ve Bakım scrutiny özellikle yüksek bir düzeyde sağlar [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] korumalı alan kodu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik](../../../docs/framework/wpf/security-wpf.md)  
 [WPF kısmi güven güvenliği](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [WPF güvenlik stratejisi - Platform güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Güvenilir bilgi işlem](http://www.microsoft.com/mscorp/twc/default.mspx)  
 [Uygulama iş parçacığı modelleme](http://msdn.microsoft.com/security/securecode/threatmodeling/acetm/)  
 [Güvenlik yönergeleri: .NET Framework 2.0](http://msdn.microsoft.com/library/default.asp?url=/library/dnpag2/html/PAGGuidelines0003.asp)

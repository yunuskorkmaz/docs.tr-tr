---
title: Uygulama Performansını Planlama
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
ms.openlocfilehash: 70dda68112d47d3e5a0609a5df7696920477c698
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210210"
---
# <a name="planning-for-application-performance"></a>Uygulama Performansını Planlama
Ne kadar iyi performans stratejinizi geliştirmek başarım hedeflerinizi başarısını bağlıdır. Planlama herhangi bir ürün geliştirmeye ilk aşamasıdır. Bu konu, iyi bir performans stratejisi geliştirme için birkaç basit kuralları açıklar.  
  
## <a name="think-in-terms-of-scenarios"></a>Senaryoları açısından düşünün  
 Senaryolarında size yardımcı olabilir, uygulamanızın kritik bileşenleri üzerinde odaklanın. Senaryoları, genellikle, müşteriler ek olarak rekabetçi ürünleri türetilir. Her zaman müşterilerinize incelemek ve hangi gerçekten bunları ürün ve rakiplerinizin ürünler hakkında heyecan hale getirdiğini öğrenin. Müşterilerinizin geri bildirim, uygulamanızın Birincil senaryo belirlemenize yardımcı olabilir. Başlatma sırasında kullanılacak bir bileşeni tasarlıyorsanız, örneğin, uygulama başlatıldığında, bileşeni'nin yalnızca bir kez çağırılır olasıdır. Başlangıç zamanı, anahtar senaryonuz haline gelir. Önemli senaryolar diğer örnekleri animasyon dizileri için istenen kare hızı olması ya da çalışma kümesi uygulama için izin verilen en yüksek olabilir.  
  
## <a name="define-goals"></a>Hedeflerinizi  
 Hedefleri, uygulama daha hızlı veya daha yavaş çalışıp çalışmadığını belirlemenize yardımcı olur. Hedefleri tüm senaryolarınız için tanımlamanız gerekir. Tanımladığınız tüm performans hedeflerini takımınızın müşterilerinizin beklentilerini üzerinde bağlı olmalıdır. Kümesi performans amaçlarını erkenden uygulama geliştirme döngüsü varken çözülmemiş bir çok zor olabilir. Ancak, bir ilk hedef ayarlayın ve daha sonraki bir hedefe hiç olmaması için gözden geçirme daha iyidir.  
  
## <a name="understand-your-platform"></a>Platformunuza anlama  
 Her zaman, ölçme, araştırma, uygulama geliştirme döngüsü sırasında daraltma/düzeltme süreçlerini sürdürün. Geliştirme döngüsü sonuna başından beri güvenilir ve kararlı bir ortamda, uygulamanızın performansını ölçmek gerekir. Dış faktörlerden kaynaklanan değişkenlik kaçınmanız gerekir. Örneğin, performans testi, virüsten koruma veya SMS gibi herhangi bir otomatik güncelleştirme devre dışı bırakmak, test sonuçları sırada değil performansı etkileyebilir. Uygulamanızın performansını cinsinden ölçülen sonra büyük geliştirmeler neden olabilecek değişiklikleri tanımlayın gerekir. Uygulamanızı oluşturduktan sonra döngüyü yeniden başlatın.  
  
## <a name="make-performance-tuning-an-iterative-process"></a>Performans ayarlama bir süreçtir olun  
 Kullanacağınız her bir özellik göreli maliyetini bilmeniz gerekir. Örneğin, Microsoft .NET Framework'te yansıma kullanımı, genellikle dikkatli kullanmak istediğiniz şekilde bilgi işlem kaynaklarını bakımından yoğun performans bağlıdır. Yalnızca kullandığınız özellikler, performans talepleri, uygulamanızın performans gereksinimlerine dengelemek dikkatli olmanız gerekir, bu yansıma, kullanımını önlemek anlamına gelmez.  
  
## <a name="build-towards-graphical-richness"></a>Grafik zenginliği doğrultusunda derleyin  
 Doğrultusunda ölçeklenebilir bir yaklaşım oluşturmak için önemli bir tekniktir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama performansı, grafik zenginlik ve karmaşıklık doğrultusunda oluşturulacak. Her zaman senaryonun hedeflerinize ulaşmak için en az performans yoğunluğu olan kaynakları kullanarak başlayın. Bu hedefleri gerçekleştirmeye sonra grafik zenginliği doğrultusunda her zaman senaryonun hedeflerinize göz önünde bulundurarak daha fazla performans yoğun özelliklerini kullanarak oluşturun. Unutmayın, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çok zengin bir platform ve çok zengin grafik özellikleri sağlar. Yoğun performans özelliklerini düşünmeden kullanarak genel uygulama performansınızı olumsuz yönde etkileyebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri geniş yayılım özelleştirmesi, denetim davranışlarını değiştirmeden, görünüm için izin vererek kendiliğinden genişletilebilir. Denetim şablonları stiller ve veri şablonları yararlanarak, oluşturabilir ve artımlı olarak özelleştirilebilen [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] performans gereksinimlerinizi uyum sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Donanımdan Yararlanma](optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Metin](optimizing-performance-text.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)

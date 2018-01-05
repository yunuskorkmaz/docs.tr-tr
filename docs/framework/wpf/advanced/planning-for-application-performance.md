---
title: "Uygulama Performansını Planlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6bdb140d90de02fa817c55a05f40e57fcd0d636c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="planning-for-application-performance"></a>Uygulama Performansını Planlama
Performans hedefleriniz elde başarısı ne kadar iyi performans stratejinizi geliştirin bağlıdır. Planlama herhangi bir ürün geliştirme ilk aşamasıdır. Bu konu, iyi bir performans stratejisi geliştirme için birkaç basit kuralları açıklar.  
  
## <a name="think-in-terms-of-scenarios"></a>Senaryolar açısından düşünün  
 Senaryoları yardımcı olabilir, uygulamanızın önemli bileşenlerinden odaklanmak. Senaryoları genellikle, müşteriler yanı sıra rekabet ürünleri türetilir. Her zaman müşterilerinize araştırmak ve ne gerçekten bunları ürününüzü ve rakiplerinizin ürünleri hakkında heyecan kolaylaştırdığını öğrenin. Müşterilerinizin geri bildirimi uygulamanızın birincil senaryosunu belirlemenize yardımcı olabilir. Başlatmada kullanılan bir bileşen tanımlıyorsanız, örneğin, uygulama başlatıldığında, bileşeni'nin yalnızca bir kez çağrılır olasıdır. Başlangıç zamanı anahtar senaryonuz olur. Diğer örnekleri senaryoları, animasyon sıraları için istenen kare hızı olması ya da çalışma kümesi uygulama için izin verilen en fazla olabilir.  
  
## <a name="define-goals"></a>Hedeflerinizi  
 Hedefler, uygulamanın daha hızlı veya daha yavaş çalışıp çalışmadığını belirlemek için yardımcı. Hedefleri tüm senaryolarınız için tanımlamanız gerekir. Tanımladığınız tüm performans hedeflerini müşterilerinizin beklentilerini bağlı olmalıdır. Hala birçok çözülmemiş bir sorun olduğunda amaçlarını erkenden uygulama geliştirme döngüsü kümesi performans zor olabilir. Ancak, bir başlangıç amacı ayarlamanız ve daha sonraki bir hedefe hiç olmamasından düzeltmek daha iyi olur.  
  
## <a name="understand-your-platform"></a>Platformunuzu anlayın  
 Her zaman ölçme, araştırma, uygulama geliştirme döngüsü sırasında daraltmayı/düzeltme süreçlerini sürdürün. Başlangıçtan itibaren geliştirme döngüsü sonuna, güvenilir ve kararlı bir ortamda, uygulamanızın performansını ölçmek gerekir. Dış faktörler tarafından neden değişkenlik kaçınmalısınız. Örneğin, performansı test edilirken virüsten koruma veya SMS gibi herhangi bir otomatik güncelleştirmeyi devre dışı bırakma, test sonuçları sırada değil etkisi performans. Uygulamanızın performansını ölçülen sonra büyük yenilikleri neden olacak değişiklikleri tanımlamanız gerekir. Uygulamanızı değiştirdiğinizde döngüyü yeniden başlatın.  
  
## <a name="make-performance-tuning-an-iterative-process"></a>Performans yinelemeli süreç ayarlama yapmak  
 Kullanacağınız her bir özelliğin göreli maliyetini bilmeniz gerekir. Örneğin, yansıma kullanımını [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] genellikle performans dikkatli kullanmak istersiniz, bilgi işlem kaynakları açısından yoğun içindir. Yalnızca uygulamanızı performans gereksinimlerine, kullandığınız özellikleri performans taleplerini dengelemek için dikkatli olmalıdır, bu yansıma, kullanımını önlemek anlamına gelmez.  
  
## <a name="build-towards-graphical-richness"></a>Grafik zenginliğini derleme  
 Doğrultusunda ölçeklendirilebilir bir yaklaşım oluşturmak için bir anahtar teknik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama performansını grafik zenginliğini ve karmaşıklık doğrultusunda yapı etmektir. Her zaman senaryonun hedeflerinize ulaşmak için en az başarım yoğunluğu olan kaynakları kullanarak başlayın. Bu amaca sonra doğru grafik zenginliğini her zaman senaryonun hedeflerinize göz önünde bulundurarak daha fazla performans yoğun özelliklerini kullanarak oluşturun. Unutmayın, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çok zengin bir platformun ve çok zengin grafik özellikleri sağlar. Performans Düşünmeden yoğun özellikleri kullanarak, genel uygulama performansını olumsuz yönde etkileyebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetimleri wide yayılan özelleştirmesi, denetim davranışlarını değiştirmeden, görünüm için izin vererek kendiliğinden genişletilebilir. Stiller, veri şablonları ve denetim şablonlarından yararlanarak, oluşturabilir ve artımlı olarak özelleştirilebilen [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] performans gereksinimlerinizi uyum sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Donanımdan Yararlanma](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Nesne Davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Uygulama Kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)

---
title: 'Performansı iyileştirme: Donanımdan Yararlanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: 683804acf43065543fa5d4ffb1a5ecf7e5b4c49a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773170"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Performansı iyileştirme: Donanımdan Yararlanma
Mimarisini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iki işlenen ardışık düzen, donanım ve yazılım vardır. Bu konuda, uygulamalarınızın performans iyileştirmeleri hakkında kararlar almanıza yardımcı olmak için bu işleme ardışık düzenleri hakkında bilgi sağlar.  
  
## <a name="hardware-rendering-pipeline"></a>Donanımla işlenen ardışık düzen  
 Belirlemek için en önemli faktör [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] performansı, işleme bağlı olduğunu — daha fazla piksel işlemek zorunda kalırsanız maliyeti daha yüksek performans. Ancak, daha fazla işleme için boşaltılabilecek [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], daha fazla performans avantajlarını elde edebilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulama donanımla işlenen ardışık düzen tüm avantajlarından yararlanır [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] en az destekleyen donanım özellikleri [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] sürüm 7.0. İyileştirmelerin destekleyen donanım tarafından kazanılabilir [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] sürüm 7.0 ve PixelShader 2.0 + özellikleri.  
  
## <a name="software-rendering-pipeline"></a>Yazılımla işlenen ardışık düzen  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yazılımla işlenen ardışık düzen olan tamamen CPU'ya bağlıdır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SSE ve SSE2 yönerge yararlanır CPU bir en iyi duruma getirilmiş, tam özellikli yazılım tarayıcısı uygulamak için ayarlar. Geri dönüş için yazılım uygulama işlevselliği donanımla işlenen ardışık düzen kullanarak işlenemiyor. istediğiniz zaman sorunsuz olarak gerçekleştirilir.  
  
 Büyük bir performans sorunu işlediğiniz piksel sayısı tanımlanır ve oranı doldurmak için işleme yazılım modunda işlerken karşılaşırsınız. Bir pikselin çizilme sayısını en aza indirmek yazılım işleme modunda performansıyla ilgili endişeleriniz varsa deneyin. Örneğin, ardından biraz saydam bir görüntü üzerinden işleyen, mavi arka plan ile bir uygulama varsa tüm pikselleri uygulamadaki iki kez işlenir. Sonuç olarak, iki kez mavi arka plan tablonuz varsa daha görüntü ile uygulama oluşturmak için uzun sürer.  
  
### <a name="graphics-rendering-tiers"></a>Grafik İşleme Katmanları  
 Uygulamanızın üzerinde çalışacağı donanım yapılandırması tahmin etmek oldukça zor olabilir. Ancak, her farklı donanım yapılandırması tüm avantajlarından yararlanabilmeniz sorunsuz bir şekilde özellikleri farklı bir donanım üzerinde çalışırken uygulamanızın izin veren bir tasarımı düşünün isteyebilirsiniz.  
  
 Bunu başarmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zamanında sistemin grafik kapasitesini belirlemek için işlevsellik sağlar. Grafik yeteneği, üç işleme yeteneği katmanları biri olarak ekran kartı gruplayarak belirlenir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıma sunan bir [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] işleme yeteneği katmanını sorgulamak bir uygulama sağlar. Uygulamanızı daha sonra donanım tarafından desteklenen işleme katmanına bağlı olarak çalışma zamanında farklı kod yollarını da alabilir.  
  
 En çok katmanı işleme düzeyleri etkileyen grafik donanımının özellikleri şunlardır:  
  
- **Video RAM** birleştirme grafik için kullanılan arabellek sayısı ve boyutu grafik donanımının video bellek miktarı belirler.  
  
- **Piksel gölgelendirici** piksel gölgelendirici efektleri piksel başına temelinde hesaplar işlevi bir grafik olduğundan. Görüntülenen grafiklerin çözümleme bağlı olarak, her görüntü çerçevesi için işlenmesi gereken birkaç milyon piksel olabilir.  
  
- **Köşe gölgelendirici** köşe gölgelendiricisi olan nesnenin köşe verileri matematiksel işlemler gerçekleştiren işlevi bir grafik.  
  
- **Çoklu doku desteği** bir 3B grafik nesnede karıştırma işlemi sırasında iki veya daha fazla farklı dokular uygulama özelliği başvurduğu çoklu doku desteği. Çoklu doku desteği derecesini grafik donanımının çoklu doku birimleri sayısına göre belirlenir.  
  
 Piksel gölgelendirici, köşe gölgelendiricisi ve çoklu doku özellikleri belirli tanımlamak için kullanılan [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] , buna karşılık, farklı işleme katmanları tanımlamak için kullanılan sürüm düzeylerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 İşleme yeteneğini grafik donanımının özelliklerini belirlemek bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sistem üç işleme katmanları tanımlar:  
  
- **Katman 0 işleme** donanım grafik ivmesi. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi sürüm 7.0 azdır.  
  
- **Katman 1 işleme** kısmi grafik donanım hızlandırma. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Büyüktür veya eşittir sürüm 7.0 sürüm düzeyi ve **daha az** sürüm 9.0 daha.  
  
- **Katman 2 işleme** grafik donanım hızlandırmayı çoğu grafik özellikleri kullanın. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi 9.0 sürümüne eşit veya daha büyük.  
  
 Daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme katmanları bkz [grafik işleme katmanları](graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Metin](optimizing-performance-text.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)

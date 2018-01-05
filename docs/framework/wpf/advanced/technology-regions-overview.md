---
title: "Teknoloji Bölgelerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- window regions [WPF]
- Win32 code [WPF], WPF interoperation
- Win32 code [WPF], airspace
- airspace [WPF]
- interoperability [WPF], airspace
- Win32 code [WPF], window regions
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 142973793fd002925bbe2b4b09ce8e6d34553031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="technology-regions-overview"></a>Teknoloji Bölgelerine Genel Bakış
WPF, Win32 ya da DirectX gibi bir uygulama içinde birden çok sunu teknolojileri kullanılıyorsa, ortak bir üst düzey penceresi içinde işleme alanlarını paylaşması gerekir. Bu konu, sunu ve WPF birlikte çalışabilirlik uygulamanız için giriş etkileyebilir sorunları açıklar.  
  
## <a name="regions"></a>Bölgeler  
 Üst düzey bir pencere içinde ("Hava Sahası" olarak da bilinir), kendi bölge birlikte çalışabilirlik uygulama teknolojilerden birine oluşur her HWND olan kavramsallaştırabilirsiniz. Pencere içindeki her piksel o HWND bölge oluşturduğunu tam olarak bir HWND aittir. (NET olarak söylemek var. birden fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsa birden fazla bölge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, ancak bu tartışma amaçları doğrultusunda, yalnızca bir tane kabul edilebilir). Bölge tüm katmanlar veya uygulama ömrü boyunca o piksel işleme girişimi diğer windows aynı işleme düzeyi teknolojisinin bir parçası olması anlamına gelir. İşlenecek çalışırken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pikseller üzerinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] istenmeyen sonuçlara yol açar ve birlikte çalışabilirlik ile mümkün olduğunca izin verilmeyen [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].  
  
### <a name="region-examples"></a>Bölge örnekleri  
 Aşağıdaki çizimde karıştırır uygulamanın gösterir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Her bir teknolojinin kendi ayrı, örtüşmeyen piksel kümesini kullanır ve hiçbir bölge sorunları vardır.  
  
 ![Hava sahası sorunları sahip olmayan bir pencere](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle01.png "MigrationInteropArchitectArticle01")  
  
 Bu uygulama bu üç bölgeleri hiçbirini işlemek için çalışır bir animasyon oluşturmak için fare işaretçisi konumuna kullandığını varsayın. Bu teknoloji, hangi teknoloji animasyon için sorumlu olsun diğer iki bölge ihlal ediyor. Aşağıdaki çizimde bir WPF daire Win32 bölge oluşturma girişimi gösterir.  
  
 ![Birlikte çalışabilirlik diyagramı](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle02.png "MigrationInteropArchitectArticle02")  
  
 Başka bir ihlali saydamlık/alfa farklı teknolojiler arasında karışım kullanmayı deneyin ' dir.  Aşağıdaki çizimde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kutusunu ihlal [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] bölgeleri. Çünkü pikseller [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kutusunu yarı saydam, bunların her ikisi için de ortaklaşa sahibi gerekirdi [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mümkün değildir.  Bu nedenle bu başka bir ihlali ve oluşturulamıyor.  
  
 ![Birlikte çalışabilirlik diyagramı](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle03.png "MigrationInteropArchitectArticle03")  
  
 Önceki üç örnek dikdörtgen bölgeler kullanır, ancak farklı şekillerdeki mümkündür.  Örneğin, bir bölge delik olabilir. Aşağıdaki çizimde gösterildiği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] boyutu budur dikdörtgen delik bölgesiyle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] birleştirilmiş bölgeleri.  
  
 ![Birlikte çalışabilirlik diyagramı](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle04.png "MigrationInteropArchitectArticle04")  
  
 Bölgeleri de tamamen dikdörtgen olmayan olabilir veya tarafından olmayan herhangi bir şekli bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HRGN (bölge).  
  
 ![Birlikte çalışabilirlik diyagramı](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle05.png "MigrationInteropArchitectArticle05")  
  
## <a name="transparency-and-top-level-windows"></a>Saydamlık ve üst düzey Windows  
 Windows penceresi Manager'da yalnızca gerçekten işler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Cwnd'lerden. Bu nedenle, her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND değil. <xref:System.Windows.Window> HWND her HWND için genel kurallar tarafından uymanız gerekir. O HWND içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu ne olursa olsun bütün yapabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] destekler. Ancak masaüstünde diğer Cwnd'lerden ile etkileşim için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tarafından uymanız gerekir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve işleme kurallarına.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Dikdörtgen olmayan windows kullanarak destekler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]— dikdörtgen olmayan windows ve piksel başına alfa için katmanlı windows için HRGN'ler.  
  
 Sabit alfa ve renk anahtarları desteklenmez.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]katmanlı pencere yetenekleri platforma göre değişir.  
  
 Katmanlı windows yapabilir tüm pencereyi yarı saydam (yarı saydam) her piksel penceresinde uygulamak için alfa değeri belirterek.  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aslında piksel başına alfa destekler, ancak bu bu modda, tüm alt çizmek gerekir çünkü pratik programlarda kullanmak oldukça zor HWND kendiniz iletişim kutuları ve bırakmalar dahil olmak üzere).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]HRGN'ler destekler; Ancak, yönetilmeyen [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] bu işlevsellik için. Platform kullanabilirsiniz çağırma ve <xref:System.Windows.Interop.HwndSource> ilgili çağırmak için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Daha fazla bilgi için bkz: [yönetilen koddan yerel işlevleri çağırma](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Katmanlı windows farklı işletim sistemleri üzerinde farklı özelliklere sahiptir. Bunun nedeni, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] işlemek için katmanlı windows öncelikle için tasarlanmış ve [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] işleme değil, [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] işleme.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]üzerinde destekleyen donanım hızlandırılmış katmanlı windows [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] ve daha sonra. Üzerinde donanım hızlandırılmış katmanlı windows [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] desteğine gereksiniminiz [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)], bu yetenekleri sürümüne bağlıdır [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] bu makinede.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]saydamlık renk anahtarlarını desteklemez çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] istediğiniz, özellikle işleme donanım hızlandırılmış olduğu zaman tam renk işlemeyi garanti edemez.  
  
-   Uygulamanızı çalışıyorsa [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)], windows üzerinde katmanlanmış [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] yüzeyleri Titreşim zaman [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] uygulama işler.  (Gerçek işleme dizisi [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] katmanlı pencere sonra gizler [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] çizer ve ardından [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] katmanlı pencereyi geri koyar).  Olmayan[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] katmanlı windows de bu sınırlamaya sahiptir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [İzlenecek yol: Win32'de WPF Saati Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-clock-in-win32.md)  
 [WPF'de Win32 İçeriği Barındırma](../../../../docs/framework/wpf/advanced/hosting-win32-content-in-wpf.md)

---
title: Teknoloji Bölgelerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- window regions [WPF]
- Win32 code [WPF], WPF interoperation
- Win32 code [WPF], airspace
- airspace [WPF]
- interoperability [WPF], airspace
- Win32 code [WPF], window regions
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
ms.openlocfilehash: 978cd428989aa76f82f01711ccfa566b57352f48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695747"
---
# <a name="technology-regions-overview"></a>Teknoloji Bölgelerine Genel Bakış
WPF, Win32 veya DirectX gibi bir uygulamada birden fazla sunu teknolojileri kullanılıyorsa bunların üst düzey bir genel pencere oluşturma alanları paylaşmanız gerekir. Bu konu, sunu ve WPF birlikte çalışabilirlik uygulamanız için giriş etkileyebilir sorunları açıklar.  
  
## <a name="regions"></a>Bölgeleri  
 Üst düzey bir pencere içinde birlikte çalışabilirlik uygulamanın teknolojilerden birine oluşur her HWND ("Hava Sahası" olarak da bilinir) kendi bölgesine sahip kavramsallaştırmak. Her bir pikseli penceresi içinde HWND bölgeyi oluşturan tam olarak bir HWND aittir. (NET olarak söylemek gerekirse, var olan birden fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsa birden fazla bölgeye [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, ancak bu tartışma amacı doğrultusunda, yalnızca bir kabul edilebilir). Bölge, tüm katmanları veya uygulama ömrü boyunca bu piksel işleme girişimi diğer windows aynı işleme düzeyi teknoloji parçası olması anlamına gelir. İşlemeye çalışırken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pikseller üzerinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] istenmeyen sonuçlara yol açar ve birlikte çalışması mümkün olduğunca izin verilmeyen [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].  
  
### <a name="region-examples"></a>Bölge örnekleri  
 Karıştırır bir uygulama aşağıdaki çizimde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Her bir teknolojiyi piksel kendi ayrı, örtüşmeyen kümesi kullanır ve bölge sorun yok.  
  
 ![Hava sahası sorunları sahip olmayan bir pencere](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle01.png "MigrationInteropArchitectArticle01")  
  
 Bu uygulama bu üç bölgelerden birini oluşturma girişiminde bir animasyon oluşturmak için fare işaretçisi konumunu kullandığını varsayalım. Hangi teknoloji animasyon için sorumlu olduğu ne olursa olsun, bu teknoloji diğer iki bölgeyi ihlal ediyor. Aşağıdaki çizimde, bir WPF daire bir Win32 bölge işleme girişimi gösterir.  
  
 ![Birlikte çalışabilirlik diyagramı](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle02.png "MigrationInteropArchitectArticle02")  
  
 Saydamlık/alfa karıştırma farklı teknolojiler arasında kullanmaya çalışırsanız başka bir ihlal eder.  Aşağıdaki çizimde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kutusu ihlal [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] bölgeleri. Çünkü pikseller [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kutusu yarı saydam, bunlar tarafından ortaklaşa ait gerekirdi [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mümkün değildir.  Bu nedenle başka bir ihlal eder ve oluşturulamıyor.  
  
 ![Birlikte çalışabilirlik diyagramı](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle03.png "MigrationInteropArchitectArticle03")  
  
 Önceki üç örnek dikdörtgen bölge kullanılan, ancak farklı şekiller mümkündür.  Örneğin, bir bölgede delik olabilir. Aşağıdaki çizimde gösterildiği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] boyutu budur dikdörtgen delik bölgeyle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] birleştirilmiş bölgeleri.  
  
 ![Birlikte çalışabilirlik diyagramı](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle04.png "MigrationInteropArchitectArticle04")  
  
 Bölgelerin de tamamen dikdörtgensel olabilir ya da tarafından olmayan herhangi bir şekli bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HRGN (bölge).  
  
 ![Birlikte çalışabilirlik diyagramı](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle05.png "MigrationInteropArchitectArticle05")  
  
## <a name="transparency-and-top-level-windows"></a>Saydamlık ve üst düzey Windows  
 Windows penceresi Manager'da yalnızca gerçekten işler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Cwnd'lerden. Bu nedenle, her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> olan bir HWND. <xref:System.Windows.Window> HWND için herhangi bir HWND genel kurallara uymanız gerekir. İçinde bu HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kod ne olursa olsun genel yapabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] destekler. Ancak diğer Cwnd'lerden masaüstü ile etkileşim için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uymalıdır [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve işleme kurallarına.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Dikdörtgen olmayan windows desteklediği [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]— HRGN'ler dikdörtgen olmayan windows ve piksel başına alpha için katmanlı windows.  
  
 Sabit alfa ve renk anahtarları desteklenmiyor.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] katmanlı pencere özellikleri platforma göre değişir.  
  
 Katmanlı windows yapabilir tüm pencere saydam (yarı saydam) penceresinde her piksel uygulamak için bir alfa değeri belirterek.  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aslında piksel başına alfa destekler, ancak bu bu modda, tüm alt çizmek gerekir çünkü pratik programlarda kullanmak oldukça zor HWND kendiniz iletişim kutularını ve açılan menüleri dahil olmak üzere).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HRGN'ler destekler. Ancak, yönetilmeyen [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] bu işlevselliği. Platform kullanabileceğiniz çağırmak ve <xref:System.Windows.Interop.HwndSource> ilgili çağrılacak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Daha fazla bilgi için [yönetilen koddan yerel işlevleri çağırma](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Katmanlı windows, farklı işletim sistemleri üzerinde farklı özelliklere sahip. Bunun nedeni, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] işlemek için katmanlı windows öncelikle için tasarlanmış ve [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] işleme değil [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] işleme.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hızlandırılmış destekleyen donanım üzerinde windows katmanlı [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] ve daha sonra. Donanım hızlandırılmış windows üzerinde katmanlı [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] desteğine gereksiniminiz [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]özellikleri sürümüne bağlıdır. Bu nedenle [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] o makinedeki.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saydamlık rengi anahtarları desteklemez çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] istediğiniz, özellikle Donanım hızlandırmalı işleme olduğu zamanlarda tam renk işlemeyi garanti edemez.  
  
-   Uygulama çalışıyorsa [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)], windows üzerinde katmanlanmış [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] yüzeylerinin olduğunda [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] uygulama oluşturur.  (Gerçek işleme dizisi [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] katmanlı pencerenin ardından gizler [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] çizer, ardından [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] katmanlı pencereyi geri alır).  Olmayan[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] katmanlı windows de bu sınırlamaya sahiptir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
- [İzlenecek yol: Win32'de WPF saati barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-clock-in-win32.md)
- [WPF'de Win32 İçeriği Barındırma](../../../../docs/framework/wpf/advanced/hosting-win32-content-in-wpf.md)

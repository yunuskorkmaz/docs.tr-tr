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
ms.openlocfilehash: e2c93f4471db2d72851a5d5bd8806b59a3e5ee28
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629855"
---
# <a name="technology-regions-overview"></a>Teknoloji Bölgelerine Genel Bakış
WPF, Win32 veya DirectX gibi bir uygulamada birden çok sunum teknolojisi kullanılıyorsa, ortak bir üst düzey pencere içinde işleme alanlarının paylaşılması gerekir. Bu konu, WPF birlikte çalışabilirlik uygulamanızın sunumunu ve girişini etkileyebilecek sorunları açıklar.  
  
## <a name="regions"></a>Regions  
 Üst düzey bir pencerede, birlikte çalışabilirlik uygulamasının teknolojisinden birini oluşturan her bir HWND 'nin kendi bölgesine ("hava sahası" olarak da bilinir) sahip olduğunu kavramaya dönüştürebilirsiniz. Penceredeki her bir piksel, bu HWND 'nin bölgesini oluşturan tam olarak bir HWND 'e aittir. (Kesinlikle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birden çok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND varsa, ancak bu tartışmanın amaçları doğrultusunda, yalnızca bir tane olduğunu varsayabilirsiniz. Bölge, uygulamanın yaşam süresi boyunca o pikselin üzerinde işlemeyi deneyen tüm katmanların veya diğer pencerelerin aynı işleme düzeyi teknolojisinin parçası olması gerektiğini belirtir. Pikselleri, istenmeyen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sonuçlara müşteri [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] adayları üzerinden işlemeye çalışırken, birlikte çalışabilirlik API 'leri aracılığıyla mümkün olduğunca izin verilmez.  
  
### <a name="region-examples"></a>Bölge örnekleri  
 Aşağıdaki çizimde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)],, DirectX ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanan bir uygulama gösterilmektedir. Her teknoloji kendi ayrı, çakışmayan bir piksel kümesini kullanır ve hiçbir bölge sorunu yoktur.  
  
 ![Win32, DirectX ve WPF 'i hedefleyen bir uygulama örneği.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Bu uygulamanın fare işaretçisi konumunu kullandığını ve bu üç bölgenin herhangi biri üzerinde işleme girişiminde bulunan bir animasyon oluşturmasını varsayalım. Animasyonun kendisinden sorumlu olduğu herhangi bir teknolojinin ne olduğuna bakılmaksızın, bu teknoloji diğer iki bölgenin bölgesini ihlal edebilir. Aşağıdaki çizimde, bir Win32 bölgesi üzerinde bir WPF dairesini işleme girişimi gösterilmektedir.  
  
 ![Bir Win32 bölgesi üzerinde bir WPF çemberi işleme girişiminde bulunuldu.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Farklı teknolojiler arasında saydamlık/Alfa karıştırma kullanmayı denerseniz başka bir ihlal vardır.  Aşağıdaki çizimde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kutu, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve DirectX bölgelerini ihlal ediyor. Bu kutudaki pikseller yarı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saydam olduğundan, bunların hem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]DirectX hem de bu mümkün olmayan bir şekilde birlikte bulunması gerekir.  Bu, başka bir ihlalin ve derlenemez.  
  
 ![Win32 ve DirectX bölgelerini ihlal eden bir WPF kutusunu gösteren diyagram.](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 Önceki üç örnek dikdörtgen bölgeleri kullandı, ancak farklı şekiller mümkündür.  Örneğin, bir bölgenin bir deliği olabilir. Aşağıdaki çizimde dikdörtgen delik olan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir bölge gösterilmektedir ve bu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birleştirilmiş ve DirectX bölgelerinin boyutudur.  
  
 ![Bir Win32 bölgesini dikdörtgen delik ile gösteren diyagram.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 Bölgeler Ayrıca tamamen dikdörtgensel olmayan bir şekilde veya bir hrgn (bölge) tarafından [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] herhangi bir şekil olarak belirtilebilir.  
  
 ![Dikdörtgen olmayan bir bölge gösteren diyagram.](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Saydamlık ve üst düzey pencereler  
 Windows 'daki Pencere Yöneticisi yalnızca, HWNDs [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 'yi işler. Bu nedenle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] her <xref:System.Windows.Window> bir HWND 'dir. <xref:System.Windows.Window> HWND tüm HWND 'ler için genel kurallara uymalıdır. Bu HWND içinde kod [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , genel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'lerin desteklediği her şeyi yapabilir. Ancak, masaüstündeki diğer HWND NDS ile etkileşimler için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kuralları [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işleyerek ve işlemek için bir IDE olmalıdır.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], alfasayısal olmayan pencereler için hrgns ve piksel başına Alfa için katmanlı pencereler olan API 'leri kullanarak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dikdörtgen olmayan pencereleri destekler.  
  
 Sabit Alfa ve renk anahtarları desteklenmez.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]katmanlı pencere özellikleri platforma göre farklılık gösterir.  
  
 Katmanlı pencereler, penceredeki her piksele uygulanacak bir alfa değeri belirterek tüm pencereyi yarı saydam (yarı saydam) yapabilir.  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aslında piksel başına Alfa destekler, ancak bu modda iletişim kutuları ve dropler de dahil olmak üzere herhangi bir alt HWND çizmeniz gerekir, ancak pratik programlarda kullanılması çok zordur.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]HRGNs; destekler Ancak, bu işlev için yönetilen API yok. Platform Invoke ' i ve ilgili <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] API 'leri çağırmak için ' i kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen koddan yerel Işlevleri çağırma](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]katmanlı pencerelerin farklı işletim sistemlerinde farklı özellikleri vardır. Bunun nedeni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , oluşturulacak DirectX 'in kullanıldığı ve katmanlı pencerelerin, DirectX işleme değil öncelikle [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] işleme için tasarlanmıştı.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] ve üzeri donanım hızlandırmalı katmanlı pencereleri destekler. Üzerinde [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] donanım hızlandırmalı katmanlı pencereler Microsoft DirectX 'in desteğini gerektirir, bu nedenle yetenekler söz konusu makinedeki Microsoft DirectX sürümüne bağlı olacaktır.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], özellikle işleme donanım hızlandırılmasıyla, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] istediğiniz tam rengi işlemeyi garanti edemediğinden, saydamlık renk tuşlarını desteklemez.  
  
- Uygulamanız üzerinde [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)]çalışıyorsa DirectX yüzeyleri üzerinde katmanlı pencereler DirectX uygulaması tarafından oluşturulduğunda titreşebilir.  (Gerçek işleme sırası [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] katmanlı pencereyi ve ardından DirectX çizmesini ve sonra [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] katmanlı pencereyi geri koyar).  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Katmanlı olmayan pencereler de bu sınırlamaya sahiptir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [İzlenecek yol: Win32 içinde WPF saati barındırma](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [WPF'de Win32 İçeriği Barındırma](hosting-win32-content-in-wpf.md)

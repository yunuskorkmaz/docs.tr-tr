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
ms.openlocfilehash: 0b6ad222737f992da3074770fb5a2bff17860c00
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740299"
---
# <a name="technology-regions-overview"></a>Teknoloji Bölgelerine Genel Bakış
WPF, Win32 veya DirectX gibi bir uygulamada birden çok sunum teknolojisi kullanılıyorsa, ortak bir üst düzey pencere içinde işleme alanlarının paylaşılması gerekir. Bu konu, WPF birlikte çalışabilirlik uygulamanızın sunumunu ve girişini etkileyebilecek sorunları açıklar.  
  
## <a name="regions"></a>Bölgeler  
 Üst düzey bir pencerede, birlikte çalışabilirlik uygulamasının teknolojisinden birini oluşturan her bir HWND 'nin kendi bölgesine ("hava sahası" olarak da bilinir) sahip olduğunu kavramaya dönüştürebilirsiniz. Penceredeki her bir piksel, bu HWND 'nin bölgesini oluşturan tam olarak bir HWND 'e aittir. (Kesinlikle birden çok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND varsa birden fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bölgesi var, ancak bu tartışmanın amaçları doğrultusunda, yalnızca bir tane olduğunu varsayabilirsiniz. Bölge, uygulamanın yaşam süresi boyunca o pikselin üzerinde işlemeyi deneyen tüm katmanların veya diğer pencerelerin aynı işleme düzeyi teknolojisinin parçası olması gerektiğini belirtir. Win32 üzerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] piksel müşteri adayları istenmeyen sonuçlara neden olunmaya çalışıyor ve birlikte çalışabilirlik API 'Leri aracılığıyla mümkün olduğunca izin verilmiyor.  
  
### <a name="region-examples"></a>Bölge örnekleri  
 Aşağıdaki çizimde, Win32, DirectX ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ile ilgili bir uygulama gösterilmektedir. Her teknoloji kendi ayrı, çakışmayan bir piksel kümesini kullanır ve hiçbir bölge sorunu yoktur.  
  
 ![Win32, DirectX ve WPF 'i hedefleyen bir uygulama örneği.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Bu uygulamanın fare işaretçisi konumunu kullandığını ve bu üç bölgenin herhangi biri üzerinde işleme girişiminde bulunan bir animasyon oluşturmasını varsayalım. Animasyonun kendisinden sorumlu olduğu herhangi bir teknolojinin ne olduğuna bakılmaksızın, bu teknoloji diğer iki bölgenin bölgesini ihlal edebilir. Aşağıdaki çizimde, bir Win32 bölgesi üzerinde bir WPF dairesini işleme girişimi gösterilmektedir.  
  
 ![Bir Win32 bölgesi üzerinde bir WPF çemberi işleme girişiminde bulunuldu.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Farklı teknolojiler arasında saydamlık/Alfa karıştırma kullanmayı denerseniz başka bir ihlal vardır.  Aşağıdaki çizimde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kutusu Win32 ve DirectX bölgelerini ihlal ediyor. Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kutusundaki pikseller yarı saydam olduğundan, bu mümkün olmayan hem DirectX hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tarafından ortaklaşa bulunması gerekir.  Bu, başka bir ihlalin ve derlenemez.  
  
 ![Win32 ve DirectX bölgelerini ihlal eden bir WPF kutusunu gösteren diyagram.](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 Önceki üç örnek dikdörtgen bölgeleri kullandı, ancak farklı şekiller mümkündür.  Örneğin, bir bölgenin bir deliği olabilir. Aşağıdaki çizimde dikdörtgen delik olan bir Win32 bölgesi gösterilmektedir ve bu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve DirectX bölgelerinin boyutudur.  
  
 ![Bir Win32 bölgesini dikdörtgen delik ile gösteren diyagram.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 Bölgeler Ayrıca tamamen dikdörtgensel olmayan bir şekilde veya bir Win32 HRGN (bölge) tarafından herhangi bir şekil tarafından bir şekilde oluşturulabilir.  
  
 ![Dikdörtgen olmayan bir bölge gösteren diyagram.](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Saydamlık ve üst düzey pencereler  
 Windows 'daki Pencere Yöneticisi yalnızca Win32 HWNDs 'yi işler. Bu nedenle, her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> bir HWND 'dir. HWND <xref:System.Windows.Window> herhangi bir HWND için genel kurallara uymalıdır. Bu HWND içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kod, genel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'Lerinin desteklediği her şeyi yapabilir. Ancak, masaüstündeki diğer HWND NDS ile etkileşimler için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 işleme ve işleme kuralları tarafından bir IDE olmalıdır.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Win32 API 'Leri kullanarak dikdörtgen olmayan pencereleri destekler — dikdörtgen olmayan pencereler için HRGNs ve piksel başına Alfa için katmanlı pencereler.  
  
 Sabit Alfa ve renk anahtarları desteklenmez.  Win32 katmanlı pencere özellikleri platforma göre farklılık gösterir.  
  
 Katmanlı pencereler, penceredeki her piksele uygulanacak bir alfa değeri belirterek tüm pencereyi yarı saydam (yarı saydam) yapabilir.  (Win32, piksel başına Alfa 'yi destekler, ancak bu modda iletişim kutuları ve açılan bileşenler dahil olmak üzere herhangi bir alt HWND çizmeniz gerekir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HRGNs; destekler Ancak, bu işlev için yönetilen API yok. İlgili Win32 API 'Lerini çağırmak için platform Invoke ve <xref:System.Windows.Interop.HwndSource> kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen koddan yerel Işlevleri çağırma](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] katmanlı pencerelerin farklı işletim sistemlerinde farklı özellikleri vardır. Bunun nedeni, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturmak için DirectX 'i kullanması ve katmanlı pencerelerin öncelikle DirectX işlemesi değil GDI işlemesi için tasarlanmıştı.  
  
- WPF, donanım hızlandırmalı katmanlı pencereleri destekler.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saydamlık renk tuşlarını desteklemez, çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], özellikle işleme donanım hızlandırılandır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [İzlenecek yol: Win32'de WPF Saati Barındırma](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [WPF'de Win32 İçeriği Barındırma](hosting-win32-content-in-wpf.md)

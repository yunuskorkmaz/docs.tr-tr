---
title: WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
ms.openlocfilehash: 93aaa8e21ef483fc21297e29189d86f93fbe138a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327860"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar
Bu konu açıklar nasıl <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi etkileşim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] farklı, ancak benzer, mantıksal bir form veya sayfadaki öğeleri konumlandırma ve boyutlandırma desteği. Karma bir kullanıcı arabirimi (UI) barındıran oluştururken [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi iki Düzen şeması tümleştirir.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>WPF ve Windows Forms arasındaki düzeni farklılıkları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Çözüm bağımsız düzenini kullanır. Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen boyutları kullanarak belirtilen *CİHAZDAN bağımsız piksel*. Bir CİHAZDAN bağımsız piksel bir doksan altıda inç boyutu ve çözümleme bağımsız olduğundan bir 72 dpi İzleyici veya 19.200 DPI yazıcı için işleme bağımsız olarak benzer sonuçlar elde.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca dayanır *dinamik düzen*. Bu, UI öğesi kendisi bir form veya sayfa içeriği ve üst düzen kapsayıcısının kullanılabilir ekran boyutuna göre düzenler, anlamına gelir. Dinamik düzen, içerdikleri dizelerin uzunluğu değiştiğinde otomatik olarak kullanıcı Arabirimi öğeleri konumunu ve boyutunu ayarlayarak yerelleştirme kolaylaştırır.  
  
 Düzende [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] cihaza bağlı ve statik olması olasılığı. Genellikle, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri konumlandırıldığı kesinlikle donanım piksel cinsinden belirtilen boyutları kullanarak bir form üzerinde. Ancak, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aşağıdaki tabloda özetlendiği gibi bazı dinamik düzen özelliklerini destekler.  
  
|Düzen özelliği|Açıklama|  
|--------------------|-----------------|  
|Otomatik boyutlandırma|Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kendilerini içeriklerini düzgün görüntülenmesi için denetimleri yeniden boyutlandırma. Daha fazla bilgi için [AutoSize özelliğine genel bakış](../../winforms/controls/autosize-property-overview.md).|  
|Sabitleme ve yerleştirme|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri konumlandırma ve boyutlandırma üst kapsayıcı tabanlı destekler. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Otomatik ölçeklendirme|Kapsayıcı denetimleri, kendileri ve alt öğelerini çıktı cihazına veya piksel cinsinden varsayılan kapsayıcı yazı tipi boyutu çözünürlüğüne göre yeniden boyutlandırın. Daha fazla bilgi için [Windows Forms'ta otomatik ölçeklendirme](../../winforms/automatic-scaling-in-windows-forms.md).|  
|Düzen kapsayıcıları|<xref:System.Windows.Forms.FlowLayoutPanel> Ve <xref:System.Windows.Forms.TableLayoutPanel> denetimleri, alt denetimlerini düzenlemek ve kendilerini içeriklerine göre boyutu.|  
  
## <a name="layout-limitations"></a>Düzen sınırlamaları  
 Genel olarak, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ölçeği ve mümkün ölçülere [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Bilinen sınırlamalar aşağıdaki listede açıklanmaktadır, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi çalışır, barındırılan bir tümleştirme [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] içine denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi.  
  
-   Bazı durumlarda, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri yeniden boyutlandırılamaz ya da yalnızca belirli boyutlara yeniden boyutlandırılabilir. Örneğin, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> denetimi, denetimin yazı tipi boyutu tarafından tanımlanan yalnızca tek bir yüksekliği destekler. İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nerede öğeleri esnetme dikey olarak barındırılan dinamik düzen <xref:System.Windows.Forms.ComboBox> beklendiği gibi denetimi uzamaz.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri Döndürülmüş veya dengesiz. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi başlatır <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> eğme veya döndürme dönüşümü uygularsanız olay. İşlememek varsa <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olay, bir <xref:System.InvalidOperationException> tetiklenir.  
  
-   Çoğu durumda [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerin orantılı ölçeklendirme desteklemez. Denetim genel boyutlarını ölçeklendirilmesine rağmen alt denetimler ve denetim bileşen öğeleri beklenen şekilde yeniden boyutlandırılabilir değil. Bu sınırlama her ne kadar iyi bağlıdır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi, ölçeklendirmeyi destekler. Ayrıca, Ölçek genişletilemiyor [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 0 piksel boyutlu aşağı denetimleri.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri form otomatik olarak kendisini ve yazı tipi boyutunu temel alan denetimlerini yeniden otomatik ölçeklendirmeyi destekler. İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi boyutunu değiştirme, kullanıcı arabirimi olmayan yeniden boyutlandırma tüm düzeni tek tek öğeleri dinamik olarak yeniden boyutlandırılabilir ancak.  
  
### <a name="z-order"></a>Z düzeni  
 İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıcı arabirimi, çakışan davranışı denetlemek için öğelerin z düzenini değiştirebilirsiniz. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi üst kısmındaki her zaman çizilen için ayrı bir HWND çizilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri.  
  
 Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi ayrıca çizilir herhangi üzerine <xref:System.Windows.Documents.Adorner> öğeleri.  
  
## <a name="layout-behavior"></a>Düzen davranışı  
 Barındırırken belirli yönlerini düzen davranışı aşağıdaki bölümlerde açıklanmaktadır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Ölçeklendirme, birim dönüştürme ve cihaz bağımsızlığı  
 Her <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi ilgili işlemler gerçekleştirdiğinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] boyutları için iki koordinat sistemi söz konusu: CİHAZDAN bağımsız piksel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve donanım piksel [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Bu nedenle, tutarlı bir düzen elde etmek için uygun birim ve ölçeklendirme dönüştürmeleri uygulamanız gerekir.  
  
 Koordinat sistemleri arasında dönüştürme bağlı geçerli cihaz çözünürlüğü ve herhangi bir düzeni veya uygulanan dönüştürmeler işleme <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi veya alt öğelerinden.  
  
 Çıktı cihazına 96 DPI olduğundan ve hiçbir ölçeklendirme uygulandıktan <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, bir CİHAZDAN bağımsız piksel bir donanım piksel eşit.  
  
 Diğer tüm durumlarda, koordinat sistemini ölçeklendirme gerektirir. Barındırılan denetimi yeniden boyutlandırıldı değil. Bunun yerine, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini denetimden ve tüm alt öğe denetimlerini ölçeklendirme dener. Çünkü [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ölçeklendirme, tam desteklemez <xref:System.Windows.Forms.Integration.WindowsFormsHost> belirli denetimler tarafından desteklenen derecede öğesi ölçeklendirir.  
  
 Geçersiz kılma <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> barındırılan Windows Forms denetimi için özel bir ölçeklendirme davranışına sağlamak için yöntemi.  
  
 Ölçeklendirme, ek olarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, yuvarlama ve taşma durumlarını aşağıdaki tabloda açıklandığı gibi işler.  
  
|Dönüştürme sorunu|Açıklama|  
|----------------------|-----------------|  
|Yuvarlama|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] CİHAZDAN bağımsız piksel boyutları olarak belirtilen `double`, ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] donanım piksel boyutları olarak belirtilen `int`. Durumlarda burada `double`-tabanlı boyutlara dönüştürülür `int`-boyutları, alan <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini kullanan standart yuvarlama, böylece 0 olarak 0,5'den küçük kesirli değer yuvarlanır.|  
|taşma|Zaman <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi dönüştürür gelen `double` değerler `int` değerleri taşma mümkündür. Daha büyük olan değerleri <xref:System.Int32.MaxValue> ayarlandığından <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Düzen ilgili Özellikler  
 Düzen davranışını denetleyen özellikler [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri tarafından uygun şekilde eşlendi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi. Daha fazla bilgi için [Windows Forms ve WPF özelliğini eşleme](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Düzen değişiklikleri barındırılan denetim  
 Düzen değişiklikleri barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim yayılır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Düzen güncelleştirmeleri tetiklemek için. <xref:System.Windows.UIElement.InvalidateMeasure%2A> Metodunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimden düzen değişiklikleri neden olduğunu sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çalıştırmak için yerleşim altyapısı.  
  
### <a name="continuously-sized-windows-forms-controls"></a>Windows Forms denetimlerini sürekli olarak boyutu  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sürekli tam olarak ölçeklendirmeyi destekleyen denetimleri etkileşimde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesini kullanan <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> zamanki boyut ve barındırılan düzenlemek için yöntemleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.  
  
### <a name="sizing-algorithm"></a>Boyutlandırma algoritması  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesini denetimden boyutlandırmak için aşağıdaki yordamı kullanır:  
  
1. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesini geçersiz kılar <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemleri.  
  
2. Barındırılan denetimin boyutunu belirlemek için <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemini çağırır barındırılan denetimin <xref:System.Windows.Forms.Control.GetPreferredSize%2A> kısıtlamasına sahip yöntemi çevrilmiş geçirilen kısıtlaması gelen <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemi.  
  
3. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> Yöntem çalışır denetimden verilen boyuta kısıtlama olarak ayarlanacak.  
  
4. Varsa barındırılan denetimin <xref:System.Windows.Forms.Control.Size%2A> özelliği eşleşen belirtilen sınırlama, barındırılan denetim kısıtlaması için boyutlandırılır.  
  
 Varsa <xref:System.Windows.Forms.Control.Size%2A> özellik belirtilen sınırlama eşleşmiyor, barındırılan denetim sürekli boyutlandırma desteklemez. Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetimi yalnızca ayrık boyutları sağlar. Bu denetim için izin verilen boyutları (ay sayısını temsil eden) tamsayılar, yükseklik ve genişlik için oluşur. Bu gibi durumlarda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi aşağıdaki gibi davranır:  
  
-   Varsa <xref:System.Windows.Forms.Control.Size%2A> özelliği belirtilen sınırlama, daha büyük boyutu döndürür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini denetimden kırpar. Yükseklik ve genişlik denetimden herhangi bir yönde kırpılmış için ayrı ayrı işlenir.  
  
-   Varsa <xref:System.Windows.Forms.Control.Size%2A> özelliği belirtilen sınırlama, daha küçük bir boyuttan döndürür <xref:System.Windows.Forms.Integration.WindowsFormsHost> bu boyut değerini kabul eder ve değeri döndürür [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [İzlenecek yol: WPF’de Windows Forms Denetimlerini Düzenleme](walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [Düzenleme Windows Forms denetimleri örneği](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)
- [Geçiş ve Birlikte Çalışabilirlik](migration-and-interoperability.md)

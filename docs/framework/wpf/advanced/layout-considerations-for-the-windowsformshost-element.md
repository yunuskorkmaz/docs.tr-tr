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
ms.openlocfilehash: 786e3adae6c5b8167fbba00aa140d4d728308dc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar
Bu konuda açıklanmaktadır nasıl <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi etkileşime [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] boyutlandırma ve bir form veya sayfa üzerinde öğeleri konumlandırma için farklı fakat benzer bir mantığı destekler. Karma kullanıcı arabirimini (UI) barındıran oluşturduğunuzda [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi iki Düzen şeması tümleştirir.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>WPF ve Windows Forms arasındaki Düzen farkları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Çözümleme bağımsız düzenini kullanır. Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen boyutları kullanarak belirtilen *aygıttan bağımsız piksel*. CİHAZDAN bağımsız piksel bir doksan altıncı inç boyutu ve çözümleme bağımsız olduğundan, 72 DPI İzleyici veya 19.200 DPI yazıcıya işleme bağımsız olarak benzer sonuçlar elde.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca dayanır *dinamik düzen*. Bu, bir kullanıcı Arabirimi öğesi kendisini bir form veya sayfa içeriğini, üst düzen kapsayıcısına ve kullanılabilir ekran boyutuna göre düzenler olduğunu anlamına gelir. Dinamik düzen içerdikleri dizeler uzunluğu değiştirdiğinde otomatik olarak kullanıcı Arabirimi öğeleri konumunu ve boyutunu ayarlayarak yerelleştirme kolaylaştırır.  
  
 Düzende [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aygıta bağımlı ve büyük olasılıkla statik olarak. Genellikle, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri konumlandırıldığı kesinlikle donanım piksel cinsinden belirtilen boyutlar kullanılarak bir form üzerinde. Ancak, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bazı dinamik düzen özellikler aşağıdaki tabloda özetlendiği gibi desteklemiyor.  
  
|Düzeni özelliği|Açıklama|  
|--------------------|-----------------|  
|Otomatik boyutlandırma|Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri kendilerini içeriklerini düzgün görüntülemek için yeniden boyutlandırın. Daha fazla bilgi için bkz: [AutoSize özelliğine genel bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md).|  
|Sabitleme ve yerleştirme|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri konumlandırma ve üst kapsayıcı dayalı boyutlandırma destekler. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Otomatik ölçeklendirme|Kapsayıcı denetimleri kendilerini ve çıktı aygıtı veya piksel cinsinden varsayılan kapsayıcı yazı tipi boyutu çözümlenmesi göre bunların alt öğeleri yeniden boyutlandırın. Daha fazla bilgi için bkz: [otomatik ölçeklendirmeyi Windows Forms'ta](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md).|  
|Düzen kapsayıcıları|<xref:System.Windows.Forms.FlowLayoutPanel> Ve <xref:System.Windows.Forms.TableLayoutPanel> denetimleri kendi alt denetimleri düzenlemek ve kendilerini içeriklerini göre boyutu.|  
  
## <a name="layout-limitations"></a>Düzen sınırlamaları  
 Genel olarak, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ölçeklendirilebilir ve mümkün ölçülere [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aşağıdaki listede bilinen sınırlamaları açıklar olduğunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi çalışır barındırılan tümleştirmek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] içine denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi.  
  
-   Bazı durumlarda, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri yeniden boyutlandırılamaz ya da yalnızca belirli boyutlara boyutlandırılabilir. Örneğin, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> denetimi denetimin yazı tipi boyutu tarafından tanımlanan yalnızca tek bir yüksekliği destekler. İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] burada öğeleri uzatma dikey olarak barındırılan dinamik düzen <xref:System.Windows.Forms.ComboBox> denetimi beklendiği gibi uzamaz.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri Döndürülmüş veya eğri. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi başlatır <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> eğme veya döndürme dönüşümü uyguladığınızda olay. Değil işlemek, <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olay, bir <xref:System.InvalidOperationException> tetiklenir.  
  
-   Çoğu durumda, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri orantılı ölçeklendirmeyi desteklemez. Denetimin genel boyutlarının ölçeklendirilmesine rağmen alt denetimleri ve bileşen öğeleri denetiminin beklendiği gibi yeniden boyutlandırılabilir değil. Bu sınırlama ne kadar iyi her bağlıdır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi, ölçeklendirmeyi destekler. Ayrıca, ölçekleme olamaz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri 0 piksel boyutunun aşağı kaydırın.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri form otomatik olarak kendisini ve yazı tipi boyutuna bağlı denetimlerini yeniden otomatik ölçeklendirmeyi destekler. İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıcı arabirimi, yazı tipi boyutunu değiştirme değil yeniden boyutlandırma tüm düzeni ayrı ayrı öğeler dinamik olarak yeniden boyutlandırma ancak.  
  
### <a name="z-order"></a>Z düzeni  
 İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıcı arabirimi öğelerinin z düzenini çakışan davranışı denetlemek için değiştirebilirsiniz. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi, ayrı bir HWND içinde çizilir, her zaman üstünde çizilir nedenle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri.  
  
 Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi de çizilir herhangi üstünde <xref:System.Windows.Documents.Adorner> öğeleri.  
  
## <a name="layout-behavior"></a>Düzen davranışı  
 Aşağıdaki düzen davranışının belirli yönlerini barındırdığında bölümlerde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Ölçeklendirme, birim dönüştürme ve cihaz bağımsızlığı  
 Her <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi ilgili işlemler gerçekleştirdiğinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] boyutları, iki koordinat sistemi söz konusu: aygıttan bağımsız piksel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve donanım piksel [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Bu nedenle, tutarlı bir yerleşim elde etmek için uygun birim ve ölçeklendirme dönüşümlerini uygulamanız gerekir.  
  
 Koordinat sistemleri arasında dönüştürme bağımlıdır geçerli aygıt çözünürlüğü ve herhangi bir düzeni veya uygulanan Dönüşümlerin işleme <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi veya alt öğelerinden.  
  
 Çıktı aygıtı 96 DPI'de olması ve hiçbir ölçeklendirme uygulandıktan <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, bir CİHAZDAN bağımsız piksel bir donanım piksel eşit.  
  
 Diğer tüm durumlarda koordinat sistemi ölçeklendirmesini gerektirir. Barındırılan denetim yeniden boyutlandırıldı değil. Bunun yerine, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetim ve tüm alt denetimlerindeki ölçekleme dener. Çünkü [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ölçeklendirme, tam olarak desteklemez <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi ölçeklendirir belirli denetimler tarafından desteklenen derecede.  
  
 Geçersiz kılma <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> barındırılan Windows Forms denetimi için özel ölçeklendirme davranışı sağlamak için yöntem.  
  
 Ölçeklendirme, ek olarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi aşağıdaki tabloda açıklandığı gibi yuvarlama ve taşma durumlarını işler.  
  
|Dönüştürme sorunu|Açıklama|  
|----------------------|-----------------|  
|Yuvarlama|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] CİHAZDAN bağımsız piksel boyutları olarak belirtilen `double`, ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] donanım piksel boyutları olarak belirtilen `int`. Durumlarda nerede `double`-tabanlı boyutlara dönüştürüldüğü `int`-boyutları, temel <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi standart yuvarlama kullanır, böylece 0,5'den az olan kesirli değerlerin 0 aşağı yuvarlanmasını.|  
|Taşma|Zaman <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi dönüştürür `double` değerler `int` değerleri taşma mümkündür. Daha büyük olan değerleri <xref:System.Int32.MaxValue> ayarlanır <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Düzen ilgili Özellikler  
 İçindeki düzen davranışını denetleyen özellikler [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri tarafından uygun şekilde eşleştirilir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi. Daha fazla bilgi için bkz: [Windows Forms ve WPF özellik eşlemesi](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Barındırılan denetimde düzen değişiklikleri  
 Düzen değişiklikleri barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim yayılır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Düzen güncelleştirmelerini tetiklemek için. <xref:System.Windows.UIElement.InvalidateMeasure%2A> Yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimden düzen değişiklikleri neden sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çalıştırmak için yerleşim altyapısı.  
  
### <a name="continuously-sized-windows-forms-controls"></a>Sürekli olarak boyutlandırılan Windows Forms denetimleri  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sürekli tam olarak ölçeklendirmeyi destekleyen denetimleri etkileşimde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesini kullanan <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> her zamanki gibi boyutlandırmak ve barındırılan düzenlemek için yöntemleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.  
  
### <a name="sizing-algorithm"></a>Boyutlandırma algoritması  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi barındırılan denetimi boyutlandırmak için aşağıdaki yordamı kullanır:  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi geçersiz kılmaları <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemleri.  
  
2.  Barındırılan denetime boyutunu belirlemek için <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemini çağırır barındırılan denetimin <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemi kısıtlamasına sahip çevrilen geçirilen kısıtlaması gelen <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemi.  
  
3.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> Yöntemi, barındırılan denetimi verilen boyut kısıtlamasına ayarlamaya çalışır.  
  
4.  Varsa barındırılan denetimin <xref:System.Windows.Forms.Control.Size%2A> özelliği eşleşen belirtilen sınırlama, barındırılan denetim kısıtlamaya boyutlandırılır.  
  
 Varsa <xref:System.Windows.Forms.Control.Size%2A> özelliği, belirtilen sınırlama eşleşmiyor, barındırılan denetim sürekli boyutlandırmayı desteklemez. Örneğin, <xref:System.Windows.Forms.MonthCalendar> yalnızca ayrı boyutlara izin verir. Bu denetim için izin verilen boyutlar, yükseklik ve genişlik için tamsayılardan (ay sayısını temsil eden) oluşur. Bu gibi durumlarda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi aşağıdaki gibi davranır:  
  
-   Varsa <xref:System.Windows.Forms.Control.Size%2A> özelliği döndürür belirtilen sınırlama daha büyük boyutu <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi kırpar. Barındırılan denetim herhangi bir yönde kırpılmış gibi şekilde yükseklik ve genişlik ayrı ayrı işlenir.  
  
-   Varsa <xref:System.Windows.Forms.Control.Size%2A> özelliği döndürür belirtilen sınırlama daha küçük bir boyut <xref:System.Windows.Forms.Integration.WindowsFormsHost> bu boyut değerini kabul eder ve değerine döndürür [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)  
 [WPF örnek Forms denetimlerini pencereleri düzenleme](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Windows Forms ve WPF Özelliğini Eşleme](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)

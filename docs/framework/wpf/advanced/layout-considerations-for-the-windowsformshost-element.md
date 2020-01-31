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
ms.openlocfilehash: 9f97639447284b792d52cf4aa25b81f584d7291a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787899"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar
Bu konu, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemiyle nasıl etkileşime gireceğini açıklar.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve Windows Forms, bir form veya sayfadaki öğelerin boyutlandırılmasına ve konumlandırılmasına yönelik farklı, ancak benzer mantığı destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows Forms denetimleri barındıran bir karma Kullanıcı arabirimi (UI) oluşturduğunuzda, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi iki düzen şemasını tümleştirir.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>WPF ve Windows Forms arasındaki düzende farklılıklar  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çözünürlükten bağımsız düzen kullanır. Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeni boyutları *cihazdan bağımsız pikseller*kullanılarak belirtilir. Cihazdan bağımsız bir piksel, boyutun ve çözünürlükten bağımsız olarak inç bir dokun altılarından biridir, bu nedenle 72 dpi bir monitöre veya 19.200 dpi bir yazıcıda işleme yapıp olmadığına bakılmaksızın benzer sonuçlar elde edersiniz.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], *dinamik düzene*de dayalıdır. Bu, bir kullanıcı arabirimi öğesinin kendisini içeriğe, üst düzen kapsayıcısına ve kullanılabilir ekran boyutuna göre bir form veya sayfaya göre düzenler. Dinamik düzen, Kullanıcı arabirimi öğelerinin boyutunu ve konumunu, içerdikleri dizeler değişiklik uzunluğuna göre otomatik olarak ayarlayarak yerelleştirmeyi kolaylaştırır.  
  
 Windows Forms düzen cihaza bağımlıdır ve daha büyük olasılıkla statiktir. Genellikle Windows Forms denetimleri, donanım piksellerinde belirtilen boyutları kullanarak bir form üzerinde kesinlikle konumlandırılır. Ancak Windows Forms, aşağıdaki tabloda özetlenen bazı dinamik düzen özelliklerini destekler.  
  
|Düzen özelliği|Açıklama|  
|--------------------|-----------------|  
|Otomatik boyutlandırma|Bazı Windows Forms denetimleri, içeriklerinin düzgün şekilde görüntülenmesini sağlamak için kendilerini yeniden boyutlandırır. Daha fazla bilgi için bkz. [AutoSize özelliğine genel bakış](../../winforms/controls/autosize-property-overview.md).|  
|Sabitleme ve yerleştirme|Windows Forms denetimleri üst kapsayıcıya göre konumlandırmayı ve boyutlandırmayı destekler. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Otomatik ölçeklendirme|Kapsayıcı denetimleri, çıkış cihazının çözümüne veya varsayılan kapsayıcı yazı tipinin piksel cinsinden boyutuna bağlı olarak kendilerini ve alt öğelerini yeniden boyutlandırır. Daha fazla bilgi için bkz. [Windows Forms otomatik ölçeklendirme](../../winforms/automatic-scaling-in-windows-forms.md).|  
|Düzen kapsayıcıları|<xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel> denetimleri, kendi alt denetimlerini ve boyutlarını kendi içeriklerine göre düzenler.|  
  
## <a name="layout-limitations"></a>Düzen sınırlamaları  
 Genel olarak, Windows Forms denetimleri ölçeklendirilmez ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]mümkün olan ölçüde dönüştürülemez. Aşağıdaki listede <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan Windows Forms denetimini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemiyle tümleştirmeyi denediğinde oluşan bilinen sınırlamaları açıklar.  
  
- Bazı durumlarda Windows Forms denetimleri yeniden boyutlandırılamaz veya yalnızca belirli boyutlara boyutlandırılabilir. Örneğin, bir Windows Forms <xref:System.Windows.Forms.ComboBox> denetimi yalnızca denetimin yazı tipi boyutu tarafından tanımlanan tek bir yüksekliği destekler. Öğelerin dikey olarak uzatılabileceği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dinamik bir düzende, barındırılan bir <xref:System.Windows.Forms.ComboBox> denetimi beklendiği gibi uzatılacaktır.  
  
- Windows Forms denetimleri döndürülemiyor veya eğilemez. <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, bir eğme veya döndürme dönüştürmesi uyguladığınızda <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olayını oluşturur. <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olayını işlemeyin, bir <xref:System.InvalidOperationException> tetiklenir.  
  
- Çoğu durumda Windows Forms denetimleri orantılı ölçeklendirmeyi desteklemez. Denetimin genel boyutları ölçeklense de, denetimin alt denetimleri ve bileşen öğeleri beklenen şekilde yeniden boyutlandırmayabilir. Bu sınırlama, her bir Windows Forms denetiminin ölçeklendirmeyi ne kadar iyi desteklediğine bağlıdır. Ayrıca, Windows Forms denetimlerini 0 piksel boyutuna ölçeklendiremezsiniz.  
  
- Windows Forms denetimler otomatik ölçeklendirmeyi destekler, bu da formun kendisini ve denetimlerini yazı tipi boyutuna göre otomatik olarak yeniden boyutlandıracaktır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir kullanıcı arabiriminde, tek tek öğeler dinamik olarak yeniden boyutlandırabilse de yazı tipi boyutunun değiştirilmesi tüm düzeni yeniden boyutlandıramaz.  
  
### <a name="z-order"></a>Z düzeni  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir kullanıcı arabiriminde, örtüşen davranışı denetlemek için öğelerin z sırasını değiştirebilirsiniz. Barındırılan bir Windows Forms denetimi ayrı bir HWND içinde çizilir, bu nedenle her zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerin üzerine çizilir.  
  
 Barındırılan bir Windows Forms denetimi Ayrıca herhangi bir <xref:System.Windows.Documents.Adorner> öğesinin üzerine çizilir.  
  
## <a name="layout-behavior"></a>Düzen davranışı  
 Aşağıdaki bölümlerde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows Forms denetimleri barındırırken düzen davranışının belirli yönleri açıklanır.  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Ölçeklendirme, birim dönüştürme ve cihaz bağımsızlık  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve Windows Forms boyutlarla ilgili işlemler gerçekleştirdiğinde, iki koordinat sistemi vardır: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için cihazdan bağımsız pikseller ve Windows Forms için donanım pikselleri. Bu nedenle, tutarlı bir düzen elde etmek için uygun birim ve ölçekleme dönüştürmeleri uygulamanız gerekir.  
  
 Koordinat sistemleri arasında dönüştürme, geçerli cihaz çözünürlüğüne ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesine veya alt öğelerinden uygulanan herhangi bir düzen veya işleme dönüştürmelerine bağlıdır.  
  
 Çıkış cihazı 96 DPI ise ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesine hiçbir ölçeklendirme uygulanmışsa, cihazdan bağımsız bir piksel bir donanım pikseline eşittir.  
  
 Diğer tüm durumlar için koordinat sistemi Ölçeklendirmesi gerekir. Barındırılan denetim yeniden boyutlandırılmaz. Bunun yerine <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi ve onun tüm alt denetimlerini ölçeklendirmeye çalışır. Windows Forms ölçeklendirmeyi tam olarak desteklemediğinden, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi belirli denetimler tarafından desteklenen dereceye ölçeklendirir.  
  
 Barındırılan Windows Forms denetimi için özel ölçeklendirme davranışı sağlamak üzere <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> yöntemini geçersiz kılın.  
  
 Ölçeklendirmeye ek olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi aşağıdaki tabloda açıklandığı gibi yuvarlama ve taşma durumlarını işler.  
  
|Dönüştürme sorunu|Açıklama|  
|----------------------|-----------------|  
|Ondalı|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cihazdan bağımsız piksel boyutları `double`olarak belirtilir ve Windows Forms donanım piksel boyutları `int`olarak belirtilir. `double`tabanlı boyutların `int`tabanlı boyutlara dönüştürüldüğü durumlarda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi standart yuvarlama kullanır, böylece 0,5 'den küçük kesirli değerler 0 ' a yuvarlanır.|  
|Taşma|<xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi `double` değerlerinden `int` değerlere dönüştürdüğünde, taşma olasılığı vardır. <xref:System.Int32.MaxValue> daha büyük değerler <xref:System.Int32.MaxValue>olarak ayarlanır.|  
  
### <a name="layout-related-properties"></a>Düzenle ilgili özellikler  
 Windows Forms Denetimlerinde ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerindeki düzen davranışını denetleyen özellikler <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi tarafından uygun şekilde eşlenir. Daha fazla bilgi için bkz. [Windows Forms ve WPF özellik eşleme](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Barındırılan denetimdeki düzen değişiklikleri  
 Barındırılan Windows Forms denetimindeki düzen değişiklikleri tetiklenecek düzen güncelleştirmelerine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dağıtılır. <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.UIElement.InvalidateMeasure%2A> yöntemi, barındırılan denetimdeki düzen değişikliklerinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen altyapısının çalışmasına neden olur.  
  
### <a name="continuously-sized-windows-forms-controls"></a>Sürekli boyutlandırılmış Windows Forms denetimleri  
 Sürekli ölçeklendirmeyi destekleyen Windows Forms denetimleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemiyle tamamen etkileşime geçin. <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, barındırılan Windows Forms denetimi her zamanki gibi <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemlerini kullanır.  
  
### <a name="sizing-algorithm"></a>Boyutlandırma algoritması  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimin boyutunu almak için aşağıdaki yordamı kullanır:  
  
1. <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemlerini geçersiz kılar.  
  
2. Barındırılan denetimin boyutunu öğrenmek için <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemi, barındırılan denetimin <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemini <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metoduna geçirilen kısıtlamadan çevrilmiş bir kısıtlamayla çağırır.  
  
3. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemi, barındırılan denetimi verilen boyut kısıtlamasına ayarlamaya çalışır.  
  
4. Barındırılan denetimin <xref:System.Windows.Forms.Control.Size%2A> özelliği belirtilen kısıtlamayla eşleşiyorsa, barındırılan denetim kısıtlamaya boyutlandırılır.  
  
 <xref:System.Windows.Forms.Control.Size%2A> özelliği belirtilen kısıtlamayla eşleşmezse, barındırılan denetim sürekli boyutlandırmayı desteklemez. Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetimi yalnızca ayrı boyutlara izin verir. Bu denetim için izin verilen boyutlar, hem yükseklik hem genişlik için tamsayıların (ay sayısını temsil eder) oluşur. Bu gibi durumlarda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi aşağıdaki gibi davranır:  
  
- <xref:System.Windows.Forms.Control.Size%2A> özelliği belirtilen kısıtlamadan daha büyük bir boyut döndürürse, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi kırpar. Yükseklik ve genişlik ayrı olarak işlenir, bu nedenle barındırılan denetim her iki yönde de kırpılabilir.  
  
- <xref:System.Windows.Forms.Control.Size%2A> özelliği belirtilen kısıtlamadan daha küçük bir boyut döndürürse, <xref:System.Windows.Forms.Integration.WindowsFormsHost> bu boyut değerini kabul eder ve değeri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Düzen sistemine döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme](walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [WPF örneğindeki Windows Forms denetimlerini düzenleme](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)
- [Geçiş ve Birlikte Çalışabilirlik](migration-and-interoperability.md)

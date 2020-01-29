---
title: WPF ve Windows Forms birlikte çalışabilirliği
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 2dc2ea10ce8f723a0ee34c4774253e1357ba6afa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735125"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF ve Windows Forms Birlikte Çalışması
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], uygulama arabirimleri oluşturmak için iki farklı mimaride bulunabilir. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> ad alanı, ortak birlikte çalışma senaryolarını etkinleştiren sınıflar sağlar. Birlikte çalışabilirlik özelliklerini uygulayan iki temel sınıf <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost>. Bu konu, hangi birlikte çalışma senaryolarının desteklendiğini ve hangi senaryoların desteklenmediğini açıklar.  
  
> [!NOTE]
> *Karma denetim* senaryosuna özel bir değerlendirme verilmiştir. Karma denetim, diğer teknolojideki bir denetimde iç içe yerleştirilmiş bir teknolojiden denetim içerir. Buna *iç içe geçmiş birlikte çalışabilirlik*da denir. Çok *düzeyli karma denetim* , birden fazla karma denetim iç içe geçme düzeyine sahiptir. Bir çok düzeyli iç içe geçme örneği, başka bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi içeren bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi içeren [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimidir. Çok düzeyli karma denetimler desteklenmez.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>WPF Windows Forms denetimleri barındırma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi bir Windows Forms denetimi barındırıyorsa, aşağıdaki birlikte çalışabilirlik senaryoları desteklenir:  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi XAML kullanarak bir veya daha fazla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimini barındıramayabilir.  
  
- Kodu kullanarak bir veya daha fazla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimini barındıramayabilir.  
  
- Diğer [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri içeren [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kapsayıcı denetimlerini barındıramayabilir.  
  
- Ana/ayrıntı formunu bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ana ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayrıntıları ile barındırabilir.  
  
- Ana/ayrıntı formunu bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ana ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntıları ile barındırabilir.  
  
- Bir veya daha fazla ActiveX denetimini barındıramayabilir.  
  
- Bir veya daha fazla bileşik denetimi barındıramayabilir.  
  
- Karma denetimleri [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]kullanarak barındırabilir.  
  
- Kod kullanarak karma denetimleri barındıramayabilir.  
  
### <a name="layout-support"></a>Düzen desteği  
 Aşağıdaki listede <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemiyle tümleştirmeyi denediğinde oluşan bilinen sınırlamaları açıklar.  
  
- Bazı durumlarda [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri yeniden boyutlandırılamaz veya yalnızca belirli boyutlara boyutlandırılabilir. Örneğin, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> denetimi yalnızca denetimin yazı tipi boyutu tarafından tanımlanan tek bir yüksekliği destekler. Öğelerin dikey olarak uzatılabileceği varsayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dinamik bir düzende, barındırılan bir <xref:System.Windows.Forms.ComboBox> denetimi beklendiği gibi uzamaz.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri döndürülemiyor veya eğilemez. Örneğin, Kullanıcı arabiriminizi 90 derece döndürdüğünüzde barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri, sağ üst konumlarını korur.  
  
- Çoğu durumda [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri orantılı ölçeklendirmeyi desteklemez. Denetimin genel boyutları ölçeklense de, denetimin alt denetimleri ve bileşen öğeleri beklenen şekilde yeniden boyutlandırmayabilir. Bu sınırlama, her bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminin ölçeklendirmeyi ne kadar iyi desteklediğine bağlıdır.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir kullanıcı arabiriminde, örtüşen davranışı denetlemek için öğelerin z sırasını değiştirebilirsiniz. Barındırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi ayrı bir HWND içinde çizilir, bu nedenle her zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerin üzerine çizilir.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri, yazı tipi boyutuna bağlı olarak otomatik ölçeklendirmeyi destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir kullanıcı arabiriminde, tek tek öğeler dinamik olarak yeniden boyutlandırabilse de yazı tipi boyutunun değiştirilmesi tüm düzeni yeniden boyutlandıramaz.  
  
### <a name="ambient-properties"></a>Çevresel Özellikler  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerinin çevresel özelliklerinden bazılarının [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğerleri vardır. Bu çevresel özellikler barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerine yayılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminde ortak özellikler olarak sunulur. <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi her bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ambient özelliğini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğerine çevirir.  
  
 Daha fazla bilgi için bkz. [Windows Forms ve WPF özellik eşleme](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda birlikte çalışabilirlik davranışı açıklanmaktadır.  
  
|Davranış|Desteklenir|Desteklenmez|  
|--------------|---------------|-------------------|  
|Saydamlık|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim işleme saydamlığı destekler. Üst [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminin arka planı barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinin arka planı haline gelebilir.|Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri saydamlığı desteklemez. Örneğin, <xref:System.Windows.Forms.TextBox> ve <xref:System.Windows.Forms.ComboBox> denetimleri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tarafından barındırıldığı zaman saydam olmayacaktır.|  
|Sekme|Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinin sekme sırası, bu denetimlerin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]tabanlı bir uygulamada barındırıldığı zaman ile aynıdır.<br /><br /> Sekme tuşu ve SHIFT + TAB tuşları ile [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminden [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimine sekme her zamanki gibi çalışmaktadır.<br /><br /> `false` <xref:System.Windows.Forms.Control.TabStop%2A> özellik değerine sahip [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri, Kullanıcı denetimleri üzerinde sekmeden odağı almaz.<br /><br /> -Her <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi, ne zaman <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin odak alacağını belirleyen bir <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> değerine sahiptir.<br /><xref:System.Windows.Forms.Integration.WindowsFormsHost> kapsayıcısının içinde yer alan -   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği tarafından belirtilen sırayı izler. Son sekme dizininden sekme, varsa bir sonraki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimine odak koyar. Başka bir odaksız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi yoksa, sekme, sekme düzeninde ilk [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimine geri döner.<br /><xref:System.Windows.Forms.Integration.WindowsFormsHost> içindeki denetimlerin -   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> değerleri, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminde bulunan eşdüzey [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerine göre değişir.<br />-Sekme denetimine özgü davranışa kavriler. Örneğin, `true` <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> özellik değerine sahip bir <xref:System.Windows.Forms.TextBox> denetimindeki TAB tuşuna basmak, odağı taşımak yerine metin kutusunda bir sekme girer.|Yok.|  
|Ok tuşlarıyla gezinme|-<xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimindeki ok tuşları ile gezinti, sıradan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kapsayıcı denetimiyle aynı. yukarı ok ve sol ok tuşları önceki denetimi seçer ve aşağı ok ve sağ ok tuşları bir sonraki denetimi seçer.<br />-<xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminde yer alan ilk denetimdeki yukarı ok ve sol ok tuşları, SHIFT + TAB klavye kısayoluyla aynı eylemi gerçekleştirir. Odaksız bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi varsa, odak <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminin dışına taşınır. Bu davranış, son denetim için hiçbir sarmalama gerçekleşmediğinde standart <xref:System.Windows.Forms.ContainerControl> davranışından farklıdır. Odaksız başka bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi yoksa, odak sekme düzeninde son [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimine geri döner.<br />-<xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminde yer alan son denetimden aşağı ok ve sağ ok tuşları sekme tuşuyla aynı eylemi gerçekleştirir. Odaksız bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi varsa, odak <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminin dışına taşınır. Bu davranış, ilk denetimin hiçbir sarmalama gerçekleşmediğinde standart <xref:System.Windows.Forms.ContainerControl> davranışından farklıdır. Odaksız başka bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi yoksa, odak sekme düzeninde ilk [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimine geri döner.|Yok.|  
|Ekleyebilir|Hızlandırıcılar, "desteklenmeyen" sütununda belirtilenler dışında her zamanki gibi çalışır.|Teknolojilerde yinelenen Hızlandırıcılar, sıradan yinelenen hızlandırıcılar gibi çalışmaz. Hızlandırma, teknolojilerde çoğaltıldığında, en az bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi ve diğeri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminde varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi her zaman hızlandırıcıyı alır. Yinelenen Hızlandırıcı basıldığında odak denetimler arasında geçiş yapmaz.|  
|Kısayol tuşları|Kısayol tuşları, "desteklenmeyen" sütununda belirtilenler dışında her zamanki gibi çalışır.|ön işleme aşamasında işlenen -   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kısayol tuşlarının her zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kısayol tuşlarından öncelikli olması önerilir. Örneğin, CTRL + S kısayol tuşları tanımlı bir <xref:System.Windows.Forms.ToolStrip> denetiminiz varsa ve CTRL + S 'ye bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komutu varsa, odağa bakılmaksızın <xref:System.Windows.Forms.ToolStrip> denetim işleyicisi her zaman ilk olarak çağrılır.<br /><xref:System.Windows.Forms.Control.KeyDown> olayı tarafından işlenen -   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kısayol tuşları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]son olarak işlenir. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminin <xref:System.Windows.Forms.Control.IsInputKey%2A> yöntemini geçersiz kılarak veya <xref:System.Windows.Forms.Control.PreviewKeyDown> olayını işleyerek bu davranışı önleyebilirsiniz. <xref:System.Windows.Forms.Control.IsInputKey%2A> yönteminden `true` döndürün veya <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> özelliğinin değerini <xref:System.Windows.Forms.Control.PreviewKeyDown> olay işleyicinizde `true` olarak ayarlayın.|  
|AcceptsReturn, AcceptsTab ve denetime özgü diğer davranış|Varsayılan klavye davranışını değiştiren özellikler her zamanki gibi çalışarak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminin `true`döndürmek için <xref:System.Windows.Forms.Control.IsInputKey%2A> metodunu geçersiz kıldığını kabul ediyor.|<xref:System.Windows.Forms.Control.KeyDown> olayını işleyerek varsayılan klavye davranışını değiştiren [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri, ana bilgisayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminde en son işlenir. Bu denetimler en son işlendiği için, beklenmeyen davranışlar üretebilir.|  
|Olayları girme ve bırakma|Odak, içeren <xref:System.Windows.Forms.Integration.ElementHost> denetimine gitmediğinden, tek bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminde odak değiştiğinde her zamanki gibi ENTER ve Leave olayları tetiklenir.|Aşağıdaki odak değişiklikleri gerçekleştiğinde, ENTER ve Leave olayları oluşturulmaz:<br /><br /> -İçinden <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin dışına.<br />-İçinden <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin içinden.<br />-<xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi dışında.<br />-Bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminde barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminden aynı <xref:System.Windows.Forms.Integration.WindowsFormsHost>barındırılan bir <xref:System.Windows.Forms.Integration.ElementHost> denetimine.|  
|İş|Çoklu iş parçacığı oluşturma özellikleri desteklenir.|Hem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojileri tek iş parçacıklı eşzamanlılık modelini varsayar. Hata ayıklama sırasında, diğer iş parçacıklarından çerçeve nesnelerine yapılan çağrılar bu gereksinimi zorlamak için bir özel durum oluşturacak.|  
|Güvenlik|Tüm birlikte çalışabilirlik senaryoları tam güven gerektirir.|Kısmi güvende birlikte çalışabilirlik senaryolarına izin verilmez.|  
|Erişilebilirlik|Tüm Erişilebilirlik senaryoları desteklenir. Yardımcı teknoloji ürünleri, hem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri içeren karma uygulamalar için kullanıldığında doğru şekilde çalışır.|Yok.|  
|Pano|Tüm Pano işlemleri her zamanki gibi çalışır. Bu, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri arasında kesme ve yapıştırmayı içerir.|Yok.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri her zamanki gibi çalışır. Bu, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri arasındaki işlemleri içerir.|Yok.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Windows Forms içinde WPF denetimleri barındırma  
 Windows Forms denetimi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi barındırıyorsa, aşağıdaki birlikte çalışabilirlik senaryoları desteklenir:  
  
- Kodu kullanarak bir veya daha fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimini barındırma.  
  
- Bir özellik sayfasını bir veya daha fazla barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleriyle ilişkilendirme.  
  
- Bir form içinde bir veya daha fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası barındırma.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir pencere başlatılıyor.  
  
- Ana/ayrıntı formunu bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ana ile barındırma ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntıları.  
  
- Ana/ayrıntı formunu bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ana ile barındırma ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayrıntıları.  
  
- Özel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri barındırma.  
  
- Karma denetimleri barındırma.  
  
### <a name="ambient-properties"></a>Çevresel Özellikler  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinin çevresel özelliklerinden bazılarının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğerleri vardır. Bu çevresel özellikler barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerine yayılır ve <xref:System.Windows.Forms.Integration.ElementHost> denetiminde ortak özellikler olarak sunulur. <xref:System.Windows.Forms.Integration.ElementHost> denetimi her [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Ambient özelliğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğerine çevirir.  
  
 Daha fazla bilgi için bkz. [Windows Forms ve WPF özellik eşleme](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda birlikte çalışabilirlik davranışı açıklanmaktadır.  
  
|Davranış|Desteklenir|Desteklenmez|  
|--------------|---------------|-------------------|  
|Saydamlık|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim işleme saydamlığı destekler. Üst [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminin arka planı barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerinin arka planı haline gelebilir.|Yok.|  
|İş|Çoklu iş parçacığı oluşturma özellikleri desteklenir.|Hem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojileri tek iş parçacıklı eşzamanlılık modelini varsayar. Hata ayıklama sırasında, diğer iş parçacıklarından çerçeve nesnelerine yapılan çağrılar bu gereksinimi zorlamak için bir özel durum oluşturacak.|  
|Güvenlik|Tüm birlikte çalışabilirlik senaryoları tam güven gerektirir.|Kısmi güvende birlikte çalışabilirlik senaryolarına izin verilmez.|  
|Erişilebilirlik|Tüm Erişilebilirlik senaryoları desteklenir. Yardımcı teknoloji ürünleri, hem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri içeren karma uygulamalar için kullanıldığında doğru şekilde çalışır.|Yok.|  
|Pano|Tüm Pano işlemleri her zamanki gibi çalışır. Bu, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri arasında kesme ve yapıştırmayı içerir.|Yok.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri her zamanki gibi çalışır. Bu, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri arasındaki işlemleri içerir.|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)

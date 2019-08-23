---
title: WPF ve Windows Forms Birlikte Çalışması
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 0326f283cb271d1578e94b648e423c6f88c579f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917397"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF ve Windows Forms Birlikte Çalışması
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama arabirimleri oluşturmak için iki farklı mimarsunun. Ad <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> alanı, ortak birlikte çalışma senaryolarını etkinleştiren sınıflar sağlar. Birlikte çalışabilirlik özelliklerini uygulayan iki anahtar sınıfı ve ' <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost>dir. Bu konu, hangi birlikte çalışma senaryolarının desteklendiğini ve hangi senaryoların desteklenmediğini açıklar.  
  
> [!NOTE]
> *Karma denetim* senaryosuna özel bir değerlendirme verilmiştir. Karma denetim, diğer teknolojideki bir denetimde iç içe yerleştirilmiş bir teknolojiden denetim içerir. Buna *iç içe geçmiş birlikte çalışabilirlik*da denir. Çok *düzeyli karma denetim* , birden fazla karma denetim iç içe geçme düzeyine sahiptir. Bir çok düzeyli iç içe geçme örneği, başka [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bir denetim içeren bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim içeren bir denetimdir. Çok düzeyli karma denetimler desteklenmez.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>WPF Windows Forms denetimleri barındırma  
 Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim Windows Forms denetimi barındırıyorsa, aşağıdaki birlikte çalışabilirlik senaryoları desteklenir:  
  
- Denetim XAML kullanarak bir veya daha fazla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi barındıramayabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
- Kodu kullanarak bir veya daha fazla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim barındıramayabilir.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Diğer[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri içeren kapsayıcı denetimlerini barındıramayabilir.  
  
- Ana öğe ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayrıntılarla bir ana/ayrıntı formu barındırabilir.  
  
- Ana öğe ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntılarla bir ana/ayrıntı formu barındırabilir.  
  
- Bir veya daha fazla ActiveX denetimini barındıramayabilir.  
  
- Bir veya daha fazla bileşik denetimi barındıramayabilir.  
  
- Kullanılarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]karma denetimleri barındıramayabilir.  
  
- Kod kullanarak karma denetimleri barındıramayabilir.  
  
### <a name="layout-support"></a>Düzen desteği  
 Aşağıdaki listede, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi ile tümleştirmeyi denediğinde bilinen sınırlamalar açıklanmaktadır.  
  
- Bazı durumlarda, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimler yeniden boyutlandırılmaz veya yalnızca belirli boyutlara boyutlandırılabilir. Örneğin, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> denetim, denetimin yazı tipi boyutu tarafından tanımlanan tek bir yüksekliği destekler. Öğelerin dikey [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olarak uzatılabileceği varsayan dinamik bir düzende, barındırılan <xref:System.Windows.Forms.ComboBox> bir denetim beklendiği gibi genişlemez.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]denetimler döndürülemiyor veya çarpıılamıyor. Örneğin, Kullanıcı arabiriminizi 90 derece döndürdüğünüzde barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimler, kendi sağ konumlarını korur.  
  
- Çoğu durumda, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimler orantılı ölçeklendirmeyi desteklemez. Denetimin genel boyutları ölçeklense de, denetimin alt denetimleri ve bileşen öğeleri beklenen şekilde yeniden boyutlandırmayabilir. Bu sınırlama, her [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bir denetimin ölçeklendirmeyi ne kadar iyi desteklediğine bağlıdır.  
  
- Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kullanıcı arabiriminde, örtüşen davranışı denetlemek için öğelerin z sırasını değiştirebilirsiniz. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bir denetim ayrı bir HWND içinde çizilir, bu nedenle her zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerin üzerine çizilir.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]denetimler, yazı tipi boyutuna bağlı olarak otomatik ölçeklendirmeyi destekler. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kullanıcı arabiriminde, bağımsız öğeler dinamik olarak yeniden boyutlandırabilse de yazı tipi boyutunun değiştirilmesi tüm düzeni yeniden boyutlandıramaz.  
  
### <a name="ambient-properties"></a>Çevresel Özellikler  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Denetimlerin çevresel özelliklerinden bazıları eşdeğerleri vardır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] . Bu çevresel özellikler barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlere yayılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimde ortak özellikler olarak gösterilir. Denetim her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir çevresel özelliği [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğerine dönüştürür. <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
  
 Daha fazla bilgi için bkz. [Windows Forms ve WPF özellik eşleme](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda birlikte çalışabilirlik davranışı açıklanmaktadır.  
  
|Davranış|Desteklenir|Desteklenmez|  
|--------------|---------------|-------------------|  
|Saydamlık|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]Denetim işleme saydamlığı destekler. Ana [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimin arka planı barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerin arka planı haline gelebilir.|Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimler saydamlığı desteklemez. Örneğin, <xref:System.Windows.Forms.TextBox> ve <xref:System.Windows.Forms.ComboBox> denetimleri tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]barındırıldığı zaman saydam olmayacaktır.|  
|Sekme|Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerin sekme sırası, bu denetimlerin temel alınan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]uygulamada barındırıldığı zaman ile aynıdır.<br /><br /> Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimden[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Tab tuşu ve SHIFT + TAB tuşlarının bulunduğu denetime sekme, her zamanki gibi çalışmaktadır.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.TabStop%2A> özellik`false` değeri olan denetimler, Kullanıcı denetimleri üzerinde sekmeden odağı almaz.<br /><br /> -Her <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim bir <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> değere sahiptir ve bu <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin ne zaman odak alacağını belirler.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> kapsayıcı içinde yer alan denetimler, <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği tarafından belirtilen sırayı izler. Son sekme dizininden sekme, varsa odağı bir sonraki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetime koyar. Odaksız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] başka bir denetim yoksa, sekme sırasıyla ilk [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetime döner.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>içindeki denetimlerin değerleri, <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimde bulunan eşdüzey [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerle ilişkilidir.<br />-Sekme denetimine özgü davranışa kavriler. Örneğin, <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> Özellik değeri `true` olan bir denetimdeki sekme tuşuna basmak, odağı taşımak yerine metin kutusunda bir sekme girer.|Geçerli değildir.|  
|Ok tuşlarıyla gezinme|- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimdeki ok tuşlarıyla gezinti, sıradan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bir kapsayıcı denetimiyle aynı olur: YUKARı ok ve sol ok tuşları önceki denetimi seçer ve aşağı ok ve sağ ok tuşları bir sonraki denetimi seçer.<br />- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimde bulunan ilk denetimin yukarı ok ve sol ok tuşları, SHIFT + TAB klavye kısayoluyla aynı eylemi gerçekleştirir. Odaklenebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir denetim varsa, odak <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin dışına taşınır. Bu davranış, son denetim için <xref:System.Windows.Forms.ContainerControl> hiçbir sarmalama gerçekleşmediğinde standart davranıştan farklıdır. Odaksız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] başka bir denetim yoksa, odak sekme düzeninde son [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetime geri döner.<br />- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimde yer alan son denetimden aşağı ok ve sağ ok tuşları sekme tuşuyla aynı eylemi gerçekleştirir. Odaklenebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir denetim varsa, odak <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin dışına taşınır. Bu davranış, ilk denetimin hiçbir <xref:System.Windows.Forms.ContainerControl> sarmalama gerçekleşmediğinde standart davranıştan farklıdır. Odaksız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] başka bir denetim yoksa, odak sekme sırasındaki ilk [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetime geri döner.|Geçerli değildir.|  
|Ekleyebilir|Hızlandırıcılar, "desteklenmeyen" sütununda belirtilenler dışında her zamanki gibi çalışır.|Teknolojilerde yinelenen Hızlandırıcılar, sıradan yinelenen hızlandırıcılar gibi çalışmaz. Bir Hızlandırıcı, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimde en az bir denetim ve diğeri bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimde yinelendiğinden denetim her zaman hızlandırıcıyı alır. Yinelenen Hızlandırıcı basıldığında odak denetimler arasında geçiş yapmaz.|  
|Kısayol tuşları|Kısayol tuşları, "desteklenmeyen" sütununda belirtilenler dışında her zamanki gibi çalışır.|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ön işleme aşamasında işlenen kısayol tuşları her zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kısayol tuşlarından önceliklidir. Örneğin, CTRL + s kısayol tuşu <xref:System.Windows.Forms.ToolStrip> tanımlı bir denetiminiz varsa ve <xref:System.Windows.Forms.ToolStrip> CTRL + s 'ye bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komut bağlıysa, odak, odağa bakılmaksızın denetim işleyicisi her zaman çağrılır.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.KeyDown> olay tarafından işlenen kısayol tuşları son olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]işlenir. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.PreviewKeyDown> Denetimin yöntemini geçersiz kılarak veya olayı işleyerek bu davranışı önleyebilirsiniz. <xref:System.Windows.Forms.Control.IsInputKey%2A> `true` <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> Yönteminden geri dönün veya özelliğinin değerini olay işleyicinizde <xref:System.Windows.Forms.Control.PreviewKeyDown> olarak `true` ayarlayın. <xref:System.Windows.Forms.Control.IsInputKey%2A>|  
|AcceptsReturn, AcceptsTab ve denetime özgü diğer davranış|Varsayılan klavye davranışını değiştiren özellikler her zamanki gibi çalışarak, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimin döndürülecek <xref:System.Windows.Forms.Control.IsInputKey%2A> `true`yöntemi geçersiz kıldığını kabul ediyor.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.KeyDown> olayı işleyerek varsayılan klavye davranışını değiştiren denetimler, en son konak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminde işlenir. Bu denetimler en son işlendiği için, beklenmeyen davranışlar üretebilir.|  
|Olayları girme ve bırakma|Odak, içeren <xref:System.Windows.Forms.Integration.ElementHost> denetime gitmediğinden, tek <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimde odak değiştiğinde her zamanki gibi ENTER ve Leave olayları tetiklenir.|Aşağıdaki odak değişiklikleri gerçekleştiğinde, ENTER ve Leave olayları oluşturulmaz:<br /><br /> -İçinden bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin dışından.<br />-Dışından bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin içinden.<br />- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetim dışında.<br />- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimde barındırılanbir<xref:System.Windows.Forms.Integration.WindowsFormsHost>denetimden, aynı içinde barındırılan bir denetime.<xref:System.Windows.Forms.Integration.ElementHost>|  
|İş|Çoklu iş parçacığı oluşturma özellikleri desteklenir.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Hem hem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de teknolojileri tek iş parçacıklı eşzamanlılık modelini varsayar. Hata ayıklama sırasında, diğer iş parçacıklarından çerçeve nesnelerine yapılan çağrılar bu gereksinimi zorlamak için bir özel durum oluşturacak.|  
|Güvenlik|Tüm birlikte çalışabilirlik senaryoları tam güven gerektirir.|Kısmi güvende birlikte çalışabilirlik senaryolarına izin verilmez.|  
|Erişilebilirlik|Tüm Erişilebilirlik senaryoları desteklenir. Yardımcı teknoloji ürünleri, hem hem de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri içeren karma uygulamalar için kullanıldığında doğru çalışır.|Geçerli değildir.|  
|Pano|Tüm Pano işlemleri her zamanki gibi çalışır. Bu, ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri arasında kesme ve yapıştırmayı içerir.|Geçerli değildir.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri her zamanki gibi çalışır. Bu, ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] arasındaki işlemleri içerir.|Geçerli değildir.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Windows Forms içinde WPF denetimleri barındırma  
 Windows Forms denetimi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim barındırdığı zaman aşağıdaki birlikte çalışabilirlik senaryoları desteklenir:  
  
- Kodu kullanarak bir veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha fazla denetimi barındırma.  
  
- Bir özellik sayfasını bir veya daha fazla barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerle ilişkilendirme.  
  
- Bir formda bir veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha fazla sayfa barındırma.  
  
- Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencere başlatılıyor.  
  
- Ana ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntılar ile ana/ayrıntı formunu barındırma.  
  
- Ana ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayrıntılar ile ana/ayrıntı formunu barındırma.  
  
- Özel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri barındırma.  
  
- Karma denetimleri barındırma.  
  
### <a name="ambient-properties"></a>Çevresel Özellikler  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimlerin çevresel özelliklerinden bazıları eşdeğerleri vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Bu çevresel özellikler barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlere yayılır ve <xref:System.Windows.Forms.Integration.ElementHost> denetimde ortak özellikler olarak gösterilir. Denetim her [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bir çevresel özelliği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğerine dönüştürür. <xref:System.Windows.Forms.Integration.ElementHost>  
  
 Daha fazla bilgi için bkz. [Windows Forms ve WPF özellik eşleme](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda birlikte çalışabilirlik davranışı açıklanmaktadır.  
  
|Davranış|Desteklenir|Desteklenmez|  
|--------------|---------------|-------------------|  
|Saydamlık|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Denetim işleme saydamlığı destekler. Ana [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimin arka planı barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin arka planı haline gelebilir.|Geçerli değildir.|  
|İş|Çoklu iş parçacığı oluşturma özellikleri desteklenir.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Hem hem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de teknolojileri tek iş parçacıklı eşzamanlılık modelini varsayar. Hata ayıklama sırasında, diğer iş parçacıklarından çerçeve nesnelerine yapılan çağrılar bu gereksinimi zorlamak için bir özel durum oluşturacak.|  
|Güvenlik|Tüm birlikte çalışabilirlik senaryoları tam güven gerektirir.|Kısmi güvende birlikte çalışabilirlik senaryolarına izin verilmez.|  
|Erişilebilirlik|Tüm Erişilebilirlik senaryoları desteklenir. Yardımcı teknoloji ürünleri, hem hem de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri içeren karma uygulamalar için kullanıldığında doğru çalışır.|Geçerli değildir.|  
|Pano|Tüm Pano işlemleri her zamanki gibi çalışır. Bu, ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri arasında kesme ve yapıştırmayı içerir.|Geçerli değildir.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri her zamanki gibi çalışır. Bu, ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] arasındaki işlemleri içerir.|Geçerli değildir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [İzlenecek yol: WPF 'de Windows Forms denetimini barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [İzlenecek yol: WPF 'de Windows Forms Bileşik denetim barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: Windows Forms WPF bileşik denetimini barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)

---
title: WPF ve Windows Formları interop
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 76d1e97c92946267aa1217f52c93594fb63d20de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187159"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF ve Windows Forms Birlikte Çalışması
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve Windows Forms, uygulama arabirimleri oluşturmak için iki farklı mimari sunar. Ad <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> alanı, ortak işlem senaryolarını etkinleştiren sınıflar sağlar. İşlemler arası yetenekleri uygulayan iki <xref:System.Windows.Forms.Integration.WindowsFormsHost> temel <xref:System.Windows.Forms.Integration.ElementHost>sınıf ve. Bu konu, hangi işlem arasenaryolarının desteklenmediğini ve hangi senaryoların desteklenmediğini açıklar.  
  
> [!NOTE]
> *Karma kontrol* senaryosuna özel önem verilir. Hibrit kontrol, diğer teknolojinin kontrolünde iç içe olan bir teknolojinin kontrolüne sahiptir. Buna *iç içe geçmiş bir etkileşim*de denir. *Çok düzeyli bir karma denetim,* birden fazla karma kontrol iç içe geçme düzeyine sahiptir. Çok düzeyli iç içe geçmiş bir iç içe işlem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örneği, başka bir Windows Forms denetimi içeren bir denetim içeren bir Windows Forms denetimidir. Çok düzeyli karma denetimler desteklenmez.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>
## <a name="hosting-windows-forms-controls-in-wpf"></a>WPF'de Windows Form Denetimlerini Barındırma  
 Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim Windows Forms denetimi barındırdığında aşağıdaki işlem ler arası senaryolar desteklenir:  
  
- Denetim, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML kullanarak bir veya daha fazla Windows Forms denetimi barındırabilir.  
  
- Kodu kullanarak bir veya daha fazla Windows Forms denetimi barındırabilir.  
  
- Diğer Windows Forms denetimleri içeren Windows Forms kapsayıcı denetimlerini barındırabilir.  
  
- Bir ana ve Windows Formlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntıları içeren bir ana/ayrıntı formu barındırabilir.  
  
- Windows Forms yöneticisi ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntıları içeren bir ana/ayrıntı formu barındırabilir.  
  
- Bir veya daha fazla ActiveX denetimi barındırabilir.  
  
- Bir veya daha fazla bileşik denetimbarındırabilir.  
  
- Bu kullanarak hibrid [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]kontrolleri barındırabilir.  
  
- Kod kullanarak karma denetimleri barındırabilir.  
  
### <a name="layout-support"></a>Düzen Desteği  
 Aşağıdaki liste, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğe barındırılan Windows Forms denetimini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemine tümleştirmeye çalıştığında bilinen sınırlamaları açıklar.  
  
- Bazı durumlarda, Windows Forms denetimleri yeniden boyutlandırılamaz veya yalnızca belirli boyutlara boyutlandırılamaz. Örneğin, Windows Forms <xref:System.Windows.Forms.ComboBox> denetimi yalnızca denetimin yazı tipi boyutuyla tanımlanan tek bir yüksekliği destekler. Öğelerin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dikey olarak uzatabileceğini varsayan dinamik bir <xref:System.Windows.Forms.ComboBox> düzende, barındırılan denetim beklendiği gibi esnemez.  
  
- Windows Forms denetimleri döndürülemez veya eğriltilemez. Örneğin, kullanıcı arabiriminizi 90 derece döndürdüğünüzde, barındırılan Windows Forms denetimleri dik konumlarını korur.  
  
- Çoğu durumda, Windows Forms denetimleri orantılı ölçeklemayı desteklemez. Denetimin genel boyutları ölçeklenecek olsa da, alt denetimler ve denetimin bileşen öğeleri beklendiği gibi yeniden boyutlandırılamayabilir. Bu sınırlama, her Windows Forms denetiminin ölçeklemeyi ne kadar iyi desteklediğine bağlıdır.  
  
- Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıcı arabiriminde, çakışan davranışı denetlemek için öğelerin z sırasını değiştirebilirsiniz. Barındırılan Windows Forms denetimi ayrı bir HWND'de çizilir, bu nedenle her zaman öğelerin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] üzerine çizilir.  
  
- Windows Forms denetimleri yazı tipi boyutuna bağlı olarak otomatik küçültmeyi destekler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kullanıcı arabiriminde, yazı tipi boyutunu değiştirmek tüm düzeni yeniden boyutlandırmaz, ancak tek tek öğeler dinamik olarak yeniden boyutlandırılabilir.  
  
### <a name="ambient-properties"></a>Ortam Özellikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Denetimlerin ortam özelliklerinden bazılarıWindows Forms eşdeğerlerine sahiptir. Bu ortam özellikleri barındırılan Windows Forms denetimlerine yayılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimde ortak özellikler olarak ortaya çıkar. Denetim, <xref:System.Windows.Forms.Integration.WindowsFormsHost> her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ortam özelliğini Windows Forms eşdeğerine çevirir.  
  
 Daha fazla bilgi için [Windows Formları ve WPF Özellik Eşleme'ye](windows-forms-and-wpf-property-mapping.md)bakın.  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda işlem ler arası davranış açıklanmaktadır.  
  
|Davranış|Destekleniyor|Desteklenmiyor|  
|--------------|---------------|-------------------|  
|Saydamlık|Windows Forms denetim oluşturma saydamlığı destekler. Üst [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimin arka planı, barındırılan Windows Forms denetimlerinin arka planı olabilir.|Bazı Windows Forms denetimleri saydamlığı desteklemez. Örneğin, <xref:System.Windows.Forms.TextBox> ve <xref:System.Windows.Forms.ComboBox> denetimleri tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]barındırıldığında saydam olmayacaktır.|  
|Sekme|Barındırılan Windows Forms denetimleri için sekme sırası, bu denetimlerin Windows Forms tabanlı bir uygulamada barındırıldığı denetimlerle aynıdır.<br /><br /> TAB tuşu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve SHIFT+TAB tuşları yla bir denetimden Windows Forms denetimine sekme her zamanki gibi çalışır.<br /><br /> Windows Forms, kullanıcı <xref:System.Windows.Forms.Control.TabStop%2A> denetimleri `false` sekmediğinde odak alma özelliğine sahip denetimler alır.<br /><br /> - <xref:System.Windows.Forms.Integration.WindowsFormsHost> Her denetim, bu <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin ne zaman odaklanacağını belirleyen bir değere sahiptir.<br />- Bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> kapsayıcının içinde bulunan Windows Forms <xref:System.Windows.Forms.Control.TabIndex%2A> denetimleri, özellik tarafından belirtilen sırayı izler. Son sekme dizininden sekme, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsa bir sonraki denetime odaklanır. Başka bir odaklanılabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim yoksa, sekme sekmesi sırasına göre ilk Windows Forms denetimine geri döner.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>içindeki denetimlere <xref:System.Windows.Forms.Integration.WindowsFormsHost> ait değerler, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimde bulunan kardeş Windows Forms denetimlerine göredir.<br />- Tabbing, denetime özgü davranışı onurlandırıyor. Örneğin, odak hareket yerine <xref:System.Windows.Forms.TextBox> metin kutusuna <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> bir `true` sekme girer özellik değeri olan bir denetimTAB tuşuna basarak.|Geçerli değildir.|  
|Ok tuşları ile gezinme|- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimde ok tuşları ile gezinme sıradan bir Windows Forms konteyner kontrolü ile aynıdır: UP ARROW ve SOL OK tuşları önceki kontrolü seçin ve DOWN ARROW ve SAĞ OK tuşları sonraki kontrolü seçin.<br />- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimde bulunan ilk denetimden gelen UP ARROW ve LEFT ARROW tuşları SHIFT+TAB klavye kısayolu ile aynı eylemi gerçekleştirir. Odaklanabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir denetim varsa, odak <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin dışına taşınır. Bu davranış, son <xref:System.Windows.Forms.ContainerControl> denetimiçin hiçbir kaydırma oluşur standart davranış farklıdır. Başka netleştirilebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim yoksa, odak sekme sırasına göre son Windows Forms denetimine geri döner.<br />- <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimde bulunan son denetimden DOWN ARROW ve RIGHT ARROW tuşları TAB tuşu ile aynı eylemi gerçekleştirir. Odaklanabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir denetim varsa, odak <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimin dışına taşınır. Bu davranış, ilk <xref:System.Windows.Forms.ContainerControl> denetime hiçbir kaydırma oluşur standart davranış farklıdır. Başka netleştirilebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim yoksa, odak sekme sırasına göre ilk Windows Forms denetimine döner.|Geçerli değildir.|  
|Hızlandırıcılar|Hızlandırıcılar, "Desteklenmeyen" sütununda belirtilen durumlar dışında her zamanki gibi çalışır.|Teknolojiler arasında yinelenen hızlandırıcılar sıradan yinelenen hızlandırıcılar gibi çalışmaz. Bir hızlandırıcı, en az bir Windows Forms denetiminde ve diğeri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimde olmak üzere teknolojiler arasında çoğaltıldığında, Windows Forms denetimi her zaman hızlandırıcıyı alır. Yinelenen hızlandırıcıya basıldığında odak, denetimler arasında geçiş yapmaz.|  
|Kısayol tuşları|Kısayol tuşları, "Desteklenmeyen" sütununda belirtilen durumlar dışında her zamanki gibi çalışır.|- Ön işleme aşamasında işlenen Windows Forms kısayol tuşları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] her zaman kısayol tuşlarından önceliklidir. Örneğin, CTRL+S <xref:System.Windows.Forms.ToolStrip> kısayol tuşları tanımlanmış bir denetiminiz varsa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve CTRL+S'e <xref:System.Windows.Forms.ToolStrip> bağlı bir komut varsa, odak ne olursa olsun, denetim işleyicisi her zaman önce çağrılır.<br />- <xref:System.Windows.Forms.Control.KeyDown> Olay tarafından işlenen Windows Forms kısayol tuşları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]en son . Windows Forms denetiminin <xref:System.Windows.Forms.Control.IsInputKey%2A> yöntemini geçersiz kılarak veya <xref:System.Windows.Forms.Control.PreviewKeyDown> olayı işleyerek bu davranışı önleyebilirsiniz. <xref:System.Windows.Forms.Control.IsInputKey%2A> Yöntemden <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> dönün `true` veya olay işleyicinizde <xref:System.Windows.Forms.Control.PreviewKeyDown> `true` özelliğin değerini ayarlayın.|  
|AcceptsReturn, AcceptsTab ve diğer denetime özgü davranışı|Varsayılan klavye davranışını değiştiren özellikler, Windows Forms denetiminin döndürme <xref:System.Windows.Forms.Control.IsInputKey%2A> `true`yöntemini geçersiz kdığını varsayarak her zamanki gibi çalışır.|Olayı işleyerek varsayılan klavye davranışını <xref:System.Windows.Forms.Control.KeyDown> değiştiren Windows Forms denetimleri ana bilgisayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminde en son işlenir. Bu denetimler en son işlendiğinden, beklenmeyen davranışlar alabilirsiniz.|  
|Etkinliklere Girin ve Ayrılın|Odak, içeren <xref:System.Windows.Forms.Integration.ElementHost> denetime gitmiyorsa, tek bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimde odak değiştiğinde Enter ve Bırak olayları her zamanki gibi yükseltilir.|Aşağıdaki odak değişiklikleri gerçekleştiğinde, olayları girin ve bırakın yükseltilmez:<br /><br /> - Bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrol içinden dışarıya.<br />- Dışarıdan kontrol <xref:System.Windows.Forms.Integration.WindowsFormsHost> içine.<br />- Bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrol dışında.<br />- Bir Windows Forms denetimi <xref:System.Windows.Forms.Integration.WindowsFormsHost> bir <xref:System.Windows.Forms.Integration.ElementHost> denetim barındırılan <xref:System.Windows.Forms.Integration.WindowsFormsHost>bir kontrol aynı içinde barındırılan bir denetim.|  
|Çoklu iş parçacığı kullanımı|Tüm çok iş parçacığı çeşitleri desteklenir.|Hem Windows Formları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hem de teknolojileri tek iş parçacığı eşzamanlılık modeli varsayar. Hata ayıklama sırasında, diğer iş parçacığı çerçeve nesnelerine yapılan çağrılar, bu gereksinimi uygulamak için bir özel durum oluşturur.|  
|Güvenlik|Tüm interoperation senaryoları tam güven gerektirir.|Kısmi güven içinde hiçbir işlem senaryosuna izin verilmez.|  
|Erişilebilirlik|Tüm erişilebilirlik senaryoları desteklenir. Yardımcı teknoloji ürünleri, hem Windows Formları hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimler içeren karma uygulamalar için kullanıldığında doğru şekilde çalışır.|Geçerli değildir.|  
|Pano|Tüm Pano işlemleri her zamanki gibi çalışır. Bu, Windows Formları ve denetimleri arasında kesme ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yapıştırma içerir.|Geçerli değildir.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri her zamanki gibi çalışır. Bu, Windows Formları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve denetimler arasındaki işlemleri içerir.|Geçerli değildir.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>
## <a name="hosting-wpf-controls-in-windows-forms"></a>WPF Denetimlerini Windows Formlarında Barındırma  
 Windows Forms denetimi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim barındırdığında aşağıdaki işlemler arası senaryolar desteklenir:  
  
- Kodu kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir veya daha fazla denetimi barındırma.  
  
- Bir özellik sayfasını bir veya daha [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fazla barındırılan denetimle ilişkilendirme.  
  
- Bir formda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir veya daha fazla sayfa barındırma.  
  
- Pencereyi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] açıyor.  
  
- Windows Forms yöneticisi ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntıları yla birlikte bir ana/ayrıntı formu barındırma.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bir ana ve Windows Forms ayrıntıları yla bir ana/ayrıntı formunu barındırma.  
  
- Özel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri barındırma.  
  
- Hibrit kontrolleri barındırma.  
  
### <a name="ambient-properties"></a>Ortam Özellikleri  
 Windows Forms denetimlerinin ortam özelliklerinden bazılarının eşdeğerleri vardır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu ortam özellikleri barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlere yayılır ve <xref:System.Windows.Forms.Integration.ElementHost> denetimde ortak özellikler olarak ortaya çıkarır. Denetim, <xref:System.Windows.Forms.Integration.ElementHost> her Windows Forms ortam özelliğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğerine çevirir.  
  
 Daha fazla bilgi için [Windows Formları ve WPF Özellik Eşleme'ye](windows-forms-and-wpf-property-mapping.md)bakın.  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda işlem ler arası davranış açıklanmaktadır.  
  
|Davranış|Destekleniyor|Desteklenmiyor|  
|--------------|---------------|-------------------|  
|Saydamlık|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]denetim oluşturma saydamlığı destekler. Üst Windows Forms denetiminin arka planı barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin arka planı olabilir.|Geçerli değildir.|  
|Çoklu iş parçacığı kullanımı|Tüm çok iş parçacığı çeşitleri desteklenir.|Hem Windows Formları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hem de teknolojileri tek iş parçacığı eşzamanlılık modeli varsayar. Hata ayıklama sırasında, diğer iş parçacığı çerçeve nesnelerine yapılan çağrılar, bu gereksinimi uygulamak için bir özel durum oluşturur.|  
|Güvenlik|Tüm interoperation senaryoları tam güven gerektirir.|Kısmi güven içinde hiçbir işlem senaryosuna izin verilmez.|  
|Erişilebilirlik|Tüm erişilebilirlik senaryoları desteklenir. Yardımcı teknoloji ürünleri, hem Windows Formları hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimler içeren karma uygulamalar için kullanıldığında doğru şekilde çalışır.|Geçerli değildir.|  
|Pano|Tüm Pano işlemleri her zamanki gibi çalışır. Bu, Windows Formları ve denetimleri arasında kesme ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yapıştırma içerir.|Geçerli değildir.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri her zamanki gibi çalışır. Bu, Windows Formları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve denetimler arasındaki işlemleri içerir.|Geçerli değildir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)

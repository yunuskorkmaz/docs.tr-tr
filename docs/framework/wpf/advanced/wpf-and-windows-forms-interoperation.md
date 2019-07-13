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
ms.openlocfilehash: b2e0ee85a7edd07e7372b04c3a26a06416fb39d9
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859874"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF ve Windows Forms Birlikte Çalışması
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama arabirimleri oluşturmak için iki farklı mimari sunar. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> Ad alanı, birlikte çalışabilirlik senaryoları etkinleştiren sınıflar sağlar. Birlikte çalışabilirlik özelliklerini uygulayan iki anahtar sınıf <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost>. Bu konuda, birlikte çalışabilirlik hangi senaryolar desteklenir ve hangi senaryolar desteklenmez açıklanmaktadır.  
  
> [!NOTE]
>  Yükseltilmesine verilir *karma denetimi* senaryo. Bir karma denetimi diğer teknolojileri denetiminden iç içe geçmiş bir teknoloji denetiminden vardır. Bu da adlandırılır bir *iç içe geçmiş birlikte çalışabilirlik*. A *düzeyli karma denetim* karma birden fazla düzey iç içe geçme denetimine sahiptir. Çok düzeyli bir iç içe geçmiş birlikte çalışma örneği olan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] içeren denetimi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimini içeren başka bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi. Çok düzeyli karma denetimleri desteklenmez.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Barındırma Windows Forms denetimlerini düzenleme  
 Aşağıdaki birlikte çalışabilirlik senaryolarında desteklenir, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimini Windows Forms denetimini barındırır:  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bir veya daha fazla denetim barındırabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] XAML kullanarak denetler.  
  
- Bir veya daha fazla barındırabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodla denetler.  
  
- Barındırabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] diğer içeren kapsayıcı denetimler [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrol eder.  
  
- İle ana/ayrıntı formu barındırabilir bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ana ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayrıntıları.  
  
- İle ana/ayrıntı formu barındırabilir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ana ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntıları.  
  
- Bir veya daha fazla ActiveX denetimleri barındırabilir.  
  
- Bir veya daha fazla bileşik denetimler barındırabilir.  
  
- Kullanarak karma denetim barındırabilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
- Kod kullanarak karma denetim barındırabilir.  
  
### <a name="layout-support"></a>Düzen desteği  
 Bilinen sınırlamalar aşağıdaki listede açıklanmaktadır, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi çalışır, barındırılan bir tümleştirme [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] içine denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi.  
  
- Bazı durumlarda, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri yeniden boyutlandırılamaz ya da yalnızca belirli boyutlara yeniden boyutlandırılabilir. Örneğin, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> denetimi, denetimin yazı tipi boyutu tarafından tanımlanan yalnızca tek bir yüksekliği destekler. İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeler dikey olarak barındırılan uzatabilirsiniz olduğunu varsayan dinamik bir düzen <xref:System.Windows.Forms.ComboBox> beklendiği gibi denetimi uzamaz.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri Döndürülmüş veya dengesiz. Örneğin, 90 derece kullanıcı arabiriminiz döndürürken, barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri, dik konumlarını koruyacaktır.  
  
- Çoğu durumda [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerin orantılı ölçeklendirme desteklemez. Denetim genel boyutlarını ölçeklendirilmesine rağmen alt denetimler ve denetim bileşen öğeleri beklenen şekilde yeniden boyutlandırılabilir değil. Bu sınırlama her ne kadar iyi bağlıdır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi, ölçeklendirmeyi destekler.  
  
- İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıcı arabirimi, çakışan davranışı denetlemek için öğelerin z düzenini değiştirebilirsiniz. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi üst kısmındaki her zaman çizilen için ayrı bir HWND çizilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri yazı tipi boyutunu temel alan otomatik ölçeklendirmeyi destekler. İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazı tipi boyutunu değiştirme, kullanıcı arabirimi olmayan yeniden boyutlandırma tüm düzeni tek tek öğeleri dinamik olarak yeniden boyutlandırılabilir ancak.  
  
### <a name="ambient-properties"></a>Ortam özellikleri  
 Bazı ortam özelliklerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetiminiz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğerleri. Bu ortam özellikleri yayılır barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetler ve bulunan genel özellik olarak kullanıma <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimi çevirir her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çevresel özelliğe kendi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğer.  
  
 Daha fazla bilgi için [Windows Forms ve WPF özelliğini eşleme](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda birlikte çalışabilirlik davranışını tanımlar.  
  
|Davranış|Desteklenen|Desteklenmiyor|  
|--------------|---------------|-------------------|  
|Saydamlık|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] saydamlık denetimi işlemeyi destekler. Arka plan üst [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi, arka planını dönüşebilir barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri.|Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri saydamlık desteklemez. Örneğin, <xref:System.Windows.Forms.TextBox> ve <xref:System.Windows.Forms.ComboBox> denetimleri tarafından barındırıldığında saydam olmayacak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Sekme|Sekme sırasını barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri aynıdır bu denetimler, barındırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-tabanlı bir uygulama.<br /><br /> Denetiminden bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sekme ve SHIFT + SEKME tuşlarını ile works zamanki denetim.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri bir <xref:System.Windows.Forms.Control.TabStop%2A> özelliği değerinin `false` kullanıcı denetimleri aracılığıyla sekme odağı almazsınız.<br /><br /> -Her <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolünde bir <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> belirleyen değeri, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim odağı alır.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] içinde bulunan denetimleri bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> kapsayıcı tarafından belirtilen sırada takip <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği. Son sekme dizininin, odak sonraki koyar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsa denetimi. Odaklanabilir diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi yoksa, ilk döndürür sekmeyle gitmeyi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sekme sırasını denetimi.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> içindeki denetimlerin değerleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> eşdüzey olan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bulunan denetimleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi.<br />-Sekme denetimine özgü davranış geliştirir. Örneğin, SEKME tuşuna basarak bir <xref:System.Windows.Forms.TextBox> olan denetim bir <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> özelliği değerinin `true` sekme odağı taşımak yerine metin kutusundaki girer.|Geçerli değildir.|  
|Ok tuşları ile Gezinti|-Gezinti ok tuşları içinde <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi, sıradan tutarların [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kapsayıcı denetimi: Yukarı Ok ve sol ok tuşlarını önceki denetimi seçer ve sonraki denetim aşağı oku ve sağ ok tuşlarını seçin.<br />-UP ve sol ok tuşları bulunan ilk denetiminden <xref:System.Windows.Forms.Integration.WindowsFormsHost> SHIFT + TAB klavye kısayolu olarak aynı eylemi gerçekleştirir. Varsa bir Odaklanabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim odağı hareket ettirir dışında <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi. Bu davranış standart olandan farklı <xref:System.Windows.Forms.ContainerControl> hiçbir son denetim sarmalama davranışından. Odaklanabilir diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi yoksa, odak en son döndürür [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sekme sırasını denetimi.<br />-Aşağı Ok ve sağ ok tuşlarını bulunan son denetiminden <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi SEKME tuşuna aynı eylemi gerçekleştirir. Varsa bir Odaklanabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim odağı hareket ettirir dışında <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi. Bu davranış standart olandan farklı <xref:System.Windows.Forms.ContainerControl> hiçbir kaydırma ilk denetime davranışından. Odaklanabilir diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi yoksa, odak moduna geri döner ilk [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sekme sırasını denetimi.|Geçerli değildir.|  
|Hızlandırıcı|"Desteklenmeyen" sütununda belirtilenler dışında Hızlandırıcıları her zamanki gibi çalışır.|Yinelenen hızlandırıcılardan teknolojilerde sıradan yinelenen hızlandırıcılardan gibi çalışmaz. Ne zaman bir Hızlandırıcı yineleniyor en az birine sahip teknolojilerde üzerinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi ve diğer bağlı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim hızlandırıcıyı her zaman alır. Odak, yinelenen Hızlandırıcı basıldığında denetimler arasında geçiş değil.|  
|Kısayol tuşları|Kısayol tuşları "Desteklenmeyen" sütununda belirtilenler dışında zamanki gibi çalışır.|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ön işleme aşamasında her zaman işlenir kısayol tuşları önceliklidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kısayol tuşları. Örneğin, bir <xref:System.Windows.Forms.ToolStrip> denetim CTRL + S kısayol tuşları ile tanımlanan ve yoktur bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] CTRL + S, bağlı komutu <xref:System.Windows.Forms.ToolStrip> denetim işleyicisi her zaman çağrılır ilk olarak, odak ne olursa olsun.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] tarafından işlenen kısayol tuşları <xref:System.Windows.Forms.Control.KeyDown> olay son olarak işlenir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Bu davranışı geçersiz kılarak engelleyebilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimin <xref:System.Windows.Forms.Control.IsInputKey%2A> yöntemi veya işleme <xref:System.Windows.Forms.Control.PreviewKeyDown> olay. Dönüş `true` gelen <xref:System.Windows.Forms.Control.IsInputKey%2A> yöntemi veya değerini <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> özelliğini `true` içinde <xref:System.Windows.Forms.Control.PreviewKeyDown> olay işleyicisi.|  
|AcceptsReturn AcceptsTab ve diğer denetim özgü davranışı|Varsayarak varsayılan klavye davranışı değiştirmek özelliklerini her zamanki şekilde çalışır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim geçersiz kılmaları <xref:System.Windows.Forms.Control.IsInputKey%2A> döndürülecek yöntemi `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klavye davranışı değiştirmek varsayılan denetim işleyerek <xref:System.Windows.Forms.Control.KeyDown> olayını en son konak işlenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi. Bu denetimler son işlendiğinden, beklenmeyen davranışlara neden olabilir.|  
|Olaylara Giriş ve bırakma|Ne zaman odağı düşülmemesini içeren <xref:System.Windows.Forms.Integration.ElementHost> denetim, giriş ve çıkış olaylarını oluştuğunda zamanki odak tek bir değişiklik olduğunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi.|Girin ve çıkış olaylarını aşağıdaki odak değişiklikler olduğunda harekete Geçirilmemesi:<br /><br /> -From İçten dışa bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi.<br />-From için bir dış içinde bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi.<br />-Dışında bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi.<br />-From bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminde barındırılan bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi bir <xref:System.Windows.Forms.Integration.ElementHost> aynı içinde barındırılan bir denetim <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Çoklu iş parçacığı kullanımı|Çoklu iş parçacığı tüm çeşitleri desteklenmiyor.|Hem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojileri eşzamanlılık tek iş parçacıklı model varsayılır. Hata ayıklama sırasında framework nesneleri çağrıları diğer iş parçacıklarından bu gereksinimini zorlamak için bir özel durum oluşturacak.|  
|Güvenlik|Tüm birlikte çalışabilirlik senaryolarında tam güven gerektirir.|Hiçbir birlikte çalışabilirlik senaryolarında kısmi güvende izin verilir.|  
|Erişilebilirlik|Tüm erişilebilirlik senaryolar desteklenir. Yardımcı teknoloji ürünlerinin işlevi doğru her ikisini de içeren hibrit uygulamalar için kullanıldığında [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Geçerli değildir.|  
|Pano|Tüm Pano işlemlerini zamanki gibi çalışır. Bu kesme ve yapıştırma arasında içerir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Geçerli değildir.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri zamanki gibi çalışır. Arasında işlemler bu ücrete dahildir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Geçerli değildir.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Windows Forms'ta WPF denetimleri barındırma  
 Aşağıdaki birlikte çalışabilirlik senaryolarında bir Windows Forms denetimi konakları, desteklenen bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi:  
  
- Bir veya daha fazla barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodla denetler.  
  
- Bir özellik sayfasını bir veya daha fazla barındırılan ilişkilendirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
- Bir veya daha fazla barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formda sayfaları.  
  
- Başlangıç bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] penceresi.  
  
- İle ana/ayrıntı formu barındıran bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ana ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntıları.  
  
- İle ana/ayrıntı formu barındıran bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ana ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayrıntıları.  
  
- Özel barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
- Karma denetimleri barındırma.  
  
### <a name="ambient-properties"></a>Ortam özellikleri  
 Bazı ortam özelliklerini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminiz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğerleri. Bu ortam özellikleri yayılır barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetler ve bulunan genel özellik olarak kullanıma <xref:System.Windows.Forms.Integration.ElementHost> denetimi. <xref:System.Windows.Forms.Integration.ElementHost> Denetimi çevirir her [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] çevresel özelliğe kendi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğer.  
  
 Daha fazla bilgi için [Windows Forms ve WPF özelliğini eşleme](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda birlikte çalışabilirlik davranışını tanımlar.  
  
|Davranış|Desteklenen|Desteklenmiyor|  
|--------------|---------------|-------------------|  
|Saydamlık|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] saydamlık denetimi işlemeyi destekler. Arka plan üst [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi, arka planını dönüşebilir barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri.|Geçerli değildir.|  
|Çoklu iş parçacığı kullanımı|Çoklu iş parçacığı tüm çeşitleri desteklenmiyor.|Hem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojileri eşzamanlılık tek iş parçacıklı model varsayılır. Hata ayıklama sırasında framework nesneleri çağrıları diğer iş parçacıklarından bu gereksinimini zorlamak için bir özel durum oluşturacak.|  
|Güvenlik|Tüm birlikte çalışabilirlik senaryolarında tam güven gerektirir.|Hiçbir birlikte çalışabilirlik senaryolarında kısmi güvende izin verilir.|  
|Erişilebilirlik|Tüm erişilebilirlik senaryolar desteklenir. Yardımcı teknoloji ürünlerinin işlevi doğru her ikisini de içeren hibrit uygulamalar için kullanıldığında [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Geçerli değildir.|  
|Pano|Tüm Pano işlemlerini zamanki gibi çalışır. Bu kesme ve yapıştırma arasında içerir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Geçerli değildir.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri zamanki gibi çalışır. Arasında işlemler bu ücrete dahildir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Geçerli değildir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [İzlenecek yol: WPF'de Windows Forms denetimini barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)

---
title: WPF ve Windows Forms Birlikte Çalışması
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 315037c49e00e097eebd51e2a511aa7f01e468ae
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF ve Windows Forms Birlikte Çalışması
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama arayüzleri oluşturmak için iki farklı mimariyi sunar. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> Ad alanı, ortak birlikte çalışabilirlik senaryolarını etkinleştiren sınıfları sağlar. Birlikte çalışabilirlik özelliklerini uygulayan iki anahtar sınıf <xref:System.Windows.Forms.Integration.WindowsFormsHost> ve <xref:System.Windows.Forms.Integration.ElementHost>. Bu konuda, hangi birlikte çalışabilirlik senaryoları desteklenir ve hangi senaryoları desteklenmez açıklanmaktadır.  
  
> [!NOTE]
>  Bir ayrıcalık verilen *karma denetimi* senaryo. Bir karma denetimi diğer teknolojileri denetimden iç içe geçmiş bir teknoloji denetimden sahiptir. Bu da adlandırılır bir *iç içe geçmiş birlikte çalışabilirlik*. A *düzeyli karma denetim* karma birden fazla düzey iç içe geçme denetimine sahiptir. Çok düzeyli bir iç içe geçmiş birlikte çalışabilirlik örneği bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] içeren denetimi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimini içeren başka bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim. Çok düzeyli karma denetimleri desteklenmez.  
  
  
<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Barındırma Windows Forms denetimlerini düzenleme  
 Aşağıdaki birlikte çalışabilirlik senaryoları desteklenir olduğunda bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimini barındıran bir Windows Forms denetimi:  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bir veya daha fazla denetim barındırabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] XAML kullanılarak denetler.  
  
-   Bir veya daha fazla barındırabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kod kullanarak denetler.  
  
-   Barındırabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] diğer içeren kapsayıcı denetimleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrol eder.  
  
-   Ana/ayrıntı formu ile barındırabilir bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ana ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayrıntıları.  
  
-   Ana/ayrıntı formu ile barındırabilir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ana ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntıları.  
  
-   Bir veya daha fazla barındırabilir [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] kontrol eder.  
  
-   Bir veya daha fazla bileşik denetimler barındırabilir.  
  
-   Kullanarak karma denetimleri barındırabilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
-   Kod kullanarak karma denetimleri barındırabilir.  
  
### <a name="layout-support"></a>Düzen desteği  
 Aşağıdaki listede bilinen sınırlamaları açıklar olduğunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi çalışır barındırılan tümleştirmek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] içine denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen sistemi.  
  
-   Bazı durumlarda, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri yeniden boyutlandırılamaz ya da yalnızca belirli boyutlara boyutlandırılabilir. Örneğin, bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> denetimi denetimin yazı tipi boyutu tarafından tanımlanan yalnızca tek bir yüksekliği destekler. İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerini dikey olarak barındırılan uzatabilirsiniz olduğunu varsayar dinamik düzen <xref:System.Windows.Forms.ComboBox> denetimi beklendiği gibi uzamaz.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri Döndürülmüş veya eğri. Örneğin, Kullanıcı Arabiriminizin 90 derece döndürdüğünüzde barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri dik konumlarını koruyacaktır.  
  
-   Çoğu durumda, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri orantılı ölçeklendirmeyi desteklemez. Denetimin genel boyutlarının ölçeklendirilmesine rağmen alt denetimleri ve bileşen öğeleri denetiminin beklendiği gibi yeniden boyutlandırılabilir değil. Bu sınırlama ne kadar iyi her bağlıdır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi, ölçeklendirmeyi destekler.  
  
-   İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıcı arabirimi öğelerinin z düzenini çakışan davranışı denetlemek için değiştirebilirsiniz. Barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi, ayrı bir HWND içinde çizilir, her zaman üstünde çizilir nedenle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri yazı tipi boyutuna göre otomatik ölçeklendirmeyi destekler. İçinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıcı arabirimi, yazı tipi boyutunu değiştirme değil yeniden boyutlandırma tüm düzeni ayrı ayrı öğeler dinamik olarak yeniden boyutlandırma ancak.  
  
### <a name="ambient-properties"></a>Ortam özellikleri  
 Bazı ortam özelliklerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleriniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğerleri. Bu ortam özelliklerine yayılır barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetler ve ortak özellik olarak sunulur <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Denetimi her çevirir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içine ortam özelliği kendi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğer.  
  
 Daha fazla bilgi için bkz: [Windows Forms ve WPF özellik eşlemesi](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda birlikte çalışabilirlik davranışını tanımlar.  
  
|Davranış|Desteklenir|Desteklenmez|  
|--------------|---------------|-------------------|  
|Saydamlık|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi geçirgenliği destekler. Arka plan üst [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim arka planını dönüşebilir barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrol eder.|Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri saydamlığı desteklemez. Örneğin, <xref:System.Windows.Forms.TextBox> ve <xref:System.Windows.Forms.ComboBox> denetimleri tarafından barındırıldığında saydam olmayacak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Sekme|Sekme sırasını barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri aynıdır bu denetimleri zaman barındırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-tabanlı.<br /><br /> Denetiminden bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimini bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] SEKME tuşunu ve üst karakter + sekme tuşlarını ile works her zamanki gibi denetleme.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri bir <xref:System.Windows.Forms.Control.TabStop%2A> özellik değerinin `false` kullanıcı denetimlerde sekme açtığında odak almaz.<br /><br /> -Her <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi sahip bir <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> belirleyen değeri, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim odağı alır.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] içinde bulunan denetimleri bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> kapsayıcı izleyin tarafından belirtilen sıraya <xref:System.Windows.Forms.Control.TabIndex%2A> özelliği. Son sekme dizininin odak sonraki koyar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim varsa. Odaklanabilir diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi yoksa, ilk döndürür sekme [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sekme sırasını denetiminde.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> içindeki denetimleri için değerleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> eşdüzey olan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] bulunan denetimleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim.<br />-Sekme denetimi özgü davranışı geliştirir. Örneğin, SEKME tuşuna basarak bir <xref:System.Windows.Forms.TextBox> sahip denetimini bir <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> özellik değerinin `true` odağı taşıma yerine metin kutusuna bir sekme girer.|Yok.|  
|Ok tuşları ile Gezinti|-Gezinme ok tuşları <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimidir sıradan olduğu gibi aynı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kapsayıcı denetimi: Yukarı Ok ve sol ok tuşları önceki denetim ve aşağı ok ve sağ ok tuşları sonraki denetimi seçin.<br />-UP ve sol ok tuşları bulunan ilk denetiminden <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim üst karakter + sekme klavye kısayolu ile aynı eylemi gerçekleştirir. Varsa Odaklanabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi odağı taşır dışında <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim. Bu davranış standart farklıdır <xref:System.Windows.Forms.ContainerControl> son denetime kaydırma olmadığı davranışından. Odaklanabilir diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi yoksa, odak en son döner [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sekme sırasını denetiminde.<br />-Bulunan en son denetim ok ve sağ ok tuşları aşağı <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi için SEKME tuşunu ile aynı eylemi gerçekleştirir. Varsa Odaklanabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi odağı taşır dışında <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim. Bu davranış standart farklıdır <xref:System.Windows.Forms.ContainerControl> ilk denetime kaydırma olmadığı için davranışından. Odaklanabilir diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi yoksa, odak döndürür ilk [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sekme sırasını denetiminde.|Yok.|  
|Hızlandırıcı|Hızlandırıcı "Desteklenmeyen" sütununda belirtilenler dışında her zamanki gibi çalışır.|Yinelenen hızlandırıcılardan teknolojilerde sıradan yinelenen hızlandırıcılardan gibi çalışmaz. Ne zaman Hızlandırıcı çoğaltılmış en az bir tane ile teknolojilerde üzerinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi ve diğer bağlı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim Hızlandırıcı her zaman alır. Odağı yinelenen Hızlandırıcı basıldığında denetimleri arasında geçiş değil.|  
|Kısayol tuşları|Kısayol tuşları "Desteklenmeyen" sütununda belirtilenler dışında her zamanki gibi çalışır.|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] önişlem aşamasında her zaman işlenir kısayol tuşları önceliklidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kısayol tuşları. Örneğin, bir <xref:System.Windows.Forms.ToolStrip> kontrol CTRL + S kısayol tuşları ile tanımlanan ve olmadığından bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] CTRL + S bağlı komutu <xref:System.Windows.Forms.ToolStrip> denetim işleyicisi her zaman çağrılır ilk olarak, bağımsız olarak odak.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] tarafından işlenen kısayol tuşları <xref:System.Windows.Forms.Control.KeyDown> olay son olarak işlenir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Bu davranışı geçersiz kılarak engelleyebilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimin <xref:System.Windows.Forms.Control.IsInputKey%2A> yöntemi veya işleme <xref:System.Windows.Forms.Control.PreviewKeyDown> olay. Dönüş `true` gelen <xref:System.Windows.Forms.Control.IsInputKey%2A> yöntemi veya değerini <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> özelliğine `true` içinde <xref:System.Windows.Forms.Control.PreviewKeyDown> olay işleyicisi.|  
|AcceptsReturn, AcceptsTab ve diğer denetim özgü davranışı|Olduğunu varsayarak varsayılan klavye davranışını değiştiren özelliklerini her zamanki gibi iş [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim geçersiz kılmaları <xref:System.Windows.Forms.Control.IsInputKey%2A> döndürülecek yöntemi `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Varsayılan değiştirme denetimleri klavye davranışı işleyerek <xref:System.Windows.Forms.Control.KeyDown> olay son ana bilgisayarda işlenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim. Bu denetimlerin son işlendiğinden beklenmeyen davranışlara neden olabilir.|  
|Olaylara Giriş ve bırakma|Ne zaman odak değil olduğuna içeren <xref:System.Windows.Forms.Integration.ElementHost> denetlemek, girin ve bırakın olayları ortaya çıkar her zamanki gibi tek bir odak değiştiğinde, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim.|Girin ve aşağıdaki odak değişiklikleri oluştuğunda bırakın olayları oluşmaz:<br /><br /> -From İçten dışa bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim.<br />-From outside içinde bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim.<br />-Dışında bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetim.<br />-From bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminde barındırılan bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimini bir <xref:System.Windows.Forms.Integration.ElementHost> aynı içinde barındırılan denetim <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Çoklu iş parçacığı kullanımı|Çoklu iş parçacığı tüm çeşitleri desteklenir.|Hem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojileri tek iş parçacıklı eşzamanlılık modeli varsayar. Hata ayıklama sırasında diğer iş parçacıklarından çerçeve nesnelerine yapılan çağrılar bu gereksinimi zorlamak için bir özel durum oluşturacak.|  
|Güvenlik|Tüm birlikte çalışabilirlik senaryoları tam güven gerektirir.|Birlikte çalışabilirlik senaryolarına kısmi güvende izin verilir.|  
|Erişilebilirlik|Tüm erişilebilirlik senaryoları desteklenir. Yardımcı teknoloji ürünlerinin işlev doğru her ikisini de içeren karma uygulamalar için kullanıldığında [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Yok.|  
|Pano|Tüm Pano işlemleri her zamanki gibi çalışır. Bu arasında kesme ve yapıştırmayı içerir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Yok.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri her zamanki gibi çalışır. Bu işlemler arasında içerir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Yok.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Windows Forms içerisinde WPF denetimleri barındırma  
 Bir Windows Forms denetimi ana durumunda aşağıdaki birlikte çalışabilirlik senaryoları desteklenir bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi:  
  
-   Bir veya daha fazla barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kod kullanarak denetler.  
  
-   Bir özellik sayfasını bir veya daha fazla barındırılan ilişkilendirme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
-   Bir veya daha fazla barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfaları bir biçimde.  
  
-   Başlangıç bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] penceresi.  
  
-   Ana/ayrıntı formu ile barındıran bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ana ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayrıntıları.  
  
-   Ana/ayrıntı formu ile barındıran bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ana ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ayrıntıları.  
  
-   Özel barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.  
  
-   Karma denetimleri barındırma.  
  
### <a name="ambient-properties"></a>Ortam özellikleri  
 Bazı ortam özelliklerini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleriniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğerleri. Bu ortam özelliklerine yayılır barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetler ve ortak özellik olarak sunulur <xref:System.Windows.Forms.Integration.ElementHost> denetim. <xref:System.Windows.Forms.Integration.ElementHost> Denetimi her çevirir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ortam özelliği kendi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşdeğer.  
  
 Daha fazla bilgi için bkz: [Windows Forms ve WPF özellik eşlemesi](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Davranış  
 Aşağıdaki tabloda birlikte çalışabilirlik davranışını tanımlar.  
  
|Davranış|Desteklenir|Desteklenmez|  
|--------------|---------------|-------------------|  
|Saydamlık|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi geçirgenliği destekler. Arka plan üst [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim arka planını dönüşebilir barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Yok.|  
|Çoklu iş parçacığı kullanımı|Çoklu iş parçacığı tüm çeşitleri desteklenir.|Hem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teknolojileri tek iş parçacıklı eşzamanlılık modeli varsayar. Hata ayıklama sırasında diğer iş parçacıklarından çerçeve nesnelerine yapılan çağrılar bu gereksinimi zorlamak için bir özel durum oluşturacak.|  
|Güvenlik|Tüm birlikte çalışabilirlik senaryoları tam güven gerektirir.|Birlikte çalışabilirlik senaryolarına kısmi güvende izin verilir.|  
|Erişilebilirlik|Tüm erişilebilirlik senaryoları desteklenir. Yardımcı teknoloji ürünlerinin işlev doğru her ikisini de içeren karma uygulamalar için kullanıldığında [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Yok.|  
|Pano|Tüm Pano işlemleri her zamanki gibi çalışır. Bu arasında kesme ve yapıştırmayı içerir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Yok.|  
|Sürükle ve bırak özelliği|Tüm sürükle ve bırak işlemleri her zamanki gibi çalışır. Bu işlemler arasında içerir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder.|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Windows Forms ve WPF Özelliğini Eşleme](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)

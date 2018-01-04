---
title: "İletişim Kutularına Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 112a9badaf9a64b2c6d3f73d64c27fbc36ec48a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dialog-boxes-overview"></a>İletişim Kutularına Genel Bakış
Bağımsız uygulamalar genellikle her ikisi de görüntülediğini ana veri uygulama üzerinden çalışır ve aracılığıyla bu verileri işlemek için işlevselliği kullanıma sunan bir ana penceresi sahip [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mekanizmaları menü çubukları, araç çubukları ve durum çubukları gibi. Önemsiz olmayan bir uygulama Ayrıca aşağıdakileri yapmak için ek windows görüntülenebilir:  
  
-   Belirli bilgileri kullanıcıya görüntüler.  
  
-   Kullanıcılardan bilgi toplayın.  
  
-   Hem görüntülemek ve bilgi toplayın.  
  
 Windows bu tür olarak da bilinir *iletişim kutuları*, ve iki tür vardır: kalıcı ve kalıcı olmayan.  
  
 A *kalıcı* işlevi devam etmek için bir kullanıcıdan ek verilere ihtiyaç duyduğunda bir işlev tarafından iletişim kutusu görüntülenir. Veri toplamak üzere modal iletişim kutusu işlevi bağımlı olduğundan kalıcı bir iletişim kutusu açık kalırken diğer windows uygulamasında etkinleştirme kullanıcı ayrıca engeller. Çoğu durumda, bir modal iletişim kutusu kullanıcının ya basarak modal iletişim kutusuyla bitirdikten sonra sinyal izin verir. bir **Tamam** veya **iptal** düğmesi. Tuşuna basarak **Tamam** düğmesini gösteren bir kullanıcı veri geçtiğini ve işlevi veri işleme devam etmek istiyor. Tuşuna basarak **iptal** düğmesini gösteren kullanıcı tamamen yürütülmesini işlevi durdurmak istiyor. Kalıcı iletişim kutuları en yaygın örnekleri açma, kaydetme ve veri yazdırmak için gösterilir.  
  
 A *kalıcı olmayan* iletişim kutusu, diğer yandan engellemez kullanıcı açık durumdayken diğer windows etkinleştirme. Örneğin, bir kullanıcı bir belgedeki belirli bir sözcük oluşumlarını bulmak isterse, ana pencereyi genellikle bir kullanıcı aradıklarını hangi word sormak için bir iletişim kutusunu açın. Yana bulma bir word belgesi düzenleme kullanıcı engellemez, ancak iletişim kutusunun kalıcı olması gerekmez. En az bir kalıcı olmayan iletişim kutusu sağlar bir **kapatmak** iletişim kutusunu kapatmak için düğmesini ve belirli işlevleri gibi yürütmek için ek düğmeler sağlayabilen bir **Sonrakini Bul** Sonrakini Bul düğmesi, word sözcük arama Bul ölçütlerini eşleşir.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]iletişim kutuları, ileti kutuları, ortak iletişim kutuları ve özel iletişim kutuları gibi çeşitli türlerde oluşturmanıza olanak sağlar. Bu konu, her açıklar ve [iletişim kutusu örnek](http://go.microsoft.com/fwlink/?LinkID=159984) eşleşen örnekler verilmektedir.  
  
 
  
<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>İleti kutuları  
 A *ileti kutusu* metinsel bilgileri görüntülemek için ve düğmelerle kararlar yapmalarına izin vermek için kullanılan bir iletişim kutusudur. Aşağıdaki şekil metinsel bilgi görüntüler, soru soran ve kullanıcı soruyu yanıtlamak için üç düğme sağlar bir ileti kutusu gösterir.  
  
 ![Sözcük işlemci iletişim kutusu](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure1.png "DialogBoxesOverviewFigure1")  
  
 Bir ileti kutusu oluşturmak için kullandığınız <xref:System.Windows.MessageBox> sınıfı. <xref:System.Windows.MessageBox>ileti kutusu metni, başlık, simge ve aşağıdaki gibi kod kullanarak düğmeleri, yapılandırmanızı sağlar.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Bir ileti kutusu göstermek için arama `static` <xref:System.Windows.MessageBox.Show%2A> aşağıdaki kodda gösterildiği gibi yöntemi.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Bir ileti kutusu gösterir kod algılar ve kullanıcının karar (hangi düğmesine basıldı) işlemek gerektiğinde kodu aşağıdaki kodda gösterildiği gibi ileti kutusu sonucu inceleyebilirsiniz.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 İleti kutuları kullanma hakkında daha fazla bilgi için bkz: <xref:System.Windows.MessageBox>, [MessageBox örnek](http://go.microsoft.com/fwlink/?LinkID=160023), ve [iletişim kutusu örnek](http://go.microsoft.com/fwlink/?LinkID=159984).  
  
 Ancak <xref:System.Windows.MessageBox> kullanmanın avantajı bir basit iletişim kutusunu kullanıcı deneyimi sunabilir <xref:System.Windows.MessageBox> kısmi güven güvenlik sandbox içinde çalışan uygulamalar tarafından gösterilen penceresi türü olan (bkz: [güvenlik](../../../../docs/framework/wpf/security-wpf.md)), aşağıdaki gibi [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 Çoğu iletişim kutusu görüntülemek ve metin, seçim (onay kutuları) birbirini dışlayan seçimi (radyo düğmeleri) dahil olmak üzere bir ileti kutusu sonucu'den daha karmaşık veri toplamak ve seçim (liste kutuları, birleşik giriş kutularını, açılan liste kutuları) listesi. Bu, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] birçok ortak iletişim kutuları sağlar ve ya da kullanımını tam güven ile çalışan uygulamalar için sınırlı olsa da, kendi iletişim kutuları oluşturmanıza olanak sağlar.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Ortak iletişim kutuları  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]dosyaları kaydetme ve yazdırma dosyaları açma, iletişim kutularını dahil olmak üzere tüm uygulamalar için ortak olan yeniden kullanılabilir iletişim kutuları, çeşitli uygular. Bu iletişim kutularından işletim sistemi tarafından uygulanan olduğundan, kullanıcı deneyimini tutarlılık yardımcı olan işletim sistemi üzerinde çalışan tüm uygulamaları arasında paylaşılabilir; Kullanıcılar bir uygulamayı işletim sistemi tarafından sağlanan iletişim kutusunda, kullanımıyla öğrendiğinizde, diğer uygulamalar bu iletişim kutusunda kullanmayı öğrenmek gerekmez. Bu iletişim kutularından tüm uygulamalar için kullanılabilir olduğundan ve bunlar tutarlı bir kullanıcı deneyimi sağlamak için bunlar olarak da bilinir *ortak iletişim kutuları*.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]Dosya ve yazdırma ortak iletişim kutuları Kaydet'i açık dosyanın yalıtır ve tek başına uygulamalarda kullanabilmeniz için olarak yönetilen sınıflar gösterir. Bu konu, her kısa bir genel bakış sağlar.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Dosya Aç iletişim kutusu  
 Aşağıdaki şekilde gösterildiği Dosya Aç iletişim kutusu açmak için bir dosya adı almak için işlevselliği açma dosya tarafından kullanılır.  
  
 ![Aç iletişim kutusu](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure2.png "DialogBoxesOverviewFigure2")  
  
 Ortak Dosya Aç iletişim kutusu olarak uygulanan <xref:Microsoft.Win32.OpenFileDialog> sınıfı ve bulunan <xref:Microsoft.Win32> ad alanı. Aşağıdaki kod oluşturma, yapılandırma ve bir Göster ve sonucu işle nasıl gösterir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Dosya Aç iletişim kutusu hakkında daha fazla bilgi için bkz: <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog>güvenli bir şekilde dosya adları almak için kısmi güven ile çalışan uygulamalar tarafından kullanılabilir (bkz [güvenlik](../../../../docs/framework/wpf/security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Dosya Kaydet iletişim kutusu  
 Kaydetme dosya iletişim kutusunda, aşağıdaki şekilde gösterildiği kaydetmek için bir dosya adını almak için işlevselliği kaydetme dosya tarafından kullanılır.  
  
 ![Farklı Kaydet iletişim kutusunda](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure3.png "DialogBoxesOverviewFigure3")  
  
 Dosya iletişim kutusu kaydetme genel olarak uygulanan <xref:Microsoft.Win32.SaveFileDialog> sınıfı ve bulunan <xref:Microsoft.Win32> ad alanı. Aşağıdaki kod oluşturma, yapılandırma ve bir Göster ve sonucu işle nasıl gösterir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Kaydetme hakkında daha fazla bilgi için bkz: dosya iletişim kutusu <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Yazdır iletişim kutusu  
 Aşağıdaki şekilde gösterildiği yazdırma iletişim kutusunda, yazdırma işlevselliği tarafından seçin ve kullanıcı verilerini yazdırmak istediğiniz yazıcı yapılandırmak için kullanılır.  
  
 ![Yazdır iletişim kutusu](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure4.png "DialogBoxesOverviewFigure4")  
  
 Ortak bir yazdırma iletişim kutusu olarak uygulanan <xref:System.Windows.Controls.PrintDialog> sınıfı ve bulunan <xref:System.Windows.Controls> ad alanı. Aşağıdaki kod, oluşturmak, yapılandırmak ve bir Göster gösterilmektedir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Yazdır iletişim kutusu hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. ' De yazdırmayı hakkında ayrıntılı bilgi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bkz: [yazdırma genel bakış](../../../../docs/framework/wpf/advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Özel iletişim kutuları  
 Ortak iletişim kutuları yararlıdır ve mümkün olduğunda kullanılmalıdır olsa da, etki alanına özgü iletişim kutuları gereksinimlerini desteklemez. Bu durumda, kendi iletişim kutuları oluşturmanız gerekir. Anlatıldığı gibi bir iletişim kutusu özel davranışlarla penceredir. <xref:System.Windows.Window>Bu davranışları uygular ve sonuç olarak, kullandığınız <xref:System.Windows.Window> özel kalıcı ve kalıcı olmayan iletişim kutuları oluşturmak için.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Özel bir Modal iletişim kutusu oluşturma  
 Bu konuda nasıl kullanılacağını gösterir <xref:System.Windows.Window> tipik modal iletişim kutusu uygulaması oluşturmak için kullanarak `Margins` iletişim kutusu bir örnek olarak (bkz [iletişim kutusu örnek](http://go.microsoft.com/fwlink/?LinkID=159984)). `Margins` İletişim kutusunda aşağıdaki şekilde gösterilmiştir.  
  
 ![Kenar Boşlukları iletişim kutusu](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure5.png "DialogBoxesOverviewFigure5")  
  
#### <a name="configuring-a-modal-dialog-box"></a>Modal bir iletişim kutusu yapılandırma  
 Tipik iletişim kutusu için kullanıcı arabirimi aşağıdakileri içerir:  
  
-   İstenen veri toplamak için gereken çeşitli kontrol eder.  
  
-   Gösteren bir **Tamam** kullanıcılar işlev için dönüş iletişim kutusunu kapatmak için'ı tıklatın ve işleme devam düğmesi.  
  
-   Gösteren bir **iptal** düğmesi iletişim kutusunu kapatın ve daha fazla işlemesini işlevi durdurmak için kullanıcılar'ı tıklatın.  
  
-   Gösteren bir **Kapat** başlık çubuğunda düğmesi.  
  
-   Simge gösteriliyor.  
  
-   Gösteren **simge durumuna küçült**, **Ekranı Kapla**, ve **geri** düğmeler.  
  
-   Gösteren bir **sistem** en aza indirmek için en üst düzeye çıkarmak, geri yükleme ve iletişim kutusunu kapatmak için menüsü.  
  
-   Yukarıdaki ve iletişim kutusu açılır penceresi Center'da açılıyor.  
  
-   İletişim kutuları, mümkün olduğunda iletişim kutusu çok küçük engellemek ve kullanıcı bir yararlı varsayılan boyutu ile sağlamak için hem varsayılan hem de en az ayarlamak gereken şekilde yeniden boyutlandırılabilir boyutları sırasıyla olması gerekir.  
  
-   ESC tuşuna basarak neden olan bir klavye kısayolu olarak yapılandırılmalıdır **iptal** düğmesine basıldığında. Bu ayar sağlanır <xref:System.Windows.Controls.Button.IsCancel%2A> özelliği **iptal** düğmesine `true`.  
  
-   (Veya RETURN) ENTER tuşuna basarak neden olan bir klavye kısayolu olarak yapılandırılmalıdır **Tamam** düğmesine basıldığında. Bu ayar sağlanır <xref:System.Windows.Controls.Button.IsDefault%2A> özelliği **Tamam** düğmesini `true`.  
  
 Aşağıdaki kod, bu yapılandırmayı gösterir.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 Bir iletişim kutusu için kullanıcı deneyimi de iletişim kutusu açılır pencere menü çubuğuna genişletir. Menü öğesi işlevi devam etmeden önce bir iletişim kutusu üzerinden kullanıcı etkileşimi gerektiren bir işlev çalıştığında, menü öğesi işlevi için üç nokta üstbilgisinde, aşağıda gösterildiği gibi sahip olur.  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 Menü öğesi bir hakkında iletişim kutusu gibi kullanıcı etkileşimi gerektirmeyen bir iletişim kutusu görüntüler bir işlev çalıştığında bir üç nokta gerekli değildir.  
  
#### <a name="opening-a-modal-dialog-box"></a>Kalıcı iletişim kutusunu açma  
 Bir iletişim kutusu, genellikle bir sözcük işlemci belgenin kenar boşluklarını ayarlama gibi bir etki alanına özgü işlevi gerçekleştirmek için menü öğesi seçilerek kullanıcı sonucu olarak gösterilir. Ek iletişim kutusu özgü yapılandırma gerektirse de gösteren bir pencere bir iletişim kutusu olarak normal bir pencere göstermek için benzer. Örnek oluşturma tüm işlemi, yapılandırmak ve iletişim kutusunu açıp aşağıdaki kodda gösterilir.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 Burada, kod varsayılan bilgileri (geçerli kenar boşlukları) iletişim kutusuna geçiyor. Ayrıca ayarı <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> iletişim kutusunu gösteren pencereyi başvuru özelliği. Genel olarak, her zaman tüm iletişim kutuları için ortak olan penceresi durumu ile ilgili davranışı sağlamak için bir iletişim kutusu için sahibi ayarlamanız gerekir (bkz [WPF Windows genel bakış](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md) daha fazla bilgi için).  
  
> [!NOTE]
>  Desteklemek için bir sahip sağlamalısınız [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Otomasyon iletişim kutuları için (bkz [UI Otomasyon genel bakış](../../../../docs/framework/ui-automation/ui-automation-overview.md)).  
  
 İletişim kutusu yapılandırıldıktan sonra kalıcı olarak çağrılarak gösterilen <xref:System.Windows.Window.ShowDialog%2A> yöntemi.  
  
#### <a name="validating-user-provided-data"></a>Kullanıcı tarafından sağlanan verileri doğrulama  
 Bir iletişim kutusu açılır ve kullanıcı gerekli verileri sağlar, bir iletişim kutusu aşağıdaki nedenlerle sağlanan veri geçerli olduğundan emin olmanın sorumludur:  
  
-   Güvenlik açısından bakıldığında, tüm giriş doğrulanmalıdır.  
  
-   Bir etki alanına özgü açısından bakıldığında, özel durumlar oluşturma kod tarafından işlenen veri doğrulama hatalı veri engeller.  
  
-   Kullanıcı deneyimi açısından bakıldığında, bir iletişim kutusu girmiş olduğunuz veri geçersiz göstererek kullanıcıların yardımcı olur.  
  
-   Özellikle uygulama Web Hizmetleri veya sunucu tabanlı veritabanları oluşturulduğunda performans açısından bakıldığında, istemci ve uygulama katmanları arasındaki gidiş dönüş sayısı çok katmanlı bir uygulama veri doğrulama azaltabilir.  
  
 İlişkili bir denetimde doğrulamak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bir doğrulama kuralı tanımlayın ve bağlama ile ilişkilendirmeniz gerekir. Bir doğrulama kuralı türetilen özel bir sınıftır <xref:System.Windows.Controls.ValidationRule>. Aşağıdaki örnek, bir doğrulama kuralı gösterir `MarginValidationRule`, ilişkili bir değer hangi denetimleri bir <xref:System.Double> ve belirli bir aralıkta değil.  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 Bu kodda bir doğrulama kuralı doğrulama mantığını kılarak uygulanan <xref:System.Windows.Controls.ValidationRule.Validate%2A> verileri doğrular ve uygun bir döndüren yöntemi <xref:System.Windows.Controls.ValidationResult>.  
  
 Doğrulama kuralının ilişkili denetimi ile ilişkilendirmek için aşağıdaki biçimlendirme kullanın.  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 Doğrulama kuralının ilişkilendirildiğinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] veri ilişkili denetime girildiğinde otomatik olarak uygular. Bir denetim geçersiz veri içerdiğinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geçersiz denetim etrafında kırmızı bir sınır aşağıdaki resimde gösterildiği gibi görüntülenir.  
  
 ![Geçersiz sol kenar boşluğu](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure7.png "DialogBoxesOverviewFigure7")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Geçerli veri girene kadar bir kullanıcı için geçersiz denetim kısıtlamaz. Bir iletişim kutusu için iyi davranış budur; bir kullanıcı bir iletişim kutusu denetimlerinde verileri geçerli olup olmadığını serbestçe gidebilirsiniz olmalıdır. Ancak, bir kullanıcı, geçersiz veri ve tuşuna girebilirsiniz yani **Tamam** düğmesi. Bu nedenle, kodunuzu ayrıca bir iletişim kutusu içindeki tüm denetimler doğrulamak gereken kutusunu **Tamam** düğmesi işleyerek basılı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 Bu kod bir pencere tüm bağımlılık nesnelerde numaralandırır ve geçersiz varsa (tarafından döndürülen <xref:System.Windows.Controls.Validation.GetHasError%2A>, geçersiz denetim odağı alır `IsValid` yöntemi döndürür `false`, ve pencere geçersiz olarak kabul edilir.  
  
 Bir iletişim kutusu geçerli olduğunda, onu güvenle kapatmak dönün ve. Dönüş işleminin bir parçası olarak, arama işlevi için bir sonuç döndürmesi gerekir.  
  
#### <a name="setting-the-modal-dialog-result"></a>Kalıcı iletişim sonucu ayarlama  
 Bir iletişim kutusunu kullanarak açma <xref:System.Windows.Window.ShowDialog%2A> temelde gibi bir yöntem çağırma olduğu: iletişim kutusu kullanılarak açılmasını kod <xref:System.Windows.Window.ShowDialog%2A> kadar bekler <xref:System.Windows.Window.ShowDialog%2A> döndürür. Zaman <xref:System.Windows.Window.ShowDialog%2A> döndürür, işleme devam etmek veya işlemi durdurmak için bağımsız olarak bağlı olup olmadığını karar vermek için ihtiyaçlarını adlı kod kullanıcı basılı **Tamam** düğmesini veya **iptal** düğmesi. Bu karara kolaylaştırmak için iletişim kutusu olarak kullanıcının seçimini döndürmesi gerekir bir <xref:System.Boolean> sunucudan döndürülen değer <xref:System.Windows.Window.ShowDialog%2A> yöntemi.  
  
 Zaman **Tamam** düğmesine tıklandığında, <xref:System.Windows.Window.ShowDialog%2A> döndürmelidir `true`. Bu ayar sağlanır <xref:System.Windows.Window.DialogResult%2A> özelliği iletişim kutusunda **Tamam** düğmesine tıklandığında.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 Bu ayarı Not <xref:System.Windows.Window.DialogResult%2A> özelliği de penceresi otomatik olarak kapatmak, açıkça çağırın ihtiyacını ortadan kaldırır neden <xref:System.Windows.Window.Close%2A>.  
  
 Zaman **iptal** düğmesine tıklandığında, <xref:System.Windows.Window.ShowDialog%2A> döndürmelidir `false`, aynı zamanda gerektiren ayarı <xref:System.Windows.Window.DialogResult%2A> özelliği.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 Bir düğme zaman 's <xref:System.Windows.Controls.Button.IsCancel%2A> özelliği ayarlanmış `true` ve ya da kullanıcı **iptal** düğmesini veya ESC tuşuna <xref:System.Windows.Window.DialogResult%2A> ayarlandığında otomatik olarak `false`. Aşağıdaki biçimlendirmede işlemek için gerek kalmadan önceki kod aynı etkiye sahip <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 Bir iletişim kutusu otomatik olarak döndürür `false` kullanıcı bastığında **Kapat** düğmesini başlık çubuğunda veya seçer **Kapat** menü öğesinden **sistem** menüsü.  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Kalıcı iletişim kutusundan dönen veri işleme  
 Zaman <xref:System.Windows.Window.DialogResult%2A> ayarlanmış bir iletişim kutusu tarafından açtığınız işlevi iletişim kutusu sonucunu inceleyerek alabilirsiniz <xref:System.Windows.Window.DialogResult%2A> özelliği zaman <xref:System.Windows.Window.ShowDialog%2A> döndürür.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 İletişim sonucu ise `true`, işlevi, bir ipucu olarak almak ve kullanıcı tarafından sağlanan verileri işlemek için kullanır.  
  
> [!NOTE]
>  Sonra <xref:System.Windows.Window.ShowDialog%2A> döndürdü bir iletişim kutusu olamaz yeniden açılacak. Bunun yerine, yeni bir örneğini oluşturmanız gerekir.  
  
 İletişim sonucu ise `false`, uygun şekilde işleme işlevi bitmelidir.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Kalıcı olmayan özel bir iletişim kutusu oluşturma  
 Kalıcı olmayan iletişim kutusu Bul iletişim kutusu aşağıdaki şekilde gösterildiği gibi modal iletişim kutusu olarak aynı temel görünüme sahiptir.  
  
 ![Bul iletişim kutusu](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure6.PNG "DialogBoxesOverviewFigure6")  
  
 Ancak, aşağıdaki bölümlerde açıklandığı gibi biraz farklı davranıştır.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusunu açma  
 Kalıcı olmayan iletişim kutusu çağırarak açıldığında <xref:System.Windows.Window.Show%2A> yöntemi.  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 Farklı <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> hemen döndürür. Kalıcı olmayan iletişim kutusu kapatılır ve bu nedenle, ne zaman bir iletişim kutusu sonuç denetleyin veya başka bir işleme için iletişim kutusundan veri alma hakkında bilgi sahibi değildir, bu nedenle, arama penceresinde bildiremez. Bunun yerine, iletişim kutusu veri işleme için arama penceresine dönmek için alternatif bir yol oluşturması gerekir.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusundan dönen veri işleme  
 Bu örnekte, `FindDialogBox` bir veya daha fazla bulma ana penceresinde, belirli herhangi sıklığı Aranan metin bağlı olarak sonuçlar döndürebilir. Bir modal iletişim kutusu olduğu gibi bir kalıcı olmayan iletişim kutusu özelliklerini kullanarak sonuçlar döndürebilir. Ancak, iletişim kutusu sahip pencere bu özellikleri denetlemek ne zaman bilmek ister. Bunu yapmanın bir yolu iletişim kutusu metin bulunduğunda bir olayı uygulamak olur. `FindDialogBox`uygulayan `TextFoundEvent` bu amaç için bir temsilci hangi ilk gerektirir.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 Kullanarak `TextFoundEventHandler` temsilci, `FindDialogBox` uygulayan `TextFoundEvent`.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 Sonuç olarak, `Find` arama sonucu bulunduğunda olay yükseltebilirsiniz.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 Sahip pencereyi ardından kaydetme ve bu olay işleme gerekir.  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusunu kapatma  
 Çünkü <xref:System.Windows.Window.DialogResult%2A> , kalıcı olmayan bir iletişim sistemiyle kapatılması, ayarlanmış olması gerekmez aşağıdakiler dahil mekanizmalar:  
  
-   Tıklatarak **Kapat** başlık çubuğunda düğmesi.  
  
-   ALT + F4 tuşuna basın.  
  
-   Seçme **Kapat** gelen **sistem** menüsü.  
  
 Alternatif olarak, kodunuzu çağırabilirsiniz <xref:System.Windows.Window.Close%2A> zaman **Kapat** düğmesine tıklandığında.  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Açılan Pencereye Genel Bakış](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [İletişim kutusu örneği](http://go.microsoft.com/fwlink/?LinkID=159984)  
 [ColorPicker özel denetim örneği](http://go.microsoft.com/fwlink/?LinkID=159977)

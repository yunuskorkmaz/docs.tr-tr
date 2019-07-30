---
title: Yazdırmaya Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: 31574df75ebd8ecde11f45dbcce86550bbb8c107
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629687"
---
# <a name="printing-overview"></a>Yazdırmaya Genel Bakış
Microsoft .NET Framework ile, Windows Presentation Foundation (WPF) kullanan uygulama geliştiricilerinin zengin yeni bir yazdırma ve yazdırma sistemi yönetim API 'Leri kümesi vardır. İle [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], bu yazdırma sistemi geliştirmelerinden bazıları, yönetilmeyen kod kullanan uygulamalar ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] geliştiriciler oluşturan geliştiriciler tarafından da kullanılabilir. Bu yeni işlevin çekirdeği, yeni [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] dosya biçimi [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ve yazdırma yoludur.  
  
 Bu konuda aşağıdaki bölümleri içerir.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>XPS hakkında  
 XPS elektronik belge biçimidir, bir biriktirme dosyası biçimi ve sayfa açıklaması dilidir. Platformlar arası belgeler oluşturmak için, [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]ve diğer sektör standartlarını kullanan açık bir belge biçimidir. XPS dijital belge oluşturma, paylaşılan, yazdırılma, görüntülenen ve arşivlenen işlemleri basitleştirir. XPS hakkında daha fazla bilgi için bkz. [XPS belgeleri](/windows/desktop/printdocs/documents).  
  
 Kullanarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] XPS tabanlı içeriklerin yazdırılması için çeşitli teknikler, programlı bir şekilde [XPS dosyaları yazdırma](how-to-programmatically-print-xps-files.md)bölümünde gösterilmiştir. Bu konuda yer alan içeriğin gözden geçirilmesi sırasında bu örneklere başvurmak yararlı olabilir. (Yönetilmeyen kod geliştiricileri [MXDC_ESCAPE işlevi](/windows/desktop/printdocs/mxdc-escape)için belgeler görmelidir. Windows Forms geliştiricilerin, tam <xref:System.Drawing.Printing> [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazdırma yolunu desteklemeyen, ancak karma GDI 'dan XPS 'ye yazdırma yolunu desteklediği ad alanındaki API 'yi kullanması gerekir. Aşağıdaki **yazdırma yolu mimarisini** inceleyin.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>XPS yazdırma yolu  
 XML Kağıt Belirtimi (XPS) yazdırma yolu, yazdırmanın Windows uygulamalarında [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] nasıl işlendiğini tekrar tanımlayan yeni bir özelliktir. [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] Bir belge sunumu dilini (RTF gibi), bir yazdırma biriktiricisi biçimini (örneğin, WMF) ve bir sayfa açıklaması dilini (PCL veya PostScript gibi) değiştirebilir; yeni yazdırma yolu, XPS biçimini uygulama yayınından yazdırma sürücüsü veya cihazında son işleme.  
  
 XPS yazdırma yolu, geliştirici, geliştirilmiş renk desteği ve önemli ölçüde iyileştirilmiş baskı performansı gibi [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] geliştiriciler için çeşitli avantajlar sunan XPS yazıcı sürücüsü modeli (XPSDrv) üzerine kurulmuştur. (XPSDrv hakkında daha fazla bilgi için bkz. [Windows Sürücü Seti belgeleri](/windows-hardware/drivers/).)  
  
 XPS belgelerinin yazdırma biriktiricisinin işlemi, Windows 'un önceki sürümlerindeki ile aynıdır. Ancak, mevcut [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolunun yanı sıra XPS yazdırma yolunu destekleyecek şekilde geliştirilmiştir. Yeni yazdırma yolu yerel olarak bir XPS biriktirme dosyası kullanır. Önceki sürümleri [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] için yazılan Kullanıcı modu yazıcı sürücüleri çalışmaya devam ederken, XPS yazdırma yolunu kullanabilmeniz için bir XPS yazıcı sürücüsü (XPSDrv) gereklidir.  
  
 XPS yazdırma yolunun avantajları önemlidir ve şunları içerir:  
  
- [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)]yazdırma desteği  
  
- Kanal başına 32 bit (bpc), CMYK, adlandırılmış renkler, n-mürekkepler ve saydamlık ve degradelerin yerel desteği dahil olmak üzere gelişmiş renk profillerinin yerel desteği.  
  
- Hem .NET Framework [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] hem de tabanlı uygulamalar için iyileştirilmiş yazdırma performansı.  
  
- Endüstri standardı XPS biçimi.  
  
 Temel yazdırma senaryolarında, basit ve sezgisel bir API, Kullanıcı arabirimi, yapılandırma ve iş gönderimi için tek bir giriş noktasıyla birlikte kullanılabilir. Gelişmiş senaryolar için, özelleştirme (veya tümüne Hayır [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ), zaman uyumlu veya zaman uyumsuz yazdırma ve toplu yazdırma özellikleri için ek bir destek eklenmiştir. Her iki seçenek de tam veya kısmi güven modunda yazdırma desteği sağlar.  
  
 XPS, genişletilebilirlik göz önünde bulundurularak tasarlandı. Genişletilebilirlik çerçevesini kullanarak, Özellikler ve yetenekler, XPS 'ye modüler bir şekilde eklenebilir. Genişletilebilirlik özellikleri şunlardır:  
  
- Şemayı yazdır. Ortak şema düzenli olarak güncelleştirilir ve cihaz yeteneklerinin hızlı uzantısını sunar. (Bkz. **PrintTicket ve PrintCapabilities** .)  
  
- Genişletilebilir filtre işlem hattı. XPS yazıcı sürücüsü (XPSDrv) filtre işlem hattı, XPS belgelerinin hem doğrudan hem de ölçeklenebilir yazdırılmasını etkinleştirmek üzere tasarlanmıştır. Daha fazla bilgi için bkz. [XPSDrv yazıcı sürücüleri](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Yazdırma yolu mimarisi  
 Hem hem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de .NET Framework uygulamalar XPS 'yi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] destekleirken Windows Forms uygulamalar XPS yazıcı [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] sürücüsü (XPSDrv) için XPS biçimli içerik oluşturmak üzere bir-XPS dönüştürmesi kullanır. Bu uygulamaların XPS yazdırma yolunu kullanması gerekmez ve gelişmiş meta dosyası (EMF) tabanlı yazdırma kullanmaya devam edebilir. Ancak, çoğu XPS özelliği ve geliştirmesi yalnızca XPS yazdırma yolunu hedefleyen uygulamalar tarafından kullanılabilir.  
  
 Windows Forms, ve uygulamaları tarafından kullanılan ve uygulamalar tarafından [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] desteklenen, XPS yazıcı sürücüsü (XPSDrv), XPS biçimine [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] dönüştürmeyi destekler. XPSDrv modeli, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamaların belge yazdırabilmesi [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] için XPS 'ye [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yönelik bir dönüştürücü de sağlar. Uygulamalar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] için, yazma işleminin hedef yazdırma [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] sırasının bir XPSDrv sürücüsüne sahip olmadığı her <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> seferinde, XPS <xref:System.Windows.Xps.XpsDocumentWriter> biçimine dönüştürme, sınıfının <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve yöntemleri tarafından otomatik olarak gerçekleştirilir. (Windows Forms uygulamalar belge yazdıramaz [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] .)  
  
 Aşağıdaki çizim, yazdırma alt sistemini gösterir ve tarafından [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]sunulan bölümleri ve yazılım ve donanım satıcıları tarafından tanımlanan bölümleri tanımlar:  
  
 ![Ekran görüntüsü XPS Yazdırma sistemini gösterir.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Temel XPS yazdırma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]hem temel hem de Gelişmiş API tanımlar. Kapsamlı yazdırma özelleştirmesi gerektirmeyen veya XPS özelliği 'nin tamamına erişebilen uygulamalar için, temel yazdırma desteği kullanılabilir. Temel yazdırma desteği, çok az yapılandırma ve özelliklerin tanıdık [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]olması için bir yazdırma iletişim kutusu denetimi aracılığıyla sunulur. Bu basitleştirilmiş yazdırma modeli kullanılarak birçok XPS özelliği mevcuttur.  
  
#### <a name="printdialog"></a>PrintDialog  
 Denetim, yapılandırma ve XPS işi gönderimi için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]tek bir giriş noktası sağlar. <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Denetimin örneği oluşturma ve kullanma hakkında bilgi için bkz. [bir yazdırma Iletişim kutusu çağırma](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Gelişmiş XPS yazdırma  
 XPS özelliklerinin tamamına erişmek için gelişmiş yazdırma API 'sinin kullanılması gerekir. Birkaç ilgili API aşağıda daha ayrıntılı olarak açıklanmıştır. XPS yazdırma yolu API 'lerinin tüm listesi için bkz <xref:System.Windows.Xps> . ve <xref:System.Printing> ad uzayı başvuruları.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket ve PrintCapabilities  
 <xref:System.Printing.PrintTicket> Ve<xref:System.Printing.PrintCapabilities> sınıfları, gelişmiş XPS özelliklerinin temelidir. Her iki tür nesne, [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] harmanlama, iki taraflı yazdırma, Zımbalama vb. gibi yazdırma yönelimli özelliklerin yapılarıdır. Bu yapılar, yazdırma şeması tarafından tanımlanır. Bir <xref:System.Printing.PrintTicket> yazıcıya bir yazdırma işini nasıl işleyeceğini bildirir. <xref:System.Printing.PrintCapabilities> Sınıfı, bir yazıcının yeteneklerini tanımlar. Bir yazıcının yeteneklerini sorgulayarak, yazıcının desteklenen özelliklerinden tam <xref:System.Printing.PrintTicket> olarak yararlanabilen bir oluşturulabilir. Benzer şekilde, desteklenmeyen özelliklerden kaçınılabilir.  
  
 Aşağıdaki örnek, bir yazıcının nasıl sorgulanacağını <xref:System.Printing.PrintCapabilities> ve kod <xref:System.Printing.PrintTicket> kullanarak nasıl oluşturulacağını gösterir.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>YazıcıSunucusu ve PrintQueue  
 Sınıfı bir ağ yazdırma sunucusunu temsil eder ve sınıfı <xref:System.Printing.PrintQueue> , onunla ilişkili bir yazıcıyı ve çıkış işi kuyruğunu temsil eder. <xref:System.Printing.PrintServer> Birlikte, bu API 'Ler bir sunucunun yazdırma işlerinin gelişmiş yönetimine izin verir. Bir veya türetilmiş sınıflarından biri, bir <xref:System.Printing.PrintQueue>yönetmek için kullanılır. <xref:System.Printing.PrintServer> <xref:System.Printing.PrintQueue.AddJob%2A> Yöntemi, kuyruğa yeni bir yazdırma işi eklemek için kullanılır.  
  
 Aşağıdaki örnek, kod kullanılarak nasıl oluşturulacağını <xref:System.Printing.LocalPrintServer> ve varsayılan <xref:System.Printing.PrintQueue> olarak nasıl erişileceğini gösterir.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter>, <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Printing.PrintQueue>Ve yöntemleriileXPSbelgelerinibiröğesineyazmakiçinkullanılır<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> . Örneğin, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> yöntemi XPS belgesini ve <xref:System.Printing.PrintTicket> zaman uyumlu olarak çıktısını almak için kullanılır. Yöntemi <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> , bir XPS belgesini ve <xref:System.Printing.PrintTicket> zaman uyumsuz olarak çıktısını almak için kullanılır.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Xps.XpsDocumentWriter> using kodunun nasıl oluşturulacağını göstermektedir.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Yöntemler de yazdırma yollarını sağlar. Bkz. [Program aracılığıyla XPS dosyalarını yazdırma](how-to-programmatically-print-xps-files.md). daha fazla bilgi için.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>GDI yazdırma yolu  
 Uygulamalar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] XPS yazdırma yolunu yerel olarak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] destekleirken ve Windows Forms uygulamalar, bazı XPS özelliklerinden de faydalanabilir. XPS yazıcı sürücüsü (XPSDrv), temel çıktıyı [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] XPS biçimine dönüştürebilir. Gelişmiş senaryolar için, [MICROSOFT XPS Belge Dönüştürücüsü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)kullanılarak içeriğin özel dönüştürmesi desteklenir. Benzer şekilde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , uygulamalar, <xref:System.Windows.Xps.XpsDocumentWriter> sınıfının <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ya <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> da [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yöntemlerinden birini çağırarak ve XPSDrv olmayan bir yazıcıyı hedef yazdırma kuyruğu olarak tanımlayarak yazdırma yoluna da çıkış yapabilir.  

XPS işlevselliği veya desteği gerektirmeyen uygulamalar için geçerli [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolu değişmeden kalır.  
  
- [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] Yazdırma yolu ve çeşitli XPS dönüştürme seçenekleri hakkında ek başvuru malzemeleri için bkz. [Microsoft XPS Belge Dönüştürücüsü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) ve [XPSDrv yazıcı sürücüleri](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>XPSDrv sürücü modeli  
 XPS yazdırma yolu, XPS özellikli bir yazıcıya veya sürücüye yazdırırken yerel yazdırma kuyruğu biçimi olarak XPS kullanarak biriktirici verimliliğini geliştirir. Basitleştirilmiş biriktirme işlemi, belge belleğe alınmadan önce, EMF veri dosyası gibi bir ara biriktirme dosyası oluşturma gereksinimini ortadan kaldırır. Daha küçük biriktirme dosya boyutları ile XPS yazdırma yolu, ağ trafiğini azaltabilir ve yazdırma performansını iyileştirebilir.  
  
 EMF, uygulama çıkışını işleme Hizmetleri [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] için bir dizi çağrı olarak temsil eden kapalı bir biçimdir. EMF 'den farklı olarak, XPS biriktirme biçimi, XPS tabanlı bir yazıcı sürücüsüne (XPSDrv) çıkış yaparken daha fazla yorum gerektirmeden gerçek belgeyi temsil eder. Sürücüler doğrudan biçimdeki veriler üzerinde çalışabilir. Bu özellik, EMF dosyalarını ve [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]tabanlı yazdırma sürücülerini kullandığınızda gereken veri ve renk alanı dönüştürmelerini ortadan kaldırır.  
  
 , EMF eşdeğerlerine kıyasla bir XPS yazıcı sürücüsünü (XPSDrv) hedefleyen XPS belgelerini kullandığınızda biriktirme dosya boyutları genellikle azaltılır; Ancak, özel durumlar vardır:  
  
- Çok karmaşık, çok katmanlı veya yeterince yazılamaz bir vektör grafiği aynı grafiğin bit eşlemli sürümünden daha büyük olabilir.  
  
- Ekran görüntüleme amacıyla, XPS dosyaları cihaz yazı tiplerini ve bilgisayar tabanlı yazı tiplerini de katıştırır; GDI biriktirme dosyaları cihaz yazı tiplerini katıştırmaz. Ancak her iki tür yazı tipi de alt kümelenir (aşağıya bakın) ve yazıcı sürücüleri dosyayı yazıcıya iletmeden önce cihaz yazı tiplerini kaldırabilir.  
  
 Biriktirme boyutu azaltma çeşitli mekanizmalar aracılığıyla gerçekleştirilir:  
  
- **Yazı tipi alt kümeleme**. Yalnızca gerçek belge içinde kullanılan karakterler XPS dosyasında depolanır.  
  
- **Gelişmiş grafik desteği**. Saydamlık ve gradyan temel elemanlar için yerel destek, [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgedeki içeriğin Rasterleştirmeye karşı.  
  
- **Ortak kaynakların tanımlanması**. Birden çok kez kullanılan kaynaklar (bir kurumsal logoyu temsil eden bir görüntü gibi), paylaşılan kaynaklar olarak değerlendirilir ve yalnızca bir kez yüklenir.  
  
- **ZIP sıkıştırması**. Tüm XPS belgeleri ZIP sıkıştırması kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Nasıl Yapılır Konuları](printing-how-to-topics.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [XPS belgeleri](/windows/desktop/printdocs/documents)
- [Belge Serileştirme ve Depolama](document-serialization-and-storage.md)
- [Microsoft XPS Belge Dönüştürücüsü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)

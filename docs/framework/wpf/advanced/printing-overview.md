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
ms.openlocfilehash: acfc252708bf8be7abacb1adc2968122501315a0
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860206"
---
# <a name="printing-overview"></a>Yazdırmaya Genel Bakış
Microsoft .NET Framework ile Windows Presentation Foundation (WPF) kullanarak uygulama geliştiricileri sahip yeni zengin bir yazdırma ve yazdırma sistemi yönetimi API'leri. İle [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], bazı bu yazdırma sistemi geliştirmeler de oluşturma geliştiricilere sunulan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamaların ve geliştiricilerin kullanarak yönetilmeyen kod. Bu yeni işlevselliği özünde yenilikler [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] dosya biçimi ve [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazdırma yolu.  
  
 Bu konuda aşağıdaki bölümleri içerir.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>XPS hakkında  
 XPS, bir elektronik belge biçimi, bir Biriktirme dosyası biçimi ve sayfa açıklaması dili içindir. Kullanan açık belge biçimi olan [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]ve platformlar arası belgeleri oluşturmak için diğer endüstri standartları. XPS olarak dijital belgeleri oluşturulan, paylaşılan, yazdırılan, görüntülenen arşivlenmiş ve işlemini basitleştirir. XPS hakkında ek bilgi için bkz. [XPS belgeleri](/windows/desktop/printdocs/documents).  
  
 Yazdırma XPS tabanlı içerik kullanmaya yönelik çeşitli teknikler [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] örneklerde gösterildiği [program aracılığıyla XPS dosyalarını yazdırma](how-to-programmatically-print-xps-files.md). Bu konuda yer alan içeriği gözden geçirme sırasında bu örnekleri başvuru daha faydalı olabilir. (Yönetilmeyen kod geliştiriciler için belgeleri görmeniz [MXDC_ESCAPE işlevi](/windows/desktop/printdocs/mxdc-escape). Windows Forms geliştiriciler API'de kullanmalıdır <xref:System.Drawing.Printing> tam desteklemeyen ad alanı [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazdırma yolu, ancak bir karma GDI XPS yazdırma yolu yoksa desteği. Bkz: **yazdırma yolu mimarisi** aşağıda.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>XPS yazdırma yolu  
 XML Kağıt Belirtimi (XPS) yazdırma yolu bir yenilikler [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] yazdırma Windows uygulamalarında nasıl işlendiğini'ı yeniden tanımladığı özelliği. Çünkü [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] (RTF gibi) bir belge sunum dili (WMF gibi) bir yazdırma biriktiricisi biçimi ve sayfa açıklaması dili (örneğin, PCL veya PostScript'i) değiştirebilirsiniz; yeni yazdırma yolu için uygulama yayından XPS biçiminde tutar. Son işleme yazdırma sürücüsü veya cihaz.  
  
 XPS yazdırma yolu, geliştiriciler için gibi çeşitli avantajlar sağlayan XPS yazıcı sürücüsü modeli üzerinde (XPSDrv) yerleşik [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] Yazdırma rengi desteği geliştirildi ve yazdırma performansı önemli ölçüde geliştirildi. (XPSDrv hakkında daha fazla bilgi için bkz. [Windows Sürücü Seti belgelerine](/windows-hardware/drivers/).)  
  
 XPS belgeleri yazdırma biriktiricisi işleminde temelde Windows önceki sürümlerindekilerle aynıdır. Ancak, bunu varolan yanı sıra XPS yazdırma yolu destekleyecek şekilde geliştirilmiştir [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolu. Yeni yazdırma yolunun yerel olarak XPS Biriktirme dosyası kullanır. While önceki sürümleri için yazılmış kullanıcı modu yazıcı sürücülerini [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] çalışmaya devam eder, XPS yazıcı sürücüsü (XPSDrv) XPS yazdırma yolu kullanmak için gereklidir.  
  
 XPS yazdırma yolu avantajlarını önemlidir ve şunları içerir:  
  
- [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] yazdırma desteği  
  
- Kanal (bpc) CMYK başına 32 bit dahil gelişmiş renk profillerinin yerel destek adlı renkleri, n-mürekkep ve saydamlık gradyanlar ve yerel destek.  
  
- Hem .NET Framework için yazdırma performansı geliştirildi ve [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] tabanlı uygulamalar.  
  
- Sektör standardı XPS biçim.  
  
 Temel yazdırma senaryoları için basit ve sezgisel bir API kullanıcı arabirimi, yapılandırma ve iş gönderme için tek giriş noktası ile kullanılabilir. Gelişmiş senaryolar için bir ek destek için eklenen [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] özelleştirme (veya hiç [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hiç), zaman uyumlu veya zaman uyumsuz yazdırma ve yazdırma yetenekleri toplu. Seçeneklerin tam veya kısmi güven modunda yazdırma desteği sağlar.  
  
 XPS aklınızda genişletilebilirlik ile tasarlanmıştır. Genişletilebilirlik Çerçevesi'ni kullanarak, özellikler ve yetenekler için XPS modüler bir şekilde eklenebilir. Genişletilebilirlik özellikleri şunlardır:  
  
- Şema yazdırın. Ortak şema düzenli olarak güncelleştirilir ve cihaz özelliklerinden hızlı uzantısını etkinleştirir. (Bkz **PrintTicket ve PrintCapabilities** aşağıda.)  
  
- Genişletilebilir filtre ardışık düzen. XPS yazıcı sürücüsü (XPSDrv) filtre ardışık düzen, XPS belgeleri doğrudan ve ölçeklenebilir yazdırmayı etkinleştirmek için tasarlanmıştır. Daha fazla bilgi için [XPSDrv yazıcı sürücülerini](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Yazdırma yolu mimarisi  
 Her ikisi de while [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve .NET Framework uygulamaları, XPS, destek [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms uygulamaları bir [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] XPS'ye XPS oluşturmak için dönüştürme biçimlendirilmiş XPS yazıcı sürücüsü (XPSDrv) için içerik. Bu uygulamalar, XPS yazdırma yolu kullanmak için gerekli değildir ve kullanmaya devam edebilirsiniz [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] yazdırma bağlı. Ancak, çoğu XPS özellikler ve geliştirmeler yalnızca XPS yazdırma yolu hedefleyen uygulamalar için kullanılabilir.  
  
 XPSDrv tabanlı yazıcılar tarafından kullanımını etkinleştirmek için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms uygulamaları XPS yazıcı sürücüsü (XPSDrv) dönüştürülmesini destekler [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] XPS'ye biçimlendirin. XPSDrv modeli XPS'ye bir dönüştürücü ayrıca sağlar [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] biçimi böylece [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamaları yazdırabilirsiniz [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgeleri. İçin [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları, dönüştürme için XPS [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] biçimi tarafından otomatik olarak yapılır <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinin <xref:System.Windows.Xps.XpsDocumentWriter> yazma işleminin hedef yazdırma sırasını XPSDrv sürücü yok. her sınıf. (Windows Forms uygulamaları olamaz yazdırma [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgeler.)  
  
 Aşağıdaki çizim yazdırma alt sistemi gösterir ve tarafından sağlanan bölümleri tanımlar [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]ve yazılım ve donanım satıcıları tarafından tanımlanan bölümleri:  
  
 ![Ekran görüntüsü, XPS yazdırma sistemi gösterir.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Temel XPS yazdırma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Her iki temel tanımlar ve Gelişmiş [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Kapsamlı yazdırma özelleştirme veya tam XPS özelliğe gerek yoktur, bu uygulamalar için ayarlanmış, temel yazdırma desteği sunulmaktadır. En az yapılandırma gerektirir ve bir bilinen özellikleri bir yazdırma iletişim kutusu denetim temel yazdırma desteği kullanıma sunulan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Birçok XPS bu Basitleştirilmiş yazdırma model kullanılarak özellikleridir.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Denetim için tek giriş noktası sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], yapılandırma ve XPS iş gönderme. Denetim oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Yazdır iletişim kutusu çağırma](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Gelişmiş XPS yazdırma  
 XPS özelliklerin tam bir set erişmek için Gelişmiş yazdırma API kullanılmalıdır. Birkaç ilgili API aşağıda daha ayrıntılı olarak açıklanmıştır. XPS yazdırma yolu API'leri tam bir listesi için bkz. <xref:System.Windows.Xps> ve <xref:System.Printing> ad alanı başvurularını.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket ve PrintCapabilities  
 <xref:System.Printing.PrintTicket> Ve <xref:System.Printing.PrintCapabilities> Gelişmiş XPS özelliklerine temel sınıflardır. Her iki tür nesneleri [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] yazdırma yönelimli özelliği harmanlaması, iki taraflı yazdırma, zımbalama, vb. gibi yapıları biçimlendirilmiş. Bu yapılar, yazdırma şeması tarafından tanımlanır. A <xref:System.Printing.PrintTicket> bir yazdırma işi işlemek nasıl bir yazıcı bildirir. <xref:System.Printing.PrintCapabilities> Sınıfı bir yazıcı yeteneklerini tanımlar. Bir yazıcı yeteneklerini sorgulamak bir <xref:System.Printing.PrintTicket> tam yararlanır yazıcı desteklenen özellikler oluşturulabilir. Benzer şekilde, desteklenmeyen özellikler önlenebilir.  
  
 Aşağıdaki örnek nasıl sorgulanacağını gösterir <xref:System.Printing.PrintCapabilities> yazıcının oluşturup bir <xref:System.Printing.PrintTicket> kod kullanarak.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer ve PrintQueue  
 <xref:System.Printing.PrintServer> Sınıfı, bir ağ yazdırma sunucusu temsil eder ve <xref:System.Printing.PrintQueue> yazıcı ve onunla ilişkili çıkış iş kuyruğu sınıfı temsil eder. Birlikte, bu API'ler, bir sunucunun yazdırma işlerinin Gelişmiş Yönetim izin verir. A <xref:System.Printing.PrintServer>, ya da ondan türetilen sınıflardan birini yönetmek için kullanılan bir <xref:System.Printing.PrintQueue>. <xref:System.Printing.PrintQueue.AddJob%2A> Yöntemi yeni bir yazdırma işi kuyruğa eklemek için kullanılır.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Printing.LocalPrintServer> ve varsayılan erişim <xref:System.Printing.PrintQueue> kodu kullanarak.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Bir <xref:System.Windows.Xps.XpsDocumentWriter>, kendi çok ile <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemleri, XPS belgeleri yazmak için kullanılan bir <xref:System.Printing.PrintQueue>. Örneğin, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> yöntemi dokument XPS çıktısını almak için kullanılır ve <xref:System.Printing.PrintTicket> zaman uyumlu olarak. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> Yöntemi dokument XPS çıktısını almak için kullanılır ve <xref:System.Printing.PrintTicket> zaman uyumsuz olarak.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Xps.XpsDocumentWriter> kod kullanarak.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Yöntemleri de yazdırmak için yollar sağlar. Bkz: [program aracılığıyla XPS dosyalarını yazdırma](how-to-programmatically-print-xps-files.md). Ayrıntılar için.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>GDI yazdırma yolu  
 Sırada [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yerel olarak destekleyen uygulamaları XPS yazdırma yolu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms uygulamalarının da bazı XPS özelliklerden yararlanın. XPS yazıcı sürücüsü (XPSDrv) dönüştürebilirsiniz [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] XPS biçiminde çıktı bağlı. Gelişmiş senaryolar için içerik özel dönüştürme kullanarak desteklenen [Microsoft XPS Belge dönüştürücü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Benzer şekilde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları de için çıkış [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] birini çağırarak yazdırma yolu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> veya <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinin <xref:System.Windows.Xps.XpsDocumentWriter> sınıfı ve hedef olarak XpsDrv yazıcısı belirleme yazdırma sırası.  

Gerektirmeyen XPS işlevselliği veya desteği, geçerli uygulamalar için [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolu değişmeden kalır.  
  
- Hakkında referans materyalleri için [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yolu ve çeşitli XPS dönüştürme seçenekleri, bkz [Microsoft XPS Belge dönüştürücü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) ve [XPSDrv yazıcı sürücülerini](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>XPSDrv sürücü modeli  
 XPS yazdırma yolu XPS yerel yazdırma biriktiricisi biçimi olarak bir XPS'ye yazdırmayı kullanarak biriktirici verimliliğini artırır.-yazıcı sürücüsü etkin. Basitleştirilmiş biriktirme işlemini gibi bir ara Biriktirme dosyası oluşturmak için ihtiyacını ortadan kaldıran bir [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] belge belleğe önce veri dosyası. XPS yazdırma yolu küçük biriktirme dosya boyutları ile ağ trafiğini azaltmak ve yazdırma performansı.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] Uygulama çıktısı çağırıyor bir dizi olarak temsil eden bir kapalı biçimi [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] oluşturma hizmetleri için. Aksine [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], XPS biriktirme biçimi, başka bir XPS tabanlı yazıcı sürücüsü (XPSDrv) çıkış yorumu gerektirmeden gerçek belgeyi temsil eder. Sürücüleri biçimde veriler üzerinde doğrudan çalışabilir. Bu özelliği kullandığınızda gerekli veri ve renk alanı dönüştürmeler ortadan [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] dosyaları ve [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]-yazıcı sürücülerinin bağlı.  
  
 XPS belgeleri, compared with bir XPS yazıcı sürücüsü (XPSDrv) hedef kullandığınızda, biriktirme dosya boyutları azaltılmış genellikle kendi [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] eşdeğerleri; ancak, özel durumlar vardır:  
  
- Çok karmaşık, çok katmanlı ya da verimsiz yazılı bir vektör grafik, bir grafiğin eşlemli sürümden büyük olamaz.  
  
- Ekran görüntüleme amacıyla XPS dosyaları cihaz yazı tipleri ve bunun yanı sıra bilgisayar tabanlı yazı tipleri katıştır; GDI yazdırma biriktiricisi dosyalarını, cihaz yazı tipleri katıştır değil ise. Ancak her iki yazı tiplerinin alt kümelenmiş (aşağıya bakın) türleridir ve yazıcı sürücülerini yazıcı dosyasına aktarmadan önce cihaz yazı tipleri kaldırabilirsiniz.  
  
 Biriktirme boyutu azaltma çeşitli mekanizmalar gerçekleştirilir:  
  
- **Yazı tipi alt kümeleme**. Yalnızca gerçek belgenin içinde kullanılan karakterler XPS dosyası depolanır.  
  
- **Gelişmiş grafik desteği**. Saydamlık ve gradyan temelleri için yerel destek önler içeriğinin tarama [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belge.  
  
- **Ortak kaynakları tanımlaması**. (Şirket logosunu temsil eden birden çok kez bir görüntü gibi) kullanılan kaynaklar, paylaşılan kaynaklar olarak kabul edilir ve yalnızca bir kez yüklenir.  
  
- **ZIP sıkıştırma**. Tüm XPS belgeleri ZIP sıkıştırma işlevini kullanır.  
  
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
- [Microsoft XPS Belge dönüştürücü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)

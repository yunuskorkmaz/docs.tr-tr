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
ms.openlocfilehash: 04ea64f0e6563012a3b272306df6be4575ed7659
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597701"
---
# <a name="printing-overview"></a>Yazdırmaya Genel Bakış
Microsoft .NET Framework ile Windows Presentation Foundation (WPF) kullanarak uygulama geliştiricilerin yeni zengin bir yazdırma ve yazdırma sistemi yönetimi sahip [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. İle [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], bazı bu yazdırma sistemi geliştirmeler de oluşturma geliştiricilere sunulan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamaların ve geliştiricilerin kullanarak yönetilmeyen kod. Bu yeni işlevselliği özünde yenilikler [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] dosya biçimi ve [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazdırma yolu.  
  
 Bu konuda aşağıdaki bölümleri içerir.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>XPS hakkında  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] bir elektronik belge biçimi, bir Biriktirme dosyası biçimi ve sayfa açıklaması dili içindir. Kullanan açık belge biçimi olan [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]ve platformlar arası belgeleri oluşturmak için diğer endüstri standartları. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tarafından dijital belgeleri oluşturulan, paylaşılan, yazdırılır, görüntülediğiniz arşivlenmiş ve işlemini basitleştirir. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], bkz: [XPS Web sitesi](https://www.microsoft.com/xps).  
  
 Yazdırma için çeşitli teknikler [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tabanlı içerik kullanarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] örneklerde gösterildiği [program aracılığıyla XPS dosyalarını yazdırma](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Bu konuda yer alan içeriği gözden geçirme sırasında bu örnekleri başvuru daha faydalı olabilir. (Yönetilmeyen kod geliştiriciler için belgeleri görmeniz [MXDC_ESCAPE işlevi](https://msdn.microsoft.com/library/windows/desktop/dd162739.aspx). Windows Forms geliştiriciler kullanmalıdır [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] içinde <xref:System.Drawing.Printing> tam desteklemeyen ad alanı [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazdırma yolu, ancak bir karma GDI XPS yazdırma yolu yoksa desteği. Bkz: **yazdırma yolu mimarisi** aşağıda.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>XPS yazdırma yolu  
 [!INCLUDE[TLA#tla_metro](../../../../includes/tlasharptla-metro-md.md)] Yazdırma yolu olan yeni bir [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] yazdırma Windows uygulamalarında nasıl işlendiğini'ı yeniden tanımladığı özelliği. Çünkü [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] (RTF gibi) bir belge sunum dili (WMF gibi) bir yazdırma biriktiricisi biçimi ve sayfa açıklaması dili (örneğin, PCL veya PostScript'i) değiştirebilirsiniz; yeni yazdırma yolu tutar [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] uygulama biçimi yazdırma sürücüsü ya da cihaz son işlemeye yayını.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Yazdırma yolu üzerine kurulmuştur [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] , geliştiriciler için gibi çeşitli avantajlar sağlayan yazıcı sürücüsü modelinde (XPSDrv) [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] Yazdırma rengi desteği geliştirildi ve yazdırma performansı önemli ölçüde geliştirildi. (XPSDrv hakkında daha fazla bilgi için bkz. [Windows Sürücü Geliştirme Seti](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
 Yazdırma Biriktiricisi için işlemi [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belgeleri olan temelde Windows önceki sürümlerindekilerle aynı. Ancak, onu desteklemek için geliştirilmiştir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yanı sıra mevcut yazdırma yolu [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolu. Yeni yazdırma yolunun yerel olarak kullanan bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Biriktirme dosyası. While önceki sürümleri için yazılmış kullanıcı modu yazıcı sürücülerini [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] çalışmaya devam edecek bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazıcı sürücüsü (XPSDrv) kullanmak için gerekli [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu.  
  
 Avantajlarını [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu önemlidir ve içerir:  
  
-   [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] yazdırma desteği  
  
-   Kanal (bpc) CMYK başına 32 bit dahil gelişmiş renk profillerinin yerel destek adlı renkleri, n-mürekkep ve saydamlık gradyanlar ve yerel destek.  
  
-   Hem .NET Framework için yazdırma performansı geliştirildi ve [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] tabanlı uygulamalar.  
  
-   Sektör standardı [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biçimi.  
  
 Temel yazdırma senaryolar için basit ve sezgisel bir [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] kullanıcı arabirimi, yapılandırma ve iş gönderme için tek giriş noktası ile kullanılabilir. Gelişmiş senaryolar için bir ek destek için eklenen [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] özelleştirme (veya hiç [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hiç), zaman uyumlu veya zaman uyumsuz yazdırma ve yazdırma yetenekleri toplu. Seçeneklerin tam veya kısmi güven modunda yazdırma desteği sağlar.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ile genişletilebilirlik düşünülerek tasarlanmıştır. Genişletilebilirlik Çerçevesi'ni kullanarak, özellikler ve yetenekler eklenebilir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] modüler bir şekilde. Genişletilebilirlik özellikleri şunlardır:  
  
-   Şema yazdırın. Ortak şema düzenli olarak güncelleştirilir ve cihaz özelliklerinden hızlı uzantısını etkinleştirir. (Bkz **PrintTicket ve PrintCapabilities** aşağıda.)  
  
-   Genişletilebilir filtre ardışık düzen. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Yazıcı sürücüsü (XPSDrv) filtre ardışık düzen, doğrudan ve ölçeklenebilir yazdırmayı etkinleştirmek için tasarlanmış [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belgeleri. (Arama "XPSDrv" içinde [Windows Sürücü Seti](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
### <a name="print-path-architecture"></a>Yazdırma yolu mimarisi  
 While hem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve .NET Framework uygulamaları destekleyen [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms uygulamaları bir [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] oluşturmak için dönüştürme [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biçimlendirilmiş içiniçerik[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]yazıcı sürücüsü (XPSDrv). Bu uygulamaları kullanmak için gerekli değildir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu ve kullanmaya devam edebilirsiniz [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] yazdırma bağlı. Ancak, çoğu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellikler ve geliştirmeler yalnızca hedefleyen uygulamalar için kullanılabilir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu.  
  
 XPSDrv tabanlı yazıcılar tarafından kullanımını etkinleştirmek için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms uygulamaları [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] (XPSDrv) yazıcı sürücüsü dönüştürülmesini destekler [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biçimi. XPSDrv modeli için bir dönüştürücü de sağlar. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] için [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] biçimi böylece [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamaları yazdırabilirsiniz [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgeleri. İçin [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları, dönüştürme [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] için [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] biçimi tarafından otomatik olarak yapılır <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinin <xref:System.Windows.Xps.XpsDocumentWriter> yazma işleminin hedef yazdırma sırasını olmayan her sınıfı bir XPSDrv sürücüsü. (Windows Forms uygulamaları olamaz yazdırma [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgeler.)  
  
 Aşağıdaki çizim yazdırma alt sistemi gösterir ve tarafından sağlanan bölümleri tanımlar [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]ve yazılım ve donanım satıcıları tarafından tanımlanan bölümleri.  
  
 ![XPS yazdırma sistemi](../../../../docs/framework/wpf/advanced/media/xpsprint.PNG "XPSPrint")  
  
### <a name="basic-xps-printing"></a>Temel XPS yazdırma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Her iki temel tanımlar ve Gelişmiş [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Kapsamlı gerektirmeyen bu uygulamaları özelleştirme ve tam erişim yazdırmak için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellik kümesi, temel yazdırma destek sunulmaktadır. En az yapılandırma gerektirir ve bir bilinen özellikleri bir yazdırma iletişim kutusu denetim temel yazdırma desteği kullanıma sunulan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Birçok [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellikleri bu Basitleştirilmiş yazdırma model kullanılarak kullanılabilir.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Denetim için tek giriş noktası sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], yapılandırması ve [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] iş gönderme. Denetim oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Yazdır iletişim kutusu çağırma](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Gelişmiş XPS yazdırma  
 Eksiksiz erişmeye [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellikleri, Gelişmiş Yazdırma [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] kullanılmalıdır. İlgili birkaç [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] aşağıda daha ayrıntılı olarak açıklanmıştır. Tam bir listesi için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], bkz: <xref:System.Windows.Xps> ve <xref:System.Printing> ad alanı başvurularını.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket ve PrintCapabilities  
 <xref:System.Printing.PrintTicket> Ve <xref:System.Printing.PrintCapabilities> sınıflardır Gelişmiş temelini [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellikleri. Her iki tür nesneleri [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] yazdırma yönelimli özelliği harmanlaması, iki taraflı yazdırma, zımbalama, vb. gibi yapıları biçimlendirilmiş. Bu yapılar, yazdırma şeması tarafından tanımlanır. A <xref:System.Printing.PrintTicket> bir yazdırma işi işlemek nasıl bir yazıcı bildirir. <xref:System.Printing.PrintCapabilities> Sınıfı bir yazıcı yeteneklerini tanımlar. Bir yazıcı yeteneklerini sorgulamak bir <xref:System.Printing.PrintTicket> tam yararlanır yazıcı desteklenen özellikler oluşturulabilir. Benzer şekilde, desteklenmeyen özellikler önlenebilir.  
  
 Aşağıdaki örnek nasıl sorgulanacağını gösterir <xref:System.Printing.PrintCapabilities> yazıcının oluşturup bir <xref:System.Printing.PrintTicket> kod kullanarak.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](../../../../samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer ve PrintQueue  
 <xref:System.Printing.PrintServer> Sınıfı, bir ağ yazdırma sunucusu temsil eder ve <xref:System.Printing.PrintQueue> yazıcı ve onunla ilişkili çıkış iş kuyruğu sınıfı temsil eder. Birlikte, bunlar [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] sunucunun yazdırma işlerinin Gelişmiş yönetime izin verecek. A <xref:System.Printing.PrintServer>, ya da ondan türetilen sınıflardan birini yönetmek için kullanılan bir <xref:System.Printing.PrintQueue>. <xref:System.Printing.PrintQueue.AddJob%2A> Yöntemi yeni bir yazdırma işi kuyruğa eklemek için kullanılır.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Printing.LocalPrintServer> ve varsayılan erişim <xref:System.Printing.PrintQueue> kodu kullanarak.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Bir <xref:System.Windows.Xps.XpsDocumentWriter>, kendi çok ile <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemleri yazmak için kullanılan [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belgeler için bir <xref:System.Printing.PrintQueue>. Örneğin, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> yöntemi kullanılır çıktıya bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belge ve <xref:System.Printing.PrintTicket> zaman uyumlu olarak. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> Yöntemi kullanılır çıktıya bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belge ve <xref:System.Printing.PrintTicket> zaman uyumsuz olarak.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Xps.XpsDocumentWriter> kod kullanarak.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Yöntemleri de yazdırmak için yollar sağlar. Bkz: [program aracılığıyla XPS dosyalarını yazdırma](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Ayrıntılar için.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>GDI yazdırma yolu  
 Sırada [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları yerel olarak destekleyen [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms uygulamalarının da yararlanabilir bazı [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellikleri. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] (XPSDrv) yazıcı sürücüsü dönüştürebilir [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] çıkışı tabanlı [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biçimi. Gelişmiş senaryolar için içerik özel dönüştürme kullanarak desteklenen [Microsoft XPS Belge dönüştürücü (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx). Benzer şekilde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaları de için çıkış [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] birini çağırarak yazdırma yolu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> veya <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinin <xref:System.Windows.Xps.XpsDocumentWriter> sınıfı ve hedef olarak XpsDrv yazıcısı belirleme yazdırma sırası.  

Gerekli olmayan uygulamalar için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] işlevselliği veya desteği, geçerli [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolu değişmeden kalır.  
  
-   Hakkında referans materyalleri için [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolu ve çeşitli [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dönüştürme seçeneklerini görmek [Microsoft XPS Belge dönüştürücü (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx) ve "XPSDrv" [Windows Sürücü Seti](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>XPSDrv sürücü modeli  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Yazdırma yolu kullanarak biriktirme verimliliğini artıran [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] için yazdırırken yerel yazdırma biriktiricisi biçiminde bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] -yazıcı sürücüsü etkin. Basitleştirilmiş biriktirme işlemini gibi bir ara Biriktirme dosyası oluşturmak için ihtiyacını ortadan kaldıran bir [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] belge belleğe önce veri dosyası. Küçük biriktirme dosya boyutları aracılığıyla [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu, ağ trafiğini azaltmak ve yazdırma performansı geliştirin.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] Uygulama çıktısı çağırıyor bir dizi olarak temsil eden bir kapalı biçimi [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] oluşturma hizmetleri için. Farklı [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biriktirme biçimi için çıkış başka yorumu gerek kalmadan gerçek belgeyi temsil eder bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]-based yazıcı sürücüsü (XPSDrv). Sürücüleri biçimde veriler üzerinde doğrudan çalışabilir. Bu özelliği kullandığınızda gerekli veri ve renk alanı dönüştürmeler ortadan [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] dosyaları ve [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]-yazıcı sürücülerinin bağlı.  
  
 Kullandığınızda, biriktirme dosya boyutu azaltıldı genellikle [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] hedefleyen belgeleri bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazıcı sürücüsü (XPSDrv) kıyasla ile kendi [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] eşdeğerleri; ancak, özel durumlar vardır:  
  
-   Çok karmaşık, çok katmanlı ya da verimsiz yazılı bir vektör grafik, bir grafiğin eşlemli sürümden büyük olamaz.  
  
-   Ekran görüntüleme amacıyla XPS dosyaları cihaz yazı tipleri ve bunun yanı sıra bilgisayar tabanlı yazı tipleri katıştır; GDI yazdırma biriktiricisi dosyalarını, cihaz yazı tipleri katıştır değil ise. Ancak her iki yazı tiplerinin alt kümelenmiş (aşağıya bakın) türleridir ve yazıcı sürücülerini yazıcı dosyasına aktarmadan önce cihaz yazı tipleri kaldırabilirsiniz.  
  
 Biriktirme boyutu azaltma çeşitli mekanizmalar gerçekleştirilir:  
  
-   **Yazı tipi alt kümeleme**. Yalnızca gerçek belgenin içinde kullanılan karakterler depolanır [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dosya.  
  
-   **Gelişmiş grafik desteği**. Saydamlık ve gradyan temelleri için yerel destek önler içeriğinin tarama [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belge.  
  
-   **Ortak kaynakları tanımlaması**. (Şirket logosunu temsil eden birden çok kez bir görüntü gibi) kullanılan kaynaklar, paylaşılan kaynaklar olarak kabul edilir ve yalnızca bir kez yüklenir.  
  
-   **ZIP sıkıştırma**. Tüm [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ZIP sıkıştırma belgeleri kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.PrintDialog>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.PrintQueue>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/printing-how-to-topics.md)  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [XPS](https://www.microsoft.com/xps)  
 [Belge Serileştirme ve Depolama](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)  
 [Microsoft XPS Belge dönüştürücü (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx)

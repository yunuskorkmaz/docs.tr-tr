---
title: 'Nasıl yapılır: Program Aracılığıyla XPS Dosyalarını Yazdırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: 25c0b34bd33bee626df14c8dbedce0b82e895b58
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398273"
---
# <a name="how-to-programmatically-print-xps-files"></a>Nasıl yapılır: Program Aracılığıyla XPS Dosyalarını Yazdırma
Bir aşırı yüklemesini kullanabilirsiniz <xref:System.Printing.PrintQueue.AddJob%2A> yazdırmak için yöntemi [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] açmadan dosyaları bir <xref:System.Windows.Controls.PrintDialog> veya İlkesi, tüm [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] hiç.  
  
 Ayrıca yazdırabilirsiniz [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] çok kullanarak dosyaları <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinin <xref:System.Windows.Xps.XpsDocumentWriter>. Bu hakkında daha fazla bilgi için [XPS Belge yazdırma](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90)).  
  
 Başka bir şekilde yazdırma [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] kullanmaktır <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> veya <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> yöntemlerinin <xref:System.Windows.Controls.PrintDialog> denetimi. Bkz: [Yazdır iletişim kutusu çağırma](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Örnek  
 Üç parametre kullanarak yönelik temel adımlar <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yöntemi aşağıdaki gibidir. Aşağıdaki örnekte ayrıntılarını verir.  
  
1.  Yazıcı XPSDrv yazıcısı olup olmadığını belirler. (Bkz [yazdırma genel bakış](printing-overview.md) XPSDrv hakkında daha fazla bilgi için.)  
  
2.  Yazıcı XPSDrv yazıcısı değilse, çoklu iş parçacığı için iş parçacığının grubunu ayarlayın.  
  
3.  Bir yazdırma sunucusu ve yazdırma sırası nesne örneği.  
  
4.  Yazdırılacak dosyayı bir proje adı belirterek bu yöntemi çağırın ve <xref:System.Boolean> bayrak belirten XPSDrv yazıcısı yazıcı olup olmadığını.  
  
 Aşağıdaki örnekte, tüm yazdırma toplu işlemi gösterilmektedir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] bir dizindeki dosyaları. Uygulamanın üç parametre depolayacağınız dizini belirtmek için kullanıcıdan rağmen <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yöntemi gerekli olmadığı bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Sahip olduğunuz herhangi bir kod yolunda kullanılabilir bir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dosya adı ve kendisine geçirebilirsiniz yolu.  
  
 Üç parametre <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> aşırı yükünü <xref:System.Printing.PrintQueue.AddJob%2A> bir tek iş parçacığı grubu çalıştırmalısınız her <xref:System.Boolean> parametresi `false`, XPSDrv yazıcısı kullanıldığında, olması gerekir. Bununla birlikte, varsayılan grup durumu için [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] birden çok iş parçacığıdır. Bu varsayılan örnek XPSDrv yazıcısı varsaydığından tersine çevrilmesi gerekir.  
  
 Varsayılan değeri değiştirmek için iki yolu vardır. Bir kolayca ediyor <xref:System.STAThreadAttribute> (diğer bir deyişle, "`[System.STAThreadAttribute()]`") uygulamanın ilk satırının hemen üstüne `Main` yöntemi (genellikle "`static void Main(string[] args)`"). Ancak, çoğu uygulama gerektiren `Main` yöntemi ikinci bir yöntem olduğundan, birden çok iş parçacıklı durumuna sahiptir: çağrı yerleştirmek <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> Grup durumu ayarlanmış ayrı bir iş parçacığı <xref:System.Threading.ApartmentState.STA> ile <xref:System.Threading.Thread.SetApartmentState%2A>. Aşağıdaki örnekte, ikinci bu tekniği kullanır.  
  
 Buna örnek oluşturarak başlar. bir <xref:System.Threading.Thread> nesne ve geçirerek bir **PrintXPS** yöntemi olarak <xref:System.Threading.ThreadStart> parametresi. ( **PrintXPS** yöntemi, örnek tanımlanır.) Sonraki iş parçacığı bir tek iş parçacığı grubu olarak ayarlanır. Yalnızca kalan kod `Main` yöntemi yeni iş parçacığını başlatır.  
  
 Örneğin et bulunduğu `static` **BatchXPSPrinterçPrintXPS** yöntemi. Bir yazdırma sunucusunu ve kuyruk oluşturduktan sonra yöntemi içeren bir dizin için kullanıcıdan [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dosyaları. Dizinin var olup olmadığını ve varlığından destek alan doğrulama sonra \*.xps dosyaları içinde yöntem her bir dosya yazdırma sırasını ekler. Örneği geçiriyoruz şekilde yazıcı XPSDrv olmayan, olduğunu varsayar `false` son parametresi için <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yöntemi. Bu nedenle, yöntem doğrulayacaktır [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazıcının sayfa açıklaması diline dönüştürülecek denemeden önce dosyayı işaretlemede. Doğrulama başarısız olursa bir özel durum oluşturulur. Örnek kod özel durumu yakalar, bu hakkında kullanıcıya bildirim ve sonraki işlemek için Git [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dosya.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 XPSDrv yazıcısı kullandığınız sonra son parametre ayarlayabileceğiniz `true`. Bu durumda, bu yana [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazıcının sayfa açıklaması dili, yöntem, doğrulamadan veya başka bir sayfa açıklaması dili dönüştürme, yazıcıya dosya gönderir. Tasarım zamanında XPSDrv yazıcısı uygulamayı kullanarak emin değilseniz, okumak için uygulamayı değiştirebilirsiniz <xref:System.Printing.PrintQueue.IsXpsDevice%2A> özelliği ve dal bulgulara göre.  
  
 Başlangıçta olacağından az XPSDrv kullanılabilir sürümünden sonra hemen [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] ve Microsoft .NET Framework, bir XPSDrv yazıcısı XPSDrv yazıcısı olarak değerlendiremez gerekebilir. Bunu yapmak için uygulamanızı çalıştıran bilgisayara aşağıdaki kayıt defteri anahtarı dosyaların listesini Pipelineconfig.xml'i ekleyin:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter>* \DependentFiles  
  
 Burada  *\<PseudoXPSPrinter >* herhangi bir yazdırma sırası. Makine daha sonra yeniden başlatılması gerekiyor.  
  
 Bu gizleme geçirmenize olanak tanır `true` son parametre olarak <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> ancak bir özel duruma neden olmadan  *\<PseudoXPSPrinter >* gerçekten XPSDrv yazıcısı değil yalnızca anlamsız yazdırır.  
  
 **Not** kolaylık sağlamak için yukarıdaki örnekte varlığını kullanan bir \*.xps uzantısı bir dosya, test olarak [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Ancak, [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] bu uzantıya sahip dosya yok. [İsXPS.exe (isXPS uyumluluk aracı)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100)) bir testi için bir dosya yolu [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] geçerlilik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](https://www.microsoft.com/xps)  
 [XPS Belge yazdırma](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90))  
 [Yönetilen ve yönetilmeyen iş parçacığı oluşturma](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))  
 [isXPS.exe (isXPS uyumluluk aracı)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100))  
 [WPF'deki Belgeler](documents-in-wpf.md)  
 [Yazdırmaya Genel Bakış](printing-overview.md)

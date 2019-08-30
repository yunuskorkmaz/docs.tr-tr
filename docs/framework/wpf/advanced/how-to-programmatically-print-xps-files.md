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
ms.openlocfilehash: 6642fad7d20e60a8b92e5860b763511f4fc0be72
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169176"
---
# <a name="how-to-programmatically-print-xps-files"></a>Nasıl yapılır: Program Aracılığıyla XPS Dosyalarını Yazdırma
<xref:System.Printing.PrintQueue.AddJob%2A> [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] Bir veyaöğesini[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] açmadan dosyaları yazdırmak için yönteminin bir aşırı yüklemesini kullanabilirsiniz. <xref:System.Windows.Controls.PrintDialog>  
  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] Ayrıca, <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> uygulamasının birçok ve yöntemlerini kullanarak dosyaları yazdırabilirsiniz. <xref:System.Windows.Xps.XpsDocumentWriter> Bunun hakkında daha fazla bilgi için, [BIR XPS belgesi yazdırılıyor](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).  
  
 Yazdırmanın [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> <xref:System.Windows.Controls.PrintDialog> başka bir yolu da denetimin veyayöntemlerininbiryoludur.<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> Bkz. [yazdırma Iletişim kutusu çağırma](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Örnek  
 Üç parametreli <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yöntemi kullanmanın ana adımları aşağıdaki gibidir. Aşağıdaki örnekte ayrıntılar verilmektedir.  
  
1. Yazıcının bir XPSDrv yazıcı olup olmadığını belirleme. (XPSDrv hakkında daha fazla bilgi için bkz. [yazdırmayla Ilgili genel bakış](printing-overview.md) )  
  
2. Yazıcı bir XPSDrv yazıcı değilse, iş parçacığının Apartment öğesini tek iş parçacığı olarak ayarlayın.  
  
3. Yazdırma sunucusu ve yazdırma kuyruğu nesnesi örneği oluşturun.  
  
4. Bir iş adı, yazdırılacak dosya ve yazıcının bir XPSDrv yazıcı olup olmadığını belirten bir <xref:System.Boolean> bayrak belirterek yöntemi çağırın.  
  
 Aşağıdaki örnekte, bir dizindeki tüm [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dosyaları toplu olarak nasıl yazdırabileceğiniz gösterilmektedir. Uygulama kullanıcıdan Dizin belirtmesini isterse, ancak üç parametreli <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> Yöntem bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]gerektirmez. Bu, kendisine geçirebileceğiniz bir dosya adı ve yolunuz varsa herhangi [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] bir kod yolunda kullanılabilir.  
  
 Öğesinin <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> <xref:System.Boolean> `false`Üç parametreli aşırı yüklemesi, parametresi her olduğunda tek bir iş parçacığı grubu içinde çalışmalıdır ve bu, XPSDrv olmayan bir yazıcı kullanılırken olması gerekir. <xref:System.Printing.PrintQueue.AddJob%2A> Ancak, .NET için varsayılan Grup durumu birden çok iş parçacığıdır. Örnek XPSDrv olmayan bir yazıcıya varsaydığından bu varsayılan değer ters alınmalıdır.  
  
 Varsayılanı değiştirmek için iki yol vardır. Tek yol <xref:System.STAThreadAttribute> , uygulamanın `Main` yönteminin`[System.STAThreadAttribute()]`ilksatırınınhemenüzerinde(yani"")yalnızca("")eklemektir.`static void Main(string[] args)` `Main` Ancak birçok uygulama, yöntemin çok iş parçacıklı bir grup durumuna sahip olmasını gerektirir, bu nedenle ikinci bir yöntem vardır: <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> çağrısını, Grup durumu ile <xref:System.Threading.Thread.SetApartmentState%2A>olarak <xref:System.Threading.ApartmentState.STA> ayarlanan ayrı bir iş parçacığında koyun. Aşağıdaki örnek bu ikinci tekniği kullanır.  
  
 Buna göre, örnek bir <xref:System.Threading.Thread> nesneyi örnekleyerek ve bir **PrintXPS** metodunu <xref:System.Threading.ThreadStart> parametresi olarak geçirerek başlar. ( **PrintXPS** yöntemi örnekte daha sonra tanımlanır.) Daha sonra iş parçacığı tek bir iş parçacığı grubu olarak ayarlanır. `Main` Yöntemin yalnızca geri kalan kodu yeni iş parçacığını başlatır.  
  
 Örneğin et, `static` **batchxpsprınter. PrintXPS** yönteminde bulunur. Yazdırma sunucusu ve sıra oluşturduktan sonra, Yöntemi kullanıcıdan dosya içeren [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] bir dizin ister. Dizinin varlığını ve içindeki \*. XPS dosyalarının varlığını doğruladıktan sonra, yöntemi bu her bir dosyayı yazdırma kuyruğuna ekler. Örnek, yazıcının XPSDrv olmayan olduğunu varsayar, bu yüzden `false` <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metodun son parametresine geçiririz. Bu nedenle yöntemi, dosyanın yazıcının sayfa açıklaması diline [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dönüştürmeyi denemeden önce dosyadaki biçimlendirmeyi doğrular. Doğrulama başarısız olursa, bir özel durum oluşturulur. Örnek kod, özel durumu yakalar, kullanıcıyı hakkında bilgilendirir ve sonra bir sonraki [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dosyayı işlemeye devam eder.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Bir XPSDrv yazıcı kullanıyorsanız, son parametresini olarak `true`ayarlayabilirsiniz. Bu durumda, [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazıcının sayfa açıklaması dili olduğundan, yöntemi dosyayı doğrulamadan veya başka bir sayfa açıklaması diline dönüştürmeden dosyayı yazıcıya gönderir. Uygulamanın bir XPSDrv yazıcı kullanıp kullanmadığını tasarlarken tasarım zamanında emin değilseniz, uygulamayı bulma <xref:System.Printing.PrintQueue.IsXpsDevice%2A> özelliğine göre özelliği ve dalı okumasını sağlayacak şekilde değiştirebilirsiniz.  
  
 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] Ve Microsoft .NET Framework 'ün yayımlanmasından hemen sonra birkaç XPSDrv yazıcısı kullanılabilir olacağı için, XPSDrv olmayan bir yazıcıyı bir XPSDrv yazıcı olarak gizleyebilmeniz gerekebilir. Bunu yapmak için, uygulamanızı çalıştıran bilgisayarın aşağıdaki kayıt defteri anahtarındaki, Pipelineconfig. xml ' i dosya listesine ekleyin:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<PseudoXPSPrinter>* \DependentFiles  
  
 sözde >, herhangi bir yazdırma kuyruğu olsun.  *\<* Makinenin yeniden başlatılması gerekir.  
  
 Bu gizleme `true` <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>  *birözeldurumanedenolmadansonparametresiolarakgeçirmenizeimkantanır,ancaksözde>,gerçektenbirXPSDrvyazıcıolmadığından,yalnızcaatıkyazdırılır.\<*  
  
 **Göz önünde** Kolaylık olması için yukarıdaki örnek, bir dosyanın olduğu \* [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]test olarak bir. XPS uzantısının varlığını kullanır. Ancak, [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dosyaların bu uzantıya sahip olması gerekmez. [İsXPS. exe (ısxps uygunluk aracı)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) bir dosyayı [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] bir geçerliliği test etmenin bir yoludur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.AddJob%2A>
- <xref:System.Threading.ApartmentState>
- <xref:System.STAThreadAttribute>
- [XPS belgeleri](/windows/desktop/printdocs/documents)
- [XPS belgesi yazdırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))
- [Yönetilen ve yönetilmeyen Iş parçacığı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [isXPS. exe (ısxps uygunluk aracı)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)

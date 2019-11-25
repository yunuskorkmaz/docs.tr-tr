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
ms.openlocfilehash: cc86a7e7c6a816af37c3d063825ed62583afa78a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966995"
---
# <a name="how-to-programmatically-print-xps-files"></a>Nasıl yapılır: Program Aracılığıyla XPS Dosyalarını Yazdırma

Bir <xref:System.Windows.Controls.PrintDialog> açmadan XML Kağıt Belirtimi (XPS) dosyalarını yazdırmak için <xref:System.Printing.PrintQueue.AddJob%2A> yönteminin bir aşırı yüklemesini kullanabilir ya da herhangi bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].

Ayrıca, birçok <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A?displayProperty=nameWithType> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A?displayProperty=nameWithType> yöntemini kullanarak XPS dosyalarını yazdırabilirsiniz. Daha fazla bilgi için bkz. [XPS belgesi yazdırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).

XPS 'yi yazdırmanın bir diğer yolu <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A?displayProperty=nameWithType> veya <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A?displayProperty=nameWithType> yöntemlerini kullanmaktır. Bkz. [yazdırma Iletişim kutusu çağırma](how-to-invoke-a-print-dialog.md).

## <a name="example"></a>Örnek

Üç parametreli <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yöntemini kullanmanın ana adımları aşağıdaki gibidir. Aşağıdaki örnekte ayrıntılar verilmektedir.

1. Yazıcının bir XPSDrv yazıcı olup olmadığını belirleme. XPSDrv hakkında daha fazla bilgi için bkz. [Baskıya genel bakış](printing-overview.md) .

2. Yazıcı bir XPSDrv yazıcı değilse, iş parçacığının Apartment öğesini tek iş parçacığı olarak ayarlayın.

3. Yazdırma sunucusu ve yazdırma kuyruğu nesnesi örneği oluşturun.

4. Bir iş adı, yazdırılacak dosya ve yazıcının bir XPSDrv yazıcı olup olmadığını belirten bir <xref:System.Boolean> bayrağı belirterek yöntemi çağırın.

Aşağıdaki örnekte, bir dizindeki tüm XPS dosyalarını toplu olarak nasıl yazdırabileceğiniz gösterilmektedir. Uygulama kullanıcıdan Dizin belirtmesini ister, ancak üç parametreli <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yöntemi bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]gerektirmez. Bu, kendisine geçirebileceğiniz bir XPS dosya adı ve yolunuz olduğu herhangi bir kod yolunda kullanılabilir.

<xref:System.Printing.PrintQueue.AddJob%2A> ' nin üç parametreli <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> aşırı yüklemesi, <xref:System.Boolean> parametresi `false`olduğunda tek bir iş parçacığı grubu içinde çalışmalıdır, bu da XPSDrv olmayan bir yazıcı kullanılırken olması gerekir. Ancak, .NET için varsayılan Grup durumu birden çok iş parçacığıdır. Örnek XPSDrv olmayan bir yazıcıya varsaydığından bu varsayılan değer ters alınmalıdır.

Varsayılanı değiştirmek için iki yol vardır. Tek yol, uygulamanın `Main` yönteminin (genellikle "`static void Main(string[] args)`") ilk satırının hemen üzerinde <xref:System.STAThreadAttribute> (yani "`[System.STAThreadAttribute()]`") eklemeniz yeterlidir. Ancak birçok uygulama, `Main` yönteminin çok iş parçacıklı bir grup durumuna sahip olmasını gerektirir, bu nedenle ikinci bir yöntem vardır: <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> çağrısını, Grup durumu <xref:System.Threading.Thread.SetApartmentState%2A><xref:System.Threading.ApartmentState.STA> olarak ayarlanan ayrı bir iş parçacığına koyun. Aşağıdaki örnek bu ikinci tekniği kullanır.

Buna göre, örnek bir <xref:System.Threading.Thread> nesnesini örnekleyerek ve bir **PrintXPS** yöntemini <xref:System.Threading.ThreadStart> parametresi olarak geçirerek başlar. ( **PrintXPS** yöntemi örnekte daha sonra tanımlanır.) Daha sonra iş parçacığı tek bir iş parçacığı grubu olarak ayarlanır. `Main` yönteminin yalnızca geri kalan kodu yeni iş parçacığını başlatır.

Örneğin et, `static`**Batchxpsprınter. PrintXPS** yönteminde bulunur. Yazdırma sunucusu ve sıra oluşturduktan sonra, Yöntemi kullanıcıdan XPS dosyalarını içeren bir dizin ister. Dizinin varlığını ve içinde \*. XPS dosyaları varlığını doğruladıktan sonra, yöntemi bu her bir dosyayı yazdırma kuyruğuna ekler. Örnek, yazıcının XPSDrv olmayan olduğunu varsayar, bu nedenle `false` <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yönteminin son parametresine geçiriyoruz. Bu nedenle, yöntemi, dosyanın yazıcının sayfa açıklaması diline dönüştürmeyi denemeden önce dosyadaki XPS işaretlemesini doğrular. Doğrulama başarısız olursa, bir özel durum oluşturulur. Örnek kod, özel durumu yakalar, kullanıcıdan onunla ilgili bilgilendirmesini ve ardından sonraki XPS dosyasını işlemeye devam eder.

[!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
[!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]

Bir XPSDrv yazıcı kullanıyorsanız, son parametreyi `true`olarak ayarlayabilirsiniz. Bu durumda, XPS yazıcının sayfa açıklaması dili olduğundan, bu yöntem dosyayı doğrulamadan veya başka bir sayfa açıklaması diline dönüştürmeden dosyayı yazıcıya gönderir. Uygulamanın bir XPSDrv yazıcı kullanıp kullanmadığını tasarlarken tasarım zamanında emin değilseniz, uygulamayı bulma özelliğine göre <xref:System.Printing.PrintQueue.IsXpsDevice%2A> özelliğini ve dalını okuyacak şekilde değiştirebilirsiniz.

İlk olarak Windows Vista ve Microsoft .NET çerçevesinin yayımlanmasından hemen sonra birkaç XPSDrv yazıcısı kullanılabilir olacağı için, XPSDrv olmayan bir yazıcıyı bir XPSDrv yazıcı olarak gizleyebilmeniz gerekebilir. Bunu yapmak için, uygulamanızı çalıştıran bilgisayarın aşağıdaki kayıt defteri anahtarındaki, Pipelineconfig. xml ' i dosya listesine ekleyin:

HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<sahte Doxpsprınter >* \Dependentfiles

*\<sözde >* , herhangi bir yazdırma kuyruğu olsun. Makinenin yeniden başlatılması gerekir.

Bu gizleme, bir özel duruma neden olmadan <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> son parametresi olarak `true` geçirmenize imkan tanır, ancak *\<sözde bir >* gerçekten bir XPSDrv yazıcı olmadığından, yalnızca atık yazdırılır.

> [!NOTE]
> Basitlik için yukarıdaki örnek, bir dosyanın XPS olduğu test olarak bir \*. XPS uzantısının varlığını kullanır. Ancak, XPS dosyalarının bu uzantıya sahip olması gerekmez. [İsXPS. exe (ısxps uygunluk aracı)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) , BIR dosyayı XPS geçerliliği için test etmenin bir yoludur.

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

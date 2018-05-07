---
title: "Nasıl yapılır: PrintTickets'i Doğrulama ve Birleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
ms.openlocfilehash: 11160d7ec59914afbe501ba731c0c04a85ffc4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-and-merge-printtickets"></a>Nasıl yapılır: PrintTickets'i Doğrulama ve Birleştirme
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Yazdırma şema](http://go.microsoft.com/fwlink/?LinkId=186397) esnek ve Genişletilebilir içeren <xref:System.Printing.PrintCapabilities> ve <xref:System.Printing.PrintTicket> öğeleri. Yazdırma cihazı yeteneklerini eski maddeler halinde listelemektedir ve aygıtın bu özellikler belgeleri, belgenin veya tek tek sayfa belirli bir dizi göre nasıl kullanması gereken ikinci belirtir.  
  
 Tipik bir yazdırma destekleyen bir uygulama için görev dizisi aşağıdaki gibi olur.  
  
1.  Yazıcının yeteneklerini belirler.  
  
2.  Yapılandırma bir <xref:System.Printing.PrintTicket> bu özellikleri kullanmak için.  
  
3.  Doğrulama <xref:System.Printing.PrintTicket>.  
  
 Bu makalede bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki basit örnekte, biz yalnızca olup bir yazıcıya çift yönlü baskı desteklemediği ilgilendiğiniz — iki taraflı yazdırma. Önemli adımlar aşağıdaki gibidir.  
  
1.  Alma bir <xref:System.Printing.PrintCapabilities> nesnesi ile <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemi.  
  
2.  İstediğiniz özelliğin varlığını test edin. Aşağıdaki örnekte, biz test <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> özelliği <xref:System.Printing.PrintCapabilities> nesnesi, her iki tarafında "sayfa dönmesi" ile bir sayfa yazdırma yeteneğini varlığını sayfası uzun tarafında. Bu yana <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> bir koleksiyondur kullanırız `Contains` yöntemi <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    >  Bu adım kesinlikle gerekli değildir. <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Aşağıda kullanılan yöntem her istek denetleyecek <xref:System.Printing.PrintTicket> yazıcı yeteneklerine karşı. İstenen özellik yazıcı tarafından desteklenmiyorsa, yazıcı sürücüsü içinde alternatif bir istek yerine <xref:System.Printing.PrintTicket> yöntemi tarafından döndürülen.  
  
3.  Yazıcı çift yönlü baskı destekliyorsa, örnek kod oluşturur bir <xref:System.Printing.PrintTicket> için çift yönlü baskı sorar. Ancak uygulama her olası yazıcı bulunan ayarını belirtmiyor <xref:System.Printing.PrintTicket> öğesi. Programcı ve program zamanı için kayıp olacaktır. Bunun yerine, kod yalnızca çift yönlü baskı isteği ayarlar ve bu birleştirir <xref:System.Printing.PrintTicket> , tam olarak yapılandırılmış ve doğrulandığında, varolan <xref:System.Printing.PrintTicket>, bu durumda, kullanıcının varsayılan <xref:System.Printing.PrintTicket>.  
  
4.  Buna örnek çağırır <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> yeni, birleştirme yöntemi en az <xref:System.Printing.PrintTicket> kullanıcının varsayılan ile <xref:System.Printing.PrintTicket>. Bu döndürür bir <xref:System.Printing.ValidationResult> yeni içeren <xref:System.Printing.PrintTicket> özelliklerinden biri olarak.  
  
5.  Örnek daha sonra testleri yeni <xref:System.Printing.PrintTicket> çift yönlü baskı ister. Destekliyorsa, ardından örnek kullanıcı için yeni varsayılan yazdırma bileti kolaylaştırır. Yukarıdaki adım 2 atlanmışsa ve yazıcı uzun kenar boyunca çift yönlü baskı desteklemiyor durumunda test sonuçlanırdı `false`. (Yukarıdaki nota bakın.)  
  
6.  Değişikliği kaydetmek için son önemli adım olan <xref:System.Printing.PrintQueue.UserPrintTicket%2A> özelliği <xref:System.Printing.PrintQueue> ile <xref:System.Printing.PrintQueue.Commit%2A> yöntemi.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Bu örnek hızlı bir şekilde test edebilirsiniz, geri kalanı aşağıda sunulur. Proje ve bir ad alanı oluşturmak ve bu makaledeki kod parçacıkları ad alanı bloğuna yapıştırın.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Yazdırmaya Genel Bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Şema Yazdırma](http://go.microsoft.com/fwlink/?LinkId=186397)

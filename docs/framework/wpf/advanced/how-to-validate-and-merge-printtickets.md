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
ms.openlocfilehash: 37a1c0600b8429158336968507ddc8cfb6d8f98b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485644"
---
# <a name="how-to-validate-and-merge-printtickets"></a>Nasıl yapılır: PrintTickets'i Doğrulama ve Birleştirme
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Yazdırma şema](https://go.microsoft.com/fwlink/?LinkId=186397) esnek ve Genişletilebilir içerir <xref:System.Printing.PrintCapabilities> ve <xref:System.Printing.PrintTicket> öğeleri. Yazdırma cihazı yeteneklerini eski maddeler halinde listeler ve cihaz belirli bir sırayla belgeleri, belgenin veya tek tek sayfa göre bu özellikleri nasıl kullanması gereken ikinci belirtir.  
  
 Tipik bir yazdırma destekleyen bir uygulama için görev dizisi şu şekilde olacaktır.  
  
1.  Yazıcı özellikleri belirler.  
  
2.  Yapılandırma bir <xref:System.Printing.PrintTicket> bu özellikleri kullanmak için.  
  
3.  Doğrulama <xref:System.Printing.PrintTicket>.  
  
 Bu makalede bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki basit örnekte, biz yalnızca olup bir yazıcıya çift yönlü baskı destekleyebilir ilgilendiğiniz — iki taraflı yazdırma. Önemli adımlar aşağıdaki gibidir.  
  
1.  Alma bir <xref:System.Printing.PrintCapabilities> nesnesi ile <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemi.  
  
2.  İstediğiniz yeteneğinin olup olmadığını test edin. Aşağıdaki örnekte, test ederiz <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> özelliği <xref:System.Printing.PrintCapabilities> uzun sayfa tarafında nesne iki tarafındaki "sayfa açma" ile bir sayfa yazdırma yeteneğini varlığını. Bu yana <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> bir koleksiyon olduğundan kullandığımız `Contains` yöntemi <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    >  Bu adım, kesinlikle gerekli değildir. <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Aşağıda kullanılan yöntem her isteği denetleyecek <xref:System.Printing.PrintTicket> yazıcı yeteneklerine karşı. İstenen özellik yazıcı tarafından desteklenmiyorsa, yazıcı sürücüsü alternatif bir istekte kullanacak <xref:System.Printing.PrintTicket> yöntem tarafından döndürülen.  
  
3.  Yazıcı çift yönlü baskı destekliyorsa, örnek kod oluşturur bir <xref:System.Printing.PrintTicket> için çift yönlü baskı sorar. Ancak uygulama, her olası yazıcı bulunan ayarını belirtmiyor <xref:System.Printing.PrintTicket> öğesi. Bu, hem Programcı ve program zaman kısıp olacaktır. Bunun yerine, kodu yalnızca çift yönlü baskı isteği ayarlar ve bu birleştirir <xref:System.Printing.PrintTicket> , tam olarak yapılandırılmış ve doğrulanır, varolan bir <xref:System.Printing.PrintTicket>, bu durumda, kullanıcının varsayılan <xref:System.Printing.PrintTicket>.  
  
4.  Buna örnek çağırır <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> yöntemi yeni, birleştirme için en az <xref:System.Printing.PrintTicket> kullanıcının varsayılan <xref:System.Printing.PrintTicket>. Bu döndürür bir <xref:System.Printing.ValidationResult> yeni içeren <xref:System.Printing.PrintTicket> özelliklerinden biri olarak.  
  
5.  Örnek daha sonra test yeni <xref:System.Printing.PrintTicket> çift yönlü baskı ister. Varsa, ardından örnek kullanıcı için yeni varsayılan yazdırma bileti kolaylaştırır. Yukarıdaki 2. adım atlanmışsa ve yazıcıya çift yönlü baskı uzun kenarı boyunca desteklemiyor durumunda, test sonuçlanırdı `false`. (Yukarıdaki nota bakın.)  
  
6.  Değişikliği kaydetmek için son önemli adım olan <xref:System.Printing.PrintQueue.UserPrintTicket%2A> özelliği <xref:System.Printing.PrintQueue> ile <xref:System.Printing.PrintQueue.Commit%2A> yöntemi.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Bu örnekte hızlıca test edebilirsiniz böylece geri kalanı aşağıda sunulmuştur. Bir proje ve bir ad alanı oluşturma ve kod parçacıkları bu makaledeki ad alanı bloğuna yapıştırın.  
  
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
 [Şema Yazdırma](https://go.microsoft.com/fwlink/?LinkId=186397)

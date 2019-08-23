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
ms.openlocfilehash: 9e5242c07179501e6b39840a36f8dd6364d65b84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918342"
---
# <a name="how-to-validate-and-merge-printtickets"></a>Nasıl yapılır: PrintTickets'i Doğrulama ve Birleştirme
Yazdırma şeması, esnek ve Genişletilebilir <xref:System.Printing.PrintCapabilities> ve <xref:System.Printing.PrintTicket> öğeleri içerir. [](https://go.microsoft.com/fwlink/?LinkId=186397) [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] Daha önce bir yazdırma cihazının özellikleri, ikincisi ise cihazın belirli bir dizi belge, tek belge veya ayrı bir sayfa için bu özellikleri nasıl kullanması gerektiğini belirtir.  
  
 Yazdırmayı destekleyen bir uygulama için tipik bir görev dizisi aşağıdaki gibidir.  
  
1. Yazıcının yeteneklerini belirleme.  
  
2. Bu özellikleri kullanacak şekilde yapılandırın. <xref:System.Printing.PrintTicket>  
  
3. ' İ doğrulayın. <xref:System.Printing.PrintTicket>  
  
 Bu makalede bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki basit örnekte, yalnızca bir yazıcının çift taraflı yazdırma gibi çift yönlü olarak bir yazıcının destekleyebilip destekleyemeyeceğini ilgileniyoruz. Ana adımlar aşağıdaki gibidir.  
  
1. Yöntemine sahip bir <xref:System.Printing.PrintCapabilities> nesne alın. <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
  
2. İstediğiniz özelliğin varlığını test edin. Aşağıdaki örnekte, sayfanın uzun tarafında "sayfa <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> açma" ile <xref:System.Printing.PrintCapabilities> bir kağıt yaprağının her iki tarafında da yazdırma yeteneğinin olması için nesnesinin özelliğini test ediyoruz. Bir koleksiyon `Contains` olduğundan, yöntemi <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>kullanırız. <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>  
  
    > [!NOTE]
    > Bu adım kesinlikle gerekli değildir. Aşağıda kullanılan <xref:System.Printing.PrintTicket> Yöntem, içindeki her isteği yazıcının özelliklerine göre denetleyecektir. <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> İstenen yetenek yazıcı tarafından desteklenmiyorsa, yazıcı sürücüsü yöntemi tarafından <xref:System.Printing.PrintTicket> döndürülen alternatif bir istek yerine geçecek.  
  
3. Yazıcı çift yönlüyi destekliyorsa, örnek kod çift yönlü için <xref:System.Printing.PrintTicket> isteyen bir oluşturur. Ancak uygulama, <xref:System.Printing.PrintTicket> öğesinde kullanılabilen her bir olası yazıcı ayarını belirtmez. Bu, hem programcı hem de program zamanının boşa harcanmasına neden olur. Bunun yerine, kod yalnızca çift yönlü istekleri ayarlar ve ardından bunu <xref:System.Printing.PrintTicket> mevcut, tam olarak yapılandırılmış ve <xref:System.Printing.PrintTicket>doğrulanan bir ile birleştirir, bu durumda kullanıcının varsayılan <xref:System.Printing.PrintTicket>' i.  
  
4. Buna göre, örnek, kullanıcının <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> varsayılan <xref:System.Printing.PrintTicket> <xref:System.Printing.PrintTicket>değeriyle yeni, en az bir birleştirme yöntemi çağırır. Bu, özelliklerinden <xref:System.Printing.ValidationResult> biri olarak yeni <xref:System.Printing.PrintTicket> bir içeren bir döndürür.  
  
5. Örnek daha sonra yeni <xref:System.Printing.PrintTicket> isteklerin çift yönlüde olmasını sınar. Varsa, örnek bunu Kullanıcı için yeni varsayılan yazdırma bileti yapar. Yukarıdaki 2. adım ayrıldıysa ve yazıcı uzun bir süre boyunca çift yönlüyi desteklemiyorsa, test sonuçlanmış `false`olur. (Yukarıdaki nota bakın.)  
  
6. Son önemli adım, <xref:System.Printing.PrintQueue.UserPrintTicket%2A> <xref:System.Printing.PrintQueue.Commit%2A> yönteminin özelliği <xref:System.Printing.PrintQueue> ile olan özelliğindeki değişikliği yürütmeniz.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Bu örneği hızlıca sınayabilmeniz için geri kalanı aşağıda sunulmuştur. Bir proje ve ad alanı oluşturun ve ardından bu makaledeki kod parçacıklarını ad alanı bloğuna yapıştırın.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [Şemayı Yazdır](https://go.microsoft.com/fwlink/?LinkId=186397)

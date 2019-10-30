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
ms.openlocfilehash: 15e328729886e0f1efc3b47705fcb4ce13013137
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035570"
---
# <a name="how-to-validate-and-merge-printtickets"></a>Nasıl yapılır: PrintTickets'i Doğrulama ve Birleştirme
Microsoft Windows [yazdırma şeması](https://go.microsoft.com/fwlink/?LinkId=186397) , esnek ve Genişletilebilir <xref:System.Printing.PrintCapabilities> ve <xref:System.Printing.PrintTicket> öğelerini içerir. Daha önce bir yazdırma cihazının özellikleri, ikincisi ise cihazın belirli bir dizi belge, tek belge veya ayrı bir sayfa için bu özellikleri nasıl kullanması gerektiğini belirtir.  
  
 Yazdırmayı destekleyen bir uygulama için tipik bir görev dizisi aşağıdaki gibidir.  
  
1. Yazıcının yeteneklerini belirleme.  
  
2. Bu özellikleri kullanmak için bir <xref:System.Printing.PrintTicket> yapılandırın.  
  
3. <xref:System.Printing.PrintTicket>doğrulayın.  
  
 Bu makalede bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki basit örnekte, yalnızca bir yazıcının çift taraflı yazdırma gibi çift yönlü olarak bir yazıcının destekleyebilip destekleyemeyeceğini ilgileniyoruz. Ana adımlar aşağıdaki gibidir.  
  
1. <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemi ile <xref:System.Printing.PrintCapabilities> nesnesi alın.  
  
2. İstediğiniz özelliğin varlığını test edin. Aşağıdaki örnekte, sayfanın uzun tarafında "sayfa açma" ile bir kağıt yaprağının her iki tarafında da yazdırma yeteneğinin olması için <xref:System.Printing.PrintCapabilities> nesnesinin <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> özelliğini test ediyoruz. <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> bir koleksiyon olduğundan, <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>`Contains` yöntemini kullanırız.  
  
    > [!NOTE]
    > Bu adım kesinlikle gerekli değildir. Aşağıda kullanılan <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> yöntemi, <xref:System.Printing.PrintTicket> her isteği yazıcının özelliklerine göre denetleyecektir. İstenen yetenek yazıcı tarafından desteklenmiyorsa, yazıcı sürücüsü yöntem tarafından döndürülen <xref:System.Printing.PrintTicket> alternatif bir istek yerine geçecek.  
  
3. Yazıcı çift yönlüyi destekliyorsa, örnek kod, çift yönlü için soran bir <xref:System.Printing.PrintTicket> oluşturur. Ancak uygulama <xref:System.Printing.PrintTicket> öğesinde kullanılabilir olan her bir yazıcı ayarını belirtmez. Bu, hem programcı hem de program zamanının boşa harcanmasına neden olur. Bunun yerine, kod yalnızca çift yönlü istekleri ayarlar ve ardından bu <xref:System.Printing.PrintTicket> mevcut, tam olarak yapılandırılmış ve doğrulanan <xref:System.Printing.PrintTicket>ile birleştirir, bu durumda kullanıcının varsayılan <xref:System.Printing.PrintTicket>.  
  
4. Buna göre, örnek, kullanıcının varsayılan <xref:System.Printing.PrintTicket>yeni, minimal <xref:System.Printing.PrintTicket> birleştirmek için <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> yöntemini çağırır. Bu, özelliklerinden biri olarak yeni <xref:System.Printing.PrintTicket> içeren bir <xref:System.Printing.ValidationResult> döndürür.  
  
5. Örnek daha sonra yeni <xref:System.Printing.PrintTicket> çift yönlü olarak istekli testi sınar. Varsa, örnek bunu Kullanıcı için yeni varsayılan yazdırma bileti yapar. Yukarıdaki 2. adım ayrıldıysa ve yazıcı uzun bir süre boyunca çift yönlüyi desteklemiyorsa, test `false`sonuçlanmış olur. (Yukarıdaki nota bakın.)  
  
6. Son önemli adım, <xref:System.Printing.PrintQueue.Commit%2A> yöntemiyle <xref:System.Printing.PrintQueue> <xref:System.Printing.PrintQueue.UserPrintTicket%2A> özelliğindeki değişikliği yürütmeniz.  
  
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

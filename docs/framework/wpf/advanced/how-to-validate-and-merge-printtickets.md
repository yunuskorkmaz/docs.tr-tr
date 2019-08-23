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
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="32416-102">Nasıl yapılır: PrintTickets'i Doğrulama ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="32416-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="32416-103">Yazdırma şeması, esnek ve Genişletilebilir <xref:System.Printing.PrintCapabilities> ve <xref:System.Printing.PrintTicket> öğeleri içerir. [](https://go.microsoft.com/fwlink/?LinkId=186397) [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32416-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="32416-104">Daha önce bir yazdırma cihazının özellikleri, ikincisi ise cihazın belirli bir dizi belge, tek belge veya ayrı bir sayfa için bu özellikleri nasıl kullanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="32416-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="32416-105">Yazdırmayı destekleyen bir uygulama için tipik bir görev dizisi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="32416-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="32416-106">Yazıcının yeteneklerini belirleme.</span><span class="sxs-lookup"><span data-stu-id="32416-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="32416-107">Bu özellikleri kullanacak şekilde yapılandırın. <xref:System.Printing.PrintTicket></span><span class="sxs-lookup"><span data-stu-id="32416-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="32416-108">' İ doğrulayın. <xref:System.Printing.PrintTicket></span><span class="sxs-lookup"><span data-stu-id="32416-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="32416-109">Bu makalede bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="32416-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32416-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="32416-110">Example</span></span>  
 <span data-ttu-id="32416-111">Aşağıdaki basit örnekte, yalnızca bir yazıcının çift taraflı yazdırma gibi çift yönlü olarak bir yazıcının destekleyebilip destekleyemeyeceğini ilgileniyoruz.</span><span class="sxs-lookup"><span data-stu-id="32416-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="32416-112">Ana adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="32416-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="32416-113">Yöntemine sahip bir <xref:System.Printing.PrintCapabilities> nesne alın. <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A></span><span class="sxs-lookup"><span data-stu-id="32416-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="32416-114">İstediğiniz özelliğin varlığını test edin.</span><span class="sxs-lookup"><span data-stu-id="32416-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="32416-115">Aşağıdaki örnekte, sayfanın uzun tarafında "sayfa <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> açma" ile <xref:System.Printing.PrintCapabilities> bir kağıt yaprağının her iki tarafında da yazdırma yeteneğinin olması için nesnesinin özelliğini test ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="32416-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="32416-116">Bir koleksiyon `Contains` olduğundan, yöntemi <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>kullanırız. <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A></span><span class="sxs-lookup"><span data-stu-id="32416-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="32416-117">Bu adım kesinlikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="32416-117">This step is not strictly necessary.</span></span> <span data-ttu-id="32416-118">Aşağıda kullanılan <xref:System.Printing.PrintTicket> Yöntem, içindeki her isteği yazıcının özelliklerine göre denetleyecektir. <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A></span><span class="sxs-lookup"><span data-stu-id="32416-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="32416-119">İstenen yetenek yazıcı tarafından desteklenmiyorsa, yazıcı sürücüsü yöntemi tarafından <xref:System.Printing.PrintTicket> döndürülen alternatif bir istek yerine geçecek.</span><span class="sxs-lookup"><span data-stu-id="32416-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="32416-120">Yazıcı çift yönlüyi destekliyorsa, örnek kod çift yönlü için <xref:System.Printing.PrintTicket> isteyen bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="32416-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="32416-121">Ancak uygulama, <xref:System.Printing.PrintTicket> öğesinde kullanılabilen her bir olası yazıcı ayarını belirtmez.</span><span class="sxs-lookup"><span data-stu-id="32416-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="32416-122">Bu, hem programcı hem de program zamanının boşa harcanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="32416-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="32416-123">Bunun yerine, kod yalnızca çift yönlü istekleri ayarlar ve ardından bunu <xref:System.Printing.PrintTicket> mevcut, tam olarak yapılandırılmış ve <xref:System.Printing.PrintTicket>doğrulanan bir ile birleştirir, bu durumda kullanıcının varsayılan <xref:System.Printing.PrintTicket>' i.</span><span class="sxs-lookup"><span data-stu-id="32416-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="32416-124">Buna göre, örnek, kullanıcının <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> varsayılan <xref:System.Printing.PrintTicket> <xref:System.Printing.PrintTicket>değeriyle yeni, en az bir birleştirme yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="32416-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="32416-125">Bu, özelliklerinden <xref:System.Printing.ValidationResult> biri olarak yeni <xref:System.Printing.PrintTicket> bir içeren bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="32416-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="32416-126">Örnek daha sonra yeni <xref:System.Printing.PrintTicket> isteklerin çift yönlüde olmasını sınar.</span><span class="sxs-lookup"><span data-stu-id="32416-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="32416-127">Varsa, örnek bunu Kullanıcı için yeni varsayılan yazdırma bileti yapar.</span><span class="sxs-lookup"><span data-stu-id="32416-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="32416-128">Yukarıdaki 2. adım ayrıldıysa ve yazıcı uzun bir süre boyunca çift yönlüyi desteklemiyorsa, test sonuçlanmış `false`olur.</span><span class="sxs-lookup"><span data-stu-id="32416-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="32416-129">(Yukarıdaki nota bakın.)</span><span class="sxs-lookup"><span data-stu-id="32416-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="32416-130">Son önemli adım, <xref:System.Printing.PrintQueue.UserPrintTicket%2A> <xref:System.Printing.PrintQueue.Commit%2A> yönteminin özelliği <xref:System.Printing.PrintQueue> ile olan özelliğindeki değişikliği yürütmeniz.</span><span class="sxs-lookup"><span data-stu-id="32416-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="32416-131">Bu örneği hızlıca sınayabilmeniz için geri kalanı aşağıda sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="32416-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="32416-132">Bir proje ve ad alanı oluşturun ve ardından bu makaledeki kod parçacıklarını ad alanı bloğuna yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="32416-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="32416-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32416-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="32416-134">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="32416-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="32416-135">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="32416-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="32416-136">Şemayı Yazdır</span><span class="sxs-lookup"><span data-stu-id="32416-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)

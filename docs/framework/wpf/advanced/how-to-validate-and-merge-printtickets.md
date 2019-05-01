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
ms.openlocfilehash: be8b299c99515394bc676cfd7a715cb82ac4d58c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051122"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="49f90-102">Nasıl yapılır: PrintTickets'i Doğrulama ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="49f90-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="49f90-103">[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Yazdırma şema](https://go.microsoft.com/fwlink/?LinkId=186397) esnek ve Genişletilebilir içerir <xref:System.Printing.PrintCapabilities> ve <xref:System.Printing.PrintTicket> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="49f90-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="49f90-104">Yazdırma cihazı yeteneklerini eski maddeler halinde listeler ve cihaz belirli bir sırayla belgeleri, belgenin veya tek tek sayfa göre bu özellikleri nasıl kullanması gereken ikinci belirtir.</span><span class="sxs-lookup"><span data-stu-id="49f90-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="49f90-105">Tipik bir yazdırma destekleyen bir uygulama için görev dizisi şu şekilde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="49f90-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="49f90-106">Yazıcı özellikleri belirler.</span><span class="sxs-lookup"><span data-stu-id="49f90-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="49f90-107">Yapılandırma bir <xref:System.Printing.PrintTicket> bu özellikleri kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="49f90-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="49f90-108">Doğrulama <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="49f90-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="49f90-109">Bu makalede bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="49f90-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49f90-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="49f90-110">Example</span></span>  
 <span data-ttu-id="49f90-111">Aşağıdaki basit örnekte, biz yalnızca olup bir yazıcıya çift yönlü baskı destekleyebilir ilgilendiğiniz — iki taraflı yazdırma.</span><span class="sxs-lookup"><span data-stu-id="49f90-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="49f90-112">Önemli adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="49f90-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="49f90-113">Alma bir <xref:System.Printing.PrintCapabilities> nesnesi ile <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="49f90-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="49f90-114">İstediğiniz yeteneğinin olup olmadığını test edin.</span><span class="sxs-lookup"><span data-stu-id="49f90-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="49f90-115">Aşağıdaki örnekte, test ederiz <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> özelliği <xref:System.Printing.PrintCapabilities> uzun sayfa tarafında nesne iki tarafındaki "sayfa açma" ile bir sayfa yazdırma yeteneğini varlığını.</span><span class="sxs-lookup"><span data-stu-id="49f90-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="49f90-116">Bu yana <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> bir koleksiyon olduğundan kullandığımız `Contains` yöntemi <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="49f90-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49f90-117">Bu adım, kesinlikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="49f90-117">This step is not strictly necessary.</span></span> <span data-ttu-id="49f90-118"><xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Aşağıda kullanılan yöntem her isteği denetleyecek <xref:System.Printing.PrintTicket> yazıcı yeteneklerine karşı.</span><span class="sxs-lookup"><span data-stu-id="49f90-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="49f90-119">İstenen özellik yazıcı tarafından desteklenmiyorsa, yazıcı sürücüsü alternatif bir istekte kullanacak <xref:System.Printing.PrintTicket> yöntem tarafından döndürülen.</span><span class="sxs-lookup"><span data-stu-id="49f90-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="49f90-120">Yazıcı çift yönlü baskı destekliyorsa, örnek kod oluşturur bir <xref:System.Printing.PrintTicket> için çift yönlü baskı sorar.</span><span class="sxs-lookup"><span data-stu-id="49f90-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="49f90-121">Ancak uygulama, her olası yazıcı bulunan ayarını belirtmiyor <xref:System.Printing.PrintTicket> öğesi.</span><span class="sxs-lookup"><span data-stu-id="49f90-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="49f90-122">Bu, hem Programcı ve program zaman kısıp olacaktır.</span><span class="sxs-lookup"><span data-stu-id="49f90-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="49f90-123">Bunun yerine, kodu yalnızca çift yönlü baskı isteği ayarlar ve bu birleştirir <xref:System.Printing.PrintTicket> , tam olarak yapılandırılmış ve doğrulanır, varolan bir <xref:System.Printing.PrintTicket>, bu durumda, kullanıcının varsayılan <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="49f90-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="49f90-124">Buna örnek çağırır <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> yöntemi yeni, birleştirme için en az <xref:System.Printing.PrintTicket> kullanıcının varsayılan <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="49f90-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="49f90-125">Bu döndürür bir <xref:System.Printing.ValidationResult> yeni içeren <xref:System.Printing.PrintTicket> özelliklerinden biri olarak.</span><span class="sxs-lookup"><span data-stu-id="49f90-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="49f90-126">Örnek daha sonra test yeni <xref:System.Printing.PrintTicket> çift yönlü baskı ister.</span><span class="sxs-lookup"><span data-stu-id="49f90-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="49f90-127">Varsa, ardından örnek kullanıcı için yeni varsayılan yazdırma bileti kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="49f90-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="49f90-128">Yukarıdaki 2. adım atlanmışsa ve yazıcıya çift yönlü baskı uzun kenarı boyunca desteklemiyor durumunda, test sonuçlanırdı `false`.</span><span class="sxs-lookup"><span data-stu-id="49f90-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="49f90-129">(Yukarıdaki nota bakın.)</span><span class="sxs-lookup"><span data-stu-id="49f90-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="49f90-130">Değişikliği kaydetmek için son önemli adım olan <xref:System.Printing.PrintQueue.UserPrintTicket%2A> özelliği <xref:System.Printing.PrintQueue> ile <xref:System.Printing.PrintQueue.Commit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="49f90-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="49f90-131">Bu örnekte hızlıca test edebilirsiniz böylece geri kalanı aşağıda sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="49f90-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="49f90-132">Bir proje ve bir ad alanı oluşturma ve kod parçacıkları bu makaledeki ad alanı bloğuna yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="49f90-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="49f90-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49f90-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="49f90-134">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="49f90-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="49f90-135">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="49f90-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="49f90-136">Şema Yazdırma</span><span class="sxs-lookup"><span data-stu-id="49f90-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)

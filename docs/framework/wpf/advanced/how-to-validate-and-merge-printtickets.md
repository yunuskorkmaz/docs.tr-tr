---
title: "Nasıl yapılır: PrintTickets'i Doğrulama ve Birleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5cf2091d50433bb936b3d4976d1c3eabea73edc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="07c53-102">Nasıl yapılır: PrintTickets'i Doğrulama ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="07c53-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="07c53-103">[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Yazdırma şema](http://go.microsoft.com/fwlink/?LinkId=186397) esnek ve Genişletilebilir içeren <xref:System.Printing.PrintCapabilities> ve <xref:System.Printing.PrintTicket> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="07c53-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](http://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="07c53-104">Yazdırma cihazı yeteneklerini eski maddeler halinde listelemektedir ve aygıtın bu özellikler belgeleri, belgenin veya tek tek sayfa belirli bir dizi göre nasıl kullanması gereken ikinci belirtir.</span><span class="sxs-lookup"><span data-stu-id="07c53-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="07c53-105">Tipik bir yazdırma destekleyen bir uygulama için görev dizisi aşağıdaki gibi olur.</span><span class="sxs-lookup"><span data-stu-id="07c53-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1.  <span data-ttu-id="07c53-106">Yazıcının yeteneklerini belirler.</span><span class="sxs-lookup"><span data-stu-id="07c53-106">Determine a printer's capabilities.</span></span>  
  
2.  <span data-ttu-id="07c53-107">Yapılandırma bir <xref:System.Printing.PrintTicket> bu özellikleri kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="07c53-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3.  <span data-ttu-id="07c53-108">Doğrulama <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="07c53-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="07c53-109">Bu makalede bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="07c53-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07c53-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="07c53-110">Example</span></span>  
 <span data-ttu-id="07c53-111">Aşağıdaki basit örnekte, biz yalnızca olup bir yazıcıya çift yönlü baskı desteklemediği ilgilendiğiniz — iki taraflı yazdırma.</span><span class="sxs-lookup"><span data-stu-id="07c53-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="07c53-112">Önemli adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="07c53-112">The major steps are as follows.</span></span>  
  
1.  <span data-ttu-id="07c53-113">Alma bir <xref:System.Printing.PrintCapabilities> nesnesi ile <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07c53-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2.  <span data-ttu-id="07c53-114">İstediğiniz özelliğin varlığını test edin.</span><span class="sxs-lookup"><span data-stu-id="07c53-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="07c53-115">Aşağıdaki örnekte, biz test <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> özelliği <xref:System.Printing.PrintCapabilities> nesnesi, her iki tarafında "sayfa dönmesi" ile bir sayfa yazdırma yeteneğini varlığını sayfası uzun tarafında.</span><span class="sxs-lookup"><span data-stu-id="07c53-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="07c53-116">Bu yana <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> bir koleksiyondur kullanırız `Contains` yöntemi <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="07c53-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07c53-117">Bu adım kesinlikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="07c53-117">This step is not strictly necessary.</span></span> <span data-ttu-id="07c53-118"><xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Aşağıda kullanılan yöntem her istek denetleyecek <xref:System.Printing.PrintTicket> yazıcı yeteneklerine karşı.</span><span class="sxs-lookup"><span data-stu-id="07c53-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="07c53-119">İstenen özellik yazıcı tarafından desteklenmiyorsa, yazıcı sürücüsü içinde alternatif bir istek yerine <xref:System.Printing.PrintTicket> yöntemi tarafından döndürülen.</span><span class="sxs-lookup"><span data-stu-id="07c53-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3.  <span data-ttu-id="07c53-120">Yazıcı çift yönlü baskı destekliyorsa, örnek kod oluşturur bir <xref:System.Printing.PrintTicket> için çift yönlü baskı sorar.</span><span class="sxs-lookup"><span data-stu-id="07c53-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="07c53-121">Ancak uygulama her olası yazıcı bulunan ayarını belirtmiyor <xref:System.Printing.PrintTicket> öğesi.</span><span class="sxs-lookup"><span data-stu-id="07c53-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="07c53-122">Programcı ve program zamanı için kayıp olacaktır.</span><span class="sxs-lookup"><span data-stu-id="07c53-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="07c53-123">Bunun yerine, kod yalnızca çift yönlü baskı isteği ayarlar ve bu birleştirir <xref:System.Printing.PrintTicket> , tam olarak yapılandırılmış ve doğrulandığında, varolan <xref:System.Printing.PrintTicket>, bu durumda, kullanıcının varsayılan <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="07c53-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4.  <span data-ttu-id="07c53-124">Buna örnek çağırır <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> yeni, birleştirme yöntemi en az <xref:System.Printing.PrintTicket> kullanıcının varsayılan ile <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="07c53-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="07c53-125">Bu döndürür bir <xref:System.Printing.ValidationResult> yeni içeren <xref:System.Printing.PrintTicket> özelliklerinden biri olarak.</span><span class="sxs-lookup"><span data-stu-id="07c53-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5.  <span data-ttu-id="07c53-126">Örnek daha sonra testleri yeni <xref:System.Printing.PrintTicket> çift yönlü baskı ister.</span><span class="sxs-lookup"><span data-stu-id="07c53-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="07c53-127">Destekliyorsa, ardından örnek kullanıcı için yeni varsayılan yazdırma bileti kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="07c53-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="07c53-128">Yukarıdaki adım 2 atlanmışsa ve yazıcı uzun kenar boyunca çift yönlü baskı desteklemiyor durumunda test sonuçlanırdı `false`.</span><span class="sxs-lookup"><span data-stu-id="07c53-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="07c53-129">(Yukarıdaki nota bakın.)</span><span class="sxs-lookup"><span data-stu-id="07c53-129">(See the note above.)</span></span>  
  
6.  <span data-ttu-id="07c53-130">Değişikliği kaydetmek için son önemli adım olan <xref:System.Printing.PrintQueue.UserPrintTicket%2A> özelliği <xref:System.Printing.PrintQueue> ile <xref:System.Printing.PrintQueue.Commit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07c53-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="07c53-131">Bu örnek hızlı bir şekilde test edebilirsiniz, geri kalanı aşağıda sunulur.</span><span class="sxs-lookup"><span data-stu-id="07c53-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="07c53-132">Proje ve bir ad alanı oluşturmak ve bu makaledeki kod parçacıkları ad alanı bloğuna yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="07c53-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="07c53-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07c53-133">See Also</span></span>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="07c53-134">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="07c53-134">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="07c53-135">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="07c53-135">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="07c53-136">Şema Yazdırma</span><span class="sxs-lookup"><span data-stu-id="07c53-136">Print Schema</span></span>](http://go.microsoft.com/fwlink/?LinkId=186397)

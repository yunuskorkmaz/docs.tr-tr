---
title: "Nasıl yapılır: Yazdırma Kuyruklarının Alt Kümesini Numaralandırma"
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
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 393d1692526551b1eb9aa16f48d3c78c3cd6692f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="60cce-102">Nasıl yapılır: Yazdırma Kuyruklarının Alt Kümesini Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="60cce-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="60cce-103">Yazıcılar şirket çapında kümesi yönetme bilgi teknolojisi (BT) uzmanları tarafından karşılaşılan yaygın bir durum, belirli özelliklere sahip yazıcıların listesini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="60cce-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="60cce-104">Bu işlev tarafından sağlanan <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemi bir <xref:System.Printing.PrintServer> nesne ve <xref:System.Printing.EnumeratedPrintQueueTypes> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="60cce-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60cce-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="60cce-105">Example</span></span>  
 <span data-ttu-id="60cce-106">Aşağıdaki örnek kod listelemek istediğimiz yazdırma sıralarını özelliklerini belirtin bayraklar dizisi oluşturarak başlar.</span><span class="sxs-lookup"><span data-stu-id="60cce-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="60cce-107">Bu örnekte, yazdırma sunucusunda yerel olarak yüklenir ve paylaşılan yazdırma sıralarını arıyoruz.</span><span class="sxs-lookup"><span data-stu-id="60cce-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="60cce-108"><xref:System.Printing.EnumeratedPrintQueueTypes> Numaralandırması pek çok olasılığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="60cce-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="60cce-109">Kod sonra oluşturur bir <xref:System.Printing.LocalPrintServer> nesnesi, türetilmiş bir sınıf <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="60cce-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="60cce-110">Yerel yazdırma sunucusuna uygulama çalıştıran bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="60cce-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="60cce-111">Son önemli adım diziye geçirmektir <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="60cce-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="60cce-112">Son olarak, sonuçların kullanıcıya sunulur.</span><span class="sxs-lookup"><span data-stu-id="60cce-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="60cce-113">Bu örnek sağlayarak genişletebilirsiniz `foreach` her bir yazdırma sırası daha da incelemek döngü filtreleme.</span><span class="sxs-lookup"><span data-stu-id="60cce-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="60cce-114">Örneğin, iki taraflı yazdırma döngüyle çağırarak desteklemeyen yazıcıları her yazdırma sırasının ekran <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemi ve çift yönlü baskı varlığını test döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="60cce-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60cce-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60cce-115">See Also</span></span>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="60cce-116">WPF belgeleri</span><span class="sxs-lookup"><span data-stu-id="60cce-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="60cce-117">Yazdırma genel bakış</span><span class="sxs-lookup"><span data-stu-id="60cce-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="60cce-118">Microsoft XPS Belge Yazıcısı</span><span class="sxs-lookup"><span data-stu-id="60cce-118">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)

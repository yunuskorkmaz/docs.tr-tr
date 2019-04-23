---
title: 'Nasıl yapılır: Yazdırma Kuyruklarının Alt Kümesini Numaralandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: adcfff0196bd0430ec1ae563fbd5489062de11f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217191"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="8ea2d-102">Nasıl yapılır: Yazdırma Kuyruklarının Alt Kümesini Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="8ea2d-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="8ea2d-103">Belirli özelliklere sahip yazıcıların listesini oluşturmak için olduğu yazıcıların şirket genelindeki bir ayar kümesini yönetme, bilgi teknolojisi (BT) uzmanları tarafından karşılaşılan yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="8ea2d-104">Bu işlev tarafından sağlanan <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemi bir <xref:System.Printing.PrintServer> nesne ve <xref:System.Printing.EnumeratedPrintQueueTypes> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ea2d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ea2d-105">Example</span></span>  
 <span data-ttu-id="8ea2d-106">Aşağıdaki örnekte, bir dizi listelemek istediğiniz yazdırma sıralarını özelliklerini belirten bayrakları oluşturarak kodu başlar.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="8ea2d-107">Bu örnekte, yazdırma sunucusunda yerel olarak yüklenir ve paylaşılan yazdırma sıraları için arıyoruz.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="8ea2d-108"><xref:System.Printing.EnumeratedPrintQueueTypes> Numaralandırma birçok diğer olanaklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="8ea2d-109">Ardından kod oluşturur bir <xref:System.Printing.LocalPrintServer> türetilmiş bir sınıf nesnesi <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="8ea2d-110">Yerel yazdırma sunucusu, uygulamanın çalıştığı bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="8ea2d-111">Son önemli adım dizisine geçirmektir <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="8ea2d-112">Son olarak, sonuçları kullanıcıya gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="8ea2d-113">Bu örnek sağlayarak genişletilebiliyordu `foreach` her bir yazdırma sırası daha da incelemek döngü filtreleme.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="8ea2d-114">Örneğin, iki taraflı yazdırma döngüyle tarafından desteklemeyen yazıcıları her yazıcı sırasının ekran <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemi ve çift yönlü baskı varlığını test döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea2d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ea2d-115">See also</span></span>

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="8ea2d-116">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="8ea2d-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="8ea2d-117">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8ea2d-117">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="8ea2d-118">Microsoft XPS Belge Yazıcısı</span><span class="sxs-lookup"><span data-stu-id="8ea2d-118">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)

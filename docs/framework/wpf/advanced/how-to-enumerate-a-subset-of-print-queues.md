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
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094546"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="b57ad-102">Nasıl yapılır: Yazdırma Kuyruklarının Alt Kümesini Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="b57ad-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="b57ad-103">Şirket genelinde bir yazıcı kümesini yöneten Bilişim Teknolojileri (BT) uzmanlarının karşılaştığı yaygın bir durum, belirli özelliklere sahip yazıcıların bir listesini oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="b57ad-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="b57ad-104">Bu işlevsellik, bir <xref:System.Printing.PrintServer> nesnesinin <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemi ve <xref:System.Printing.EnumeratedPrintQueueTypes> numaralandırması tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b57ad-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b57ad-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b57ad-105">Example</span></span>  
 <span data-ttu-id="b57ad-106">Aşağıdaki örnekte kod, listelemek istediğimiz yazdırma sıralarının özelliklerini belirten bir bayrak dizisi oluşturarak başlar.</span><span class="sxs-lookup"><span data-stu-id="b57ad-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="b57ad-107">Bu örnekte, yazdırma sunucusuna yerel olarak yüklenen ve paylaşılan yazdırma kuyruklarını arıyoruz.</span><span class="sxs-lookup"><span data-stu-id="b57ad-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="b57ad-108"><xref:System.Printing.EnumeratedPrintQueueTypes> numaralandırması birçok farklı olasılık sağlar.</span><span class="sxs-lookup"><span data-stu-id="b57ad-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="b57ad-109">Kod daha sonra, <xref:System.Printing.PrintServer>türetilmiş bir sınıf olan bir <xref:System.Printing.LocalPrintServer> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b57ad-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="b57ad-110">Yerel yazdırma sunucusu, uygulamanın çalıştığı bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="b57ad-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="b57ad-111">Son önemli adım diziyi <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemine geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="b57ad-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="b57ad-112">Son olarak, sonuçlar kullanıcıya sunulur.</span><span class="sxs-lookup"><span data-stu-id="b57ad-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="b57ad-113">Bu örneği, her bir yazdırma kuyruğundaki adımları daha fazla filtreleyerek `foreach` döngüsüne sahip olacak şekilde genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b57ad-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="b57ad-114">Örneğin, döngüyü her bir yazdırma sırasının <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemini çağırarak ve çift yönlülüme varlığı için döndürülen değeri test ederek iki taraflı yazdırmayı desteklemeyen yazıcılar izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b57ad-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b57ad-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b57ad-115">See also</span></span>

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="b57ad-116">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="b57ad-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="b57ad-117">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b57ad-117">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="b57ad-118">Microsoft XPS Belge Yazıcısı</span><span class="sxs-lookup"><span data-stu-id="b57ad-118">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)

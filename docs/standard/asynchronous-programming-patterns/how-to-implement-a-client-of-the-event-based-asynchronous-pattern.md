---
title: 'Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: a6363bc5900c797ebd3422430f368bf2668d3364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567282"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="04ea6-102">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama</span><span class="sxs-lookup"><span data-stu-id="04ea6-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="04ea6-103">Aşağıdaki kod örneğinde aynılarını bir bileşen kullanımı gösterilmiştir [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="04ea6-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="04ea6-104">Bu örnek için form kullanır `PrimeNumberCalculator` açıklanan bileşen [nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="04ea6-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="04ea6-105">Bu örnek kullanan proje çalıştırdığınızda bir kılavuz ve iki düğme "Asal sayı hesaplayıcı" formla görürsünüz: **yeni görev Başlat** ve **iptal**.</span><span class="sxs-lookup"><span data-stu-id="04ea6-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="04ea6-106">Tıklayabilirsiniz **yeni görev Başlat** birkaç kez art arda düğmesini ve her tıklatma için rastgele oluşturulmuş test sayının asal olup olmadığını belirlemek için bir hesaplama zaman uyumsuz bir işlem başlatılacak.</span><span class="sxs-lookup"><span data-stu-id="04ea6-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="04ea6-107">Form düzenli aralıklarla ilerleme ve artımlı sonuçlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="04ea6-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="04ea6-108">Her bir işlemin benzersiz görev kimlik atanır.</span><span class="sxs-lookup"><span data-stu-id="04ea6-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="04ea6-109">Hesaplamanın sonucu görüntülenen **sonuç** sütun; test sayı prime değilse olarak etiketlenir **bileşik,** ve ilk bölen görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="04ea6-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="04ea6-110">İle tüm bekleyen işlemi iptal edilebilir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="04ea6-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="04ea6-111">Birden çok seçimin yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="04ea6-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04ea6-112">Çoğu numaraları asal olmaz.</span><span class="sxs-lookup"><span data-stu-id="04ea6-112">Most numbers will not be prime.</span></span> <span data-ttu-id="04ea6-113">Sonra birkaç tamamlanmış işlemler asal sayı bulunan değil, yalnızca diğer görevler başlatın ve bazı asal sayılar sonunda bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="04ea6-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04ea6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="04ea6-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="04ea6-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04ea6-115">See Also</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>

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
ms.openlocfilehash: f834ce4a0ec2208eee80ce8c3ffebfa6fdeeb5b1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289414"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="a12e4-102">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama</span><span class="sxs-lookup"><span data-stu-id="a12e4-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="a12e4-103">Aşağıdaki kod örneği, [olay tabanlı zaman uyumsuz düzene genel bakış](event-based-asynchronous-pattern-overview.md)'a uygun bir bileşenin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a12e4-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="a12e4-104">Bu örnek için form, `PrimeNumberCalculator` [nasıl yapılır: olay tabanlı zaman uyumsuz kalıbı destekleyen bir bileşeni uygulama](component-that-supports-the-event-based-asynchronous-pattern.md)bölümünde açıklanan bileşeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="a12e4-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="a12e4-105">Bu örneği kullanan bir projeyi çalıştırdığınızda, kılavuz ve iki düğme içeren bir "ana sayı Hesaplayıcı" formu görürsünüz: **Yeni görev başlatın** ve **iptal edin**.</span><span class="sxs-lookup"><span data-stu-id="a12e4-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="a12e4-106">**Yeni görev Başlat** düğmesine art arda birkaç kez tıklayabilirsiniz ve her tıklama için zaman uyumsuz bir işlem, rastgele oluşturulmuş bir test numarasının asal olup olmadığını belirlemekte bir hesaplama başlatır.</span><span class="sxs-lookup"><span data-stu-id="a12e4-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="a12e4-107">Form düzenli olarak ilerleme ve artımlı sonuçları görüntüleyecektir.</span><span class="sxs-lookup"><span data-stu-id="a12e4-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="a12e4-108">Her işleme benzersiz bir görev KIMLIĞI atanır.</span><span class="sxs-lookup"><span data-stu-id="a12e4-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="a12e4-109">Hesaplama sonucu **sonuç** sütununda görüntülenir; sınama numarası ana değilse, bileşik olarak etiketlenir ve ilk **böleni** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a12e4-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="a12e4-110">Bekleyen tüm işlemler **iptal** düğmesi ile iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a12e4-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="a12e4-111">Birden çok seçim yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="a12e4-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a12e4-112">Çoğu sayı ana olmaz.</span><span class="sxs-lookup"><span data-stu-id="a12e4-112">Most numbers will not be prime.</span></span> <span data-ttu-id="a12e4-113">Birkaç tamamlanmış işlemden sonra bir asal sayı bulmadıysanız, daha fazla görev başlatmanız yeterlidir ve sonuç olarak bazı asal sayılar bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a12e4-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a12e4-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a12e4-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="a12e4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a12e4-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>

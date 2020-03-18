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
ms.openlocfilehash: 50aa36d2caf774638ad20323813f0de3703aab2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "69950714"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="936c9-102">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama</span><span class="sxs-lookup"><span data-stu-id="936c9-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="936c9-103">Aşağıdaki kod örneği, [Olay tabanlı Asynchronous Desen Genel Bakış'a](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)uyan bir bileşenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="936c9-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="936c9-104">Bu örnekteki form, `PrimeNumberCalculator` Nasıl [Tanımlanır: Olay tabanlı Asynchronous Deseni destekleyen bir Bileşeni Uygulama'da](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)açıklanan bileşeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="936c9-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="936c9-105">Bu örneği kullanan bir proje çalıştırdığınızda, ızgaralı ve iki düğmeli bir "Asal Sayı Hesapmakinesi" formu görürsünüz: **Yeni Görevi Başlat** ve İptal **Et.**</span><span class="sxs-lookup"><span data-stu-id="936c9-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="936c9-106">Yeni Görev **Başlat** düğmesini art arda birkaç kez tıklatabilirsiniz ve her tıklama için, rasgele oluşturulan test numarasının asal olup olmadığını belirlemek için bir hesaplama başlatılır.</span><span class="sxs-lookup"><span data-stu-id="936c9-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="936c9-107">Form periyodik olarak ilerleme ve artımlı sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="936c9-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="936c9-108">Her işlem benzersiz bir görev kimliği atanır.</span><span class="sxs-lookup"><span data-stu-id="936c9-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="936c9-109">Hesaplama sonucu **Sonuç** sütununda görüntülenir; test numarası asal değilse, **Bileşik** olarak etiketlenir ve ilk bölengörüntülenir.</span><span class="sxs-lookup"><span data-stu-id="936c9-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="936c9-110">Bekleyen herhangi bir işlem **İptal** düğmesi ile iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="936c9-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="936c9-111">Birden çok seçim yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="936c9-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="936c9-112">Çoğu sayı asal olmaz.</span><span class="sxs-lookup"><span data-stu-id="936c9-112">Most numbers will not be prime.</span></span> <span data-ttu-id="936c9-113">Tamamlanan birkaç işlemden sonra bir asal sayı bulamadıysanız, daha fazla görev başlatmanız yeterlidir ve sonunda bazı asal sayılar bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="936c9-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="936c9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="936c9-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="936c9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="936c9-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>

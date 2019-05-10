---
title: BackgroundWorker Bileşenine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: da1d87464ef30fb549a2c201170e81c45cbdf6fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587734"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="dad13-102">BackgroundWorker Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dad13-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="dad13-103">Yürütmek için uzun bir zaman alabilir çok sık gerçekleştirilen işlemler vardır.</span><span class="sxs-lookup"><span data-stu-id="dad13-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="dad13-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="dad13-104">For example:</span></span>  
  
- <span data-ttu-id="dad13-105">Görüntüyü indirir</span><span class="sxs-lookup"><span data-stu-id="dad13-105">Image downloads</span></span>  
  
- <span data-ttu-id="dad13-106">Web hizmeti çağrıları</span><span class="sxs-lookup"><span data-stu-id="dad13-106">Web service invocations</span></span>  
  
- <span data-ttu-id="dad13-107">Dosya indirir ve yükler (eşler arası uygulamalar dahil)</span><span class="sxs-lookup"><span data-stu-id="dad13-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
- <span data-ttu-id="dad13-108">Karmaşık yerel hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="dad13-108">Complex local computations</span></span>  
  
- <span data-ttu-id="dad13-109">Veritabanı işlemleri</span><span class="sxs-lookup"><span data-stu-id="dad13-109">Database transactions</span></span>  
  
- <span data-ttu-id="dad13-110">Göreli bellek erişimi yavaş hızını verilen, yerel disk erişimi</span><span class="sxs-lookup"><span data-stu-id="dad13-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="dad13-111">Bunlar gibi işlemler, bunlar çalışırken kesmek, kullanıcı arabirimi neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dad13-111">Operations like these can cause your user interface to hang while they are running.</span></span> <span data-ttu-id="dad13-112">Duyarlı bir kullanıcı Arabirimi istediğiniz ve uzun gecikmeler gibi işlemlerle ilişkili ile karşı karşıya kalmaktadır <xref:System.ComponentModel.BackgroundWorker> bileşeni, uygun bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="dad13-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="dad13-113"><xref:System.ComponentModel.BackgroundWorker> Bileşen zaman uyumsuz olarak ("arka planda"), zaman alıcı işlemleri yürütmek için yeteneği sağlar, uygulamanızın ana UI iş parçacığından farklı bir iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="dad13-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="dad13-114">Kullanılacak bir <xref:System.ComponentModel.BackgroundWorker>, yalnızca arka planda yürütülmesi için ne zaman çalışan yöntemi bildirmek ve ardından çağırmanızı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dad13-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="dad13-115">Çağıran iş parçacığını çalışan yöntemin zaman uyumsuz olarak çalışırken normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="dad13-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="dad13-116">Yöntemi tamamlandığında <xref:System.ComponentModel.BackgroundWorker> Açmadığınızda tarafından çağıran iş parçacığını uyarıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> isteğe bağlı olarak işlemin sonuçlarını içeren olay.</span><span class="sxs-lookup"><span data-stu-id="dad13-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="dad13-117"><xref:System.ComponentModel.BackgroundWorker> Bileşen kullanılabilir **araç kutusu**, **bileşenleri** sekmesi. Eklemek için bir <xref:System.ComponentModel.BackgroundWorker> formunuza sürükleyin <xref:System.ComponentModel.BackgroundWorker> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="dad13-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="dad13-118">Bileşen tepsisinde görünür ve özelliklerini görünür **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="dad13-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="dad13-119">Zaman uyumsuz işlemi başlatmak için <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dad13-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="dad13-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> İsteğe bağlı alan `object` çalışan yönteminize bağımsız değişkenleri geçirmek için kullanılan parametre.</span><span class="sxs-lookup"><span data-stu-id="dad13-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="dad13-121"><xref:System.ComponentModel.BackgroundWorker> Sınıfı kullanıma sunan <xref:System.ComponentModel.BackgroundWorker.DoWork> olayı, kendisine, iş parçacığı bağlı aracılığıyla bir <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="dad13-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="dad13-122"><xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisini alır bir <xref:System.ComponentModel.DoWorkEventArgs> olan parametre bir <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="dad13-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="dad13-123">Bu özellik parametresinden alır <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve çağırılacak olan çalışan yönteminize iletilen <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="dad13-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="dad13-124">Aşağıdaki örnek adlı bir çalışan yöntemden bir sonuç atama gösterir `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="dad13-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="dad13-125">Konumunda bulabilirsiniz daha büyük bir örneğin parçasıdır [nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="dad13-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="dad13-126">Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz. [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="dad13-126">For more information on using event handlers, see [Events](../../../standard/events/index.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="dad13-127">Her türlü çoklu iş parçacığı kullanırken, büyük olasılıkla kendiniz çok önemli ve karmaşık hataları ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="dad13-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="dad13-128">Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="dad13-128">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="dad13-129">Kullanma hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker> sınıfı [nasıl yapılır: Arka planda işlem çalıştırma](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="dad13-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad13-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dad13-130">See also</span></span>

- [<span data-ttu-id="dad13-131">Yönetilen iş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="dad13-131">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="dad13-132">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dad13-132">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="dad13-133">Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="dad13-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)

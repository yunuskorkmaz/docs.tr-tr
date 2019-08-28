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
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046100"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="50c16-102">BackgroundWorker Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="50c16-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="50c16-103">Yürütülmesi uzun zaman alabilir çok sayıda gerçekleştirilen işlem vardır.</span><span class="sxs-lookup"><span data-stu-id="50c16-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="50c16-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="50c16-104">For example:</span></span>  
  
- <span data-ttu-id="50c16-105">Görüntü İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="50c16-105">Image downloads</span></span>  
  
- <span data-ttu-id="50c16-106">Web hizmeti etkinleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="50c16-106">Web service invocations</span></span>  
  
- <span data-ttu-id="50c16-107">Dosya indirmeleri ve karşıya yüklemeleri (eşler arası uygulamalar için de dahil)</span><span class="sxs-lookup"><span data-stu-id="50c16-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
- <span data-ttu-id="50c16-108">Karmaşık yerel hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="50c16-108">Complex local computations</span></span>  
  
- <span data-ttu-id="50c16-109">Veritabanı işlemleri</span><span class="sxs-lookup"><span data-stu-id="50c16-109">Database transactions</span></span>  
  
- <span data-ttu-id="50c16-110">Yerel disk erişimi, bellek erişimine göre yavaş hız olarak verildi</span><span class="sxs-lookup"><span data-stu-id="50c16-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="50c16-111">Bunlar gibi işlemler, Kullanıcı arabiriminize çalışırken engel olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="50c16-111">Operations like these can cause your user interface to block while they are running.</span></span> <span data-ttu-id="50c16-112">Yanıt veren bir kullanıcı arabirimi istediğinizde ve söz konusu işlemlerle ilişkili uzun gecikmeler varsa, <xref:System.ComponentModel.BackgroundWorker> bileşen kullanışlı bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="50c16-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="50c16-113"><xref:System.ComponentModel.BackgroundWorker> Bileşen, uygulamanızın ana kullanıcı arabirimi iş parçacığından farklı bir iş parçacığında zaman uyumsuz işlemleri ("arka planda") yürütme yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="50c16-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="50c16-114">Bir <xref:System.ComponentModel.BackgroundWorker>kullanmak için, arka planda hangi zaman tüketen çalışan yönteminin yürütüleceğini ve sonra <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi çağırılacağını söylemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="50c16-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="50c16-115">Çalışan yöntemi zaman uyumsuz olarak çalışırken, çağıran iş parçacığınız normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="50c16-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="50c16-116">Yöntem tamamlandığında <xref:System.ComponentModel.BackgroundWorker> , isteğe bağlı olarak işlemin sonuçlarını içeren <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayı tetikleyerek çağıran iş parçacığını uyarır.</span><span class="sxs-lookup"><span data-stu-id="50c16-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="50c16-117">Bileşen araç kutusundan, **Bileşenler** sekmesinde kullanılabilir. <xref:System.ComponentModel.BackgroundWorker> Formunuza bir <xref:System.ComponentModel.BackgroundWorker> eklemek için, <xref:System.ComponentModel.BackgroundWorker> bileşeni formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="50c16-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="50c16-118">Bileşen tepsisinde görünür ve özellikleri **Özellikler** penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="50c16-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="50c16-119">Zaman uyumsuz işleminizi başlatmak için <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="50c16-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="50c16-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>, çalışan yönteminizin `object` bağımsız değişkenlerini geçirmek için kullanılabilen isteğe bağlı bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="50c16-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="50c16-121">Sınıfı, çalışan iş <xref:System.ComponentModel.BackgroundWorker.DoWork> parçacığınız bir <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi aracılığıyla bağlı olan olayı ortaya koyar. <xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="50c16-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="50c16-122">Olay işleyicisi bir <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği olan <xref:System.ComponentModel.DoWorkEventArgs> bir parametre alır. <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="50c16-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="50c16-123">Bu özellik öğesinden <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> parametresini alır ve <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisinde çağrılabilecek çalışan yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="50c16-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="50c16-124">Aşağıdaki örnekte, adlı `ComputeFibonacci`bir çalışan yönteminden bir sonucun nasıl atanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50c16-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="50c16-125">Daha büyük bir örnek bir parçasıdır ve bu, [nasıl yapılır: Arka plan Işlemi](how-to-implement-a-form-that-uses-a-background-operation.md)kullanan bir form uygulayın.</span><span class="sxs-lookup"><span data-stu-id="50c16-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="50c16-126">Olay işleyicilerini kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="50c16-126">For more information on using event handlers, see [Events](../../../standard/events/index.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="50c16-127">Herhangi bir sıralamanın çoklu iş parçacığı kullanımı kullanılırken, kendinizi çok önemli ve karmaşık hatalara maruz kalırsınız.</span><span class="sxs-lookup"><span data-stu-id="50c16-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="50c16-128">Çoklu iş parçacığı kullanan herhangi bir çözümü uygulamadan önce, [yönetilen Iş parçacığı En Iyi uygulamalarına](../../../standard/threading/managed-threading-best-practices.md) danışın.</span><span class="sxs-lookup"><span data-stu-id="50c16-128">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="50c16-129"><xref:System.ComponentModel.BackgroundWorker> Sınıfını kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir Işlemi arka planda](how-to-run-an-operation-in-the-background.md)çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="50c16-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c16-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50c16-130">See also</span></span>

- [<span data-ttu-id="50c16-131">Yönetilen Iş parçacığı</span><span class="sxs-lookup"><span data-stu-id="50c16-131">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="50c16-132">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="50c16-132">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="50c16-133">Nasıl yapılır: Arka plan Işlemi kullanan bir form uygulama</span><span class="sxs-lookup"><span data-stu-id="50c16-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)

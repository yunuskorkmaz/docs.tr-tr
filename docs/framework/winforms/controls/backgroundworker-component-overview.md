---
title: "BackgroundWorker Bileşenine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: BackgroundWorker
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96fc5e1929589321872ba30d8c3821b4fd47ca8b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="1304f-102">BackgroundWorker Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1304f-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="1304f-103">Yürütmek için uzun zaman alabilir pek çok sık gerçekleştirilen işlemler vardır.</span><span class="sxs-lookup"><span data-stu-id="1304f-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="1304f-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1304f-104">For example:</span></span>  
  
-   <span data-ttu-id="1304f-105">Görüntüyü indirir</span><span class="sxs-lookup"><span data-stu-id="1304f-105">Image downloads</span></span>  
  
-   <span data-ttu-id="1304f-106">Web hizmeti çağrıları</span><span class="sxs-lookup"><span data-stu-id="1304f-106">Web service invocations</span></span>  
  
-   <span data-ttu-id="1304f-107">Dosyası indirilir ve (eşler arası uygulamaları dahil) yükler</span><span class="sxs-lookup"><span data-stu-id="1304f-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
-   <span data-ttu-id="1304f-108">Karmaşık yerel hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="1304f-108">Complex local computations</span></span>  
  
-   <span data-ttu-id="1304f-109">Veritabanı işlemleri</span><span class="sxs-lookup"><span data-stu-id="1304f-109">Database transactions</span></span>  
  
-   <span data-ttu-id="1304f-110">Göreli bellek erişimi yavaş hızı verilen yerel disk erişimi</span><span class="sxs-lookup"><span data-stu-id="1304f-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="1304f-111">Bunlar gibi işlemleri Kullanıcı Arabiriminizin çalıştıkları sırada askıda kalmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1304f-111">Operations like these can cause your user interface to hang while they are running.</span></span> <span data-ttu-id="1304f-112">Bir yanıt veren UI istediğiniz ve gecikmelere gibi işlemlerle ilişkili ile karşılaştığı <xref:System.ComponentModel.BackgroundWorker> bileşeni, uygun bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="1304f-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="1304f-113"><xref:System.ComponentModel.BackgroundWorker> Bileşen imkanı sunar, zaman uyumsuz olarak ("arka planda"), zaman alıcı işlemlerini yürütmek için uygulamanızın ana kullanıcı Arabirimi iş parçacığından farklı bir iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="1304f-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="1304f-114">Kullanılacak bir <xref:System.ComponentModel.BackgroundWorker>, yalnızca arka planda yürütmek için ne zaman çalışan yöntem bildirin ve size çağrısı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1304f-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="1304f-115">Çağıran, iş parçacığı çalışan yöntemi zaman uyumsuz olarak çalışırken normal şekilde çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="1304f-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="1304f-116">Yöntem tamamlandığında <xref:System.ComponentModel.BackgroundWorker> çağıran iş parçacığı tarafından tetikleme uyarıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> isteğe bağlı olarak işlemi sonuçlarını içeren olay.</span><span class="sxs-lookup"><span data-stu-id="1304f-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="1304f-117"><xref:System.ComponentModel.BackgroundWorker> Bileşen edinilebilir **araç**, **bileşenleri** sekmesi. Eklemek için bir <xref:System.ComponentModel.BackgroundWorker> formunuza sürükleyin <xref:System.ComponentModel.BackgroundWorker> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="1304f-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="1304f-118">Bileşen tepsisinde görünür ve özelliklerini görüntülenmesini **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="1304f-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="1304f-119">Zaman uyumsuz işlemi başlatmak için kullanmak <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1304f-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="1304f-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>İsteğe bağlı bir alan `object` çalışan yönteminizi bağımsız değişkenleri geçirmek için kullanılan parametre.</span><span class="sxs-lookup"><span data-stu-id="1304f-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="1304f-121"><xref:System.ComponentModel.BackgroundWorker> Sınıf çıkarır <xref:System.ComponentModel.BackgroundWorker.DoWork> için çalışan iş parçacığı kullanıma açılmış üzerinden olay, bir <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1304f-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="1304f-122"><xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi geçen bir <xref:System.ComponentModel.DoWorkEventArgs> sahip parametresi bir <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1304f-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="1304f-123">Bu özellik parametreyi alır <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve çağrılacağı içinde çalışan yönteminize iletilen <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1304f-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="1304f-124">Aşağıdaki örnek, bir sonucu olarak adlandırılan bir alt yöntemden atamak gösterilmiştir `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="1304f-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="1304f-125">Konumunda bulabilirsiniz daha büyük bir örneğin parçasıdır [nasıl yapılır: bir arka plan işlemi kullanan bir Form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="1304f-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="1304f-126">Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz: [olayları](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="1304f-126">For more information on using event handlers, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1304f-127">Her tür çoklu iş parçacığı kullanımı kullanırken, potansiyel olarak kendiniz için çok önemli ve karmaşık hatalar kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="1304f-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="1304f-128">Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../../docs/standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="1304f-128">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="1304f-129">Kullanma hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker> sınıfı için bkz: [nasıl yapılır: bir işlemi arka planda çalışan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="1304f-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1304f-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1304f-130">See Also</span></span>  
 [<span data-ttu-id="1304f-131">IN derleme değil: Visual Basic'te çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="1304f-131">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [<span data-ttu-id="1304f-132">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="1304f-132">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)

---
title: BackgroundWorker Bileşeni
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
ms.openlocfilehash: 0baf54d27cf33eef7e4df7019ee98b42eba40205
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011807"
---
# <a name="backgroundworker-component"></a><span data-ttu-id="ccc86-102">BackgroundWorker Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ccc86-102">BackgroundWorker Component</span></span>
<span data-ttu-id="ccc86-103">`BackgroundWorker` Bileşen form veya bir işlem zaman uyumsuz olarak çalıştırmak için denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccc86-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ccc86-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ccc86-104">In This Section</span></span>  
 [<span data-ttu-id="ccc86-105">BackgroundWorker Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ccc86-105">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="ccc86-106">Açıklar `BackgroundWorker` bileşeni, uygulamanızın ana UI iş parçacığından farklı bir iş parçacığında zaman uyumsuz olarak ("arka planda"), zaman alıcı işlemlerinin olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccc86-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="ccc86-107">İzlenecek yol: Arka planda işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ccc86-107">Walkthrough: Running an Operation in the Background</span></span>](walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="ccc86-108">Nasıl kullanılacağını gösteren `BackgroundWorker` Bileşen tasarımcısında uzun süren bir işlem ayrı bir iş parçacığı üzerinde çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="ccc86-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="ccc86-109">Nasıl yapılır: Arka planda işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ccc86-109">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="ccc86-110">Nasıl kullanılacağını gösteren `BackgroundWorker` bileşen uzun süren bir işlem ayrı bir iş parçacığı üzerinde çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="ccc86-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="ccc86-111">İzlenecek yol: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="ccc86-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="ccc86-112">Zaman uyumsuz olarak matematiksel hesaplamalar yapan Tasarımcı kullanarak bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ccc86-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="ccc86-113">Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="ccc86-113">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="ccc86-114">Zaman uyumsuz olarak matematiksel hesaplamalar yapan bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ccc86-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="ccc86-115">Nasıl yapılır: Arka planda dosya indirme</span><span class="sxs-lookup"><span data-stu-id="ccc86-115">How to: Download a File in the Background</span></span>](how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="ccc86-116">Nasıl kullanılacağını gösteren `BackgroundWorker` ayrı bir iş parçacığında bir dosyayı indirmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="ccc86-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ccc86-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ccc86-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="ccc86-118">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="ccc86-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="ccc86-119">Verileri tutan türünü açıklayan <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="ccc86-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="ccc86-120">Verileri tutan türünü açıklayan <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="ccc86-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ccc86-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ccc86-121">Related Sections</span></span>  
 [<span data-ttu-id="ccc86-122">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ccc86-122">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="ccc86-123">Ne zaman uyumsuz desen çok iş parçacıklı uygulamalar avantajları pek çok iş parçacıklı tasarımında devralınan karmaşık sorunların gizleyerek kullanılabilir hale getirir açıklar.</span><span class="sxs-lookup"><span data-stu-id="ccc86-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>

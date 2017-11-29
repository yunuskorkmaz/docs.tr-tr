---
title: "BackgroundWorker Bileşeni"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cbcbc786c19ad1af74114915b0fd0689d466fcbe
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="backgroundworker-component"></a><span data-ttu-id="cede7-102">BackgroundWorker Bileşeni</span><span class="sxs-lookup"><span data-stu-id="cede7-102">BackgroundWorker Component</span></span>
<span data-ttu-id="cede7-103">`BackgroundWorker` Bileşen form veya bir işlem zaman uyumsuz olarak çalıştırmak için denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="cede7-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cede7-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cede7-104">In This Section</span></span>  
 [<span data-ttu-id="cede7-105">BackgroundWorker bileşenine genel bakış</span><span class="sxs-lookup"><span data-stu-id="cede7-105">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="cede7-106">Açıklar `BackgroundWorker` bileşeni, uygulamanızın ana kullanıcı Arabirimi iş parçacığından farklı bir iş parçacığı üzerinde zaman uyumsuz olarak ("arka planda"), zaman alıcı işlemlerini yürütmek için olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cede7-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="cede7-107">İzlenecek yol: bir işlemi arka planda çalışan</span><span class="sxs-lookup"><span data-stu-id="cede7-107">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="cede7-108">Nasıl kullanılacağı ortaya `BackgroundWorker` uzun süren işlem ayrı bir iş parçacığı üzerinde çalıştırmak için Tasarımcısı'nda bileşen.</span><span class="sxs-lookup"><span data-stu-id="cede7-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="cede7-109">Nasıl yapılır: bir işlemi arka planda çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cede7-109">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="cede7-110">Nasıl kullanılacağı ortaya `BackgroundWorker` uzun süren işlem ayrı bir iş parçacığı üzerinde çalıştırmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="cede7-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="cede7-111">İzlenecek yol: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="cede7-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="cede7-112">Zaman uyumsuz olarak matematiksel hesaplamalar yapan Tasarımcısı'nı kullanarak bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cede7-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="cede7-113">Nasıl yapılır: bir arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="cede7-113">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="cede7-114">Zaman uyumsuz olarak matematiksel hesaplamalar yapan bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cede7-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="cede7-115">Nasıl yapılır: arka planda dosya indirme</span><span class="sxs-lookup"><span data-stu-id="cede7-115">How to: Download a File in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="cede7-116">Nasıl kullanılacağı ortaya `BackgroundWorker` ayrı bir iş parçacığı üzerinde bir dosyayı indirmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="cede7-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cede7-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="cede7-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="cede7-118">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="cede7-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="cede7-119">İçin verileri tutar türünü açıklayan <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="cede7-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="cede7-120">İçin verileri tutar türünü açıklayan <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="cede7-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cede7-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="cede7-121">Related Sections</span></span>  
 [<span data-ttu-id="cede7-122">Olay tabanlı zaman uyumsuz desene genel bakış</span><span class="sxs-lookup"><span data-stu-id="cede7-122">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="cede7-123">Ne zaman uyumsuz desen birden çok iş parçacıklı uygulamalar avantajları birçok karmaşık sorunları birden çok iş parçacıklı tasarımında yapısında gizleme çalışırken kullanılabilir hale getirir açıklar.</span><span class="sxs-lookup"><span data-stu-id="cede7-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>

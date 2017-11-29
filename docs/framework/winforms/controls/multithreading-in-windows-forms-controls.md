---
title: "Windows Forms Denetimlerinde Çoklu Kullanım"
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
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c4651ca9707dcf0fac2edea0f004275cfcf18cf2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="a52a5-102">Windows Forms Denetimlerinde Çoklu Kullanım</span><span class="sxs-lookup"><span data-stu-id="a52a5-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="a52a5-103">Birçok uygulamada, kullanıcı arabirimi (UI) daha iyi yanıt başka bir iş parçacığında zaman işlemleri gerçekleştirerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a52a5-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="a52a5-104">Çok sayıda araç kullanılabilir çoklu iş parçacığı kullanımı dahil olmak üzere, Windows Forms denetimleri <xref:System.Threading> ad alanı, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi ve `BackgroundWorker` bileşeni.</span><span class="sxs-lookup"><span data-stu-id="a52a5-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a52a5-105">`BackgroundWorker` Bileşeni değiştirir ve işlevlerini ekler <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi; seçerseniz ancak bunlar geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="a52a5-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="a52a5-106">Daha fazla bilgi için bkz: [BackgroundWorker bileşenine genel bakış](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a52a5-106">For more information, see [BackgroundWorker Component Overview](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a52a5-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a52a5-107">In This Section</span></span>  
 [<span data-ttu-id="a52a5-108">Nasıl yapılır: Windows Forms denetimlerine iş parçacığı açısından güvenli çağrılar yapın</span><span class="sxs-lookup"><span data-stu-id="a52a5-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="a52a5-109">Windows Forms denetimlerine iş parçacığı güvenli aramalar yapma gösterir.</span><span class="sxs-lookup"><span data-stu-id="a52a5-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="a52a5-110">Nasıl yapılır: dosya aramak için arka plan iş parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="a52a5-110">How to: Use a Background Thread to Search for Files</span></span>](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="a52a5-111">Nasıl kullanılacağını gösterir <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A> dosyaları zaman uyumsuz olarak aramak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="a52a5-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a52a5-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a52a5-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="a52a5-113">Zaman uyumsuz işlemleri için iş parçacığı yalıtan bir bileşen belgeler.</span><span class="sxs-lookup"><span data-stu-id="a52a5-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="a52a5-114">Zaman uyumsuz ses yükleme belgeler.</span><span class="sxs-lookup"><span data-stu-id="a52a5-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="a52a5-115">Bir resmi zaman uyumsuz olarak yüklemek nasıl belgelenir.</span><span class="sxs-lookup"><span data-stu-id="a52a5-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a52a5-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a52a5-116">Related Sections</span></span>  
 [<span data-ttu-id="a52a5-117">Nasıl yapılır: bir işlemi arka planda çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a52a5-117">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="a52a5-118">İle uzun süren bir işlem gerçekleştirmek nasıl gösterir <xref:System.ComponentModel.BackgroundWorker> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="a52a5-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="a52a5-119">BackgroundWorker bileşenine genel bakış</span><span class="sxs-lookup"><span data-stu-id="a52a5-119">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="a52a5-120">Nasıl kullanılacağını açıklayan konuları sağlar <xref:System.ComponentModel.BackgroundWorker> zaman uyumsuz işlemleri için bileşen.</span><span class="sxs-lookup"><span data-stu-id="a52a5-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>

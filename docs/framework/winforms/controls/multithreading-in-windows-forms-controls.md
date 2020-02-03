---
title: Denetimlerde çoklu iş parçacığı
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 79832e12a10f02c909d2a28270594bcb4ea68656
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742134"
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="339c6-102">Windows Forms Denetimlerinde Çoklu Kullanım</span><span class="sxs-lookup"><span data-stu-id="339c6-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="339c6-103">Birçok uygulamada, başka bir iş parçacığı üzerinde zaman alan işlemler gerçekleştirerek Kullanıcı arabiriminizi (UI) daha hızlı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="339c6-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="339c6-104"><xref:System.Threading> ad alanı, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi ve `BackgroundWorker` bileşeni de dahil olmak üzere Windows Forms denetimlerinizi çoklu iş parçacıklı bir dizi araç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="339c6-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="339c6-105">`BackgroundWorker` bileşeni, <xref:System.Threading> ad alanına ve <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemine işlevsellik koyar. Bununla birlikte, bunlar ' ı seçerseniz hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="339c6-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="339c6-106">Daha fazla bilgi için bkz. [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="339c6-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="339c6-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="339c6-107">In This Section</span></span>  
 [<span data-ttu-id="339c6-108">Nasıl yapılır: Windows Forms Denetimlerine İş Parçacığı Güvenli Aramalar Yapma</span><span class="sxs-lookup"><span data-stu-id="339c6-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="339c6-109">Windows Forms denetimlerine iş parçacığı güvenli çağrıların nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="339c6-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="339c6-110">Nasıl Yapılır: Dosya Aramak için Arka Plan İş Parçacığı Kullanma</span><span class="sxs-lookup"><span data-stu-id="339c6-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="339c6-111"><xref:System.Threading> ad alanını ve <xref:System.Windows.Forms.Control.BeginInvoke%2A> yöntemini zaman uyumsuz olarak aramak için nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="339c6-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="339c6-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="339c6-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="339c6-113">Zaman uyumsuz işlemler için çalışan iş parçacığını kapsülleyen bir bileşeni belgeler.</span><span class="sxs-lookup"><span data-stu-id="339c6-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="339c6-114">Bir sesin zaman uyumsuz olarak nasıl yükleneceğini belgeler.</span><span class="sxs-lookup"><span data-stu-id="339c6-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="339c6-115">Bir görüntünün zaman uyumsuz olarak nasıl yükleneceğini belgeler.</span><span class="sxs-lookup"><span data-stu-id="339c6-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="339c6-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="339c6-116">Related Sections</span></span>  
 [<span data-ttu-id="339c6-117">Nasıl Yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="339c6-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="339c6-118"><xref:System.ComponentModel.BackgroundWorker> bileşeniyle zaman alan bir işlemin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="339c6-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="339c6-119">BackgroundWorker Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="339c6-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="339c6-120"><xref:System.ComponentModel.BackgroundWorker> bileşeninin zaman uyumsuz işlemler için nasıl kullanılacağını betimleyen konular sağlar.</span><span class="sxs-lookup"><span data-stu-id="339c6-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>

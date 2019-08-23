---
title: Windows Forms Denetimlerinde Çoklu Kullanım
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952680"
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="c5fe7-102">Windows Forms Denetimlerinde Çoklu Kullanım</span><span class="sxs-lookup"><span data-stu-id="c5fe7-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="c5fe7-103">Birçok uygulamada, başka bir iş parçacığı üzerinde zaman alan işlemler gerçekleştirerek Kullanıcı arabiriminizi (UI) daha hızlı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5fe7-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="c5fe7-104"><xref:System.Threading> Ad alanı `BackgroundWorker` , yöntem ve bileşen dahil Windows Forms denetimlerinizi çoklu iş parçacığı için kullanılabilir bir dizi araç vardır. <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c5fe7-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5fe7-105">Bileşeni, <xref:System.Threading> ad alanına ve <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemine işlevsellik ekler ve bu ve yöntemi sağlar; ancak, bunlar, hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. `BackgroundWorker`</span><span class="sxs-lookup"><span data-stu-id="c5fe7-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="c5fe7-106">Daha fazla bilgi için bkz. [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c5fe7-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5fe7-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c5fe7-107">In This Section</span></span>  
 [<span data-ttu-id="c5fe7-108">Nasıl yapılır: Windows Forms denetimlerine Iş parçacığına güvenli çağrılar yapma</span><span class="sxs-lookup"><span data-stu-id="c5fe7-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="c5fe7-109">Windows Forms denetimlerine iş parçacığı güvenli çağrıların nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5fe7-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="c5fe7-110">Nasıl yapılır: Dosya aramak için arka plan Iş parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="c5fe7-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="c5fe7-111">Zaman uyumsuz olarak dosya aramak <xref:System.Threading> için ad alanının <xref:System.Windows.Forms.Control.BeginInvoke%2A> ve yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5fe7-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c5fe7-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c5fe7-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="c5fe7-113">Zaman uyumsuz işlemler için çalışan iş parçacığını kapsülleyen bir bileşeni belgeler.</span><span class="sxs-lookup"><span data-stu-id="c5fe7-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="c5fe7-114">Bir sesin zaman uyumsuz olarak nasıl yükleneceğini belgeler.</span><span class="sxs-lookup"><span data-stu-id="c5fe7-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="c5fe7-115">Bir görüntünün zaman uyumsuz olarak nasıl yükleneceğini belgeler.</span><span class="sxs-lookup"><span data-stu-id="c5fe7-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c5fe7-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c5fe7-116">Related Sections</span></span>  
 [<span data-ttu-id="c5fe7-117">Nasıl yapılır: Arka planda Işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c5fe7-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="c5fe7-118"><xref:System.ComponentModel.BackgroundWorker> Bileşeniyle zaman alan bir işlemin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5fe7-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="c5fe7-119">BackgroundWorker Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5fe7-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="c5fe7-120"><xref:System.ComponentModel.BackgroundWorker> Bileşeninin zaman uyumsuz işlemler için nasıl kullanılacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5fe7-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>

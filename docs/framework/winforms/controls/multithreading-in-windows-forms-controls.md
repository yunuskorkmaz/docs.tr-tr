---
title: Windows Forms Denetimlerinde Çoklu Kullanım
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cc7f358a62c8057abb77e1f5a28544bb6c858d98
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703328"
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="d7956-102">Windows Forms Denetimlerinde Çoklu Kullanım</span><span class="sxs-lookup"><span data-stu-id="d7956-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="d7956-103">Birçok uygulamada, uygulamanızın kullanıcı arabirimini (UI) daha hızlı yanıt veren başka bir iş parçacığı üzerinde harcanan zamanı ortadan kaldırır işlemleri gerçekleştirerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7956-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="d7956-104">Araçlar kullanılabilir çoklu iş parçacığı kullanımı dahil olmak üzere, Windows Forms denetimleri <xref:System.Threading> ad alanı, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi ve `BackgroundWorker` bileşeni.</span><span class="sxs-lookup"><span data-stu-id="d7956-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7956-105">`BackgroundWorker` Bileşeni değiştirir ve işlevsellik ekler <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi; seçerseniz ancak bu geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="d7956-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="d7956-106">Daha fazla bilgi için [BackgroundWorker bileşenine genel bakış](backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d7956-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7956-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d7956-107">In This Section</span></span>  
 [<span data-ttu-id="d7956-108">Nasıl yapılır: Windows Forms denetimlerine iş parçacığı güvenli aramalar yapın</span><span class="sxs-lookup"><span data-stu-id="d7956-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="d7956-109">Windows Forms denetimlerine iş parçacığı güvenli aramalar yapma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7956-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="d7956-110">Nasıl yapılır: Dosya aramak için bir arka plan iş parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="d7956-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="d7956-111">Nasıl kullanılacağını gösterir <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A> dosyaları zaman uyumsuz olarak aramak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d7956-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d7956-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d7956-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="d7956-113">Zaman uyumsuz işlemleri için iş parçacığı kapsülleyen bir bileşen belgeler.</span><span class="sxs-lookup"><span data-stu-id="d7956-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="d7956-114">Zaman uyumsuz ses yükleme konusunda belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7956-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="d7956-115">Bir görüntüyü zaman uyumsuz olarak yükleme konusunda belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7956-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d7956-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d7956-116">Related Sections</span></span>  
 [<span data-ttu-id="d7956-117">Nasıl yapılır: Arka planda işlem çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d7956-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="d7956-118">Uzun süren bir işlem ile yapma işlemi açıklanır <xref:System.ComponentModel.BackgroundWorker> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="d7956-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="d7956-119">BackgroundWorker Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d7956-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="d7956-120">Nasıl kullanılacağını açıklayan konuları sağlar <xref:System.ComponentModel.BackgroundWorker> zaman uyumsuz işlemler için bileşen.</span><span class="sxs-lookup"><span data-stu-id="d7956-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>

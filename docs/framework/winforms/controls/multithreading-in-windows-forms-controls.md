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
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="173ae-102">Windows Forms Denetimlerinde Çoklu Kullanım</span><span class="sxs-lookup"><span data-stu-id="173ae-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="173ae-103">Birçok uygulamada, kullanıcı arabirimi (UI) daha iyi yanıt başka bir iş parçacığında zaman işlemleri gerçekleştirerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="173ae-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="173ae-104">Çok sayıda araç kullanılabilir çoklu iş parçacığı kullanımı dahil olmak üzere, Windows Forms denetimleri <xref:System.Threading> ad alanı, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi ve `BackgroundWorker` bileşeni.</span><span class="sxs-lookup"><span data-stu-id="173ae-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="173ae-105">`BackgroundWorker` Bileşeni değiştirir ve işlevlerini ekler <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> yöntemi; seçerseniz ancak bunlar geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="173ae-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="173ae-106">Daha fazla bilgi için bkz: [BackgroundWorker bileşenine genel bakış](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span><span class="sxs-lookup"><span data-stu-id="173ae-106">For more information, see [BackgroundWorker Component Overview](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="173ae-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="173ae-107">In This Section</span></span>  
 [<span data-ttu-id="173ae-108">Nasıl yapılır: Windows Forms Denetimlerine İş Parçacığı Güvenli Aramalar Yapma</span><span class="sxs-lookup"><span data-stu-id="173ae-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="173ae-109">Windows Forms denetimlerine iş parçacığı güvenli aramalar yapma gösterir.</span><span class="sxs-lookup"><span data-stu-id="173ae-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="173ae-110">Nasıl Yapılır: Dosya Aramak için Arka Plan İş Parçacığı Kullanma</span><span class="sxs-lookup"><span data-stu-id="173ae-110">How to: Use a Background Thread to Search for Files</span></span>](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="173ae-111">Nasıl kullanılacağını gösterir <xref:System.Threading> ad alanı ve <xref:System.Windows.Forms.Control.BeginInvoke%2A> dosyaları zaman uyumsuz olarak aramak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="173ae-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="173ae-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="173ae-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="173ae-113">Zaman uyumsuz işlemleri için iş parçacığı yalıtan bir bileşen belgeler.</span><span class="sxs-lookup"><span data-stu-id="173ae-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="173ae-114">Zaman uyumsuz ses yükleme belgeler.</span><span class="sxs-lookup"><span data-stu-id="173ae-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="173ae-115">Bir resmi zaman uyumsuz olarak yüklemek nasıl belgelenir.</span><span class="sxs-lookup"><span data-stu-id="173ae-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="173ae-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="173ae-116">Related Sections</span></span>  
 [<span data-ttu-id="173ae-117">Nasıl Yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="173ae-117">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="173ae-118">İle uzun süren bir işlem gerçekleştirmek nasıl gösterir <xref:System.ComponentModel.BackgroundWorker> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="173ae-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="173ae-119">BackgroundWorker Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="173ae-119">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="173ae-120">Nasıl kullanılacağını açıklayan konuları sağlar <xref:System.ComponentModel.BackgroundWorker> zaman uyumsuz işlemleri için bileşen.</span><span class="sxs-lookup"><span data-stu-id="173ae-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>

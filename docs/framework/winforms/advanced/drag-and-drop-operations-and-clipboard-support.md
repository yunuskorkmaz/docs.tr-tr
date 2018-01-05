---
title: "Sürükle ve Bırak İşlemleri ve Pano Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27ba3e94e28a1e26d370fa6daf7c93019d1e2428
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="6b66d-102">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="6b66d-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="6b66d-103">Bir dizi olay, özellikle işleyerek kullanıcı sürükle ve bırak işlemleri Windows tabanlı bir uygulama içinde etkinleştirebilirsiniz <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, ve <xref:System.Windows.Forms.Control.DragDrop> olaylar.</span><span class="sxs-lookup"><span data-stu-id="6b66d-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="6b66d-104">Kullanıcı Kes/kopyala/yapıştır desteği de uygulayabilir ve basit yöntem çağrılarını kullanarak Windows tabanlı uygulamalar içinde panoya kullanıcı veri aktarın.</span><span class="sxs-lookup"><span data-stu-id="6b66d-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b66d-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6b66d-105">In This Section</span></span>  
 [<span data-ttu-id="6b66d-106">İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6b66d-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="6b66d-107">Sürükle ve bırak işlemi başlatmak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b66d-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="6b66d-108">Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6b66d-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="6b66d-109">Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirmek nasıl gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b66d-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="6b66d-110">Nasıl yapılır: Panoya Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="6b66d-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="6b66d-111">Programlama yoluyla panoya bilgi eklemek için bir yol anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b66d-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="6b66d-112">Nasıl yapılır: Panodan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="6b66d-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="6b66d-113">Pano'ya depolanan verilere erişmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="6b66d-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6b66d-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6b66d-114">Related Sections</span></span>  
 [<span data-ttu-id="6b66d-115">Windows Forms'ta Sürükle ve Bırak İşlevi</span><span class="sxs-lookup"><span data-stu-id="6b66d-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="6b66d-116">Yöntem, olayları ve sürükle ve bırak davranışı uygulamak için kullanılan sınıflar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b66d-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="6b66d-117">Sürükleme işlemi devam etmek için izin ister olayın ayrıntılı olarak incelenmektedir açıklar.</span><span class="sxs-lookup"><span data-stu-id="6b66d-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="6b66d-118">Sürükleme işlemi başlangıç için merkezi yöntemin ayrıntılı olarak incelenmektedir açıklar.</span><span class="sxs-lookup"><span data-stu-id="6b66d-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="6b66d-119">Ayrıca bkz. [nasıl yapılır: etkin MDI alt verileri Gönder](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6b66d-119">Also see [How to: Send Data to the Active MDI Child](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span></span>

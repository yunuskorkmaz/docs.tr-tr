---
title: Sürükle ve Bırak İşlemleri ve Pano Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: c2bb3c24298ffe5308af03c5af5bae697a22c33b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398638"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="7e4fb-102">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="7e4fb-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="7e4fb-103">Bir dizi olayı, özellikle işleyerek Windows tabanlı bir uygulama içinde kullanıcı sürükle ve bırak işlemleri etkinleştirebilirsiniz <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, ve <xref:System.Windows.Forms.Control.DragDrop> olayları.</span><span class="sxs-lookup"><span data-stu-id="7e4fb-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="7e4fb-104">Kullanıcı Kes/kopyala/yapıştır desteği de uygulayabilirsiniz ve basit bir yöntem çağrıları kullanarak kullanıcı verilerini Windows tabanlı uygulamalarınızı içinde panoya aktarır.</span><span class="sxs-lookup"><span data-stu-id="7e4fb-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e4fb-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7e4fb-105">In This Section</span></span>  
 [<span data-ttu-id="7e4fb-106">İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="7e4fb-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="7e4fb-107">Bir Sürükle ve bırak işlemini başlatmak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e4fb-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="7e4fb-108">Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="7e4fb-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="7e4fb-109">Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e4fb-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="7e4fb-110">Nasıl yapılır: Panoya Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="7e4fb-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="7e4fb-111">Programlama yoluyla panoya bilgi eklemek için bir yol açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e4fb-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="7e4fb-112">Nasıl yapılır: Panodan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="7e4fb-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="7e4fb-113">Panodaki depolanan verilere nasıl erişileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e4fb-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7e4fb-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7e4fb-114">Related Sections</span></span>  
 [<span data-ttu-id="7e4fb-115">Windows Forms'ta Sürükle ve Bırak İşlevi</span><span class="sxs-lookup"><span data-stu-id="7e4fb-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="7e4fb-116">Yöntemler, olaylar ve sürükle-bırak davranışı uygulamak için kullanılan sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e4fb-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="7e4fb-117">Sürükleme işlemi devam etmek için izin isteyen etkinliğin ayrıntılı olarak incelenmektedir açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e4fb-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="7e4fb-118">Bir sürükleme işlemi başlangıcı için merkezi bir yöntemin ayrıntılı olarak incelenmektedir açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e4fb-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="7e4fb-119">Ayrıca bkz: [nasıl yapılır: etkin MDI alt veri gönderme](https://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7e4fb-119">Also see [How to: Send Data to the Active MDI Child](https://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span></span>

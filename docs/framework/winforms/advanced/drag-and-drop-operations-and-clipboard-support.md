---
title: Sürükle ve Bırak İşlemleri ve Pano Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 5e7bb75b648163dab7e410a159d55ebbb75f1b0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756435"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="ec4af-102">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="ec4af-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="ec4af-103">Bir dizi olayı, özellikle işleyerek Windows tabanlı bir uygulama içinde kullanıcı sürükle ve bırak işlemleri etkinleştirebilirsiniz <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, ve <xref:System.Windows.Forms.Control.DragDrop> olayları.</span><span class="sxs-lookup"><span data-stu-id="ec4af-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="ec4af-104">Kullanıcı Kes/kopyala/yapıştır desteği de uygulayabilirsiniz ve basit bir yöntem çağrıları kullanarak kullanıcı verilerini Windows tabanlı uygulamalarınızı içinde panoya aktarır.</span><span class="sxs-lookup"><span data-stu-id="ec4af-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec4af-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ec4af-105">In This Section</span></span>  
 [<span data-ttu-id="ec4af-106">İzlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ec4af-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="ec4af-107">Bir Sürükle ve bırak işlemini başlatmak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec4af-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="ec4af-108">Nasıl yapılır: Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ec4af-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="ec4af-109">Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec4af-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="ec4af-110">Nasıl yapılır: Panoya veri ekleme</span><span class="sxs-lookup"><span data-stu-id="ec4af-110">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="ec4af-111">Programlama yoluyla panoya bilgi eklemek için bir yol açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec4af-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="ec4af-112">Nasıl yapılır: Panodan veri alma</span><span class="sxs-lookup"><span data-stu-id="ec4af-112">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="ec4af-113">Panodaki depolanan verilere nasıl erişileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec4af-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ec4af-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ec4af-114">Related Sections</span></span>  
 [<span data-ttu-id="ec4af-115">Windows Forms'ta Sürükle ve Bırak İşlevi</span><span class="sxs-lookup"><span data-stu-id="ec4af-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="ec4af-116">Yöntemler, olaylar ve sürükle-bırak davranışı uygulamak için kullanılan sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec4af-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="ec4af-117">Sürükleme işlemi devam etmek için izin isteyen etkinliğin ayrıntılı olarak incelenmektedir açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec4af-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="ec4af-118">Bir sürükleme işlemi başlangıcı için merkezi bir yöntemin ayrıntılı olarak incelenmektedir açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec4af-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="ec4af-119">Ayrıca bkz: [nasıl yapılır: Etkin MDI alt öğesine veri gönderme](how-to-send-data-to-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="ec4af-119">Also see [How to: Send Data to the Active MDI Child](how-to-send-data-to-the-active-mdi-child.md).</span></span>

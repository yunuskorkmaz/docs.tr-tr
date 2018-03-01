---
title: "Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 514c283575ca54e74d23ae31d3590979be2c3ef0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a><span data-ttu-id="3a965-102">Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="3a965-102">How to: Perform Drag-and-Drop Operations Between Applications</span></span>
<span data-ttu-id="3a965-103">Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirme Bu eylem, uygulama içinde etkinleştirme daha farklı "arasında kurulan Sözleşmesi" göre katılan her iki uygulamayı davranır sürece <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> ve <xref:System.Windows.Forms.DragEventArgs.Effect%2A> Özellikler.</span><span class="sxs-lookup"><span data-stu-id="3a965-103">Performing drag-and-drop operations between applications is no different than enabling this action within an application, as long as both applications involved behave according to the "contract" established between the <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> and <xref:System.Windows.Forms.DragEventArgs.Effect%2A> properties.</span></span>  
  
 <span data-ttu-id="3a965-104">Aşağıdaki yordamda, oluşturduğunuz Windows tabanlı bir uygulama ve uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirmek için Windows işletim sistemiyle eklenmiştir WordPad sözcük işlemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a965-104">In the following procedure, you will use a Windows-based application you create and the WordPad word processor that is included with the Windows operating system to perform drag-and-drop operations between applications.</span></span> <span data-ttu-id="3a965-105">WordPad sürüklenip bırakılmasına metnin için izin verilen etkileri belirli kümesine sahiptir; Windows tabanlı bir uygulama için kod yazacaksınız bu efektleri ile çalışır. böylece sürükle ve bırak işlemleri başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3a965-105">WordPad has a certain set of allowed effects for text being dragged and dropped; the Windows-based application you will write code for will work with these effects so that drag-and-drop operations may be completed successfully.</span></span>  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a><span data-ttu-id="3a965-106">Uygulamalar arasında sürükle ve bırak yordamı gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="3a965-106">To perform a drag-and-drop procedure between applications</span></span>  
  
1.  <span data-ttu-id="3a965-107">Yeni bir Windows Forms uygulaması oluşturma.</span><span class="sxs-lookup"><span data-stu-id="3a965-107">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="3a965-108">Ekleme bir <xref:System.Windows.Forms.TextBox> Formunuza denetim.</span><span class="sxs-lookup"><span data-stu-id="3a965-108">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
3.  <span data-ttu-id="3a965-109">Yapılandırma <xref:System.Windows.Forms.TextBox> bırakılan veri almak için denetim.</span><span class="sxs-lookup"><span data-stu-id="3a965-109">Configure the <xref:System.Windows.Forms.TextBox> control to receive dropped data.</span></span>  
  
     <span data-ttu-id="3a965-110">Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3a965-110">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
4.  <span data-ttu-id="3a965-111">Windows tabanlı uygulamanızı çalıştırın ve uygulama çalışırken, WordPad çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3a965-111">Run your Windows-based application, and while the application is running, run WordPad.</span></span>  
  
     <span data-ttu-id="3a965-112">WordPad sürükle ve bırak işlemleri sağlayan Windows tarafından yüklenen bir metin Düzenleyicisi ' dir.</span><span class="sxs-lookup"><span data-stu-id="3a965-112">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="3a965-113">Tuşlarına basarak erişilebilir durumda **Başlat** düğmesi, seçme **çalıştırmak**, yazarak `WordPad` metin kutusuna **çalıştırmak** iletişim kutusu ve tıklayarak**Tamam**.</span><span class="sxs-lookup"><span data-stu-id="3a965-113">It is accessible by pressing the **Start** button, selecting **Run**, and then typing `WordPad` into the text box of the **Run** dialog box and clicking **OK**.</span></span>  
  
5.  <span data-ttu-id="3a965-114">WordPad açıldıktan sonra bir metin dizesinin içine yazın.</span><span class="sxs-lookup"><span data-stu-id="3a965-114">Once WordPad is open, type a string of text into it.</span></span>  
  
6.  <span data-ttu-id="3a965-115">Fare kullanarak, metni seçin ve ardından seçili metnin üzerine sürükleyin <xref:System.Windows.Forms.TextBox> Windows tabanlı uygulamanızda denetim.</span><span class="sxs-lookup"><span data-stu-id="3a965-115">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.TextBox> control in your Windows-based application.</span></span>  
  
     <span data-ttu-id="3a965-116">Üzerinden fare olduğunda, gözlemlemek <xref:System.Windows.Forms.TextBox> denetimi (ve sonuç olarak, Yükselt <xref:System.Windows.Forms.Control.DragEnter> olay), imleç ve seçili metne düşürebilir <xref:System.Windows.Forms.TextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="3a965-116">Observe that when you mouse over the <xref:System.Windows.Forms.TextBox> control (and, consequently, raise the <xref:System.Windows.Forms.Control.DragEnter> event), the cursor changes, and you can drop the selected text into the <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
     <span data-ttu-id="3a965-117">Ayrıca, yapılandırın, <xref:System.Windows.Forms.TextBox> sürüklenen ve WordPad bırakılan metin dizelerini izin vermek için denetim.</span><span class="sxs-lookup"><span data-stu-id="3a965-117">Additionally, you can configure your <xref:System.Windows.Forms.TextBox> control to allow text strings to be dragged and dropped into WordPad.</span></span> <span data-ttu-id="3a965-118">Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3a965-118">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a965-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a965-119">See Also</span></span>  
 [<span data-ttu-id="3a965-120">Nasıl yapılır: Panoya Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="3a965-120">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [<span data-ttu-id="3a965-121">Nasıl yapılır: Panodan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="3a965-121">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [<span data-ttu-id="3a965-122">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="3a965-122">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)

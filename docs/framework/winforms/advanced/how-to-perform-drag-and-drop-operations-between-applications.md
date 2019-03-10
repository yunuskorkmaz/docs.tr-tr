---
title: 'Nasıl yapılır: Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: 1e9556a69f3f5da4a47c5f5b1a6043a9a73dd8ff
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713448"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a><span data-ttu-id="4ca76-102">Nasıl yapılır: Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="4ca76-102">How to: Perform Drag-and-Drop Operations Between Applications</span></span>
<span data-ttu-id="4ca76-103">Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirme Bu eylem, uygulamadaki etkinleştirme değerinden farklı katılan her iki uygulama arasında kurulan "Sözleşme" göre davranır sürece <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> ve <xref:System.Windows.Forms.DragEventArgs.Effect%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="4ca76-103">Performing drag-and-drop operations between applications is no different than enabling this action within an application, as long as both applications involved behave according to the "contract" established between the <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> and <xref:System.Windows.Forms.DragEventArgs.Effect%2A> properties.</span></span>  
  
 <span data-ttu-id="4ca76-104">Aşağıdaki yordamda, oluşturduğunuz ve Windows tabanlı bir uygulama ve uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirmek için Windows işletim sistemi ile birlikte sağlanan WordPad sözcük işlemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ca76-104">In the following procedure, you will use a Windows-based application you create and the WordPad word processor that is included with the Windows operating system to perform drag-and-drop operations between applications.</span></span> <span data-ttu-id="4ca76-105">WordPad belirli bir dizi olan metin için izin verilen efektleri sürüklenebilen ve bırakılan vardır; Sürükle ve bırak işlemleri başarıyla tamamlandı, Windows tabanlı bir uygulama için kod yazacaksınız bu efektleri ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="4ca76-105">WordPad has a certain set of allowed effects for text being dragged and dropped; the Windows-based application you will write code for will work with these effects so that drag-and-drop operations may be completed successfully.</span></span>  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a><span data-ttu-id="4ca76-106">Uygulamalar arasında sürükle ve bırak yordam gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="4ca76-106">To perform a drag-and-drop procedure between applications</span></span>  
  
1.  <span data-ttu-id="4ca76-107">Yeni bir Windows Forms uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ca76-107">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="4ca76-108">Ekleme bir <xref:System.Windows.Forms.TextBox> form denetimi.</span><span class="sxs-lookup"><span data-stu-id="4ca76-108">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
3.  <span data-ttu-id="4ca76-109">Yapılandırma <xref:System.Windows.Forms.TextBox> bırakılan veri almasına izin denetimi.</span><span class="sxs-lookup"><span data-stu-id="4ca76-109">Configure the <xref:System.Windows.Forms.TextBox> control to receive dropped data.</span></span>  
  
     <span data-ttu-id="4ca76-110">Daha fazla bilgi için [izlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4ca76-110">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
4.  <span data-ttu-id="4ca76-111">Windows tabanlı uygulamanızı çalıştırın ve uygulama çalışırken WordPad çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4ca76-111">Run your Windows-based application, and while the application is running, run WordPad.</span></span>  
  
     <span data-ttu-id="4ca76-112">WordPad sürükle ve bırak işlemleri sağlayan Windows tarafından yüklenen bir metin düzenleyicidir.</span><span class="sxs-lookup"><span data-stu-id="4ca76-112">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="4ca76-113">Tuşuna basarak erişilebilir durumda **Başlat** düğmesi, seçme **çalıştırmak**, ardından yazarak `WordPad` metin kutusuna **çalıştırmak** iletişim kutusu ve tıklayarak**Tamam**.</span><span class="sxs-lookup"><span data-stu-id="4ca76-113">It is accessible by pressing the **Start** button, selecting **Run**, and then typing `WordPad` into the text box of the **Run** dialog box and clicking **OK**.</span></span>  
  
5.  <span data-ttu-id="4ca76-114">WordPad açıldıktan sonra içine bir metin dizesi yazın.</span><span class="sxs-lookup"><span data-stu-id="4ca76-114">Once WordPad is open, type a string of text into it.</span></span>  
  
6.  <span data-ttu-id="4ca76-115">Fareyi kullanarak, metni seçin ve ardından seçili metin üzerine sürükleyin <xref:System.Windows.Forms.TextBox> Windows tabanlı uygulama denetimi.</span><span class="sxs-lookup"><span data-stu-id="4ca76-115">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.TextBox> control in your Windows-based application.</span></span>  
  
     <span data-ttu-id="4ca76-116">Üzerine fare imlecinizle mesajının görüntülendiğini görün <xref:System.Windows.Forms.TextBox> denetimi (ve sonuç olarak, yükseltme <xref:System.Windows.Forms.Control.DragEnter> olay), imleç ve seçilen metne bırakabilirsiniz <xref:System.Windows.Forms.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="4ca76-116">Observe that when you mouse over the <xref:System.Windows.Forms.TextBox> control (and, consequently, raise the <xref:System.Windows.Forms.Control.DragEnter> event), the cursor changes, and you can drop the selected text into the <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
     <span data-ttu-id="4ca76-117">Buna ek olarak, yapılandırabileceğiniz, <xref:System.Windows.Forms.TextBox> sürüklenebilen ve WordPad bırakılan metin dizelerini izin vermek için denetim.</span><span class="sxs-lookup"><span data-stu-id="4ca76-117">Additionally, you can configure your <xref:System.Windows.Forms.TextBox> control to allow text strings to be dragged and dropped into WordPad.</span></span> <span data-ttu-id="4ca76-118">Daha fazla bilgi için [izlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4ca76-118">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca76-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ca76-119">See also</span></span>
- [<span data-ttu-id="4ca76-120">Nasıl yapılır: Panoya veri ekleme</span><span class="sxs-lookup"><span data-stu-id="4ca76-120">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="4ca76-121">Nasıl yapılır: Panodan veri alma</span><span class="sxs-lookup"><span data-stu-id="4ca76-121">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="4ca76-122">Sürükle ve Bırak İşlemleri ve Pano Desteği</span><span class="sxs-lookup"><span data-stu-id="4ca76-122">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)

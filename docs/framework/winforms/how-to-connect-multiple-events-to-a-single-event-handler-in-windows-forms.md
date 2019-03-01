---
title: "Nasıl yapılır: Windows Forms'ta tek olay işleyicisine birden fazla olay bağlama"
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: 869ef0d7717ca64209bc61c2ae22ce929edcec5e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967873"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="e4fec-102">Nasıl yapılır: Windows Forms'ta tek olay işleyicisine birden fazla olay bağlama</span><span class="sxs-lookup"><span data-stu-id="e4fec-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="e4fec-103">Uygulama tasarımınızı, bunu tek olay işleyicisine birden fazla olaylar için kullanın veya sahip birden çok olayı aynı yordamı gerçekleştirmek için gerekli bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4fec-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="e4fec-104">Örneğin, genellikle bir güçlü zaman-bir menü komutu, bunlar aynı işlevselliği göstermek, form üzerindeki bir düğme gibi aynı olay yükseltmek için koruyucu olur.</span><span class="sxs-lookup"><span data-stu-id="e4fec-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="e4fec-105">Özellikler penceresinde olayların görünümünü kullanarak bunu yapabilirsiniz C# veya bu adı kullanıyor `Handles` anahtar sözcüğü ve **sınıf adı** ve **yöntem adı** Visual Basic Kod Düzenleyicisi'nde açılır kutuları.</span><span class="sxs-lookup"><span data-stu-id="e4fec-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="e4fec-106">Visual Basic'te tek olay işleyicisine birden fazla olay bağlama için</span><span class="sxs-lookup"><span data-stu-id="e4fec-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1.  <span data-ttu-id="e4fec-107">Formun sağ tıklatın ve seçin **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="e4fec-107">Right-click the form and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="e4fec-108">Gelen **sınıf adı** açılan kutusunda, olay işleyicisi işlemek istediğiniz denetimlerin birini seçin.</span><span class="sxs-lookup"><span data-stu-id="e4fec-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3.  <span data-ttu-id="e4fec-109">Gelen **yöntem adı** açılan kutusunda, aşağıdakilerden birini işlemek için olay işleyicisi istediğiniz olayları seçin.</span><span class="sxs-lookup"><span data-stu-id="e4fec-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4.  <span data-ttu-id="e4fec-110">Kod Düzenleyicisi, uygun bir olay işleyicisi ekler ve yöntemi içinde ekleme noktasını yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="e4fec-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="e4fec-111">Aşağıdaki örnekte olduğu <xref:System.Windows.Forms.Control.Click> olayı <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e4fec-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  <span data-ttu-id="e4fec-112">Ekleme için işlenen istediğiniz diğer olaylar `Handles` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e4fec-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  <span data-ttu-id="e4fec-113">Uygun kodu olay işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e4fec-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="e4fec-114">C'de tek olay işleyicisine birden fazla olay bağlama için\#</span><span class="sxs-lookup"><span data-stu-id="e4fec-114">To connect multiple events to a single event handler in C\#</span></span>
  
1.  <span data-ttu-id="e4fec-115">Bir olay işleyicisi bağlanmak istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="e4fec-115">Select the control to which you want to connect an event handler.</span></span>  
  
2.  <span data-ttu-id="e4fec-116">Özellikler penceresinde tıklayın **olayları** düğmesine (![olayları düğmesi](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="e4fec-116">In the Properties window, click the **Events** button (![Events Button](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3.  <span data-ttu-id="e4fec-117">Kullanmak istediğiniz olayın adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e4fec-117">Click the name of the event that you want to handle.</span></span>  
  
4.  <span data-ttu-id="e4fec-118">Olay adının yanındaki değeri bölümünde, kullanmak istediğiniz olay yöntem imzasını eşleşen var olan olay işleyicilerinin bir listesini görüntülemek için açılan düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e4fec-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5.  <span data-ttu-id="e4fec-119">Uygun bir olay işleyicisi listeden seçin.</span><span class="sxs-lookup"><span data-stu-id="e4fec-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="e4fec-120">Kodu varolan olay işleyicisine olaya bağlamak için forma eklenir.</span><span class="sxs-lookup"><span data-stu-id="e4fec-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4fec-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4fec-121">See also</span></span>
- [<span data-ttu-id="e4fec-122">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4fec-122">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="e4fec-123">Olay İşleyicilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e4fec-123">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)

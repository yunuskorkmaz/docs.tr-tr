---
title: 'Nasıl yapılır: birden çok olayı tek bir olay Işleyicisine bağlama'
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
ms.openlocfilehash: 0591291522ab1da04fef90bf1c0a73cf33ba0518
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739599"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="f1126-102">Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama</span><span class="sxs-lookup"><span data-stu-id="f1126-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="f1126-103">Uygulama tasarımınızda, birden çok olay için tek bir olay işleyicisi kullanmak veya aynı yordamı gerçekleştirmek için birden çok olay olması gerektiğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1126-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="f1126-104">Örneğin, bir menü komutuna sahip olacak bir menü komutunun aynı işlevi, aynı işlevselliğe sahip olmaları durumunda sizin formunuzdaki bir düğmeyle oluşturması için genellikle güçlü bir zaman tasarrufu vardır.</span><span class="sxs-lookup"><span data-stu-id="f1126-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="f1126-105">Bunu, içindeki C# Özellikler penceresi olaylar görünümünü kullanarak veya `Handles` anahtar sözcüğünü ve Visual Basic kod düzenleyicisinde **sınıf adı** ve **Yöntem adı** açılır kutularını kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1126-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="f1126-106">Birden çok olayı Visual Basic bir tek olay işleyicisine bağlamak için</span><span class="sxs-lookup"><span data-stu-id="f1126-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="f1126-107">Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f1126-107">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="f1126-108">**Sınıf adı** açılan kutusundan, olay işleyicisi tutamacına sahip olmasını istediğiniz denetimlerden birini seçin.</span><span class="sxs-lookup"><span data-stu-id="f1126-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="f1126-109">**Yöntem adı** açılan kutusundan, olay işleyicisinin işlemesini istediğiniz olaylardan birini seçin.</span><span class="sxs-lookup"><span data-stu-id="f1126-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="f1126-110">Kod Düzenleyicisi, uygun olay işleyicisini ekler ve ekleme noktasını yönteminin içine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="f1126-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="f1126-111">Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> denetimi için <xref:System.Windows.Forms.Control.Click> olayıdır.</span><span class="sxs-lookup"><span data-stu-id="f1126-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="f1126-112">İstediğiniz diğer olayları `Handles` yan tümcesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f1126-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="f1126-113">Olay işleyicisine uygun kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f1126-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="f1126-114">Birden çok olayı C\# tek bir olay işleyicisine bağlamak için</span><span class="sxs-lookup"><span data-stu-id="f1126-114">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="f1126-115">Bir olay işleyicisine bağlamak istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="f1126-115">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="f1126-116">Özellikler penceresi, **Olaylar** düğmesine (![Olaylar düğmesi](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f1126-116">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="f1126-117">İşlemek istediğiniz olayın adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f1126-117">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="f1126-118">Olay adının yanındaki değer bölümünde, işlemek istediğiniz olayın yöntem imzasıyla eşleşen mevcut olay işleyicilerinin listesini göstermek için açılan düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f1126-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="f1126-119">Listeden uygun olay işleyicisini seçin.</span><span class="sxs-lookup"><span data-stu-id="f1126-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="f1126-120">Olayı, var olan olay işleyicisine bağlamak için forma eklenecek.</span><span class="sxs-lookup"><span data-stu-id="f1126-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1126-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1126-121">See also</span></span>

- [<span data-ttu-id="f1126-122">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1126-122">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="f1126-123">Olay İşleyicilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f1126-123">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)

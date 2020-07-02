---
title: 'Nasıl yapılır: birden çok olayı tek bir olay Işleyicisine bağlama'
description: C# ' de Özellikler penceresi olay görünümünü kullanarak birden çok olayı Windows Forms ' de tek bir olay işleyicisine bağlamayı öğrenin.
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
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621892"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="54282-103">Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama</span><span class="sxs-lookup"><span data-stu-id="54282-103">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="54282-104">Uygulama tasarımınızda, birden çok olay için tek bir olay işleyicisi kullanmak veya aynı yordamı gerçekleştirmek için birden çok olay olması gerektiğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54282-104">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="54282-105">Örneğin, bir menü komutuna sahip olacak bir menü komutunun aynı işlevi, aynı işlevselliğe sahip olmaları durumunda sizin formunuzdaki bir düğmeyle oluşturması için genellikle güçlü bir zaman tasarrufu vardır.</span><span class="sxs-lookup"><span data-stu-id="54282-105">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="54282-106">Bunu, C# ' deki Özellikler penceresi olaylar görünümünü kullanarak veya `Handles` anahtar sözcüğünü ve Visual Basic kod Düzenleyicisi 'Ndeki **sınıf adı** ve **Yöntem adı** açılır kutularını kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54282-106">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="54282-107">Birden çok olayı Visual Basic bir tek olay işleyicisine bağlamak için</span><span class="sxs-lookup"><span data-stu-id="54282-107">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="54282-108">Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="54282-108">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="54282-109">**Sınıf adı** açılan kutusundan, olay işleyicisi tutamacına sahip olmasını istediğiniz denetimlerden birini seçin.</span><span class="sxs-lookup"><span data-stu-id="54282-109">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="54282-110">**Yöntem adı** açılan kutusundan, olay işleyicisinin işlemesini istediğiniz olaylardan birini seçin.</span><span class="sxs-lookup"><span data-stu-id="54282-110">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="54282-111">Kod Düzenleyicisi, uygun olay işleyicisini ekler ve ekleme noktasını yönteminin içine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="54282-111">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="54282-112">Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.Click> denetimin olayıdır <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="54282-112">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="54282-113">İstediğiniz diğer olayları `Handles` yan tümcesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54282-113">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="54282-114">Olay işleyicisine uygun kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54282-114">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="54282-115">Birden çok olayı C 'de tek bir olay işleyicisine bağlamak için\#</span><span class="sxs-lookup"><span data-stu-id="54282-115">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="54282-116">Bir olay işleyicisine bağlamak istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="54282-116">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="54282-117">Özellikler penceresi, **Olaylar** düğmesine (![Olaylar düğmesi](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="54282-117">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="54282-118">İşlemek istediğiniz olayın adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="54282-118">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="54282-119">Olay adının yanındaki değer bölümünde, işlemek istediğiniz olayın yöntem imzasıyla eşleşen mevcut olay işleyicilerinin listesini göstermek için açılan düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="54282-119">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="54282-120">Listeden uygun olay işleyicisini seçin.</span><span class="sxs-lookup"><span data-stu-id="54282-120">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="54282-121">Olayı, var olan olay işleyicisine bağlamak için forma eklenecek.</span><span class="sxs-lookup"><span data-stu-id="54282-121">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54282-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54282-122">See also</span></span>

- [<span data-ttu-id="54282-123">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54282-123">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="54282-124">Olay İşleyicilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="54282-124">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)

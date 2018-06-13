---
title: "Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama"
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
ms.openlocfilehash: 527a76376a4c1d5ad051f4768ca2bd42c3548b3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538586"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="7d1ec-102">Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama</span><span class="sxs-lookup"><span data-stu-id="7d1ec-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="7d1ec-103">Uygulama tasarımınız, onu tek olay işleyicisine birden çok olaylar için kullanın veya birden çok olayları aynı yordamı gerçekleştirmek için gerekli bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="7d1ec-104">Örneğin, bir güçlü zaman-formunuzda düğmesini aynı işlevselliği kullanıma durumunda olduğu gibi aynı olayını Başlat menü komutu sağlamak için koruyucu genellikle olur.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="7d1ec-105">Olaylar görünüm penceresinin C# veya kullanarak bunu yapabilirsiniz `Handles` anahtar sözcüğü ve **sınıf adı** ve **yöntem adı** açılan kutuları Visual Basic Kod Düzenleyicisi'nde.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="7d1ec-106">Visual Basic'te tek olay işleyicisine birden çok olay bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="7d1ec-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1.  <span data-ttu-id="7d1ec-107">Forma sağ tıklayın ve seçin **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-107">Right-click the form and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="7d1ec-108">Gelen **sınıf adı** açılan kutuyu, olay işleyicisi işlemek istediğiniz denetimleri birini seçin.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3.  <span data-ttu-id="7d1ec-109">Gelen **yöntem adı** açılan kutusu, işlemek için olay işleyicisi istediğiniz olayları birini seçin.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4.  <span data-ttu-id="7d1ec-110">Kod Düzenleyicisi uygun olay işleyicisi ekler ve ekleme noktasını yöntemi içindeki yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="7d1ec-111">Aşağıdaki örnek <xref:System.Windows.Forms.Control.Click> olayı <xref:System.Windows.Forms.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  <span data-ttu-id="7d1ec-112">İçin işlenen gibi diğer olaylar ekleme `Handles` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  <span data-ttu-id="7d1ec-113">Uygun kodu olay işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="7d1ec-114">C# tek olay işleyicisine birden çok olay bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="7d1ec-114">To connect multiple events to a single event handler in C#</span></span>  
  
1.  <span data-ttu-id="7d1ec-115">Olay işleyici bağlanmak istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-115">Select the control to which you want to connect an event handler.</span></span>  
  
2.  <span data-ttu-id="7d1ec-116">Özellikler penceresinde **olayları** düğmesi (![Events düğmesini](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="7d1ec-116">In the Properties window, click the **Events** button (![Events Button](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3.  <span data-ttu-id="7d1ec-117">İşlemek istediğiniz olay adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-117">Click the name of the event that you want to handle.</span></span>  
  
4.  <span data-ttu-id="7d1ec-118">Olay adının yanındaki değeri bölümünde ele almak istediğiniz olay yöntemi imzası eşleşen var olan olay işleyicileri listesini görüntülemek için açılan düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5.  <span data-ttu-id="7d1ec-119">Uygun olay işleyicisi listeden seçin.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="7d1ec-120">Kod mevcut olay işleyicisi olaya bağlamak için form eklenir.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1ec-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d1ec-121">See Also</span></span>  
 [<span data-ttu-id="7d1ec-122">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d1ec-122">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="7d1ec-123">Olay İşleyicilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7d1ec-123">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)

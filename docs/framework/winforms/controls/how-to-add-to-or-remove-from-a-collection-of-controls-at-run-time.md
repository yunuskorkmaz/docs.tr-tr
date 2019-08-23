---
title: 'Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 87ad4c957ac5b99438684d398a0c5ad7d126c406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925039"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="1d63f-102">Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="1d63f-102">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="1d63f-103">Uygulama geliştirmede ortak görevler, formlarınızda ( <xref:System.Windows.Forms.Panel> veya <xref:System.Windows.Forms.GroupBox> denetimi gibi) herhangi bir kapsayıcı denetimine denetim ekleme ve denetimleri kaldırma (hatta formun kendisi gibi).</span><span class="sxs-lookup"><span data-stu-id="1d63f-103">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="1d63f-104">Tasarım zamanında, denetimler doğrudan bir panel veya grup kutusu üzerinde sürüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1d63f-104">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="1d63f-105">Çalışma zamanında, bu denetimler, bunlara hangi `Controls` denetimlerin yerleştirileceğini izleyen bir koleksiyonu korur.</span><span class="sxs-lookup"><span data-stu-id="1d63f-105">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d63f-106">Aşağıdaki kod örneği, içindeki bir denetim koleksiyonunu tutan tüm denetimler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1d63f-106">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="1d63f-107">Bir koleksiyona programlı bir denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="1d63f-107">To add a control to a collection programmatically</span></span>  
  
1. <span data-ttu-id="1d63f-108">Eklenecek denetimin bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1d63f-108">Create an instance of the control to be added.</span></span>  
  
2. <span data-ttu-id="1d63f-109">Yeni denetimin özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d63f-109">Set properties of the new control.</span></span>  
  
3. <span data-ttu-id="1d63f-110">Denetimi üst denetimin `Controls` koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1d63f-110">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="1d63f-111">Aşağıdaki kod örneği, <xref:System.Windows.Forms.Button> denetimin bir örneğinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d63f-111">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="1d63f-112"><xref:System.Windows.Forms.Panel> Denetim içeren bir form ve `NewPanelButton_Click`oluşturulmakta olan düğme için olay işleme yönteminin zaten var olduğunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d63f-112">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code   
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {   
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code   
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="1d63f-113">Bir koleksiyondan denetimleri programlı bir şekilde kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="1d63f-113">To remove controls from a collection programmatically</span></span>  
  
1. <span data-ttu-id="1d63f-114">Olay işleyicisini olaydan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1d63f-114">Remove the event handler from the event.</span></span> <span data-ttu-id="1d63f-115">Visual Basic ' de [RemoveHandler deyimin](../../../visual-basic/language-reference/statements/removehandler-statement.md) anahtar sözcüğünü kullanın; içinde C# [-= işlecini](../../../csharp/language-reference/operators/subtraction-operator.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d63f-115">In Visual Basic, use the [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) keyword; in C#, use the [-= operator](../../../csharp/language-reference/operators/subtraction-operator.md).</span></span>  
  
2. <span data-ttu-id="1d63f-116">İstenen denetimi`Controls` panel koleksiyonundan silmek için yöntemini kullanın. `Remove`</span><span class="sxs-lookup"><span data-stu-id="1d63f-116">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3. <span data-ttu-id="1d63f-117">Denetim tarafından kullanılan tüm kaynakları serbest bırakmak için yönteminiçağırın.<xref:System.Windows.Forms.Control.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="1d63f-117">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of   
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _   
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of   
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.   
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1d63f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d63f-118">See also</span></span>

- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="1d63f-119">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="1d63f-119">Panel Control</span></span>](panel-control-windows-forms.md)

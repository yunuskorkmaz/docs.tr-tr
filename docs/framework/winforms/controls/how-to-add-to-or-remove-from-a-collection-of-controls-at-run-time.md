---
title: 'Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma'
description: Formunuz üzerinde, panel veya GroupBox denetimi gibi herhangi bir kapsayıcı denetimine denetim eklemeyi ve denetimleri kaldırmayı öğrenin.
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
ms.openlocfilehash: 6c3f2d1f42b130de4d808871265b50510cfb8f47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325852"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="ca056-103">Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="ca056-103">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="ca056-104">Uygulama geliştirmede ortak görevler, formlarınızda (veya denetimi gibi) herhangi bir kapsayıcı denetimine denetim ekleme ve denetimleri kaldırma ( <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.GroupBox> hatta formun kendisi gibi).</span><span class="sxs-lookup"><span data-stu-id="ca056-104">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="ca056-105">Tasarım zamanında, denetimler doğrudan bir panel veya grup kutusu üzerinde sürüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ca056-105">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="ca056-106">Çalışma zamanında, bu denetimler `Controls` , bunlara hangi denetimlerin yerleştirileceğini izleyen bir koleksiyonu korur.</span><span class="sxs-lookup"><span data-stu-id="ca056-106">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca056-107">Aşağıdaki kod örneği, içindeki bir denetim koleksiyonunu tutan tüm denetimler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ca056-107">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="ca056-108">Bir koleksiyona programlı bir denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="ca056-108">To add a control to a collection programmatically</span></span>  
  
1. <span data-ttu-id="ca056-109">Eklenecek denetimin bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ca056-109">Create an instance of the control to be added.</span></span>  
  
2. <span data-ttu-id="ca056-110">Yeni denetimin özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ca056-110">Set properties of the new control.</span></span>  
  
3. <span data-ttu-id="ca056-111">Denetimi `Controls` üst denetimin koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ca056-111">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="ca056-112">Aşağıdaki kod örneği, denetimin bir örneğinin nasıl oluşturulacağını gösterir <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="ca056-112">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="ca056-113">Denetim içeren bir form <xref:System.Windows.Forms.Panel> ve oluşturulmakta olan düğme için olay işleme yönteminin `NewPanelButton_Click` zaten var olduğunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ca056-113">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="ca056-114">Bir koleksiyondan denetimleri programlı bir şekilde kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="ca056-114">To remove controls from a collection programmatically</span></span>  
  
1. <span data-ttu-id="ca056-115">Olay işleyicisini olaydan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ca056-115">Remove the event handler from the event.</span></span> <span data-ttu-id="ca056-116">Visual Basic ' de [RemoveHandler deyimin](../../../visual-basic/language-reference/statements/removehandler-statement.md) anahtar sözcüğünü kullanın; C# ' de [-= işlecini](../../../csharp/language-reference/operators/subtraction-operator.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca056-116">In Visual Basic, use the [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) keyword; in C#, use the [-= operator](../../../csharp/language-reference/operators/subtraction-operator.md).</span></span>  
  
2. <span data-ttu-id="ca056-117">`Remove`İstenen denetimi Panel koleksiyonundan silmek için yöntemini kullanın `Controls` .</span><span class="sxs-lookup"><span data-stu-id="ca056-117">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3. <span data-ttu-id="ca056-118"><xref:System.Windows.Forms.Control.Dispose%2A>Denetim tarafından kullanılan tüm kaynakları serbest bırakmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ca056-118">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca056-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca056-119">See also</span></span>

- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="ca056-120">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="ca056-120">Panel Control</span></span>](panel-control-windows-forms.md)

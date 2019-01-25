---
title: 'Nasıl yapılır: Ekleme veya çalışma zamanında denetimlerin bir koleksiyondan Kaldır'
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
ms.openlocfilehash: 88a743cc6d0a1e90d2912c9ec610fae326ff5770
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744914"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="2a7b1-102">Nasıl yapılır: Ekleme veya çalışma zamanında denetimlerin bir koleksiyondan Kaldır</span><span class="sxs-lookup"><span data-stu-id="2a7b1-102">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="2a7b1-103">Uygulama geliştirme için ortak görevler için denetimler ekleme ve herhangi bir kapsayıcı denetimi, form üzerinde denetimleri kaldırma (gibi <xref:System.Windows.Forms.Panel> veya <xref:System.Windows.Forms.GroupBox> denetim veya formun kendisi bile).</span><span class="sxs-lookup"><span data-stu-id="2a7b1-103">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="2a7b1-104">Tasarım zamanında denetimler doğrudan Masası veya grup kutusu sürüklenebilen.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-104">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="2a7b1-105">Çalışma zamanında bu denetimi yöneten bir `Controls` koleksiyonunun hangi denetimlerin üzerine yerleştirilen izler.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-105">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a7b1-106">Aşağıdaki kod örneği, bir denetim koleksiyonunu tutar herhangi bir denetimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-106">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="2a7b1-107">Bir denetimin program aracılığıyla bir koleksiyona eklemek için</span><span class="sxs-lookup"><span data-stu-id="2a7b1-107">To add a control to a collection programmatically</span></span>  
  
1.  <span data-ttu-id="2a7b1-108">Eklenecek denetimin örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-108">Create an instance of the control to be added.</span></span>  
  
2.  <span data-ttu-id="2a7b1-109">Yeni denetimin özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-109">Set properties of the new control.</span></span>  
  
3.  <span data-ttu-id="2a7b1-110">Denetime eklemek `Controls` üst denetim koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-110">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="2a7b1-111">Aşağıdaki kod örneği, bir örneğini oluşturma işlemi gösterilmektedir <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-111">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="2a7b1-112">Bir formla gerektiren bir <xref:System.Windows.Forms.Panel> denetimi düğmesi için olay işleme yöntemi oluşturulmakta, `NewPanelButton_Click`, zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-112">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="2a7b1-113">Denetimleri bir koleksiyondan programlı bir şekilde kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="2a7b1-113">To remove controls from a collection programmatically</span></span>  
  
1.  <span data-ttu-id="2a7b1-114">Olay işleyici olaydan kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-114">Remove the event handler from the event.</span></span> <span data-ttu-id="2a7b1-115">Visual Basic'teki [RemoveHandler deyimi](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) anahtar sözcüğü; görselde C#, kullanın [-= işleci (C# başvuru)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2a7b1-115">In Visual Basic, use the [RemoveHandler Statement](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) keyword; in Visual C#, use the [-= Operator (C# Reference)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).</span></span>  
  
2.  <span data-ttu-id="2a7b1-116">Kullanım `Remove` istediğiniz denetimi panelinden 's silinemedi yöntemi `Controls` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-116">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3.  <span data-ttu-id="2a7b1-117">Çağrı <xref:System.Windows.Forms.Control.Dispose%2A> denetim tarafından kullanılan tüm kaynakları serbest bırakmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-117">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a7b1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a7b1-118">See also</span></span>
- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="2a7b1-119">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="2a7b1-119">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)

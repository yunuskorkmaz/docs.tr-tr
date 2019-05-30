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
ms.openlocfilehash: a868632d6868e6a82c4fa135444279b8ef4dc7af
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301407"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="774f2-102">Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="774f2-102">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="774f2-103">Uygulama geliştirme için ortak görevler için denetimler ekleme ve herhangi bir kapsayıcı denetimi, form üzerinde denetimleri kaldırma (gibi <xref:System.Windows.Forms.Panel> veya <xref:System.Windows.Forms.GroupBox> denetim veya formun kendisi bile).</span><span class="sxs-lookup"><span data-stu-id="774f2-103">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="774f2-104">Tasarım zamanında denetimler doğrudan Masası veya grup kutusu sürüklenebilen.</span><span class="sxs-lookup"><span data-stu-id="774f2-104">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="774f2-105">Çalışma zamanında bu denetimi yöneten bir `Controls` koleksiyonunun hangi denetimlerin üzerine yerleştirilen izler.</span><span class="sxs-lookup"><span data-stu-id="774f2-105">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="774f2-106">Aşağıdaki kod örneği, bir denetim koleksiyonunu tutar herhangi bir denetimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="774f2-106">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="774f2-107">Bir denetimin program aracılığıyla bir koleksiyona eklemek için</span><span class="sxs-lookup"><span data-stu-id="774f2-107">To add a control to a collection programmatically</span></span>  
  
1. <span data-ttu-id="774f2-108">Eklenecek denetimin örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="774f2-108">Create an instance of the control to be added.</span></span>  
  
2. <span data-ttu-id="774f2-109">Yeni denetimin özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="774f2-109">Set properties of the new control.</span></span>  
  
3. <span data-ttu-id="774f2-110">Denetime eklemek `Controls` üst denetim koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="774f2-110">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="774f2-111">Aşağıdaki kod örneği, bir örneğini oluşturma işlemi gösterilmektedir <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="774f2-111">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="774f2-112">Bir formla gerektiren bir <xref:System.Windows.Forms.Panel> denetimi düğmesi için olay işleme yöntemi oluşturulmakta, `NewPanelButton_Click`, zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="774f2-112">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="774f2-113">Denetimleri bir koleksiyondan programlı bir şekilde kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="774f2-113">To remove controls from a collection programmatically</span></span>  
  
1. <span data-ttu-id="774f2-114">Olay işleyici olaydan kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="774f2-114">Remove the event handler from the event.</span></span> <span data-ttu-id="774f2-115">Visual Basic'teki [RemoveHandler deyimi](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) anahtar sözcüğü; C#, kullanın [-= işleci](~/docs/csharp/language-reference/operators/subtraction-operator.md).</span><span class="sxs-lookup"><span data-stu-id="774f2-115">In Visual Basic, use the [RemoveHandler Statement](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) keyword; in C#, use the [-= operator](~/docs/csharp/language-reference/operators/subtraction-operator.md).</span></span>  
  
2. <span data-ttu-id="774f2-116">Kullanım `Remove` istediğiniz denetimi panelinden 's silinemedi yöntemi `Controls` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="774f2-116">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3. <span data-ttu-id="774f2-117">Çağrı <xref:System.Windows.Forms.Control.Dispose%2A> denetim tarafından kullanılan tüm kaynakları serbest bırakmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="774f2-117">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="774f2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="774f2-118">See also</span></span>

- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="774f2-119">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="774f2-119">Panel Control</span></span>](panel-control-windows-forms.md)

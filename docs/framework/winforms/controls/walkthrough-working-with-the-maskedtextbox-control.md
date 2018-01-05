---
title: "İzlenecek Yol: MaskedTextBox Denetimiyle Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 006dafe88c5db7cb1499d7c1902d295841bfb5ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="30bab-102">İzlenecek Yol: MaskedTextBox Denetimiyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="30bab-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="30bab-103">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="30bab-103">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="30bab-104">Başlatma <xref:System.Windows.Forms.MaskedTextBox> denetimi</span><span class="sxs-lookup"><span data-stu-id="30bab-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
-   <span data-ttu-id="30bab-105">Kullanarak <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> bir karakter maskeye uymuyor olduğunda kullanıcıyı uyarmak için olay işleyicisi</span><span class="sxs-lookup"><span data-stu-id="30bab-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
-   <span data-ttu-id="30bab-106">Bir türe atama <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği ve kullanarak <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> bunlar çalışırken yürütmek için değer türü için geçerli değilse, kullanıcıyı uyarmak için olay işleyicisi</span><span class="sxs-lookup"><span data-stu-id="30bab-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="30bab-107">Proje oluşturma ve denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="30bab-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="30bab-108">MaskedTextBox denetimi formunuza eklemek için</span><span class="sxs-lookup"><span data-stu-id="30bab-108">To add a MaskedTextBox control to your form</span></span>  
  
1.  <span data-ttu-id="30bab-109">Yerleştirmek istediğiniz formu açın <xref:System.Windows.Forms.MaskedTextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="30bab-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2.  <span data-ttu-id="30bab-110">Sürükleme bir <xref:System.Windows.Forms.MaskedTextBox> gelen denetim **araç** formunuza.</span><span class="sxs-lookup"><span data-stu-id="30bab-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3.  <span data-ttu-id="30bab-111">Denetimin sağ tıklatın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="30bab-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="30bab-112">İçinde **özellikleri** penceresinde, seçin **maskesi** özelliği ve tıklatın **...**  özellik adının yanındaki (üç nokta) düğmesi.</span><span class="sxs-lookup"><span data-stu-id="30bab-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4.  <span data-ttu-id="30bab-113">İçinde **giriş maskesi** iletişim kutusunda **kısa tarih** maske ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="30bab-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5.  <span data-ttu-id="30bab-114">İçinde **özellikleri** penceresi kümesi <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="30bab-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="30bab-115">Bu özellik, kullanıcı giriş maskesi tanımını ihlal ediyor bir karakter girişiminde her zaman ses kısa bip sesi neden olur.</span><span class="sxs-lookup"><span data-stu-id="30bab-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="30bab-116">Maske özelliğini destekleyen karakterden oluşan bir özeti Açıklamalar bölümüne bakın <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="30bab-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="30bab-117">Hataları giriş kullanıcıya uyar</span><span class="sxs-lookup"><span data-stu-id="30bab-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="30bab-118">Balon ipucu reddedilen maskesi giriş Ekle</span><span class="sxs-lookup"><span data-stu-id="30bab-118">Add a balloon tip for rejected mask input</span></span>  
  
1.  <span data-ttu-id="30bab-119">Geri dönüp **araç** ve ekleme bir <xref:System.Windows.Forms.ToolTip> formunuza.</span><span class="sxs-lookup"><span data-stu-id="30bab-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2.  <span data-ttu-id="30bab-120">İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> başlatır olay <xref:System.Windows.Forms.ToolTip> Giriş bir hata oluştuğunda.</span><span class="sxs-lookup"><span data-stu-id="30bab-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="30bab-121">Balon ipucu beş saniyede veya kullanıcı bağlantıya tıkladığında kadar görünür kalır.</span><span class="sxs-lookup"><span data-stu-id="30bab-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="30bab-122">Kullanıcı geçersiz bir tür için uyar</span><span class="sxs-lookup"><span data-stu-id="30bab-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="30bab-123">Geçersiz veri türleri için balon ipucu ekleyin</span><span class="sxs-lookup"><span data-stu-id="30bab-123">Add a balloon tip for invalid data types</span></span>  
  
1.  <span data-ttu-id="30bab-124">Formun içinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi atamak bir <xref:System.Type> nesnesini temsil eden <xref:System.DateTime> için yazın <xref:System.Windows.Forms.MaskedTextBox> denetimin <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği:</span><span class="sxs-lookup"><span data-stu-id="30bab-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  <span data-ttu-id="30bab-125">Bir olay işleyicisi ekleme <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> olay:</span><span class="sxs-lookup"><span data-stu-id="30bab-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="30bab-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30bab-126">See Also</span></span>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [<span data-ttu-id="30bab-127">MaskedTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="30bab-127">MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)

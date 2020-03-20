---
title: 'İzlenecek Yol: MaskedTextBox Denetimiyle Çalışma'
ms.date: 03/30/2017
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
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182067"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="fe869-102">İzlenecek Yol: MaskedTextBox Denetimiyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="fe869-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="fe869-103">Bu gözden geçirmede gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fe869-103">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="fe869-104"><xref:System.Windows.Forms.MaskedTextBox> Denetimi başlatma</span><span class="sxs-lookup"><span data-stu-id="fe869-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
- <span data-ttu-id="fe869-105">Bir <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> karakter maskeye uymadığında kullanıcıyı uyarmak için olay işleyicisini kullanma</span><span class="sxs-lookup"><span data-stu-id="fe869-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
- <span data-ttu-id="fe869-106"><xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> Bir tür özelliği atama ve <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> işlemeye çalıştıkları değer türü için geçerli olmadığında kullanıcıyı uyarmak için olay işleyicisini kullanma</span><span class="sxs-lookup"><span data-stu-id="fe869-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="fe869-107">Proje Oluşturma ve Denetim Ekleme</span><span class="sxs-lookup"><span data-stu-id="fe869-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="fe869-108">Formunuza MaskeliTextBox denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="fe869-108">To add a MaskedTextBox control to your form</span></span>  
  
1. <span data-ttu-id="fe869-109"><xref:System.Windows.Forms.MaskedTextBox> Denetimi yerleştirmek istediğiniz formu açın.</span><span class="sxs-lookup"><span data-stu-id="fe869-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2. <span data-ttu-id="fe869-110">Denetimi <xref:System.Windows.Forms.MaskedTextBox> Araç **Kutusu'ndan** formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="fe869-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3. <span data-ttu-id="fe869-111">Denetimi sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="fe869-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="fe869-112">**Özellikler** penceresinde Maske **özelliğini** seçin ve özellik adının yanındaki **...** (elips) düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="fe869-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4. <span data-ttu-id="fe869-113">Giriş **Maskesi** iletişim kutusunda, Kısa **Tarih** maskesini seçin ve **Tamam'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="fe869-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5. <span data-ttu-id="fe869-114">**Özellikler** penceresinde <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> özelliği `true`' ye göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fe869-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="fe869-115">Bu özellik, kullanıcı maske tanımını ihlal eden bir karakter girişi yapmaya çalıştığında kısa bir bip sesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="fe869-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="fe869-116">Maske özelliğinin desteklediği karakterlerin özeti için özelliğin Açıklamalar bölümüne <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> bakın.</span><span class="sxs-lookup"><span data-stu-id="fe869-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="fe869-117">Kullanıcıyı Giriş Hataları Konusunda Uyar</span><span class="sxs-lookup"><span data-stu-id="fe869-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="fe869-118">Reddedilen maske girişi için balon ucu ekleme</span><span class="sxs-lookup"><span data-stu-id="fe869-118">Add a balloon tip for rejected mask input</span></span>  
  
1. <span data-ttu-id="fe869-119">**Araç Kutusuna** dönün ve <xref:System.Windows.Forms.ToolTip> formunuza bir ekleme.</span><span class="sxs-lookup"><span data-stu-id="fe869-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2. <span data-ttu-id="fe869-120">Bir giriş hatası <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> <xref:System.Windows.Forms.ToolTip> oluştuğunda yükselten olay için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fe869-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="fe869-121">Balon ucu beş saniye veya kullanıcı onu tıklayana kadar görünür kalır.</span><span class="sxs-lookup"><span data-stu-id="fe869-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="fe869-122">Kullanıcıyı Geçerli Olmayan Bir Tür e karşı uyar</span><span class="sxs-lookup"><span data-stu-id="fe869-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="fe869-123">Geçersiz veri türleri için balon ucu ekleme</span><span class="sxs-lookup"><span data-stu-id="fe869-123">Add a balloon tip for invalid data types</span></span>  
  
1. <span data-ttu-id="fe869-124">Formunuzun olay <xref:System.Windows.Forms.Form.Load> <xref:System.Type> işleyicisinde, denetimin <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliğine <xref:System.DateTime> <xref:System.Windows.Forms.MaskedTextBox> türü temsil eden bir nesne atayın:</span><span class="sxs-lookup"><span data-stu-id="fe869-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
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
  
2. <span data-ttu-id="fe869-125">Olay için bir olay <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> işleyicisi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fe869-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe869-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe869-126">See also</span></span>

- <xref:System.Windows.Forms.MaskedTextBox>
- [<span data-ttu-id="fe869-127">MaskedTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="fe869-127">MaskedTextBox Control</span></span>](maskedtextbox-control-windows-forms.md)

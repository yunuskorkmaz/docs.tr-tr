---
title: 'Nasıl yapılır: Windows Forms’a Denetimler Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 04597283a8ff2e21a0f227268671d3605eac6356
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343596"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="0d576-102">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="0d576-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="0d576-103">Çoğu forms formunun yüzeyine denetimler ekleyerek, bir kullanıcı arabirimi (UI) tanımlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0d576-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="0d576-104">A *denetimi* bilgilerini görüntülemek veya kullanıcı girişi kabul etmek için kullanılan bir form üzerinde bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="0d576-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="0d576-105">Denetimleri hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="0d576-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d576-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0d576-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0d576-107">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="0d576-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0d576-108">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0d576-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="0d576-109">Formda bir denetim çizmek için</span><span class="sxs-lookup"><span data-stu-id="0d576-109">To draw a control on a form</span></span>  
  
1. <span data-ttu-id="0d576-110">Formu açın.</span><span class="sxs-lookup"><span data-stu-id="0d576-110">Open the form.</span></span> <span data-ttu-id="0d576-111">Daha fazla bilgi için [nasıl yapılır: Tasarımcıda Windows formlarını görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0d576-111">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="0d576-112">İçinde **araç kutusu**, formunuza eklemek istediğiniz denetim tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0d576-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3. <span data-ttu-id="0d576-113">Formunda bulunmasını denetimin sol üst köşesinde istediğiniz tıklayın ve konum için denetimin sağ alt köşedeki istediğiniz yere sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="0d576-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="0d576-114">Denetimin form belirtilen konumu ve boyutu ile eklenir.</span><span class="sxs-lookup"><span data-stu-id="0d576-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d576-115">Her denetim tanımlanan varsayılan boyutuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0d576-115">Each control has a default size defined.</span></span> <span data-ttu-id="0d576-116">Buradan sürükleyerek formunuza denetimin varsayılan boyutunda denetim ekleyebilirsiniz **araç kutusu** form.</span><span class="sxs-lookup"><span data-stu-id="0d576-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="0d576-117">Bir forma bir denetimi sürükleyin</span><span class="sxs-lookup"><span data-stu-id="0d576-117">To drag a control to a form</span></span>  
  
1. <span data-ttu-id="0d576-118">Formu açın.</span><span class="sxs-lookup"><span data-stu-id="0d576-118">Open the form.</span></span> <span data-ttu-id="0d576-119">Daha fazla bilgi için [nasıl yapılır: Tasarımcıda Windows formlarını görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0d576-119">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="0d576-120">İçinde **araç kutusu**, formunuza sürükleyin ve istediğiniz denetim tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0d576-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="0d576-121">Denetimin varsayılan boyutunda belirtilen konumda forma eklenir.</span><span class="sxs-lookup"><span data-stu-id="0d576-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d576-122">Bir denetimde çift tıkladığınızda **araç kutusu** varsayılan boyutunda biçiminde sol üst köşesinde eklemek için.</span><span class="sxs-lookup"><span data-stu-id="0d576-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="0d576-123">Ayrıca denetimlerini dinamik olarak bir forma çalışma zamanında ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d576-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="0d576-124">Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.TextBox> denetimi forma eklenecektir olduğunda bir <xref:System.Windows.Forms.Button> denetim tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="0d576-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d576-125">Aşağıdaki yordam bir formla gerekir bir **düğmesi** denetimi `Button1`, üzerindeki zaten yapıldı.</span><span class="sxs-lookup"><span data-stu-id="0d576-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="0d576-126">Bir denetimin program aracılığıyla bir forma eklemek için</span><span class="sxs-lookup"><span data-stu-id="0d576-126">To add a control to a form programmatically</span></span>  
  
1. <span data-ttu-id="0d576-127">Düğmenin işleyen yöntem içinde `Click` formunuzun sınıftaki kod ekleme, denetim değişkeni bir başvuru eklemek için aşağıdakine benzer bir olay kümesi denetimin `Location`ve denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0d576-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0d576-128">Ayrıca, denetimin diğer özelliklerini başlatmak için kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d576-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0d576-129">Yerel bir güvenlik riski ağ üzerinden bilgisayarınıza bir kötü amaçlı başvurarak sunabileceğinize `UserControl`.</span><span class="sxs-lookup"><span data-stu-id="0d576-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="0d576-130">Bu, yalnızca, yanlışlıkla bunu projenize ekleyerek ardından zararlı olabilecek özel bir denetim oluşturulamaz kötü amaçlı bir kişinin söz konusu olduğunda önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="0d576-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d576-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d576-131">See also</span></span>

- [<span data-ttu-id="0d576-132">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="0d576-132">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="0d576-133">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="0d576-133">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="0d576-134">Nasıl yapılır: Windows Forms'da denetimleri yeniden boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="0d576-134">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="0d576-135">Nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="0d576-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="0d576-136">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="0d576-136">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)

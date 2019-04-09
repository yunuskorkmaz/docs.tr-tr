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
ms.openlocfilehash: 72b5931a79284a93a4e0fdf3cb2cc3b03157f5f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106489"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="a8279-102">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="a8279-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="a8279-103">Çoğu forms formunun yüzeyine denetimler ekleyerek, bir kullanıcı arabirimi (UI) tanımlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8279-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="a8279-104">A *denetimi* bilgilerini görüntülemek veya kullanıcı girişi kabul etmek için kullanılan bir form üzerinde bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="a8279-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="a8279-105">Denetimleri hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="a8279-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8279-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="a8279-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a8279-107">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a8279-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a8279-108">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="a8279-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="a8279-109">Formda bir denetim çizmek için</span><span class="sxs-lookup"><span data-stu-id="a8279-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="a8279-110">Formu açın.</span><span class="sxs-lookup"><span data-stu-id="a8279-110">Open the form.</span></span> <span data-ttu-id="a8279-111">Daha fazla bilgi için [nasıl yapılır: Tasarımcıda Windows formlarını görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a8279-111">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="a8279-112">İçinde **araç kutusu**, formunuza eklemek istediğiniz denetim tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a8279-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="a8279-113">Formunda bulunmasını denetimin sol üst köşesinde istediğiniz tıklayın ve konum için denetimin sağ alt köşedeki istediğiniz yere sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="a8279-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="a8279-114">Denetimin form belirtilen konumu ve boyutu ile eklenir.</span><span class="sxs-lookup"><span data-stu-id="a8279-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8279-115">Her denetim tanımlanan varsayılan boyutuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a8279-115">Each control has a default size defined.</span></span> <span data-ttu-id="a8279-116">Buradan sürükleyerek formunuza denetimin varsayılan boyutunda denetim ekleyebilirsiniz **araç kutusu** form.</span><span class="sxs-lookup"><span data-stu-id="a8279-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="a8279-117">Bir forma bir denetimi sürükleyin</span><span class="sxs-lookup"><span data-stu-id="a8279-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="a8279-118">Formu açın.</span><span class="sxs-lookup"><span data-stu-id="a8279-118">Open the form.</span></span> <span data-ttu-id="a8279-119">Daha fazla bilgi için [nasıl yapılır: Tasarımcıda Windows formlarını görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a8279-119">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="a8279-120">İçinde **araç kutusu**, formunuza sürükleyin ve istediğiniz denetim tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a8279-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="a8279-121">Denetimin varsayılan boyutunda belirtilen konumda forma eklenir.</span><span class="sxs-lookup"><span data-stu-id="a8279-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8279-122">Bir denetimde çift tıkladığınızda **araç kutusu** varsayılan boyutunda biçiminde sol üst köşesinde eklemek için.</span><span class="sxs-lookup"><span data-stu-id="a8279-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="a8279-123">Ayrıca denetimlerini dinamik olarak bir forma çalışma zamanında ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8279-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="a8279-124">Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.TextBox> denetimi forma eklenecektir olduğunda bir <xref:System.Windows.Forms.Button> denetim tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="a8279-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8279-125">Aşağıdaki yordam bir formla gerekir bir **düğmesi** denetimi `Button1`, üzerindeki zaten yapıldı.</span><span class="sxs-lookup"><span data-stu-id="a8279-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="a8279-126">Bir denetimin program aracılığıyla bir forma eklemek için</span><span class="sxs-lookup"><span data-stu-id="a8279-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="a8279-127">Düğmenin işleyen yöntem içinde `Click` formunuzun sınıftaki kod ekleme, denetim değişkeni bir başvuru eklemek için aşağıdakine benzer bir olay kümesi denetimin `Location`ve denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a8279-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
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
    >  <span data-ttu-id="a8279-128">Ayrıca, denetimin diğer özelliklerini başlatmak için kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8279-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a8279-129">Yerel bir güvenlik riski ağ üzerinden bilgisayarınıza bir kötü amaçlı başvurarak sunabileceğinize `UserControl`.</span><span class="sxs-lookup"><span data-stu-id="a8279-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="a8279-130">Bu, yalnızca, yanlışlıkla bunu projenize ekleyerek ardından zararlı olabilecek özel bir denetim oluşturulamaz kötü amaçlı bir kişinin söz konusu olduğunda önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="a8279-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8279-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8279-131">See also</span></span>

- [<span data-ttu-id="a8279-132">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="a8279-132">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="a8279-133">Windows Formlarında Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a8279-133">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="a8279-134">Nasıl yapılır: Windows Forms’da Denetimleri Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="a8279-134">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="a8279-135">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a8279-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="a8279-136">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="a8279-136">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)

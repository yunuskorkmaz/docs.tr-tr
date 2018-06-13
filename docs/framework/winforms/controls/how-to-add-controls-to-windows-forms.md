---
title: 'Nasıl yapılır: Windows Formlarına Denetimler Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 2dd048fb074d1ec5bb7bc0a67f196d5d51281545
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528483"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="93285-102">Nasıl yapılır: Windows Formlarına Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="93285-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="93285-103">Çoğu form formun yüzeye denetimler ekleyerek, bir kullanıcı arabirimi (UI) tanımlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="93285-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="93285-104">A *denetim* bilgilerini görüntülemek veya kullanıcı girişi kabul etmek için kullanılan bir form üzerinde bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="93285-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="93285-105">Denetimleri hakkında daha fazla bilgi için bkz: [Windows Forms denetimleri](../../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="93285-105">For more information about controls, see [Windows Forms Controls](../../../../docs/framework/winforms/controls/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93285-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="93285-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="93285-107">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="93285-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="93285-108">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="93285-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="93285-109">Bir form üzerinde denetim çizmek için</span><span class="sxs-lookup"><span data-stu-id="93285-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="93285-110">Formu açın.</span><span class="sxs-lookup"><span data-stu-id="93285-110">Open the form.</span></span> <span data-ttu-id="93285-111">Daha fazla bilgi için bkz: [nasıl yapılır: görüntü Windows Forms Tasarımcısı'nda](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="93285-111">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="93285-112">İçinde **araç**, formunuza eklemek istediğiniz denetimi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="93285-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="93285-113">Form yerleştirilecek denetimin sol üst köşesinde istediğiniz yeri tıklatın ve bulunması için denetimin sağ alt köşedeki istediğiniz yere sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="93285-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="93285-114">Denetim belirtilen konum ve boyutlarının formla eklenir.</span><span class="sxs-lookup"><span data-stu-id="93285-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93285-115">Her denetim tanımlanan varsayılan boyutuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="93285-115">Each control has a default size defined.</span></span> <span data-ttu-id="93285-116">Bir denetim denetimin varsayılan boyutu formunuzda ondan sürükleyerek ekleyebileceğiniz **araç** form.</span><span class="sxs-lookup"><span data-stu-id="93285-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="93285-117">Forma denetim sürükleyin</span><span class="sxs-lookup"><span data-stu-id="93285-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="93285-118">Formu açın.</span><span class="sxs-lookup"><span data-stu-id="93285-118">Open the form.</span></span> <span data-ttu-id="93285-119">Daha fazla bilgi için bkz: [nasıl yapılır: görüntü Windows Forms Tasarımcısı'nda](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="93285-119">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="93285-120">İçinde **araç**, istediğiniz ve formunuza sürükleyin denetimi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="93285-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="93285-121">Denetim formun varsayılan boyutuna belirtilen konumda eklenir.</span><span class="sxs-lookup"><span data-stu-id="93285-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93285-122">Denetim içinde çift tıklayarak **araç** varsayılan boyutuna formunda sol üst köşesindeki eklemek için.</span><span class="sxs-lookup"><span data-stu-id="93285-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="93285-123">Ayrıca denetimleri dinamik olarak forma çalışma zamanında ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93285-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="93285-124">Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.TextBox> denetim forma eklenecek olduğunda bir <xref:System.Windows.Forms.Button> denetim tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="93285-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93285-125">Aşağıdaki yordam bir formla gerekir. bir **düğmesini** denetimi `Button1`, üzerindeki zaten yerleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="93285-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="93285-126">Program aracılığıyla bir forma denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="93285-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="93285-127">Düğmenin işleme yöntemi `Click` , formun sınıftaki ekleme kodu, denetim değişkeni bir başvuru eklemek için aşağıdakine benzer olay ayarlamak denetimin `Location`ve denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="93285-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
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
    >  <span data-ttu-id="93285-128">Diğer denetim özelliklerini başlatmak için kod de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93285-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="93285-129">Yerel bir güvenlik riski ağ üzerinden bilgisayarınıza bir kötü amaçlı başvurarak doğurabilir `UserControl`.</span><span class="sxs-lookup"><span data-stu-id="93285-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="93285-130">Bu, yalnızca, yanlışlıkla projenize ekleme ve ardından zararlı olabilecek özel bir denetim oluşturma kötü niyetli bir kişi olması durumunda ilgili bir sorun olabilir.</span><span class="sxs-lookup"><span data-stu-id="93285-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93285-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93285-131">See Also</span></span>  
 [<span data-ttu-id="93285-132">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="93285-132">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="93285-133">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="93285-133">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="93285-134">Nasıl yapılır: Windows Forms’da Denetimleri Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="93285-134">How to: Resize Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [<span data-ttu-id="93285-135">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="93285-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="93285-136">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="93285-136">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)

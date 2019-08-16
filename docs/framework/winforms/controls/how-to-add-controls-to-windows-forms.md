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
ms.openlocfilehash: 5c57d86b2f08733dc4a729bf6091eab23c6035f2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039704"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="e67d8-102">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="e67d8-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="e67d8-103">Çoğu form, bir kullanıcı arabirimi (UI) tanımlamak için formun yüzeyine denetimler eklenerek tasarlanır.</span><span class="sxs-lookup"><span data-stu-id="e67d8-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="e67d8-104">*Denetim* , bilgileri göstermek veya Kullanıcı girişini kabul etmek için kullanılan bir form bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="e67d8-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="e67d8-105">Denetimler hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="e67d8-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>

## <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="e67d8-106">Form üzerinde bir denetim çizmek için</span><span class="sxs-lookup"><span data-stu-id="e67d8-106">To draw a control on a form</span></span>

1. <span data-ttu-id="e67d8-107">Formunu açın.</span><span class="sxs-lookup"><span data-stu-id="e67d8-107">Open the form.</span></span> <span data-ttu-id="e67d8-108">Daha fazla bilgi için [nasıl yapılır: Tasarımcıda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))Windows Forms görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="e67d8-108">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="e67d8-109">**Araç kutusunda**formunuza eklemek istediğiniz denetime tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e67d8-109">In the **Toolbox**, click the control you want to add to your form.</span></span>

3. <span data-ttu-id="e67d8-110">Form üzerinde, denetimin sol üst köşesinin bulunmasını istediğiniz yere tıklayın ve denetimin sağ alt köşesinin bulunmasını istediğiniz yere sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="e67d8-110">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>

     <span data-ttu-id="e67d8-111">Denetim, belirtilen konum ve boyutla forma eklenir.</span><span class="sxs-lookup"><span data-stu-id="e67d8-111">The control is added to the form with the specified location and size.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e67d8-112">Her denetim için varsayılan bir boyut tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="e67d8-112">Each control has a default size defined.</span></span> <span data-ttu-id="e67d8-113">**Araç kutusundan** forma sürükleyerek, denetimin varsayılan boyutundaki formunuza bir denetim ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e67d8-113">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>

## <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="e67d8-114">Bir denetimi forma sürüklemek için</span><span class="sxs-lookup"><span data-stu-id="e67d8-114">To drag a control to a form</span></span>

1. <span data-ttu-id="e67d8-115">Formunu açın.</span><span class="sxs-lookup"><span data-stu-id="e67d8-115">Open the form.</span></span> <span data-ttu-id="e67d8-116">Daha fazla bilgi için [nasıl yapılır: Tasarımcıda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))Windows Forms görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="e67d8-116">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="e67d8-117">**Araç kutusunda**istediğiniz denetime tıklayın ve formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="e67d8-117">In the **Toolbox**, click the control you want and drag it to your form.</span></span>

     <span data-ttu-id="e67d8-118">Denetim, varsayılan boyutunda belirtilen konumda bulunan forma eklenir.</span><span class="sxs-lookup"><span data-stu-id="e67d8-118">The control is added to the form at the specified location in its default size.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e67d8-119">**Araç kutusundaki** bir denetime çift tıklayarak formun varsayılan boyutunda sol üst köşesine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e67d8-119">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>

     <span data-ttu-id="e67d8-120">Ayrıca, çalışma zamanında bir forma dinamik olarak denetim ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e67d8-120">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="e67d8-121">Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Button> denetim tıklandığında forma bir denetim eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="e67d8-121">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e67d8-122">Aşağıdaki yordam, bir **düğme** denetimi `Button1`olan bir form olması gerekir, zaten üzerine yerleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="e67d8-122">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>

## <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="e67d8-123">Bir forma programlı bir şekilde denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="e67d8-123">To add a control to a form programmatically</span></span>

1. <span data-ttu-id="e67d8-124">Formunuzun sınıfı içindeki düğmenin `Click` olayını işleyen yöntemde, denetim değişkeninizin başvurusunu eklemek, `Location`denetimin öğesini ayarlamak ve denetimi eklemek için aşağıdakine benzer bir kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e67d8-124">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>

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
    >  <span data-ttu-id="e67d8-125">Ayrıca, denetimin diğer özelliklerini başlatmak için de kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e67d8-125">You can also add code to initialize other properties of the control.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="e67d8-126">Kötü amaçlı `UserControl`olarak başvurarak yerel bilgisayarınızı ağ üzerinden bir güvenlik riskine maruz kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e67d8-126">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="e67d8-127">Bu durum yalnızca zararlı bir kişinin zararlı bir denetim oluşturan bir sorun olduğu ve bunu projenize yanlışlıkla ekleyerek bir sorun olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e67d8-127">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="e67d8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e67d8-128">See also</span></span>

- [<span data-ttu-id="e67d8-129">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="e67d8-129">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="e67d8-130">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="e67d8-130">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="e67d8-131">Nasıl yapılır: Windows Forms denetimleri yeniden boyutlandır</span><span class="sxs-lookup"><span data-stu-id="e67d8-131">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="e67d8-132">Nasıl yapılır: Windows Forms denetimi tarafından görünen metni ayarlama</span><span class="sxs-lookup"><span data-stu-id="e67d8-132">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="e67d8-133">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="e67d8-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)

---
title: BindingNavigator denetimine yükleme, kaydetme ve Iptal düğmeleri ekleme
description: Windows Forms BindingNavigator denetimine yükleme, kaydetme ve Iptal düğmeleri eklemeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173425"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="54ad5-103">Nasıl yapılır: Windows Formları BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="54ad5-103">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="54ad5-104"><xref:System.Windows.Forms.BindingNavigator>Denetim, <xref:System.Windows.Forms.ToolStrip> formunuzda verilere bağlı olan denetimleri gezme ve düzenleme için tasarlanan özel amaçlı bir denetimdir.</span><span class="sxs-lookup"><span data-stu-id="54ad5-104">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="54ad5-105">Bir <xref:System.Windows.Forms.ToolStrip> Denetim olduğundan, <xref:System.Windows.Forms.BindingNavigator> bileşen Kullanıcı için ek veya alternatif komutlar içerecek şekilde kolayca değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="54ad5-105">Because it's a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="54ad5-106">Aşağıdaki yordamda, bir <xref:System.Windows.Forms.TextBox> Denetim verilere bağlanır ve <xref:System.Windows.Forms.ToolStrip> forma eklenen denetim, yükleme, kaydetme ve İptal düğmelerini içerecek şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="54ad5-106">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="54ad5-107">BindingNavigator bileşenine yükleme, kaydetme ve iptal düğmeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="54ad5-107">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="54ad5-108">Visual Studio 'da <xref:System.Windows.Forms.TextBox> formunuza bir denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54ad5-108">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="54ad5-109">Bir <xref:System.Windows.Forms.BindingSource> veri kaynağına bağlı olan öğesine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="54ad5-109">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="54ad5-110">Bu örnekte, <xref:System.Windows.Forms.BindingSource> bir veritabanına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="54ad5-110">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="54ad5-111">Veri kümesi ve tablo bağdaştırıcısı oluşturulduktan sonra forma bir denetim sürükleyin <xref:System.Windows.Forms.BindingNavigator> .</span><span class="sxs-lookup"><span data-stu-id="54ad5-111">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="54ad5-112"><xref:System.Windows.Forms.BindingNavigator>Denetimin <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini, <xref:System.Windows.Forms.BindingSource> denetimlere bağlı olan form üzerinde olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54ad5-112">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="54ad5-113">Denetimi seçin <xref:System.Windows.Forms.BindingNavigator> .</span><span class="sxs-lookup"><span data-stu-id="54ad5-113">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="54ad5-114">(Küçük siyah ok) tasarımcı eylemleri simgesine tıklayın, ![ ](./media/designer-actions-glyph.gif) böylece **BindingNavigator görevler** Iletişim kutusu görünür ve **öğeleri Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="54ad5-114">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="54ad5-115">**Öğeler koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="54ad5-115">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="54ad5-116">**Öğe koleksiyonu düzenleyicisinde**, aşağıdakileri doldurun:</span><span class="sxs-lookup"><span data-stu-id="54ad5-116">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="54ad5-117"><xref:System.Windows.Forms.ToolStripSeparator> <xref:System.Windows.Forms.ToolStripButton> Uygun türü seçerek ve <xref:System.Windows.Forms.ToolStripItem> **Ekle** düğmesine tıklayarak, ve üç öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54ad5-117">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="54ad5-118"><xref:System.Windows.Forms.ToolStripItem.Name%2A>Düğmelerin özelliğini sırasıyla **loadButton**, **saveButton**ve **CancelButton**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54ad5-118">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="54ad5-119"><xref:System.Windows.Forms.ToolStripItem.Text%2A> **Yüklenecek**, **kaydedilecek**ve **iptal**edilecek düğmelerin özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54ad5-119">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="54ad5-120"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>Düğmelerin her bir özelliğini **metin**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54ad5-120">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="54ad5-121">Alternatif olarak, bu özelliği **Image** veya **ImageAndText**olarak ayarlayabilir ve görüntüde görüntülenecek şekilde ayarlayabilirsiniz <xref:System.Windows.Forms.ToolStripItem.Image%2A> .</span><span class="sxs-lookup"><span data-stu-id="54ad5-121">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="54ad5-122">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="54ad5-122">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="54ad5-123">Düğmeleri öğesine eklenir <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="54ad5-123">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="54ad5-124">Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="54ad5-124">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="54ad5-125">Kod Düzenleyicisi 'nde, tablo bağdaştırıcısına veri yükleyen kod satırını bulun.</span><span class="sxs-lookup"><span data-stu-id="54ad5-125">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="54ad5-126">Bu kod, adım 2 ' de veri bağlamayı ayarlarken oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="54ad5-126">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="54ad5-127">Kod aşağıdakine benzer olmalıdır: `TableAdapterName.Fill(DataSetName.TableName)` .</span><span class="sxs-lookup"><span data-stu-id="54ad5-127">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="54ad5-128">Büyük olasılıkla formun <xref:System.Windows.Forms.Form.Load> olayında olacaktır.</span><span class="sxs-lookup"><span data-stu-id="54ad5-128">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="54ad5-129"><xref:System.Windows.Forms.ToolStripItem.Click>Daha önce oluşturduğunuz **yükün** olayı için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripButton> ve bu veri yükleme kodunu buna taşıyın.</span><span class="sxs-lookup"><span data-stu-id="54ad5-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="54ad5-130">Kodunuz artık aşağıdakine benzer şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="54ad5-130">Your code should now look similar to the following:</span></span>

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. <span data-ttu-id="54ad5-131"><xref:System.Windows.Forms.ToolStripItem.Click>Daha önce oluşturduğunuz **kaydetme** olayı için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripButton> ve denetimin bağlandığı tablodaki verileri güncelleştirmek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="54ad5-131">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="54ad5-132">Bazı durumlarda, <xref:System.Windows.Forms.BindingNavigator> bileşen zaten bir **Kaydet** düğmesine sahiptir, ancak Windows Form Tasarımcısı hiçbir kod üretilmez.</span><span class="sxs-lookup"><span data-stu-id="54ad5-132">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="54ad5-133">Bu durumda, <xref:System.Windows.Forms.ToolStripItem.Click> üzerinde tamamen yeni bir düğme oluşturmak yerine, önceki kodu bu düğmeye ait olay işleyicisine yerleştirebilirsiniz <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="54ad5-133">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="54ad5-134">Ancak düğme varsayılan olarak devre dışıdır, bu nedenle düğmenin <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğini düğme işlevine doğru olacak şekilde ayarlamanız gerekir `true` .</span><span class="sxs-lookup"><span data-stu-id="54ad5-134">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="54ad5-135"><xref:System.Windows.Forms.ToolStripItem.Click>Daha önce oluşturduğunuz **iptal etme** olayı için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripButton> ve görüntülenen veri kaydındaki tüm değişiklikleri iptal etmek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="54ad5-135">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="54ad5-136"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A>Yöntemi, veri satırının kapsamına alınır.</span><span class="sxs-lookup"><span data-stu-id="54ad5-136">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="54ad5-137">Bir sonraki kayda gitmeden önce bu tek kaydı görüntülerken yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="54ad5-137">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="54ad5-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54ad5-138">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="54ad5-139">BindingNavigator denetimi</span><span class="sxs-lookup"><span data-stu-id="54ad5-139">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="54ad5-140">BindingSource Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="54ad5-140">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)

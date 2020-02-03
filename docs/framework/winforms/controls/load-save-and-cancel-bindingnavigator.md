---
title: BindingNavigator denetimine yükleme, kaydetme ve Iptal düğmeleri ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: ac862d163f1bd8b66f29160d836bc459e4bf4081
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745133"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="f5d98-102">Nasıl yapılır: Windows Formları BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="f5d98-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="f5d98-103"><xref:System.Windows.Forms.BindingNavigator> denetimi, formunuzda verilere bağlı olan denetimleri gezme ve düzenleme için tasarlanan özel amaçlı bir <xref:System.Windows.Forms.ToolStrip> denetimidir.</span><span class="sxs-lookup"><span data-stu-id="f5d98-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="f5d98-104"><xref:System.Windows.Forms.ToolStrip> bir denetim olduğundan, <xref:System.Windows.Forms.BindingNavigator> bileşen Kullanıcı için ek veya alternatif komutlar içerecek şekilde kolayca değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5d98-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="f5d98-105">Aşağıdaki yordamda, <xref:System.Windows.Forms.TextBox> bir denetim verilere bağlanır ve forma eklenen <xref:System.Windows.Forms.ToolStrip> denetimi yükleme, kaydetme ve İptal düğmelerini içerecek şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="f5d98-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="f5d98-106">BindingNavigator bileşenine yükleme, kaydetme ve iptal düğmeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="f5d98-106">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="f5d98-107">Visual Studio 'da formunuza bir <xref:System.Windows.Forms.TextBox> denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f5d98-107">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="f5d98-108">Bir veri kaynağına bağlı bir <xref:System.Windows.Forms.BindingSource>bağlayın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="f5d98-109">Bu örnek için <xref:System.Windows.Forms.BindingSource> bir veritabanına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f5d98-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="f5d98-110">Veri kümesi ve tablo bağdaştırıcısı oluşturulduktan sonra forma <xref:System.Windows.Forms.BindingNavigator> denetimini sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="f5d98-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="f5d98-111"><xref:System.Windows.Forms.BindingNavigator> denetiminin <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini, denetimlere bağlı olan <xref:System.Windows.Forms.BindingSource> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="f5d98-112"><xref:System.Windows.Forms.BindingNavigator> denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="f5d98-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="f5d98-113">**BindingNavigator görevleri** iletişim kutusunun görünmesi ve **öğeleri Düzenle**' yi seçmek için akıllı etiket kabartmasını (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="f5d98-114">**Öğeler koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="f5d98-114">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="f5d98-115">**Öğe koleksiyonu düzenleyicisinde**, aşağıdakileri doldurun:</span><span class="sxs-lookup"><span data-stu-id="f5d98-115">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="f5d98-116">Uygun türdeki <xref:System.Windows.Forms.ToolStripItem> seçerek ve **Ekle** düğmesine tıklayarak <xref:System.Windows.Forms.ToolStripSeparator> ve üç <xref:System.Windows.Forms.ToolStripButton> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f5d98-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="f5d98-117">Düğmelerin <xref:System.Windows.Forms.ToolStripItem.Name%2A> özelliğini sırasıyla **loadButton**, **saveButton**ve **CancelButton**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="f5d98-118">**Yüklenecek**, **kaydedilecek**ve **iptal**edilecek düğmelerin <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="f5d98-119">Düğmelerin her biri için <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini **metin**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="f5d98-120">Alternatif olarak, bu özelliği **Image** veya **ImageAndText**olarak ayarlayabilir ve <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliğinde görüntülenecek şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5d98-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="f5d98-121">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-121">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="f5d98-122">Düğmeler <xref:System.Windows.Forms.ToolStrip>eklenir.</span><span class="sxs-lookup"><span data-stu-id="f5d98-122">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="f5d98-123">Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f5d98-123">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="f5d98-124">Kod Düzenleyicisi 'nde, tablo bağdaştırıcısına veri yükleyen kod satırını bulun.</span><span class="sxs-lookup"><span data-stu-id="f5d98-124">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="f5d98-125">Bu kod, adım 2 ' de veri bağlamayı ayarlarken oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f5d98-125">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="f5d98-126">Kod aşağıdakine benzer olmalıdır: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="f5d98-126">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="f5d98-127">Büyük olasılıkla formun <xref:System.Windows.Forms.Form.Load> olayında olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f5d98-127">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="f5d98-128">Daha önce oluşturduğunuz **yükleme** <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturun ve bu veri yükleme kodunu buna taşıyın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-128">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="f5d98-129">Kodunuz artık aşağıdakine benzer şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="f5d98-129">Your code should now look similar to the following:</span></span>

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

11. <span data-ttu-id="f5d98-130">Daha önce oluşturduğunuz **kayıt**<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturun ve denetimin bağlandığı tablodaki verileri güncelleştirmek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-130">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

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
    > <span data-ttu-id="f5d98-131">Bazı durumlarda <xref:System.Windows.Forms.BindingNavigator> bileşeni zaten bir **Kaydet** düğmesine sahiptir, ancak Windows Form Tasarımcısı tarafından hiçbir kod üretilmez.</span><span class="sxs-lookup"><span data-stu-id="f5d98-131">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="f5d98-132">Bu durumda, <xref:System.Windows.Forms.ToolStrip>üzerinde tamamen yeni bir düğme oluşturmak yerine, önceki kodu bu düğme için <xref:System.Windows.Forms.ToolStripItem.Click> olay işleyicisine yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5d98-132">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="f5d98-133">Ancak, düğme varsayılan olarak devre dışıdır, bu nedenle düğmenin <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğini düğmenin doğru çalışması için `true` olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5d98-133">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="f5d98-134">Daha önce oluşturduğunuz **iptal** <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturun ve görüntülenen veri kaydındaki tüm değişiklikleri iptal etmek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="f5d98-134">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

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
    > <span data-ttu-id="f5d98-135"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A> yöntemi, veri satırının kapsamına alınır.</span><span class="sxs-lookup"><span data-stu-id="f5d98-135">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="f5d98-136">Bir sonraki kayda gitmeden önce bu tek kaydı görüntülerken yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f5d98-136">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5d98-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5d98-137">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="f5d98-138">BindingNavigator Denetimi</span><span class="sxs-lookup"><span data-stu-id="f5d98-138">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="f5d98-139">BindingSource Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f5d98-139">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)

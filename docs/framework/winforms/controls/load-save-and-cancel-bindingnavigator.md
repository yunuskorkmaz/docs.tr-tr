---
title: 'Nasıl yapılır: Windows Forms BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 2d4867c0bc4feb7b43e15614fc56a3c709cef9e7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991733"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="2689b-102">Nasıl yapılır: Windows Forms BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="2689b-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="2689b-103">Denetim, formunuzda verilere bağlı olan denetimleri <xref:System.Windows.Forms.ToolStrip> gezme ve düzenleme için tasarlanan özel amaçlı bir denetimdir. <xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="2689b-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="2689b-104">Bir <xref:System.Windows.Forms.ToolStrip> denetim olduğundan <xref:System.Windows.Forms.BindingNavigator> , bileşen Kullanıcı için ek veya alternatif komutlar içerecek şekilde kolayca değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2689b-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="2689b-105">Aşağıdaki yordamda, bir <xref:System.Windows.Forms.TextBox> denetim verilere bağlanır <xref:System.Windows.Forms.ToolStrip> ve forma eklenen denetim, yükleme, kaydetme ve İptal düğmelerini içerecek şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="2689b-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="2689b-106">BindingNavigator bileşenine yükleme, kaydetme ve iptal düğmeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="2689b-106">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="2689b-107">Visual Studio 'da formunuza bir <xref:System.Windows.Forms.TextBox> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2689b-107">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="2689b-108">Bir <xref:System.Windows.Forms.BindingSource>veri kaynağına bağlı olan öğesine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="2689b-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="2689b-109">Bu örnekte <xref:System.Windows.Forms.BindingSource> , bir veritabanına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="2689b-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="2689b-110">Veri kümesi ve tablo bağdaştırıcısı oluşturulduktan sonra forma bir <xref:System.Windows.Forms.BindingNavigator> denetim sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="2689b-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="2689b-111">Denetimin özelliğini ,<xref:System.Windows.Forms.BindingSource> denetimlere bağlı olan form üzerinde olarak ayarlayın. <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> <xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="2689b-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="2689b-112"><xref:System.Windows.Forms.BindingNavigator> Denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="2689b-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="2689b-113">**BindingNavigator görevleri** iletişim kutusu görünür ve **öğeleri Düzenle**' yi seçerek akıllı etiket glifi ' ne (![akıllı etiket karakteri](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2689b-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="2689b-114">**Öğeler koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="2689b-114">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="2689b-115">**Öğe koleksiyonu düzenleyicisinde**, aşağıdakileri doldurun:</span><span class="sxs-lookup"><span data-stu-id="2689b-115">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="2689b-116"><xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripSeparator> Uygun türü<xref:System.Windows.Forms.ToolStripItem> seçerek ve Ekle düğmesine tıklayarak, ve üç öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2689b-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="2689b-117">Düğmelerin özelliğini sırasıyla **loadButton**, **saveButton**ve **CancelButton**olarak ayarlayın. <xref:System.Windows.Forms.ToolStripItem.Name%2A></span><span class="sxs-lookup"><span data-stu-id="2689b-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="2689b-118">Yüklenecek, **kaydedilecek**ve **iptal**edilecek düğmelerin özelliğiniayarlayın.<xref:System.Windows.Forms.ToolStripItem.Text%2A></span><span class="sxs-lookup"><span data-stu-id="2689b-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="2689b-119">Düğmelerin her bir özelliğinimetinolarak<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2689b-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="2689b-120">Alternatif olarak, bu özelliği **Image** veya **ImageAndText**olarak ayarlayabilir ve görüntüde <xref:System.Windows.Forms.ToolStripItem.Image%2A> görüntülenecek şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2689b-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="2689b-121">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="2689b-121">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="2689b-122">Düğmeleri öğesine <xref:System.Windows.Forms.ToolStrip>eklenir.</span><span class="sxs-lookup"><span data-stu-id="2689b-122">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="2689b-123">Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2689b-123">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="2689b-124">Kod Düzenleyicisi 'nde, tablo bağdaştırıcısına veri yükleyen kod satırını bulun.</span><span class="sxs-lookup"><span data-stu-id="2689b-124">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="2689b-125">Bu kod, adım 2 ' de veri bağlamayı ayarlarken oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="2689b-125">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="2689b-126">Kod aşağıdakine benzer olmalıdır: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="2689b-126">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="2689b-127">Büyük olasılıkla formun <xref:System.Windows.Forms.Form.Load> olayında olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2689b-127">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="2689b-128">Daha önce oluşturduğunuz <xref:System.Windows.Forms.ToolStripItem.Click> **yükün** <xref:System.Windows.Forms.ToolStripButton> olayı için bir olay işleyicisi oluşturun ve bu veri yükleme kodunu buna taşıyın.</span><span class="sxs-lookup"><span data-stu-id="2689b-128">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="2689b-129">Kodunuz artık aşağıdakine benzer şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="2689b-129">Your code should now look similar to the following:</span></span>

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

11. <span data-ttu-id="2689b-130">Daha önce oluşturduğunuz <xref:System.Windows.Forms.ToolStripItem.Click> **kaydetme** <xref:System.Windows.Forms.ToolStripButton> olayı için bir olay işleyicisi oluşturun ve denetimin bağlandığı tablodaki verileri güncelleştirmek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="2689b-130">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

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
    > <span data-ttu-id="2689b-131">Bazı durumlarda, <xref:System.Windows.Forms.BindingNavigator> bileşen zaten bir **Kaydet** düğmesine sahiptir, ancak Windows Form Tasarımcısı hiçbir kod üretilmez.</span><span class="sxs-lookup"><span data-stu-id="2689b-131">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="2689b-132">Bu durumda, <xref:System.Windows.Forms.ToolStrip>üzerinde tamamen yeni bir düğme oluşturmak yerine, önceki <xref:System.Windows.Forms.ToolStripItem.Click> kodu bu düğmeye ait olay işleyicisine yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2689b-132">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="2689b-133">Ancak düğme varsayılan olarak devre dışıdır, bu nedenle düğmenin <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> özelliğini `true` düğme işlevine doğru olacak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2689b-133">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="2689b-134">Daha önce oluşturduğunuz <xref:System.Windows.Forms.ToolStripItem.Click> **iptal etme** <xref:System.Windows.Forms.ToolStripButton> olayı için bir olay işleyicisi oluşturun ve görüntülenen veri kaydındaki tüm değişiklikleri iptal etmek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="2689b-134">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

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
    > <span data-ttu-id="2689b-135"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Yöntemi, veri satırının kapsamına alınır.</span><span class="sxs-lookup"><span data-stu-id="2689b-135">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="2689b-136">Bir sonraki kayda gitmeden önce bu tek kaydı görüntülerken yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2689b-136">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="2689b-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2689b-137">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="2689b-138">BindingNavigator Denetimi</span><span class="sxs-lookup"><span data-stu-id="2689b-138">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="2689b-139">BindingSource Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2689b-139">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)

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
ms.openlocfilehash: 52d4fc32836a5d20bd99d8ebfd3119c761376e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098721"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="60faf-102">Nasıl yapılır: Windows Forms BindingNavigator Denetimine Yükleme, Kaydetme ve İptal Düğmeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="60faf-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="60faf-103"><xref:System.Windows.Forms.BindingNavigator> Denetimidir özel amaçlı <xref:System.Windows.Forms.ToolStrip> denetimi gezinme ve verilere bağlı denetimler formunuzdaki işlemek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="60faf-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="60faf-104">Çünkü bu bir <xref:System.Windows.Forms.ToolStrip> denetimi <xref:System.Windows.Forms.BindingNavigator> bileşen kolayca değiştirilebilir ek veya alternatif komut kullanıcı için eklenecek.</span><span class="sxs-lookup"><span data-stu-id="60faf-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="60faf-105">Aşağıdaki yordamda bir <xref:System.Windows.Forms.TextBox> denetimin verilere bağlı ve <xref:System.Windows.Forms.ToolStrip> kaydetme, yükleme, içerir ve İptal düğmeleri değiştirilmişse forma eklenen denetimi.</span><span class="sxs-lookup"><span data-stu-id="60faf-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="60faf-106">Yük eklemek, kaydetme ve İptal düğmeleri BindingNavigator bileşenine</span><span class="sxs-lookup"><span data-stu-id="60faf-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="60faf-107">Ekleme bir <xref:System.Windows.Forms.TextBox> form denetimi.</span><span class="sxs-lookup"><span data-stu-id="60faf-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="60faf-108">Öğeyi bir <xref:System.Windows.Forms.BindingSource>, bir veri kaynağına bağlı.</span><span class="sxs-lookup"><span data-stu-id="60faf-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="60faf-109">Bu örnekte, <xref:System.Windows.Forms.BindingSource> veritabanına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="60faf-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="60faf-110">Veri kümesi ve tablo bağdaştırıcısı oluşturulur, sonra sürükleyin bir <xref:System.Windows.Forms.BindingNavigator> forma.</span><span class="sxs-lookup"><span data-stu-id="60faf-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="60faf-111">Ayarlama <xref:System.Windows.Forms.BindingNavigator> denetimin <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini <xref:System.Windows.Forms.BindingSource> denetimlere bağlı form üzerindeki.</span><span class="sxs-lookup"><span data-stu-id="60faf-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="60faf-112">Seçin <xref:System.Windows.Forms.BindingNavigator> denetimi.</span><span class="sxs-lookup"><span data-stu-id="60faf-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="60faf-113">Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) böylece **BindingNavigator görevleri** iletişim kutusu açılır ve seçin **öğedüzenleme**.</span><span class="sxs-lookup"><span data-stu-id="60faf-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="60faf-114">**Öğeler Koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="60faf-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="60faf-115">İçinde **öğeler Koleksiyonu Düzenleyicisi**, aşağıdaki adımları tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="60faf-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="60faf-116">Ekle bir <xref:System.Windows.Forms.ToolStripSeparator> ve üç <xref:System.Windows.Forms.ToolStripButton> uygun türünü seçerek öğeleri <xref:System.Windows.Forms.ToolStripItem> tıklayıp **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="60faf-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="60faf-117">Ayarlama <xref:System.Windows.Forms.ToolStripItem.Name%2A> düğmelere özelliği **LoadButton**, **saveButton yapın**, ve **CancelButton**sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="60faf-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="60faf-118">Ayarlama <xref:System.Windows.Forms.ToolStripItem.Text%2A> düğmelere özelliği **yük**, **Kaydet**, ve **iptal**.</span><span class="sxs-lookup"><span data-stu-id="60faf-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>  
  
    4.  <span data-ttu-id="60faf-119">Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> her düğme için özellik **metin**.</span><span class="sxs-lookup"><span data-stu-id="60faf-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="60faf-120">Alternatif olarak, bu özelliği ayarlayın **görüntü** veya **ImageAndText**ve görüntülenen resmi ayarlama <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="60faf-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="60faf-121">Tıklayın **Tamam** iletişim kutusunu kapatın. Düğmeleri eklenen <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="60faf-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="60faf-122">Formun sağ tıklatın ve seçin **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="60faf-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="60faf-123">Kod Düzenleyicisi'nde tablo bağdaştırıcısı veri yükleyen kod satırını bulun.</span><span class="sxs-lookup"><span data-stu-id="60faf-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="60faf-124">Veri bağlama 2. adımda ayarladığınızda bu kod üretildi.</span><span class="sxs-lookup"><span data-stu-id="60faf-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="60faf-125">Kodu aşağıdakine benzer olmalıdır: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="60faf-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="60faf-126">Çoğu olacak büyük olasılıkla formun olması <xref:System.Windows.Forms.Form.Load> olay.</span><span class="sxs-lookup"><span data-stu-id="60faf-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="60faf-127">İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı **yük** <xref:System.Windows.Forms.ToolStripButton> daha önce oluşturduğunuz ve bu veri yükleme kod içine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="60faf-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="60faf-128">Kodunuzun aşağıdakine benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="60faf-128">Your code should now look similar to the following:</span></span>  
  
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
  
11. <span data-ttu-id="60faf-129">İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı **Kaydet** <xref:System.Windows.Forms.ToolStripButton> daha önce oluşturduğunuz ve tablo denetimi içindeki verileri güncelleştirmek için kod yazma bağlanır.</span><span class="sxs-lookup"><span data-stu-id="60faf-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
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
    > <span data-ttu-id="60faf-130">Bazı durumlarda, <xref:System.Windows.Forms.BindingNavigator> bileşeni zaten sahip olacak bir **Kaydet** düğmesi, ancak hiçbir kod oluşturulduğunu Windows Form Tasarımcısı tarafından.</span><span class="sxs-lookup"><span data-stu-id="60faf-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a **Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="60faf-131">Bu durumda, önceki kodu koyabilirsiniz <xref:System.Windows.Forms.ToolStripItem.Click> üzerinde tamamen yeni bir düğme oluşturmak yerine bu düğme için olay işleyicisi <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="60faf-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="60faf-132">Ayarlamanız gerekir ancak düğmenin varsayılan olarak devre dışıdır <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> düğmenin özelliği `true` düğme işlevi doğru olması.</span><span class="sxs-lookup"><span data-stu-id="60faf-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>
  
12. <span data-ttu-id="60faf-133">İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.ToolStripItem.Click> olayı **iptal** <xref:System.Windows.Forms.ToolStripButton> daha önce oluşturduğunuz ve görüntülenen veri kaydına değişiklikleri iptal etmek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="60faf-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
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
    >  <span data-ttu-id="60faf-134"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Yöntemi veri satırı için kapsamlı.</span><span class="sxs-lookup"><span data-stu-id="60faf-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="60faf-135">Sonraki kayda gitmeden önce tek bir kayıt görüntülerken yaptığınız tüm değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="60faf-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60faf-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60faf-136">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="60faf-137">BindingNavigator Denetimi</span><span class="sxs-lookup"><span data-stu-id="60faf-137">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="60faf-138">BindingSource Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="60faf-138">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)

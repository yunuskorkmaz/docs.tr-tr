---
title: "Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme"
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
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8518fdcaca7ebed65d0923b9bc1fe1a6797b97c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="253d9-102">Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="253d9-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="253d9-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="253d9-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="253d9-104">Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="253d9-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="253d9-105">Farklı renkler için çeşitli kısımlarını uygulayarak bir <xref:System.Windows.Forms.DataGrid> denetim bilgileri okumak ve yorumlamak kolaylaştırmak için yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="253d9-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="253d9-106">Renk satırlara ve sütunlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="253d9-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="253d9-107">Satırları ve sütunları da gizlenebilir veya kümeleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="253d9-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="253d9-108">Biçimlendirme üç temel nokta <xref:System.Windows.Forms.DataGrid> denetim.</span><span class="sxs-lookup"><span data-stu-id="253d9-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="253d9-109">Verilerin görüntülendiği varsayılan stilini kurmak için özellikleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="253d9-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="253d9-110">Bu taban, belirli tabloları çalışma zamanında görüntülenme biçimini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="253d9-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="253d9-111">Son olarak, hangi sütunların renkleri yanı sıra veri kılavuzu görüntülenen değiştirebilir ve diğer biçimlendirme gösterilir.</span><span class="sxs-lookup"><span data-stu-id="253d9-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="253d9-112">Veri Kılavuzu biçimlendirme bir ilk adım, özellikleri ayarlayabilirsiniz <xref:System.Windows.Forms.DataGrid> kendisi.</span><span class="sxs-lookup"><span data-stu-id="253d9-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="253d9-113">Bu renk ve biçime seçimler, ardından veri tabloları ve sütunları görüntülenen bağlı olarak değişiklik yapabilirsiniz bir temel oluşturur.</span><span class="sxs-lookup"><span data-stu-id="253d9-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="253d9-114">DataGrid denetimi için varsayılan stil oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="253d9-114">To establish a default style for the DataGrid control</span></span>  
  
1.  <span data-ttu-id="253d9-115">Aşağıdaki özellikleri uygun şekilde ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="253d9-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="253d9-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="253d9-116">Property</span></span>|<span data-ttu-id="253d9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="253d9-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="253d9-118"><xref:System.Windows.Forms.DataGrid.BackColor%2A> Özelliği ızgaranın sayılı satırların rengi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="253d9-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="253d9-119">Ayarladığınızda <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özelliği için farklı bir renk, her bir satır ayarlanmış bu yeni renge (satırları 1, 3, 5 ve benzeri).</span><span class="sxs-lookup"><span data-stu-id="253d9-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="253d9-120">Izgaranın sayılı satırların arka plan rengi (satırları 0, 2, 4, 6 ve benzeri).</span><span class="sxs-lookup"><span data-stu-id="253d9-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="253d9-121">Oysa <xref:System.Windows.Forms.DataGrid.BackColor%2A> ve <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özellikleri ızgara satırların rengini belirler <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özelliği, kılavuzun altına kaydırılan veya birkaç satır içerdiği yalnızca görülebilir nonrow alanının rengini belirler Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="253d9-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="253d9-122">Izgaranın kenarlık stili, aşağıdakilerden birini <xref:System.Windows.Forms.BorderStyle> numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="253d9-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="253d9-123">Hemen kılavuz görüntülenen kılavuz penceresinin başlık arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="253d9-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="253d9-124">Izgaranın üst başlık yazı tipi.</span><span class="sxs-lookup"><span data-stu-id="253d9-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="253d9-125">Izgaranın penceresinin başlık arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="253d9-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="253d9-126">Kılavuzda metni görüntülemek için kullanılan yazıtipi.</span><span class="sxs-lookup"><span data-stu-id="253d9-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="253d9-127">Veri Kılavuzu satırlardaki verileri tarafından görüntülenen yazı tipi rengi.</span><span class="sxs-lookup"><span data-stu-id="253d9-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="253d9-128">Veri Kılavuzu kılavuz çizgilerinin rengi.</span><span class="sxs-lookup"><span data-stu-id="253d9-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="253d9-129">Kılavuz birini hücrelerinin ayırarak çizgi stilini <xref:System.Windows.Forms.DataGridLineStyle> numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="253d9-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="253d9-130">Satır ve sütun üstbilgilerini arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="253d9-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="253d9-131">Sütun üst bilgileri için kullanılan yazıtipi.</span><span class="sxs-lookup"><span data-stu-id="253d9-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="253d9-132">Kılavuz sütun başlıklarını sütunu üstbilgi metni ve (birden fazla ilgili tablo görüntülendiğinde satırları genişletmek için) artı/eksi karakterleri dahil olmak üzere, ön plan rengi.</span><span class="sxs-lookup"><span data-stu-id="253d9-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="253d9-133">Alt tablolar, ilişki adı ve benzeri bağlantılar dahil olmak üzere veri kılavuzunda tüm bağlantıların metnin rengi.</span><span class="sxs-lookup"><span data-stu-id="253d9-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="253d9-134">Bir alt tabloda üst satırların arka plan rengini budur.</span><span class="sxs-lookup"><span data-stu-id="253d9-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="253d9-135">Bir alt tabloda üst satırların ön plan rengini budur.</span><span class="sxs-lookup"><span data-stu-id="253d9-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="253d9-136">Tablo ve sütun adlarını yoluyla üst satırda görüntülenip görüntülenmediğini belirler <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="253d9-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="253d9-137">Kılavuz sütunu varsayılan genişliğini (piksel cinsinden).</span><span class="sxs-lookup"><span data-stu-id="253d9-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="253d9-138">Sıfırlamadan önce bu özelliği ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı ayrı aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), ya da özelliğinin hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="253d9-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="253d9-139">Özelliği 0'dan daha düşük bir değere ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="253d9-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="253d9-140">Izgaradaki satırların (piksel cinsinden) satır yüksekliği.</span><span class="sxs-lookup"><span data-stu-id="253d9-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="253d9-141">Sıfırlamadan önce bu özelliği ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı ayrı aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), ya da özelliğinin hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="253d9-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="253d9-142">Özelliği 0'dan daha düşük bir değere ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="253d9-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="253d9-143">Izgaranın satır üstbilgilerinin genişliği.</span><span class="sxs-lookup"><span data-stu-id="253d9-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="253d9-144">Bir satır veya hücre seçildiğinde, arka plan rengini budur.</span><span class="sxs-lookup"><span data-stu-id="253d9-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="253d9-145">Bir satır veya hücre seçildiğinde, ön plan rengini budur.</span><span class="sxs-lookup"><span data-stu-id="253d9-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="253d9-146">Denetimi zayıf renk seçim (örneğin, kırmızı ve yeşil) nedeniyle erişilemez hale da mümkündür denetimlerin renkleri özelleştirirken unutmayın.</span><span class="sxs-lookup"><span data-stu-id="253d9-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="253d9-147">Kullanılabilir renklerini kullan **sistem renkleri** bu sorunu önlemek için palet.</span><span class="sxs-lookup"><span data-stu-id="253d9-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="253d9-148">Aşağıdaki yordamlar formunuz olduğunu varsayalım bir <xref:System.Windows.Forms.DataGrid> denetimine bağlı bir veri tablosuna.</span><span class="sxs-lookup"><span data-stu-id="253d9-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="253d9-149">Daha fazla bilgi için bkz: [Windows Forms DataGrid denetimini veri kaynağına bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="253d9-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="253d9-150">Veri tablosu tablo ve sütun stilini programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="253d9-150">To set the table and column style of a data table programmatically</span></span>  
  
1.  <span data-ttu-id="253d9-151">Yeni tablo stili oluşturun ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="253d9-151">Create a new table style and set its properties.</span></span>  
  
2.  <span data-ttu-id="253d9-152">Bir sütun stili oluşturun ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="253d9-152">Create a column style and set its properties.</span></span>  
  
3.  <span data-ttu-id="253d9-153">Sütun stili tablo stili 's sütun stilleri koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="253d9-153">Add the column style to the table style's column styles collection.</span></span>  
  
4.  <span data-ttu-id="253d9-154">Tablo Stili veri kılavuzunun tablo stilleri koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="253d9-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5.  <span data-ttu-id="253d9-155">Aşağıdaki örnekte, yeni bir örneğini oluşturmak <xref:System.Windows.Forms.DataGridTableStyle> ve kendi <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="253d9-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6.  <span data-ttu-id="253d9-156">Yeni bir örneğini oluşturmak bir **GridColumnStyle** ve kendi **MappingName** (ve diğer bazı düzeni ve görüntü özelliklerini).</span><span class="sxs-lookup"><span data-stu-id="253d9-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7.  <span data-ttu-id="253d9-157">Oluşturmak istediğiniz her sütun stili için 2 ile 6 arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="253d9-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="253d9-158">Aşağıdaki örnek gösterilmektedir nasıl bir <xref:System.Windows.Forms.DataGridTextBoxColumn> sütunda görüntülenecek bir ad olduğu için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="253d9-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="253d9-159">Ayrıca, sütun stili eklemek <xref:System.Windows.Forms.GridColumnStylesCollection> tablo stili ve tablo stiline ekleyin <xref:System.Windows.Forms.GridTableStylesCollection> veri kılavuzunun.</span><span class="sxs-lookup"><span data-stu-id="253d9-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName   
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName   
       ' to the name of a DataColumn in the DataTable.   
       ' Set the HeaderText and Width properties.   
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to   
       ' the GridTableStylesCollection.   
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName   
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName   
       // to the name of a DataColumn in the DataTable.   
       // Set the HeaderText and Width properties.   
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to   
       // the GridTableStylesCollection.   
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName   
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName   
          // to the name of a DataColumn in the DataTable.   
          // Set the HeaderText and Width properties.   
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to   
          // the GridTableStylesCollection.   
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="253d9-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="253d9-160">See Also</span></span>  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [<span data-ttu-id="253d9-161">Nasıl yapılır: sütunları silme veya gizleme Windows Forms DataGrid denetimi</span><span class="sxs-lookup"><span data-stu-id="253d9-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="253d9-162">DataGrid denetimi</span><span class="sxs-lookup"><span data-stu-id="253d9-162">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)

---
title: DataGrid denetimini biçimlendirme
ms.date: 03/30/2017
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
ms.openlocfilehash: 30342a89f3176255fa7217ccbbbd91c166ff7f35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732965"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="e7de7-102">Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e7de7-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="e7de7-103"><xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="e7de7-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="e7de7-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e7de7-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="e7de7-105"><xref:System.Windows.Forms.DataGrid> denetiminin çeşitli bölümlerine farklı renkler uygulamak, bilgilerin okunmasını ve yorumlanması daha kolay hale getirmenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7de7-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="e7de7-106">Renk, satırlara ve sütunlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e7de7-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="e7de7-107">Satırlar ve sütunlar da gizlenebilir veya sizin için de görünür.</span><span class="sxs-lookup"><span data-stu-id="e7de7-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="e7de7-108"><xref:System.Windows.Forms.DataGrid> denetimini biçimlendirmenin üç temel yönü vardır.</span><span class="sxs-lookup"><span data-stu-id="e7de7-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="e7de7-109">Özellikleri, verilerin görüntülendiği varsayılan bir stil oluşturmak için ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7de7-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="e7de7-110">Bu temelden, belirli tabloların çalışma zamanında görüntülenme şeklini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7de7-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="e7de7-111">Son olarak, veri kılavuzunda görüntülenecek sütunları ve gösterilen renkleri ve diğer biçimlendirmeleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7de7-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="e7de7-112">Bir veri kılavuzunu biçimlendirirken ilk adım olarak, <xref:System.Windows.Forms.DataGrid> özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7de7-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="e7de7-113">Bu renk ve biçim seçimleri, daha sonra görünen veri tablolarına ve sütunlara göre değişiklik yapabileceğiniz bir temel oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e7de7-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="e7de7-114">DataGrid denetimi için varsayılan bir stil oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e7de7-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="e7de7-115">Aşağıdaki özellikleri uygun şekilde ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e7de7-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="e7de7-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="e7de7-116">Property</span></span>|<span data-ttu-id="e7de7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7de7-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="e7de7-118"><xref:System.Windows.Forms.DataGrid.BackColor%2A> özelliği, kılavuzun çift sayılı satırlarının rengini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7de7-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="e7de7-119"><xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özelliğini farklı bir renge ayarladığınızda, diğer her satır bu yeni renge ayarlanır (satır 1, 3, 5, vb.).</span><span class="sxs-lookup"><span data-stu-id="e7de7-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="e7de7-120">Kılavuzun çift sayılı satırlarının arka plan rengi (satırlar 0, 2, 4, 6, vb.).</span><span class="sxs-lookup"><span data-stu-id="e7de7-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="e7de7-121"><xref:System.Windows.Forms.DataGrid.BackColor%2A> ve <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özellikleri kılavuzdaki satırların rengini belirlerse, <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özelliği yalnızca ızgara en alta kaydırıldığında veya kılavuzda yalnızca birkaç satır mevcutsa görünür olan satır olmayan alanın rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="e7de7-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="e7de7-122"><xref:System.Windows.Forms.BorderStyle> sabit listesi değerlerinden biri olan kılavuzun kenarlık stili.</span><span class="sxs-lookup"><span data-stu-id="e7de7-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="e7de7-123">Kılavuzun hemen üstünde görünen kılavuzun pencere açıklamalı arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="e7de7-124">Kılavuzun üst kısmındaki başlık yazı tipi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="e7de7-125">Kılavuzun pencere açıklamalı arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="e7de7-126">Kılavuzdaki metni göstermek için kullanılan yazı tipi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="e7de7-127">Veri kılavuzu satırlarındaki veriler tarafından gösterilecek yazı tipi rengi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="e7de7-128">Veri kılavuzunun kılavuz çizgilerinin rengi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="e7de7-129"><xref:System.Windows.Forms.DataGridLineStyle> sabit listesi değerlerinden biri olan kılavuzun hücrelerini ayıran çizgilerin stili.</span><span class="sxs-lookup"><span data-stu-id="e7de7-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="e7de7-130">Satır ve sütun üst bilgilerinin arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="e7de7-131">Sütun başlıkları için kullanılan yazı tipi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="e7de7-132">Kılavuzun sütun üstbilgilerinin, sütun üst bilgisi metni ve artı/eksi glifleri (birden çok ilişkili tablo görüntülenirken satırları genişletmek için) dahil ön plan rengi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="e7de7-133">Veri kılavuzundaki tüm bağlantıların, alt tablolara bağlantılar, ilişki adı vb. gibi tüm bağlantıların metin rengi.</span><span class="sxs-lookup"><span data-stu-id="e7de7-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="e7de7-134">Alt tabloda, bu, üst satırların arka plan rengidir.</span><span class="sxs-lookup"><span data-stu-id="e7de7-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="e7de7-135">Alt tabloda, bu, üst satırların ön plan rengidir.</span><span class="sxs-lookup"><span data-stu-id="e7de7-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="e7de7-136">Tablo ve sütun adlarının, <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> numaralandırması aracılığıyla üst satırda görüntülenip görüntülenmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="e7de7-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="e7de7-137">Kılavuzdaki sütunların varsayılan genişliği (piksel cinsinden).</span><span class="sxs-lookup"><span data-stu-id="e7de7-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="e7de7-138"><xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini sıfırlamadan önce (ayrı olarak veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi aracılığıyla) bu özelliği ayarlayın, ya da özelliğin hiçbir etkisi olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e7de7-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="e7de7-139">Özellik 0 ' dan küçük bir değere ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="e7de7-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="e7de7-140">Kılavuzdaki satırların satır yüksekliği (piksel cinsinden).</span><span class="sxs-lookup"><span data-stu-id="e7de7-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="e7de7-141"><xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini sıfırlamadan önce (ayrı olarak veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi aracılığıyla) bu özelliği ayarlayın, ya da özelliğin hiçbir etkisi olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e7de7-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="e7de7-142">Özellik 0 ' dan küçük bir değere ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="e7de7-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="e7de7-143">Kılavuzun satır üst bilgilerinin genişliği.</span><span class="sxs-lookup"><span data-stu-id="e7de7-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="e7de7-144">Bir satır veya hücre seçildiğinde, bu arka plan rengidir.</span><span class="sxs-lookup"><span data-stu-id="e7de7-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="e7de7-145">Bir satır veya hücre seçildiğinde bu, ön plan rengidir.</span><span class="sxs-lookup"><span data-stu-id="e7de7-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="e7de7-146">Denetimlerin renklerini özelleştirirken, kötü renk seçimi (örneğin, kırmızı ve yeşil) nedeniyle denetimi erişilemez hale getirmek mümkün olduğunca göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e7de7-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="e7de7-147">Bu sorundan kaçınmak için **sistem renkleri** paletindeki kullanılabilir renkleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7de7-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="e7de7-148">Aşağıdaki yordamlarda formunuzun bir veri tablosuna göre <xref:System.Windows.Forms.DataGrid> denetimi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e7de7-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="e7de7-149">Daha fazla bilgi için, bkz. [Windows Forms DataGrid denetimini bir veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="e7de7-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="e7de7-150">Bir veri tablosunun tablo ve sütun stilini programlı bir şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e7de7-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="e7de7-151">Yeni bir tablo stili oluşturun ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e7de7-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="e7de7-152">Sütun stili oluşturun ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e7de7-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="e7de7-153">Sütun stilini tablo stilinin sütun stilleri koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e7de7-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="e7de7-154">Tablo stilini veri kılavuzunun tablo stilleri koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e7de7-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="e7de7-155">Aşağıdaki örnekte, yeni bir <xref:System.Windows.Forms.DataGridTableStyle> örneği oluşturun ve <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e7de7-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="e7de7-156">Bir **GridColumnStyle** 'ın yeni bir örneğini oluşturun ve onun **MappingName** değerini (ve diğer düzen ve görüntü özelliklerini) ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e7de7-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="e7de7-157">Oluşturmak istediğiniz her sütun stili için 2 ile 6 arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="e7de7-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="e7de7-158">Aşağıdaki örnek, sütununda bir ad görüntülenecek şekilde bir <xref:System.Windows.Forms.DataGridTextBoxColumn> nasıl oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7de7-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="e7de7-159">Ayrıca, sütun stilini tablo stilinin <xref:System.Windows.Forms.GridColumnStylesCollection> eklersiniz ve tablo stilini veri kılavuzunun <xref:System.Windows.Forms.GridTableStylesCollection> eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="e7de7-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7de7-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7de7-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="e7de7-161">Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme</span><span class="sxs-lookup"><span data-stu-id="e7de7-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="e7de7-162">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="e7de7-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)

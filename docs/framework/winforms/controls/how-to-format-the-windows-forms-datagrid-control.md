---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme'
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
ms.openlocfilehash: 99acef0a7b29228ddf0406352ff5a88b77294b00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966664"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="69b25-102">Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="69b25-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="69b25-103">Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="69b25-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="69b25-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="69b25-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="69b25-105">Bir <xref:System.Windows.Forms.DataGrid> denetimin çeşitli bölümlerine farklı renkler uygulamak, bilgilerin okunmasını ve yorumlanması daha kolay hale getirmenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="69b25-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="69b25-106">Renk, satırlara ve sütunlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="69b25-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="69b25-107">Satırlar ve sütunlar da gizlenebilir veya sizin için de görünür.</span><span class="sxs-lookup"><span data-stu-id="69b25-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="69b25-108"><xref:System.Windows.Forms.DataGrid> Denetimi biçimlendirmenin üç temel yönü vardır.</span><span class="sxs-lookup"><span data-stu-id="69b25-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="69b25-109">Özellikleri, verilerin görüntülendiği varsayılan bir stil oluşturmak için ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b25-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="69b25-110">Bu temelden, belirli tabloların çalışma zamanında görüntülenme şeklini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b25-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="69b25-111">Son olarak, veri kılavuzunda görüntülenecek sütunları ve gösterilen renkleri ve diğer biçimlendirmeleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b25-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="69b25-112">Bir veri kılavuzunu biçimlendirirken ilk adım olarak, <xref:System.Windows.Forms.DataGrid> kendi özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b25-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="69b25-113">Bu renk ve biçim seçimleri, daha sonra görünen veri tablolarına ve sütunlara göre değişiklik yapabileceğiniz bir temel oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69b25-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="69b25-114">DataGrid denetimi için varsayılan bir stil oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="69b25-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="69b25-115">Aşağıdaki özellikleri uygun şekilde ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="69b25-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="69b25-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="69b25-116">Property</span></span>|<span data-ttu-id="69b25-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69b25-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="69b25-118"><xref:System.Windows.Forms.DataGrid.BackColor%2A> Özelliği, kılavuzun çift sayılı satırlarının rengini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="69b25-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="69b25-119"><xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> Özelliği farklı bir renge ayarladığınızda, diğer her satır bu yeni renge ayarlanır (satır 1, 3, 5, vb.).</span><span class="sxs-lookup"><span data-stu-id="69b25-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="69b25-120">Kılavuzun çift sayılı satırlarının arka plan rengi (satırlar 0, 2, 4, 6, vb.).</span><span class="sxs-lookup"><span data-stu-id="69b25-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="69b25-121">Ve özellikleri kılavuzdaki satırların rengini belirler, <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özelliği, yalnızca kılavuz en alta kaydırıldığında görünen satır olmayan alanın rengini belirler veya yalnızca birkaç satır dahil edilir. <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> <xref:System.Windows.Forms.DataGrid.BackColor%2A> kılavuz.</span><span class="sxs-lookup"><span data-stu-id="69b25-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="69b25-122">Stilin kenarlık stili, <xref:System.Windows.Forms.BorderStyle> numaralandırma değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="69b25-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="69b25-123">Kılavuzun hemen üstünde görünen kılavuzun pencere açıklamalı arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="69b25-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="69b25-124">Kılavuzun üst kısmındaki başlık yazı tipi.</span><span class="sxs-lookup"><span data-stu-id="69b25-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="69b25-125">Kılavuzun pencere açıklamalı arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="69b25-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="69b25-126">Kılavuzdaki metni göstermek için kullanılan yazı tipi.</span><span class="sxs-lookup"><span data-stu-id="69b25-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="69b25-127">Veri kılavuzu satırlarındaki veriler tarafından gösterilecek yazı tipi rengi.</span><span class="sxs-lookup"><span data-stu-id="69b25-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="69b25-128">Veri kılavuzunun kılavuz çizgilerinin rengi.</span><span class="sxs-lookup"><span data-stu-id="69b25-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="69b25-129"><xref:System.Windows.Forms.DataGridLineStyle> Numaralandırma değerlerinden biri olan kılavuzun hücrelerini ayıran çizgilerin stili.</span><span class="sxs-lookup"><span data-stu-id="69b25-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="69b25-130">Satır ve sütun üst bilgilerinin arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="69b25-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="69b25-131">Sütun başlıkları için kullanılan yazı tipi.</span><span class="sxs-lookup"><span data-stu-id="69b25-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="69b25-132">Kılavuzun sütun üstbilgilerinin, sütun üst bilgisi metni ve artı/eksi glifleri (birden çok ilişkili tablo görüntülenirken satırları genişletmek için) dahil ön plan rengi.</span><span class="sxs-lookup"><span data-stu-id="69b25-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="69b25-133">Veri kılavuzundaki tüm bağlantıların, alt tablolara bağlantılar, ilişki adı vb. gibi tüm bağlantıların metin rengi.</span><span class="sxs-lookup"><span data-stu-id="69b25-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="69b25-134">Alt tabloda, bu, üst satırların arka plan rengidir.</span><span class="sxs-lookup"><span data-stu-id="69b25-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="69b25-135">Alt tabloda, bu, üst satırların ön plan rengidir.</span><span class="sxs-lookup"><span data-stu-id="69b25-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="69b25-136">Tablo ve sütun adlarının, <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> numaralandırma yoluyla üst satırda görüntülenip görüntülenmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="69b25-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="69b25-137">Kılavuzdaki sütunların varsayılan genişliği (piksel cinsinden).</span><span class="sxs-lookup"><span data-stu-id="69b25-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="69b25-138"><xref:System.Windows.Forms.DataGrid.DataSource%2A> Ve <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> özelliklerini sıfırlamadan önce bu özelliği ayarlayın (Ayrıca, ya da yöntemi aracılığıyla) ya da özelliğin hiçbir etkisi olmayacaktır. <xref:System.Windows.Forms.DataGrid.DataMember%2A></span><span class="sxs-lookup"><span data-stu-id="69b25-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="69b25-139">Özellik 0 ' dan küçük bir değere ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="69b25-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="69b25-140">Kılavuzdaki satırların satır yüksekliği (piksel cinsinden).</span><span class="sxs-lookup"><span data-stu-id="69b25-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="69b25-141"><xref:System.Windows.Forms.DataGrid.DataSource%2A> Ve <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> özelliklerini sıfırlamadan önce bu özelliği ayarlayın (Ayrıca, ya da yöntemi aracılığıyla) ya da özelliğin hiçbir etkisi olmayacaktır. <xref:System.Windows.Forms.DataGrid.DataMember%2A></span><span class="sxs-lookup"><span data-stu-id="69b25-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="69b25-142">Özellik 0 ' dan küçük bir değere ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="69b25-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="69b25-143">Kılavuzun satır üst bilgilerinin genişliği.</span><span class="sxs-lookup"><span data-stu-id="69b25-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="69b25-144">Bir satır veya hücre seçildiğinde, bu arka plan rengidir.</span><span class="sxs-lookup"><span data-stu-id="69b25-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="69b25-145">Bir satır veya hücre seçildiğinde bu, ön plan rengidir.</span><span class="sxs-lookup"><span data-stu-id="69b25-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="69b25-146">Denetimlerin renklerini özelleştirirken, kötü renk seçimi (örneğin, kırmızı ve yeşil) nedeniyle denetimi erişilemez hale getirmek mümkün olduğunca göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="69b25-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="69b25-147">Bu sorundan kaçınmak için **sistem renkleri** paletindeki kullanılabilir renkleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="69b25-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="69b25-148">Aşağıdaki yordamlarda formunuzun bir veri tablosuna yönelik bir <xref:System.Windows.Forms.DataGrid> denetim olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="69b25-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="69b25-149">Daha fazla bilgi için, bkz. [Windows Forms DataGrid denetimini bir veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="69b25-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="69b25-150">Bir veri tablosunun tablo ve sütun stilini programlı bir şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="69b25-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="69b25-151">Yeni bir tablo stili oluşturun ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="69b25-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="69b25-152">Sütun stili oluşturun ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="69b25-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="69b25-153">Sütun stilini tablo stilinin sütun stilleri koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="69b25-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="69b25-154">Tablo stilini veri kılavuzunun tablo stilleri koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="69b25-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="69b25-155">Aşağıdaki örnekte, yeni <xref:System.Windows.Forms.DataGridTableStyle> bir örneğini oluşturun ve <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="69b25-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="69b25-156">Bir **GridColumnStyle** 'ın yeni bir örneğini oluşturun ve onun **MappingName** değerini (ve diğer düzen ve görüntü özelliklerini) ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="69b25-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="69b25-157">Oluşturmak istediğiniz her sütun stili için 2 ile 6 arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="69b25-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="69b25-158">Aşağıdaki örnekte, bir <xref:System.Windows.Forms.DataGridTextBoxColumn> ad sütununda görüntülenecek şekilde nasıl oluşturulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="69b25-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="69b25-159">Ayrıca, sütun stilini tablo stilinin öğesine <xref:System.Windows.Forms.GridColumnStylesCollection> ekler ve tablo stilini <xref:System.Windows.Forms.GridTableStylesCollection> veri kılavuzunun içine eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="69b25-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69b25-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69b25-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="69b25-161">Nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme</span><span class="sxs-lookup"><span data-stu-id="69b25-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="69b25-162">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="69b25-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)

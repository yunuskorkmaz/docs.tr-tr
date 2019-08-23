---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: 665a1af990aaf615c763c1c2eae508024d9de5c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917821"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="4af6f-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="4af6f-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="4af6f-103">Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="4af6f-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="4af6f-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4af6f-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

 <span data-ttu-id="4af6f-105">Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi, bir veri kaynağından bilgileri görüntüleyecek şekilde özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4af6f-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="4af6f-106">Denetimi tasarım zamanında, <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini ayarlayarak veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini çağırarak çalışma zamanında bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="4af6f-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="4af6f-107">Çeşitli veri kaynaklarından veri görüntüleyebilirsiniz, ancak en genel kaynaklar veri kümeleri ve veri görünümleridir.</span><span class="sxs-lookup"><span data-stu-id="4af6f-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>

 <span data-ttu-id="4af6f-108">Veri kaynağı tasarım zamanında kullanılabiliyorsa — Örneğin, form bir veri kümesinin veya bir veri görünümünün örneğini içeriyorsa — tasarım zamanında Kılavuzu veri kaynağına bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4af6f-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="4af6f-109">Ardından, verilerin kılavuzda nasıl görüneceğine ilişkin önizleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4af6f-109">You can then preview what the data will look like in the grid.</span></span>

 <span data-ttu-id="4af6f-110">Ayrıca, çalışma zamanında Kılavuzu programlı bir şekilde bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4af6f-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="4af6f-111">Bu, çalışma zamanında aldığınız bilgilere göre bir veri kaynağı ayarlamak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4af6f-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="4af6f-112">Örneğin, uygulama, kullanıcının görüntülenecek tablonun adını belirtmesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4af6f-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="4af6f-113">Veri kaynağının tasarım zamanında bulunmadığı durumlarda da gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4af6f-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="4af6f-114">Bu, diziler, koleksiyonlar, türsüz veri kümeleri ve veri okuyucuları gibi veri kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4af6f-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>

 <span data-ttu-id="4af6f-115">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGrid> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4af6f-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="4af6f-116">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4af6f-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="4af6f-117">Visual Studio 2005 ' de, <xref:System.Windows.Forms.DataGrid> denetim **araç kutusunda** varsayılan olarak değildir.</span><span class="sxs-lookup"><span data-stu-id="4af6f-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="4af6f-118">Ekleme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Araç kutusuna](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4af6f-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="4af6f-119">Ayrıca, Visual Studio 2005 ' de tasarım zamanı veri bağlama için **veri kaynakları** penceresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4af6f-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="4af6f-120">Daha fazla bilgi için bkz. [Visual Studio 'da verileri denetimlere bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="4af6f-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="4af6f-121">DataGrid denetimini tasarımcıda tek bir tabloya veri bağlamak için</span><span class="sxs-lookup"><span data-stu-id="4af6f-121">To data-bind the DataGrid control to a single table in the designer</span></span>

1. <span data-ttu-id="4af6f-122">Denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini bağlamak istediğiniz veri öğelerini içeren nesne olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4af6f-122">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="4af6f-123">Veri kaynağı bir veri kümesi ise, <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliği bağlanacak tablonun adına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4af6f-123">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>

3. <span data-ttu-id="4af6f-124">Veri kaynağı bir veri kümesi veya veri kümesi tablosuna dayalı bir veri görünüminiyorsa, veri kümesini dolduracak şekilde forma kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4af6f-124">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>

     <span data-ttu-id="4af6f-125">Kullandığınız tam kod, veri kümesinin veri alılabileceği yere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4af6f-125">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="4af6f-126">Veri kümesi doğrudan bir veritabanından doldurulursa, genellikle bir veri bağdaştırıcısının `Fill` yöntemini, aşağıdaki kod örneğinde olduğu gibi, adlı `DsCategories1`bir veri kümesini dolduran şekilde çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4af6f-126">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. <span data-ttu-id="4af6f-127">Seçim Kılavuza uygun tablo stillerini ve sütun stillerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4af6f-127">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>

     <span data-ttu-id="4af6f-128">Tablo stili yoksa, tabloyu görürsünüz, ancak en az biçimlendirme ile ve tüm sütunları görünür olur.</span><span class="sxs-lookup"><span data-stu-id="4af6f-128">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="4af6f-129">DataGrid denetimini tasarımcıda veri kümesindeki birden çok tabloya bağlamak için</span><span class="sxs-lookup"><span data-stu-id="4af6f-129">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>

1. <span data-ttu-id="4af6f-130">Denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini bağlamak istediğiniz veri öğelerini içeren nesne olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4af6f-130">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="4af6f-131">Veri kümesi ilgili tabloları içeriyorsa (yani bir ilişki nesnesi içeriyorsa), <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliği üst tablonun adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4af6f-131">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>

3. <span data-ttu-id="4af6f-132">Veri kümesini dolduracak kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="4af6f-132">Write code to fill the dataset.</span></span>

## <a name="see-also"></a><span data-ttu-id="4af6f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4af6f-133">See also</span></span>

- [<span data-ttu-id="4af6f-134">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4af6f-134">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="4af6f-135">Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="4af6f-135">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="4af6f-136">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="4af6f-136">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="4af6f-137">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="4af6f-137">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="4af6f-138">Visual Studio'da verilere erişime</span><span class="sxs-lookup"><span data-stu-id="4af6f-138">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)

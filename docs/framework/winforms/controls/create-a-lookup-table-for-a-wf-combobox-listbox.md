---
title: ComboBox, ListBox veya CheckedListBox denetimi için arama tablosu oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737375"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="beb90-102">Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="beb90-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="beb90-103">Bazen, verileri bir Windows form üzerinde Kullanıcı dostu bir biçimde göstermek yararlıdır, ancak verileri programınıza daha anlamlı bir biçimde depolar.</span><span class="sxs-lookup"><span data-stu-id="beb90-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="beb90-104">Örneğin, yiyecek için bir sipariş formu, menü öğelerini bir liste kutusunda ada göre görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="beb90-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="beb90-105">Ancak, siparişi kaydeden veri tablosu, yiyecek 'yi temsil eden benzersiz KIMLIK numaralarını içerir.</span><span class="sxs-lookup"><span data-stu-id="beb90-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="beb90-106">Aşağıdaki tablolarda, yiyecek için sipariş formu verilerinin nasıl depolandığı ve görüntüleneceği bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="beb90-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="beb90-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="beb90-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="beb90-108">Sipariş</span><span class="sxs-lookup"><span data-stu-id="beb90-108">OrderID</span></span>|<span data-ttu-id="beb90-109">ID</span><span class="sxs-lookup"><span data-stu-id="beb90-109">ItemID</span></span>|<span data-ttu-id="beb90-110">Miktar</span><span class="sxs-lookup"><span data-stu-id="beb90-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="beb90-111">4085</span><span class="sxs-lookup"><span data-stu-id="beb90-111">4085</span></span>|<span data-ttu-id="beb90-112">12</span><span class="sxs-lookup"><span data-stu-id="beb90-112">12</span></span>|<span data-ttu-id="beb90-113">1\.</span><span class="sxs-lookup"><span data-stu-id="beb90-113">1</span></span>|  
|<span data-ttu-id="beb90-114">4086</span><span class="sxs-lookup"><span data-stu-id="beb90-114">4086</span></span>|<span data-ttu-id="beb90-115">13</span><span class="sxs-lookup"><span data-stu-id="beb90-115">13</span></span>|<span data-ttu-id="beb90-116">3</span><span class="sxs-lookup"><span data-stu-id="beb90-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="beb90-117">ItemTable</span><span class="sxs-lookup"><span data-stu-id="beb90-117">ItemTable</span></span>  
  
|<span data-ttu-id="beb90-118">Kimlik</span><span class="sxs-lookup"><span data-stu-id="beb90-118">ID</span></span>|<span data-ttu-id="beb90-119">Ad</span><span class="sxs-lookup"><span data-stu-id="beb90-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="beb90-120">12</span><span class="sxs-lookup"><span data-stu-id="beb90-120">12</span></span>|<span data-ttu-id="beb90-121">Patates</span><span class="sxs-lookup"><span data-stu-id="beb90-121">Potato</span></span>|  
|<span data-ttu-id="beb90-122">13</span><span class="sxs-lookup"><span data-stu-id="beb90-122">13</span></span>|<span data-ttu-id="beb90-123">Tavuk</span><span class="sxs-lookup"><span data-stu-id="beb90-123">Chicken</span></span>|  
  
 <span data-ttu-id="beb90-124">Bu senaryoda, **OrderDetailsTable**adlı bir tablo, görüntüleme ve kaydetme konusunda endişe ettiğiniz gerçek bilgileri depolar.</span><span class="sxs-lookup"><span data-stu-id="beb90-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="beb90-125">Ancak, alan kazanmak için oldukça şifreli bir biçimde olur.</span><span class="sxs-lookup"><span data-stu-id="beb90-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="beb90-126">Diğer tablo, **ItemTable**, yalnızca hangi kimlik numarasının hangi yiyecek adına eşdeğer olduğu ve gerçek yiyecek siparişleriyle ilgili hiçbir şey hakkındaki görünümle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="beb90-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="beb90-127">**ItemTable** , üç özellik aracılığıyla <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>veya <xref:System.Windows.Forms.CheckedListBox> denetimine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="beb90-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="beb90-128">`DataSource` özelliği bu tablonun adını içerir.</span><span class="sxs-lookup"><span data-stu-id="beb90-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="beb90-129">`DisplayMember` özelliği, denetimde göstermek istediğiniz tablonun veri sütununu içerir (yiyecek adı).</span><span class="sxs-lookup"><span data-stu-id="beb90-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="beb90-130">`ValueMember` özelliği, depolanan bilgiler (KIMLIK numarası) ile ilgili tablonun veri sütununu içerir.</span><span class="sxs-lookup"><span data-stu-id="beb90-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="beb90-131">**OrderDetailsTable** , <xref:System.Windows.Forms.Control.DataBindings%2A> özelliğinden erişilen bağlama koleksiyonuyla denetime bağlanır.</span><span class="sxs-lookup"><span data-stu-id="beb90-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="beb90-132">Koleksiyona bir bağlama nesnesi eklediğinizde, bir denetim özelliğini bir veri kaynağındaki belirli bir veri üyesine (KIMLIK numaraları sütunu) bağladığınızda ( **OrderDetailsTable**).</span><span class="sxs-lookup"><span data-stu-id="beb90-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="beb90-133">Denetimde bir seçim yapıldığında bu tablo, form girişinin kaydedildiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="beb90-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="beb90-134">Arama tablosu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="beb90-134">To create a lookup table</span></span>  
  
1. <span data-ttu-id="beb90-135">Forma <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>veya <xref:System.Windows.Forms.CheckedListBox> denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="beb90-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2. <span data-ttu-id="beb90-136">Veri kaynağınıza bağlanın.</span><span class="sxs-lookup"><span data-stu-id="beb90-136">Connect to your data source.</span></span>  
  
3. <span data-ttu-id="beb90-137">İki tablo arasında bir veri ilişkisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="beb90-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="beb90-138">Bkz. [DataRelation nesnelerine giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="beb90-138">See [Introduction to DataRelation Objects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span></span>  
  
4. <span data-ttu-id="beb90-139">Aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="beb90-139">Set the following properties.</span></span> <span data-ttu-id="beb90-140">Bunlar kodda veya tasarımcıda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="beb90-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="beb90-141">Özellik</span><span class="sxs-lookup"><span data-stu-id="beb90-141">Property</span></span>|<span data-ttu-id="beb90-142">Ayar</span><span class="sxs-lookup"><span data-stu-id="beb90-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="beb90-143">Hangi KIMLIK numarasının hangi öğe ile eşdeğer olduğunu belirten bilgi içeren tablo.</span><span class="sxs-lookup"><span data-stu-id="beb90-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="beb90-144">Önceki senaryoda bu `ItemTable`.</span><span class="sxs-lookup"><span data-stu-id="beb90-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="beb90-145">Denetimde görüntülenmesini istediğiniz veri kaynağı tablosunun sütunu.</span><span class="sxs-lookup"><span data-stu-id="beb90-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="beb90-146">Önceki senaryoda bu `"Name"` (kod içinde ayarlamak için tırnak işaretleri kullanın).</span><span class="sxs-lookup"><span data-stu-id="beb90-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="beb90-147">Depolanan bilgileri içeren veri kaynağı tablosunun sütunu.</span><span class="sxs-lookup"><span data-stu-id="beb90-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="beb90-148">Önceki senaryoda bu `"ID"` (kod içinde ayarlamak için tırnak işaretleri kullanın).</span><span class="sxs-lookup"><span data-stu-id="beb90-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5. <span data-ttu-id="beb90-149">Yordamda, denetimin <xref:System.Windows.Forms.ListControl.SelectedValue%2A> özelliğini form girişini kaydeden tabloya bağlamak için <xref:System.Windows.Forms.ControlBindingsCollection> sınıfının <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="beb90-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="beb90-150">Ayrıca, **Özellikler** penceresindeki denetimin <xref:System.Windows.Forms.Control.DataBindings%2A> özelliğine erişerek bunu kod yerine tasarımcıda de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beb90-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="beb90-151">Önceki senaryoda bu `OrderDetailsTable`ve sütun `"ItemID"`.</span><span class="sxs-lookup"><span data-stu-id="beb90-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="beb90-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="beb90-152">See also</span></span>

- [<span data-ttu-id="beb90-153">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="beb90-153">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="beb90-154">ListBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="beb90-154">ListBox Control Overview</span></span>](listbox-control-overview-windows-forms.md)
- [<span data-ttu-id="beb90-155">ComboBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="beb90-155">ComboBox Control Overview</span></span>](combobox-control-overview-windows-forms.md)
- [<span data-ttu-id="beb90-156">CheckedListBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="beb90-156">CheckedListBox Control Overview</span></span>](checkedlistbox-control-overview-windows-forms.md)
- [<span data-ttu-id="beb90-157">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="beb90-157">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)

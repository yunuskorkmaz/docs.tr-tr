---
title: 'Nasıl yapılır: ComboBox, ListBox veya CheckedListBox denetiminde bir Windows Forms için arama tablosu oluşturma'
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
ms.openlocfilehash: eaa92c2b95d8dd8578b46e44a948127e201bb351
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724633"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="09fa2-102">Nasıl yapılır: ComboBox, ListBox veya CheckedListBox denetiminde bir Windows Forms için arama tablosu oluşturma</span><span class="sxs-lookup"><span data-stu-id="09fa2-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="09fa2-103">Bazen bir Windows Form üzerinde kolay bir biçimde verileri görüntüler ancak programınız için daha anlamlı bir biçimde verileri depolamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="09fa2-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="09fa2-104">Örneğin, bir sipariş formu Gıda için bir liste kutusunda ad olarak menü öğeleri görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="09fa2-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="09fa2-105">Ancak, siparişin kaydı veri tablosu Gıda temsil eden benzersiz kimlik numaraları içerecektir.</span><span class="sxs-lookup"><span data-stu-id="09fa2-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="09fa2-106">Aşağıdaki tablolarda, depolamak ve yemek siparişi biçimli verileri görüntülemek nasıl bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="09fa2-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="09fa2-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="09fa2-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="09fa2-108">Sipariş Kimliği</span><span class="sxs-lookup"><span data-stu-id="09fa2-108">OrderID</span></span>|<span data-ttu-id="09fa2-109">öğe kimliği</span><span class="sxs-lookup"><span data-stu-id="09fa2-109">ItemID</span></span>|<span data-ttu-id="09fa2-110">Miktar</span><span class="sxs-lookup"><span data-stu-id="09fa2-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="09fa2-111">4085</span><span class="sxs-lookup"><span data-stu-id="09fa2-111">4085</span></span>|<span data-ttu-id="09fa2-112">12</span><span class="sxs-lookup"><span data-stu-id="09fa2-112">12</span></span>|<span data-ttu-id="09fa2-113">1.</span><span class="sxs-lookup"><span data-stu-id="09fa2-113">1</span></span>|  
|<span data-ttu-id="09fa2-114">4086</span><span class="sxs-lookup"><span data-stu-id="09fa2-114">4086</span></span>|<span data-ttu-id="09fa2-115">13</span><span class="sxs-lookup"><span data-stu-id="09fa2-115">13</span></span>|<span data-ttu-id="09fa2-116">3</span><span class="sxs-lookup"><span data-stu-id="09fa2-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="09fa2-117">ItemTable</span><span class="sxs-lookup"><span data-stu-id="09fa2-117">ItemTable</span></span>  
  
|<span data-ttu-id="09fa2-118">Kimlik</span><span class="sxs-lookup"><span data-stu-id="09fa2-118">ID</span></span>|<span data-ttu-id="09fa2-119">Ad</span><span class="sxs-lookup"><span data-stu-id="09fa2-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="09fa2-120">12</span><span class="sxs-lookup"><span data-stu-id="09fa2-120">12</span></span>|<span data-ttu-id="09fa2-121">Patates</span><span class="sxs-lookup"><span data-stu-id="09fa2-121">Potato</span></span>|  
|<span data-ttu-id="09fa2-122">13</span><span class="sxs-lookup"><span data-stu-id="09fa2-122">13</span></span>|<span data-ttu-id="09fa2-123">Tavuk</span><span class="sxs-lookup"><span data-stu-id="09fa2-123">Chicken</span></span>|  
  
 <span data-ttu-id="09fa2-124">Bu senaryoda, bir tablo **OrderDetailsTable**, kaydetme ve görüntüleme ile ilgili gerçek bilgileri depolar.</span><span class="sxs-lookup"><span data-stu-id="09fa2-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="09fa2-125">Ancak, alandan kazanmak için bunu oldukça şifreli biçimde yapar.</span><span class="sxs-lookup"><span data-stu-id="09fa2-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="09fa2-126">Diğer bir tabloda **ItemTable**, hangi kimliği hakkında sayıdır hangi Gıda adına ve gerçek Gıda siparişler hakkında hiçbir şey eşdeğer yalnızca görünüm güvenlikle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="09fa2-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="09fa2-127">**ItemTable** bağlı <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, veya <xref:System.Windows.Forms.CheckedListBox> üç özellikleri aracılığıyla denetimi.</span><span class="sxs-lookup"><span data-stu-id="09fa2-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="09fa2-128">`DataSource` Özelliği bu tablonun adını içerir.</span><span class="sxs-lookup"><span data-stu-id="09fa2-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="09fa2-129">`DisplayMember` Özelliği, bu tablonun (Gıda adı) denetiminde görüntülemek istediğiniz veri sütunu içerir.</span><span class="sxs-lookup"><span data-stu-id="09fa2-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="09fa2-130">`ValueMember` Özelliği, bu tablonun saklı bilgileri (kimlik numarası) ile veri sütunu içerir.</span><span class="sxs-lookup"><span data-stu-id="09fa2-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="09fa2-131">**OrderDetailsTable** aracılığıyla erişilen kendi bağlamaları koleksiyona göre denetimine bağlı <xref:System.Windows.Forms.Control.DataBindings%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="09fa2-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="09fa2-132">Koleksiyona bağlama nesnesi eklediğinizde, bir denetim özelliği bir veri kaynağındaki belirli veri üyesini (kimliği sayı sütununun) bağlandığınız ( **OrderDetailsTable**).</span><span class="sxs-lookup"><span data-stu-id="09fa2-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="09fa2-133">Denetimdeki seçim yapıldığında, bu form girişi kaydedildiği tablodur.</span><span class="sxs-lookup"><span data-stu-id="09fa2-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="09fa2-134">Arama tablosu oluşturma</span><span class="sxs-lookup"><span data-stu-id="09fa2-134">To create a lookup table</span></span>  
  
1.  <span data-ttu-id="09fa2-135">Ekleme bir <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, veya <xref:System.Windows.Forms.CheckedListBox> forma.</span><span class="sxs-lookup"><span data-stu-id="09fa2-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2.  <span data-ttu-id="09fa2-136">Veri kaynağınıza bağlayın.</span><span class="sxs-lookup"><span data-stu-id="09fa2-136">Connect to your data source.</span></span>  
  
3.  <span data-ttu-id="09fa2-137">İki tablo arasında bir veri ilişkisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="09fa2-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="09fa2-138">Bkz: [DataRelation nesnelerine giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="09fa2-138">See [Introduction to DataRelation Objects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span></span>  
  
4.  <span data-ttu-id="09fa2-139">Aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="09fa2-139">Set the following properties.</span></span> <span data-ttu-id="09fa2-140">Bunlar, kod veya tasarımcı ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="09fa2-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="09fa2-141">Özellik</span><span class="sxs-lookup"><span data-stu-id="09fa2-141">Property</span></span>|<span data-ttu-id="09fa2-142">Ayar</span><span class="sxs-lookup"><span data-stu-id="09fa2-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="09fa2-143">Hangi kimliği numarasını hangi öğesine eşdeğerdir bilgilerini içeren tablo.</span><span class="sxs-lookup"><span data-stu-id="09fa2-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="09fa2-144">Önceki senaryoda budur `ItemTable`.</span><span class="sxs-lookup"><span data-stu-id="09fa2-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="09fa2-145">Denetiminde görüntülemek istediğiniz veri kaynağı tablosu içeren sütun.</span><span class="sxs-lookup"><span data-stu-id="09fa2-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="09fa2-146">Önceki senaryoda budur `"Name"` (kodda ayarlamak için tırnak işaretleri kullanın).</span><span class="sxs-lookup"><span data-stu-id="09fa2-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="09fa2-147">Depolanan bilgiler içeren veri kaynağı tablosu içeren sütun.</span><span class="sxs-lookup"><span data-stu-id="09fa2-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="09fa2-148">Önceki senaryoda budur `"ID"` (kodda ayarlamak için tırnak işaretleri kullanın).</span><span class="sxs-lookup"><span data-stu-id="09fa2-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5.  <span data-ttu-id="09fa2-149">Bir yordamda çağrı <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> yöntemi <xref:System.Windows.Forms.ControlBindingsCollection> denetimin bağlamak için sınıf <xref:System.Windows.Forms.ListControl.SelectedValue%2A> özelliğini form girişi kayıt tablosu.</span><span class="sxs-lookup"><span data-stu-id="09fa2-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="09fa2-150">Ayrıca, kodda yerine tasarımcısında denetimin erişerek bunu yapabilirsiniz <xref:System.Windows.Forms.Control.DataBindings%2A> özelliğinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="09fa2-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="09fa2-151">Önceki senaryoda budur `OrderDetailsTable`, ve sütun `"ItemID"`.</span><span class="sxs-lookup"><span data-stu-id="09fa2-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="09fa2-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09fa2-152">See also</span></span>
- [<span data-ttu-id="09fa2-153">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="09fa2-153">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="09fa2-154">ListBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="09fa2-154">ListBox Control Overview</span></span>](listbox-control-overview-windows-forms.md)
- [<span data-ttu-id="09fa2-155">ComboBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="09fa2-155">ComboBox Control Overview</span></span>](combobox-control-overview-windows-forms.md)
- [<span data-ttu-id="09fa2-156">CheckedListBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="09fa2-156">CheckedListBox Control Overview</span></span>](checkedlistbox-control-overview-windows-forms.md)
- [<span data-ttu-id="09fa2-157">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="09fa2-157">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)

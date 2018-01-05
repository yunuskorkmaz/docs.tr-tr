---
title: "Nasıl yapılır: Windows Formları BindingSource Bileşeniyle Arama Tablosu Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 324e4ed290b98d2268dd82fa55b81deaeb849770
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="4f827-102">Nasıl yapılır: Windows Formları BindingSource Bileşeniyle Arama Tablosu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4f827-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="4f827-103">Arama tablosu ilişkili bir tabloda kayıttan alınan verileri görüntüleyen bir sütun olan verilerin bir tablosu verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f827-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="4f827-104">Aşağıdaki yordamlarda bulunan bir <xref:System.Windows.Forms.ComboBox> denetimi üst alt tablosuna yabancı anahtar ilişkisi alanıyla görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f827-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="4f827-105">Bu iki tablo ve bu ilişkiyi görselleştirmenize yardımcı olmak için üst ve alt tablo örneği aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="4f827-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="4f827-106">CustomersTable (üst tablo)</span><span class="sxs-lookup"><span data-stu-id="4f827-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="4f827-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="4f827-107">CustomerID</span></span>|<span data-ttu-id="4f827-108">customerName</span><span class="sxs-lookup"><span data-stu-id="4f827-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="4f827-109">712</span><span class="sxs-lookup"><span data-stu-id="4f827-109">712</span></span>|<span data-ttu-id="4f827-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="4f827-110">Paul Koch</span></span>|  
|<span data-ttu-id="4f827-111">713</span><span class="sxs-lookup"><span data-stu-id="4f827-111">713</span></span>|<span data-ttu-id="4f827-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="4f827-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="4f827-113">OrdersTable (alt tablo)</span><span class="sxs-lookup"><span data-stu-id="4f827-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="4f827-114">OrderID</span><span class="sxs-lookup"><span data-stu-id="4f827-114">OrderID</span></span>|<span data-ttu-id="4f827-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="4f827-115">OrderDate</span></span>|<span data-ttu-id="4f827-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="4f827-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="4f827-117">903</span><span class="sxs-lookup"><span data-stu-id="4f827-117">903</span></span>|<span data-ttu-id="4f827-118">12 Şubat 2004</span><span class="sxs-lookup"><span data-stu-id="4f827-118">February 12, 2004</span></span>|<span data-ttu-id="4f827-119">712</span><span class="sxs-lookup"><span data-stu-id="4f827-119">712</span></span>|  
|<span data-ttu-id="4f827-120">904</span><span class="sxs-lookup"><span data-stu-id="4f827-120">904</span></span>|<span data-ttu-id="4f827-121">13 Şubat 2004</span><span class="sxs-lookup"><span data-stu-id="4f827-121">February 13, 2004</span></span>|<span data-ttu-id="4f827-122">713</span><span class="sxs-lookup"><span data-stu-id="4f827-122">713</span></span>|  
  
 <span data-ttu-id="4f827-123">Bu senaryoda, bir tablo, CustomersTable, görüntülemek ve kaydetmek istediğiniz gerçek bilgileri depolar.</span><span class="sxs-lookup"><span data-stu-id="4f827-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="4f827-124">Ancak alanı kaydetmek için tablonun netlik ekleyen verileri bırakır.</span><span class="sxs-lookup"><span data-stu-id="4f827-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="4f827-125">Diğer tablo, OrdersTable, hangi müşteri numarası hangi sipariş tarihi ve Sipariş Kimliği'eşdeğerdir yalnızca görünüm ilgili bilgiler de içerir</span><span class="sxs-lookup"><span data-stu-id="4f827-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="4f827-126">Hiçbir Bahsetme müşterilerin adlarını yoktur.</span><span class="sxs-lookup"><span data-stu-id="4f827-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="4f827-127">Dört önemli özellikleri ayarlandığında [ComboBox denetimi](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) arama tablosu oluşturma için denetimi.</span><span class="sxs-lookup"><span data-stu-id="4f827-127">Four important properties are set on the [ComboBox Control](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
-   <span data-ttu-id="4f827-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> Özelliği tablo adını içerir.</span><span class="sxs-lookup"><span data-stu-id="4f827-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
-   <span data-ttu-id="4f827-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> Özelliği (Müşteri'nin adı) kontrol metni için görüntülemek istediğiniz bu tablonun veri sütunu içerir.</span><span class="sxs-lookup"><span data-stu-id="4f827-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
-   <span data-ttu-id="4f827-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> Özelliği (kimlik numarası üst tablodan) depolanmış bilgilerle bu tablonun veri sütunu içerir.</span><span class="sxs-lookup"><span data-stu-id="4f827-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
-   <span data-ttu-id="4f827-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> Özelliği, bağlı alt tablo için arama değeri sağlar <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f827-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="4f827-132">Aşağıdaki yordamlar bir arama tablosu formunuzu düzenleme ve denetimlere veri bağlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4f827-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="4f827-133">Başarıyla yordamları tamamlamak için daha önce belirtildiği gibi bir yabancı anahtar ilişkisine sahip üst ve alt tablolar ile bir veri kaynağı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f827-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="4f827-134">Kullanıcı arabirimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4f827-134">To create the user interface</span></span>  
  
1.  <span data-ttu-id="4f827-135">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.ComboBox> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="4f827-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="4f827-136">Bu denetim, üst tablodan sütun görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4f827-136">This control will display the column from parent table.</span></span>  
  
2.  <span data-ttu-id="4f827-137">Alt tablosundan ayrıntılarını görüntülemek için diğer denetimleri sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="4f827-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="4f827-138">Tablosunda veri biçimi, seçtiğiniz hangi denetimlerin belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f827-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="4f827-139">Daha fazla bilgi için bkz: [işleve göre Windows Forms denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="4f827-139">For more information, see [Windows Forms Controls by Function](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span></span>  
  
3.  <span data-ttu-id="4f827-140">Sürükleme bir <xref:System.Windows.Forms.BindingNavigator> denetim forma; bu alt tablodaki verileri gezinmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4f827-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="4f827-141">Veri bağlanmak ve denetimlere bağlama</span><span class="sxs-lookup"><span data-stu-id="4f827-141">To connect to the data and bind it to controls</span></span>  
  
1.  <span data-ttu-id="4f827-142">Seçin <xref:System.Windows.Forms.ComboBox> akıllı görev iletişim kutusu görüntülemek için akıllı görev karakter'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4f827-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2.  <span data-ttu-id="4f827-143">Seçin **kullanım verileri bağlı öğeleri**.</span><span class="sxs-lookup"><span data-stu-id="4f827-143">Select **Use data bound items**.</span></span>  
  
3.  <span data-ttu-id="4f827-144">Yanındaki oka tıklayın **veri kaynağı** açılan kutusu.</span><span class="sxs-lookup"><span data-stu-id="4f827-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="4f827-145">Bir veri kaynağı, daha önce proje veya form için yapılandırılmışsa, görünür; Aksi takdirde, (Bu örnekte Northwind örnek veritabanı müşteriler ve Siparişler tablolarını kullanır ve bunlara parantez içine başvuru yapan) aşağıdaki adımları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="4f827-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1.  <span data-ttu-id="4f827-146">Tıklatın **proje veri kaynağı Ekle** veri bağlanmak ve bir veri kaynağı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4f827-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2.  <span data-ttu-id="4f827-147">Üzerinde **veri kaynağı Yapılandırma Sihirbazı** Karşılama sayfasında, tıklatın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="4f827-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="4f827-148">Seçin **veritabanı** üzerinde **bir veri kaynağı türü seç** sayfası.</span><span class="sxs-lookup"><span data-stu-id="4f827-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4.  <span data-ttu-id="4f827-149">Kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin **veri bağlantınızı** sayfası.</span><span class="sxs-lookup"><span data-stu-id="4f827-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="4f827-150">İstenen veri bağlantınızı kullanılabilir durumda değilse, seçin **yeni bağlantı** yeni bir veri bağlantısı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="4f827-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5.  <span data-ttu-id="4f827-151">Tıklatın **Evet, bağlantı kaydetme** uygulama yapılandırma dosyasında bağlantı dizesini kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="4f827-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6.  <span data-ttu-id="4f827-152">Uygulamanıza getirmek için veritabanı nesneleri seçin.</span><span class="sxs-lookup"><span data-stu-id="4f827-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="4f827-153">Bu durumda, bir üst tablo ve yabancı anahtar ilişkisi alt tabloda (örneğin, müşteriler ve siparişler) seçin.</span><span class="sxs-lookup"><span data-stu-id="4f827-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7.  <span data-ttu-id="4f827-154">İsterseniz varsayılan veri kümesi adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4f827-154">Replace the default dataset name if you want.</span></span>  
  
    8.  <span data-ttu-id="4f827-155">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4f827-155">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="4f827-156">İçinde **görüntü üye** açılan kutusunda görüntülenecek sütun adı (örneğin, ContactName) açılan kutusunda seçin.</span><span class="sxs-lookup"><span data-stu-id="4f827-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5.  <span data-ttu-id="4f827-157">İçinde **değer üyesi** açılan kutu, alt tabloda arama işlemi gerçekleştirmek için sütun (örneğin, CustomerID) seçin.</span><span class="sxs-lookup"><span data-stu-id="4f827-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6.  <span data-ttu-id="4f827-158">İçinde **seçili değer** açılır kutusunda, gitmek **proje veri kaynaklarını** ve üst ve alt tablolar içeren yeni oluşturduğunuz veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="4f827-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="4f827-159">Üst tablo (örneğin, siparişler.MüşteriNo) değeri üyesi olan alt tablo aynı özelliğini seçin.</span><span class="sxs-lookup"><span data-stu-id="4f827-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="4f827-160">Uygun <xref:System.Windows.Forms.BindingSource> , veri kümesi ve tablo bağdaştırıcısı bileşenleri oluşturulur ve forma eklenir.</span><span class="sxs-lookup"><span data-stu-id="4f827-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7.  <span data-ttu-id="4f827-161">Bağlama <xref:System.Windows.Forms.BindingNavigator> denetimini <xref:System.Windows.Forms.BindingSource> alt tablonun (örneğin, `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="4f827-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8.  <span data-ttu-id="4f827-162">Denetimleri dışında bağlamak <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.BindingNavigator> alt tablonun ayrıntıları alanlara denetiminden <xref:System.Windows.Forms.BindingSource> (örneğin, `OrdersBindingSource`) görüntülemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="4f827-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f827-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f827-163">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="4f827-164">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="4f827-164">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="4f827-165">ComboBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="4f827-165">ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)  
 [<span data-ttu-id="4f827-166">Visual Studio'da verilere denetimler bağlama</span><span class="sxs-lookup"><span data-stu-id="4f827-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

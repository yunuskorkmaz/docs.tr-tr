---
title: 'Nasıl yapılır: Windows Forms BindingSource Bileşeniyle Arama Tablosu Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 481774e9127531bb38df0cc71ac8e7eab76da695
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321906"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="962bb-102">Nasıl yapılır: Windows Forms BindingSource Bileşeniyle Arama Tablosu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="962bb-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="962bb-103">Arama tablosu kayıttan alınan ilişkili bir tabloda görüntüleyen bir sütun olan verilerin bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="962bb-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="962bb-104">Aşağıdaki yordamlarda, bir <xref:System.Windows.Forms.ComboBox> denetimi üst alt tablo için yabancı anahtar ilişkisi alanıyla görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="962bb-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="962bb-105">Bu iki tablo ve bu ilişkiyi görselleştirmenize yardımcı olmak için üst ve alt tablo örneği aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="962bb-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="962bb-106">CustomersTable (üst tablo)</span><span class="sxs-lookup"><span data-stu-id="962bb-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="962bb-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="962bb-107">CustomerID</span></span>|<span data-ttu-id="962bb-108">CustomerName</span><span class="sxs-lookup"><span data-stu-id="962bb-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="962bb-109">712</span><span class="sxs-lookup"><span data-stu-id="962bb-109">712</span></span>|<span data-ttu-id="962bb-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="962bb-110">Paul Koch</span></span>|  
|<span data-ttu-id="962bb-111">713</span><span class="sxs-lookup"><span data-stu-id="962bb-111">713</span></span>|<span data-ttu-id="962bb-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="962bb-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="962bb-113">OrdersTable (alt tablo)</span><span class="sxs-lookup"><span data-stu-id="962bb-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="962bb-114">Sipariş Kimliği</span><span class="sxs-lookup"><span data-stu-id="962bb-114">OrderID</span></span>|<span data-ttu-id="962bb-115">orderDate</span><span class="sxs-lookup"><span data-stu-id="962bb-115">OrderDate</span></span>|<span data-ttu-id="962bb-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="962bb-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="962bb-117">903</span><span class="sxs-lookup"><span data-stu-id="962bb-117">903</span></span>|<span data-ttu-id="962bb-118">Şubat 12, 2004</span><span class="sxs-lookup"><span data-stu-id="962bb-118">February 12, 2004</span></span>|<span data-ttu-id="962bb-119">712</span><span class="sxs-lookup"><span data-stu-id="962bb-119">712</span></span>|  
|<span data-ttu-id="962bb-120">904</span><span class="sxs-lookup"><span data-stu-id="962bb-120">904</span></span>|<span data-ttu-id="962bb-121">13 Şubat 2004</span><span class="sxs-lookup"><span data-stu-id="962bb-121">February 13, 2004</span></span>|<span data-ttu-id="962bb-122">713</span><span class="sxs-lookup"><span data-stu-id="962bb-122">713</span></span>|  
  
 <span data-ttu-id="962bb-123">Bu senaryoda, bir tablo, CustomersTable, görüntülemek ve kaydetmek istediğiniz gerçek bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="962bb-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="962bb-124">Ancak alanı kaydetmek için tabloda açıklık veri çıkışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="962bb-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="962bb-125">Diğer tablo, OrdersTable, hangi müşterinin hakkında kimlik numarasını hangi sipariş tarihi ve sipariş kimliği için eşdeğer yalnızca görünüm ile ilgili bilgiler içerir</span><span class="sxs-lookup"><span data-stu-id="962bb-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="962bb-126">Müşterilerin adlarını hiçbir Bahsetme yoktur.</span><span class="sxs-lookup"><span data-stu-id="962bb-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="962bb-127">Dört önemli özellikleri üzerinde ayarlanır [ComboBox denetimi](combobox-control-windows-forms.md) arama tablosu oluşturma için denetimi.</span><span class="sxs-lookup"><span data-stu-id="962bb-127">Four important properties are set on the [ComboBox Control](combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
-   <span data-ttu-id="962bb-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> Özelliği tablo adını içerir.</span><span class="sxs-lookup"><span data-stu-id="962bb-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
-   <span data-ttu-id="962bb-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> Özelliği, bu tablonun (müşterinin adı) kontrol metni için görüntülemek istediğiniz veri sütunu içerir.</span><span class="sxs-lookup"><span data-stu-id="962bb-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
-   <span data-ttu-id="962bb-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> Bilgilerini (kimlik numarası üst tablodan) söz konusu tablonun veri sütununun özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="962bb-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
-   <span data-ttu-id="962bb-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> Özelliği, temel alt tablo için arama değeri sağlar <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="962bb-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="962bb-132">Aşağıdaki yordamlar, formunuzu arama tablosu olarak düzenleme ve denetimlere veri bağlama işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="962bb-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="962bb-133">Başarıyla yordamları tamamlamak için daha önce belirtildiği gibi bir yabancı anahtar ilişkisine sahip üst ve alt tablolar ile bir veri kaynağı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="962bb-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="962bb-134">Kullanıcı arabirimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="962bb-134">To create the user interface</span></span>  
  
1. <span data-ttu-id="962bb-135">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ComboBox> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="962bb-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="962bb-136">Bu denetim, üst tablo sütunu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="962bb-136">This control will display the column from parent table.</span></span>  
  
2. <span data-ttu-id="962bb-137">Alt tablo ayrıntılarını görüntülemek için diğer denetimler sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="962bb-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="962bb-138">Hangi denetimlerin seçtiğiniz tablodaki verileri biçimi belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="962bb-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="962bb-139">Daha fazla bilgi için [işleve göre Windows Forms denetimleri](windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="962bb-139">For more information, see [Windows Forms Controls by Function](windows-forms-controls-by-function.md).</span></span>  
  
3. <span data-ttu-id="962bb-140">Sürükleme bir <xref:System.Windows.Forms.BindingNavigator> forma denetim; bu alt tablodaki verileri gezinmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="962bb-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="962bb-141">Verilere bağlanmak ve denetimlere bağlama</span><span class="sxs-lookup"><span data-stu-id="962bb-141">To connect to the data and bind it to controls</span></span>  
  
1. <span data-ttu-id="962bb-142">Seçin <xref:System.Windows.Forms.ComboBox> ve akıllı bir görev iletişim kutusunu görüntülemek için akıllı bir görev karakter'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962bb-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2. <span data-ttu-id="962bb-143">Seçin **kullanım veri bağlama öğeleri**.</span><span class="sxs-lookup"><span data-stu-id="962bb-143">Select **Use data bound items**.</span></span>  
  
3. <span data-ttu-id="962bb-144">Yanındaki oka tıklayın **veri kaynağı** açılan kutusu.</span><span class="sxs-lookup"><span data-stu-id="962bb-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="962bb-145">Bir veri kaynağını daha önce proje veya form için yapılandırılmışsa, görüntülenir. Aksi takdirde, (Bu örnekte, Northwind örnek veritabanındaki müşteriler ve Siparişler tablolarını kullanır ve parantez içinde bunlara başvuran) aşağıdaki adımları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="962bb-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1.  <span data-ttu-id="962bb-146">Tıklayın **proje veri kaynağı Ekle** verilere bağlanmak ve bir veri kaynağı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="962bb-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2.  <span data-ttu-id="962bb-147">Üzerinde **veri kaynağı Yapılandırma Sihirbazı** Karşılama sayfasında, tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="962bb-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="962bb-148">Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfası.</span><span class="sxs-lookup"><span data-stu-id="962bb-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4.  <span data-ttu-id="962bb-149">Kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin **veri bağlantınızı seçin** sayfası.</span><span class="sxs-lookup"><span data-stu-id="962bb-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="962bb-150">İstenen veri bağlantısı kullanılamıyorsa seçin **yeni bağlantı** yeni bir veri bağlantısı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="962bb-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5.  <span data-ttu-id="962bb-151">Tıklayın **Evet, bağlantıyı Kaydet** bağlantı dizesini uygulama yapılandırma dosyasına kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="962bb-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6.  <span data-ttu-id="962bb-152">Uygulamanıza getirmek için veritabanı nesneleri seçin.</span><span class="sxs-lookup"><span data-stu-id="962bb-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="962bb-153">Bu durumda, bir üst tablo ve yabancı anahtar ilişkisi olan alt tablo (örneğin, müşteriler ve siparişler) seçin.</span><span class="sxs-lookup"><span data-stu-id="962bb-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7.  <span data-ttu-id="962bb-154">İsterseniz varsayılan veri kümesi adı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="962bb-154">Replace the default dataset name if you want.</span></span>  
  
    8.  <span data-ttu-id="962bb-155">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962bb-155">Click **Finish**.</span></span>  
  
4. <span data-ttu-id="962bb-156">İçinde **görünen üye** birleşik giriş kutusunda görüntülenecek sütun adı (örneğin, ContactName) açılan kutusunda seçin.</span><span class="sxs-lookup"><span data-stu-id="962bb-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5. <span data-ttu-id="962bb-157">İçinde **değer üyesi** açılan kutu, alt tablosunda arama işlemi gerçekleştirmek için (örneğin, CustomerID) sütununu seçin.</span><span class="sxs-lookup"><span data-stu-id="962bb-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6. <span data-ttu-id="962bb-158">İçinde **seçili değer** açılan kutusunda, gitmek **Zdroje dat Projektu** ve üst ve alt tablolar içeren yeni oluşturduğunuz veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="962bb-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="962bb-159">Aynı özellik üst tablo (örneğin, siparişler.MüşteriNo) değeri üyesi olan alt tablo seçin.</span><span class="sxs-lookup"><span data-stu-id="962bb-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="962bb-160">Uygun <xref:System.Windows.Forms.BindingSource> , veri kümesi ve tablo bağdaştırıcısı bileşenleri oluşturulur ve forma eklenir.</span><span class="sxs-lookup"><span data-stu-id="962bb-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7. <span data-ttu-id="962bb-161">Bağlama <xref:System.Windows.Forms.BindingNavigator> denetimini <xref:System.Windows.Forms.BindingSource> alt tablonun (örneğin, `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="962bb-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8. <span data-ttu-id="962bb-162">Denetimleri dışında bağlama <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.BindingNavigator> alt tablonun ayrıntıları alanlara denetiminden <xref:System.Windows.Forms.BindingSource> (örneğin, `OrdersBindingSource`), görüntülemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="962bb-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962bb-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="962bb-163">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="962bb-164">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="962bb-164">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="962bb-165">ComboBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="962bb-165">ComboBox Control</span></span>](combobox-control-windows-forms.md)
- [<span data-ttu-id="962bb-166">Visual Studio'da verilere denetimler bağlama</span><span class="sxs-lookup"><span data-stu-id="962bb-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

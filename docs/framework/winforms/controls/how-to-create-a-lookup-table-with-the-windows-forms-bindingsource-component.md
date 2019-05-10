---
title: 'Nasıl yapılır: Windows Forms BindingSource Bileşeniyle Arama Tablosu Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 33b9e4e98a8a3f8c0d5dd6433ebbf15c049b608e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643067"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="5a567-102">Nasıl yapılır: Windows Forms BindingSource Bileşeniyle Arama Tablosu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a567-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="5a567-103">Arama tablosu kayıttan alınan ilişkili bir tabloda görüntüleyen bir sütun olan verilerin bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="5a567-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="5a567-104">Aşağıdaki yordamlarda, bir <xref:System.Windows.Forms.ComboBox> denetimi üst alt tablo için yabancı anahtar ilişkisi alanıyla görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a567-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="5a567-105">Bu iki tablo ve bu ilişkiyi görselleştirmenize yardımcı olmak için üst ve alt tablo örneği aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="5a567-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="5a567-106">CustomersTable (üst tablo)</span><span class="sxs-lookup"><span data-stu-id="5a567-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="5a567-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="5a567-107">CustomerID</span></span>|<span data-ttu-id="5a567-108">CustomerName</span><span class="sxs-lookup"><span data-stu-id="5a567-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="5a567-109">712</span><span class="sxs-lookup"><span data-stu-id="5a567-109">712</span></span>|<span data-ttu-id="5a567-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="5a567-110">Paul Koch</span></span>|  
|<span data-ttu-id="5a567-111">713</span><span class="sxs-lookup"><span data-stu-id="5a567-111">713</span></span>|<span data-ttu-id="5a567-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="5a567-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="5a567-113">OrdersTable (alt tablo)</span><span class="sxs-lookup"><span data-stu-id="5a567-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="5a567-114">Sipariş Kimliği</span><span class="sxs-lookup"><span data-stu-id="5a567-114">OrderID</span></span>|<span data-ttu-id="5a567-115">orderDate</span><span class="sxs-lookup"><span data-stu-id="5a567-115">OrderDate</span></span>|<span data-ttu-id="5a567-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="5a567-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="5a567-117">903</span><span class="sxs-lookup"><span data-stu-id="5a567-117">903</span></span>|<span data-ttu-id="5a567-118">Şubat 12, 2004</span><span class="sxs-lookup"><span data-stu-id="5a567-118">February 12, 2004</span></span>|<span data-ttu-id="5a567-119">712</span><span class="sxs-lookup"><span data-stu-id="5a567-119">712</span></span>|  
|<span data-ttu-id="5a567-120">904</span><span class="sxs-lookup"><span data-stu-id="5a567-120">904</span></span>|<span data-ttu-id="5a567-121">13 Şubat 2004</span><span class="sxs-lookup"><span data-stu-id="5a567-121">February 13, 2004</span></span>|<span data-ttu-id="5a567-122">713</span><span class="sxs-lookup"><span data-stu-id="5a567-122">713</span></span>|  
  
 <span data-ttu-id="5a567-123">Bu senaryoda, bir tablo, CustomersTable, görüntülemek ve kaydetmek istediğiniz gerçek bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="5a567-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="5a567-124">Ancak alanı kaydetmek için tabloda açıklık veri çıkışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5a567-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="5a567-125">Diğer tablo, OrdersTable, hangi müşterinin hakkında kimlik numarasını hangi sipariş tarihi ve sipariş kimliği için eşdeğer yalnızca görünüm ile ilgili bilgiler içerir</span><span class="sxs-lookup"><span data-stu-id="5a567-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="5a567-126">Müşterilerin adlarını hiçbir Bahsetme yoktur.</span><span class="sxs-lookup"><span data-stu-id="5a567-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="5a567-127">Dört önemli özellikleri üzerinde ayarlanır [ComboBox denetimi](combobox-control-windows-forms.md) arama tablosu oluşturma için denetimi.</span><span class="sxs-lookup"><span data-stu-id="5a567-127">Four important properties are set on the [ComboBox Control](combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
- <span data-ttu-id="5a567-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> Özelliği tablo adını içerir.</span><span class="sxs-lookup"><span data-stu-id="5a567-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
- <span data-ttu-id="5a567-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> Özelliği, bu tablonun (müşterinin adı) kontrol metni için görüntülemek istediğiniz veri sütunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5a567-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
- <span data-ttu-id="5a567-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> Bilgilerini (kimlik numarası üst tablodan) söz konusu tablonun veri sütununun özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="5a567-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
- <span data-ttu-id="5a567-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> Özelliği, temel alt tablo için arama değeri sağlar <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a567-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="5a567-132">Aşağıdaki yordamlar, formunuzu arama tablosu olarak düzenleme ve denetimlere veri bağlama işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5a567-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="5a567-133">Başarıyla yordamları tamamlamak için daha önce belirtildiği gibi bir yabancı anahtar ilişkisine sahip üst ve alt tablolar ile bir veri kaynağı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a567-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="5a567-134">Kullanıcı arabirimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5a567-134">To create the user interface</span></span>  
  
1. <span data-ttu-id="5a567-135">Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ComboBox> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="5a567-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="5a567-136">Bu denetim, üst tablo sütunu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5a567-136">This control will display the column from parent table.</span></span>  
  
2. <span data-ttu-id="5a567-137">Alt tablo ayrıntılarını görüntülemek için diğer denetimler sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="5a567-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="5a567-138">Hangi denetimlerin seçtiğiniz tablodaki verileri biçimi belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a567-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="5a567-139">Daha fazla bilgi için [işleve göre Windows Forms denetimleri](windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="5a567-139">For more information, see [Windows Forms Controls by Function](windows-forms-controls-by-function.md).</span></span>  
  
3. <span data-ttu-id="5a567-140">Sürükleme bir <xref:System.Windows.Forms.BindingNavigator> forma denetim; bu alt tablodaki verileri gezinmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5a567-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="5a567-141">Verilere bağlanmak ve denetimlere bağlama</span><span class="sxs-lookup"><span data-stu-id="5a567-141">To connect to the data and bind it to controls</span></span>  
  
1. <span data-ttu-id="5a567-142">Seçin <xref:System.Windows.Forms.ComboBox> ve akıllı bir görev iletişim kutusunu görüntülemek için akıllı bir görev karakter'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5a567-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2. <span data-ttu-id="5a567-143">Seçin **kullanım veri bağlama öğeleri**.</span><span class="sxs-lookup"><span data-stu-id="5a567-143">Select **Use data bound items**.</span></span>  
  
3. <span data-ttu-id="5a567-144">Yanındaki oka tıklayın **veri kaynağı** açılan kutusu.</span><span class="sxs-lookup"><span data-stu-id="5a567-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="5a567-145">Bir veri kaynağını daha önce proje veya form için yapılandırılmışsa, görüntülenir. Aksi takdirde, (Bu örnekte, Northwind örnek veritabanındaki müşteriler ve Siparişler tablolarını kullanır ve parantez içinde bunlara başvuran) aşağıdaki adımları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="5a567-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1. <span data-ttu-id="5a567-146">Tıklayın **proje veri kaynağı Ekle** verilere bağlanmak ve bir veri kaynağı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5a567-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2. <span data-ttu-id="5a567-147">Üzerinde **veri kaynağı Yapılandırma Sihirbazı** Karşılama sayfasında, tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="5a567-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3. <span data-ttu-id="5a567-148">Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfası.</span><span class="sxs-lookup"><span data-stu-id="5a567-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4. <span data-ttu-id="5a567-149">Kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin **veri bağlantınızı seçin** sayfası.</span><span class="sxs-lookup"><span data-stu-id="5a567-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="5a567-150">İstenen veri bağlantısı kullanılamıyorsa seçin **yeni bağlantı** yeni bir veri bağlantısı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="5a567-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5. <span data-ttu-id="5a567-151">Tıklayın **Evet, bağlantıyı Kaydet** bağlantı dizesini uygulama yapılandırma dosyasına kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="5a567-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6. <span data-ttu-id="5a567-152">Uygulamanıza getirmek için veritabanı nesneleri seçin.</span><span class="sxs-lookup"><span data-stu-id="5a567-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="5a567-153">Bu durumda, bir üst tablo ve yabancı anahtar ilişkisi olan alt tablo (örneğin, müşteriler ve siparişler) seçin.</span><span class="sxs-lookup"><span data-stu-id="5a567-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7. <span data-ttu-id="5a567-154">İsterseniz varsayılan veri kümesi adı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5a567-154">Replace the default dataset name if you want.</span></span>  
  
    8. <span data-ttu-id="5a567-155">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5a567-155">Click **Finish**.</span></span>  
  
4. <span data-ttu-id="5a567-156">İçinde **görünen üye** birleşik giriş kutusunda görüntülenecek sütun adı (örneğin, ContactName) açılan kutusunda seçin.</span><span class="sxs-lookup"><span data-stu-id="5a567-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5. <span data-ttu-id="5a567-157">İçinde **değer üyesi** açılan kutu, alt tablosunda arama işlemi gerçekleştirmek için (örneğin, CustomerID) sütununu seçin.</span><span class="sxs-lookup"><span data-stu-id="5a567-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6. <span data-ttu-id="5a567-158">İçinde **seçili değer** açılan kutusunda, gitmek **Zdroje dat Projektu** ve üst ve alt tablolar içeren yeni oluşturduğunuz veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="5a567-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="5a567-159">Aynı özellik üst tablo (örneğin, siparişler.MüşteriNo) değeri üyesi olan alt tablo seçin.</span><span class="sxs-lookup"><span data-stu-id="5a567-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="5a567-160">Uygun <xref:System.Windows.Forms.BindingSource> , veri kümesi ve tablo bağdaştırıcısı bileşenleri oluşturulur ve forma eklenir.</span><span class="sxs-lookup"><span data-stu-id="5a567-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7. <span data-ttu-id="5a567-161">Bağlama <xref:System.Windows.Forms.BindingNavigator> denetimini <xref:System.Windows.Forms.BindingSource> alt tablonun (örneğin, `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="5a567-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8. <span data-ttu-id="5a567-162">Denetimleri dışında bağlama <xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.BindingNavigator> alt tablonun ayrıntıları alanlara denetiminden <xref:System.Windows.Forms.BindingSource> (örneğin, `OrdersBindingSource`), görüntülemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="5a567-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a567-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a567-163">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="5a567-164">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="5a567-164">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="5a567-165">ComboBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="5a567-165">ComboBox Control</span></span>](combobox-control-windows-forms.md)
- [<span data-ttu-id="5a567-166">Visual Studio'da verilere denetimler bağlama</span><span class="sxs-lookup"><span data-stu-id="5a567-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

---
title: BindingSource bileşeniyle arama tablosu oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: ccf2bfa6cf3f56a38b55f8c87004c42a46172891
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736807"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="c1a26-102">Nasıl yapılır: Windows Formları BindingSource Bileşeniyle Arama Tablosu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1a26-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="c1a26-103">Arama tablosu, ilişkili tablodaki kayıtlardan verileri görüntüleyen bir sütunu olan bir veri tablosudur.</span><span class="sxs-lookup"><span data-stu-id="c1a26-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="c1a26-104">Aşağıdaki yordamlarda, üst-anahtar ilişkisine sahip alanı alt tabloya göstermek için bir <xref:System.Windows.Forms.ComboBox> denetimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c1a26-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="c1a26-105">Bu iki tabloyu ve bu ilişkiyi görselleştirmenize yardımcı olmak için bir üst ve alt tablo örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c1a26-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="c1a26-106">CustomersTable (üst tablo)</span><span class="sxs-lookup"><span data-stu-id="c1a26-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="c1a26-107">Ister</span><span class="sxs-lookup"><span data-stu-id="c1a26-107">CustomerID</span></span>|<span data-ttu-id="c1a26-108">customerName</span><span class="sxs-lookup"><span data-stu-id="c1a26-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="c1a26-109">712</span><span class="sxs-lookup"><span data-stu-id="c1a26-109">712</span></span>|<span data-ttu-id="c1a26-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="c1a26-110">Paul Koch</span></span>|  
|<span data-ttu-id="c1a26-111">713</span><span class="sxs-lookup"><span data-stu-id="c1a26-111">713</span></span>|<span data-ttu-id="c1a26-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="c1a26-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="c1a26-113">OrdersTable (alt tablo)</span><span class="sxs-lookup"><span data-stu-id="c1a26-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="c1a26-114">Sipariş</span><span class="sxs-lookup"><span data-stu-id="c1a26-114">OrderID</span></span>|<span data-ttu-id="c1a26-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="c1a26-115">OrderDate</span></span>|<span data-ttu-id="c1a26-116">Ister</span><span class="sxs-lookup"><span data-stu-id="c1a26-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="c1a26-117">903</span><span class="sxs-lookup"><span data-stu-id="c1a26-117">903</span></span>|<span data-ttu-id="c1a26-118">12 Şubat 2004</span><span class="sxs-lookup"><span data-stu-id="c1a26-118">February 12, 2004</span></span>|<span data-ttu-id="c1a26-119">712</span><span class="sxs-lookup"><span data-stu-id="c1a26-119">712</span></span>|  
|<span data-ttu-id="c1a26-120">904</span><span class="sxs-lookup"><span data-stu-id="c1a26-120">904</span></span>|<span data-ttu-id="c1a26-121">13 Şubat 2004</span><span class="sxs-lookup"><span data-stu-id="c1a26-121">February 13, 2004</span></span>|<span data-ttu-id="c1a26-122">713</span><span class="sxs-lookup"><span data-stu-id="c1a26-122">713</span></span>|  
  
 <span data-ttu-id="c1a26-123">Bu senaryoda, bir tablo olan CustomersTable, göstermek ve kaydetmek istediğiniz gerçek bilgileri depolar.</span><span class="sxs-lookup"><span data-stu-id="c1a26-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="c1a26-124">Ancak alanı kazanmak için tablo, açıklık ekleyen verileri bırakır.</span><span class="sxs-lookup"><span data-stu-id="c1a26-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="c1a26-125">Diğer tablo, OrdersTable, hangi müşteri KIMLIĞI numarasının hangi sipariş tarihi ve sipariş KIMLIĞIYLE eşdeğer olduğu hakkında yalnızca görünümle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="c1a26-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="c1a26-126">Müşterilerin adlarından bahsetme yoktur.</span><span class="sxs-lookup"><span data-stu-id="c1a26-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="c1a26-127">Arama tablosu oluşturmak için [ComboBox Denetim](combobox-control-windows-forms.md) denetiminde dört önemli özellik ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c1a26-127">Four important properties are set on the [ComboBox Control](combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
- <span data-ttu-id="c1a26-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> özelliği tablonun adını içerir.</span><span class="sxs-lookup"><span data-stu-id="c1a26-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
- <span data-ttu-id="c1a26-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> özelliği, denetim metni (müşterinin adı) için görüntülenmesini istediğiniz tablonun veri sütununu içerir.</span><span class="sxs-lookup"><span data-stu-id="c1a26-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
- <span data-ttu-id="c1a26-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> özelliği, bu tablonun depolanan bilgiler (üst tablodaki KIMLIK numarası) ile veri sütununu içerir.</span><span class="sxs-lookup"><span data-stu-id="c1a26-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
- <span data-ttu-id="c1a26-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> özelliği, alt tablo için <xref:System.Windows.Forms.ListControl.ValueMember%2A>temelinde arama değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1a26-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="c1a26-132">Aşağıdaki yordamlarda, formunuzu bir arama tablosu olarak nasıl düzenleyeni ve verileri üzerinde denetimlere nasıl bağlayacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c1a26-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="c1a26-133">Yordamları başarıyla tamamlayabilmeniz için, daha önce belirtildiği gibi, yabancı anahtar ilişkisine sahip üst ve alt tablolar içeren bir veri kaynağınız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1a26-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="c1a26-134">Kullanıcı arabirimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c1a26-134">To create the user interface</span></span>  
  
1. <span data-ttu-id="c1a26-135">**Araç kutusundan**bir <xref:System.Windows.Forms.ComboBox> denetimini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="c1a26-136">Bu denetim, üst tablodaki sütunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c1a26-136">This control will display the column from parent table.</span></span>  
  
2. <span data-ttu-id="c1a26-137">Alt tablodaki ayrıntıları göstermek için diğer denetimleri sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="c1a26-138">Tablodaki verilerin biçimi hangi denetimleri istediğinizi belirlemelidir.</span><span class="sxs-lookup"><span data-stu-id="c1a26-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="c1a26-139">Daha fazla bilgi için bkz. [Windows Forms denetimleri işleve göre](windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="c1a26-139">For more information, see [Windows Forms Controls by Function](windows-forms-controls-by-function.md).</span></span>  
  
3. <span data-ttu-id="c1a26-140">Bir <xref:System.Windows.Forms.BindingNavigator> denetimini form üzerine sürükleyin; Bu, alt tablodaki verilerde gezinmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="c1a26-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="c1a26-141">Verilere bağlanmak ve denetimlere bağlamak için</span><span class="sxs-lookup"><span data-stu-id="c1a26-141">To connect to the data and bind it to controls</span></span>  
  
1. <span data-ttu-id="c1a26-142"><xref:System.Windows.Forms.ComboBox> seçin ve Akıllı Görev iletişim kutusunu göstermek için Akıllı Görev glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1a26-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2. <span data-ttu-id="c1a26-143">**Veri bağlantılı öğeleri kullan**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-143">Select **Use data bound items**.</span></span>  
  
3. <span data-ttu-id="c1a26-144">**Veri kaynağı** açılır kutusunun yanındaki oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1a26-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="c1a26-145">Bir veri kaynağı daha önce proje veya form için yapılandırıldıysa, görünür; Aksi takdirde, aşağıdaki adımları uygulayın (Bu örnek, Northwind örnek veritabanının Customers ve Orders tablolarını kullanır ve bunları parantez içinde ifade eder).</span><span class="sxs-lookup"><span data-stu-id="c1a26-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1. <span data-ttu-id="c1a26-146">Verilere bağlanmak ve bir veri kaynağı oluşturmak için **proje veri kaynağı Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1a26-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2. <span data-ttu-id="c1a26-147">**Veri kaynağı Yapılandırma Sihirbazı** 'na hoş geldiniz sayfasında **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1a26-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3. <span data-ttu-id="c1a26-148">**Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4. <span data-ttu-id="c1a26-149">**Veri bağlantınızı seçin** sayfasında kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="c1a26-150">İstediğiniz veri bağlantınız yoksa yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1a26-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5. <span data-ttu-id="c1a26-151">Bağlantı dizesini uygulama yapılandırma dosyasına kaydetmek için **Evet, bağlantıyı kaydet** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1a26-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6. <span data-ttu-id="c1a26-152">Uygulamanıza getirmek istediğiniz veritabanı nesnelerini seçin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="c1a26-153">Bu durumda, bir ana tablo ve alt tablo (örneğin, müşteriler ve siparişler) yabancı anahtar ilişkisiyle seçin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7. <span data-ttu-id="c1a26-154">İsterseniz varsayılan veri kümesi adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-154">Replace the default dataset name if you want.</span></span>  
  
    8. <span data-ttu-id="c1a26-155">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1a26-155">Click **Finish**.</span></span>  
  
4. <span data-ttu-id="c1a26-156">**Üye görüntüle** açılan kutusunda, açılan kutuda görüntülenecek sütun adını (örneğin, ContactName) seçin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5. <span data-ttu-id="c1a26-157">**Değer üyesi** açılan kutusunda, alt tabloda arama işlemini gerçekleştirmek için sütunu (örneğin, CustomerID) seçin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6. <span data-ttu-id="c1a26-158">**Seçili değer** açılır kutusunda, **proje veri kaynakları** ' na ve üst ve alt tabloları içeren yeni oluşturduğunuz veri kümesine gidin.</span><span class="sxs-lookup"><span data-stu-id="c1a26-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="c1a26-159">Üst tablonun değer üyesi olan alt tablonun aynı özelliğini seçin (örneğin, Orders. CustomerID).</span><span class="sxs-lookup"><span data-stu-id="c1a26-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="c1a26-160">Uygun <xref:System.Windows.Forms.BindingSource>, veri kümesi ve tablo bağdaştırıcısı bileşenleri oluşturulacak ve forma eklenecek.</span><span class="sxs-lookup"><span data-stu-id="c1a26-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7. <span data-ttu-id="c1a26-161"><xref:System.Windows.Forms.BindingNavigator> denetimini alt tablonun <xref:System.Windows.Forms.BindingSource> bağlayın (örneğin, `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="c1a26-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8. <span data-ttu-id="c1a26-162"><xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.BindingNavigator> denetimi dışındaki denetimleri, alt tablonun <xref:System.Windows.Forms.BindingSource> (örneğin, `OrdersBindingSource`) Ayrıntılar alanlarına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="c1a26-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a26-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1a26-163">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="c1a26-164">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="c1a26-164">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="c1a26-165">ComboBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="c1a26-165">ComboBox Control</span></span>](combobox-control-windows-forms.md)
- [<span data-ttu-id="c1a26-166">Visual Studio'da verilere denetimler bağlama</span><span class="sxs-lookup"><span data-stu-id="c1a26-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

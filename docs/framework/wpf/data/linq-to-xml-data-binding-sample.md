---
title: LINQ to XML veri bağlama örneği
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920939"
---
# <a name="linq-to-xml-data-binding-sample"></a><span data-ttu-id="82a43-102">LINQ to XML veri bağlama örneği</span><span class="sxs-lookup"><span data-stu-id="82a43-102">LINQ to XML data binding sample</span></span>

<span data-ttu-id="82a43-103">Bu makalede, Kullanıcı Arabirimi bileşenlerini gömülü bir XML veri kaynağına bağlayan bir Windows Presentation Foundation (WPF) uygulaması olan LinqToXmlDataBinding örneği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82a43-103">This article describes the LinqToXmlDataBinding sample, a Windows Presentation Foundation (WPF) app that binds user interface components to an embedded XML data source.</span></span>

## <a name="overview"></a><span data-ttu-id="82a43-104">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="82a43-104">Overview</span></span>

<span data-ttu-id="82a43-105">LinqToXmlDataBinding örneği, ve XAML kaynak dosyalarını içeren C# bir WINDOWS PRESENTATION FOUNDATION (WPF) uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="82a43-105">The LinqToXmlDataBinding sample is a Windows Presentation Foundation (WPF) app that contains C# and XAML source files.</span></span> <span data-ttu-id="82a43-106">Gömülü bir XML belgesi, kitapların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82a43-106">An embedded XML document defines a list of books.</span></span> <span data-ttu-id="82a43-107">Uygulama, kullanıcının kitap girişlerini görüntülemesini, eklemesini, silmesini ve düzenlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a43-107">The app enables the user to view, add, delete, and edit the book entries.</span></span>

<span data-ttu-id="82a43-108">İki birincil kaynak dosyası vardır:</span><span class="sxs-lookup"><span data-stu-id="82a43-108">There are two primary source files:</span></span>

- <span data-ttu-id="82a43-109">[L2DBForm. xaml](l2dbform-xaml-source-code.md) , ana pencerenin kullanıcı ARABIRIMI (UI) için XAML bildirim kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="82a43-109">[L2DBForm.xaml](l2dbform-xaml-source-code.md) contains the XAML declaration code for the user interface (UI) of the main window.</span></span> <span data-ttu-id="82a43-110">Ayrıca, kitap listeleri için bir veri sağlayıcısını ve katıştırılmış XML belgesini tanımlayan bir pencere kaynağı bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="82a43-110">It also contains a window resource section that defines a data provider and an embedded XML document for the book listings.</span></span>

- <span data-ttu-id="82a43-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) , Kullanıcı arabirimiyle ilişkili başlatma ve olay işleme yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="82a43-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contains the initialization and event-handling methods associated with the UI.</span></span>

<span data-ttu-id="82a43-112">Ana pencere aşağıdaki dört dikey UI bölümüne bölünmüştür:</span><span class="sxs-lookup"><span data-stu-id="82a43-112">The main window is divided into the following four vertical UI sections:</span></span>

- <span data-ttu-id="82a43-113">**XML** katıştırılmış kitap LISTESININ ham XML kaynağını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="82a43-113">**XML** displays the raw XML source of the embedded book listing.</span></span>

- <span data-ttu-id="82a43-114">**Kitap listesi** , kitap girişlerini standart metin olarak görüntüler ve kullanıcının tek tek girdileri seçmesini ve silmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a43-114">**Book List** displays the book entries as standard text and enables the user to select and delete individual entries.</span></span>

- <span data-ttu-id="82a43-115">**Seçili kitabı Düzenle** , kullanıcının şu anda seçili olan kitap girişiyle ilişkili değerleri düzenlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a43-115">**Edit Selected Book** enables the user to edit the values associated with the currently selected book entry.</span></span>

- <span data-ttu-id="82a43-116">**Yeni kitap ekle** , Kullanıcı tarafından girilen değerlere göre yeni bir kitap girişi oluşturulmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="82a43-116">**Add New Book** enables the creation of a new book entry based on values entered by the user.</span></span>

## <a name="run-the-sample"></a><span data-ttu-id="82a43-117">Örneği çalıştırın</span><span class="sxs-lookup"><span data-stu-id="82a43-117">Run the sample</span></span>

<span data-ttu-id="82a43-118">Bu bölümde, Visual Studio 'da LinqToXmlDataBinding projesi oluşturma ve derleme ve elde edilen LinqToXmlDataBinding Windows Presentation Foundation (WPF) uygulamasının nasıl çalıştırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82a43-118">This section shows how to create and build the LinqToXmlDataBinding project in Visual Studio, and how to run the resulting LinqToXmlDataBinding Windows Presentation Foundation (WPF) app.</span></span>

### <a name="create-the-project"></a><span data-ttu-id="82a43-119">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="82a43-119">Create the project</span></span>

1. <span data-ttu-id="82a43-120">Visual Studio 'yu açın ve **LinqToXmlDataBinding**adlı bir C# **WPF uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82a43-120">Open Visual Studio and create a C# **WPF App** named **LinqToXmlDataBinding**.</span></span>

   <span data-ttu-id="82a43-121">Projenin .NET Framework 3,5 ' i (veya üzeri) hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="82a43-121">The project should target the .NET Framework 3.5 (or later).</span></span>

1. <span data-ttu-id="82a43-122">Henüz yoksa, aşağıdaki .NET derlemeleri için proje başvuruları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="82a43-122">If not already present, add project references for the following .NET assemblies:</span></span>

    - <span data-ttu-id="82a43-123">System.Data</span><span class="sxs-lookup"><span data-stu-id="82a43-123">System.Data</span></span>
    - <span data-ttu-id="82a43-124">System. Data. Datase, sions</span><span class="sxs-lookup"><span data-stu-id="82a43-124">System.Data.DataSetExtensions</span></span>
    - <span data-ttu-id="82a43-125">System.Xml</span><span class="sxs-lookup"><span data-stu-id="82a43-125">System.Xml</span></span>
    - <span data-ttu-id="82a43-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="82a43-126">System.Xml</span></span>

1. <span data-ttu-id="82a43-127">**Ctrl** +**SHIFT** +**B**tuşlarına basarak çözümü derleyin, sonra **F5**tuşuna basarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="82a43-127">Build the solution by pressing **Ctrl**+**Shift**+**B**, then run it by pressing **F5**.</span></span>

   <span data-ttu-id="82a43-128">Projenin hata olmadan derlenmesi ve genel bir WPF uygulaması olarak çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82a43-128">The project should compile without errors and run as a generic WPF application.</span></span>

### <a name="add-code"></a><span data-ttu-id="82a43-129">Kod Ekle</span><span class="sxs-lookup"><span data-stu-id="82a43-129">Add code</span></span>

1. <span data-ttu-id="82a43-130">**Çözüm Gezgini**, **Window1. xaml** kaynak dosyasını **L2XDBForm. xaml**olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="82a43-130">In **Solution Explorer**, rename the source file **Window1.xaml** to **L2XDBForm.xaml**.</span></span>

   <span data-ttu-id="82a43-131">Window1.xaml.cs bağımlı kaynak dosyası otomatik olarak L2XDBForm.xaml.cs olarak yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="82a43-131">The dependent source file Window1.xaml.cs is automatically renamed to L2XDBForm.xaml.cs.</span></span>

1. <span data-ttu-id="82a43-132">**L2XDBForm. xaml** dosyasında bulunan kaynak kodu [L2DBForm. xaml kaynak kodu](l2dbform-xaml-source-code.md)ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="82a43-132">Replace the source code found in the file **L2XDBForm.xaml** with the [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="82a43-133">Bu dosyayla çalışmak için XAML kaynak görünümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="82a43-133">Use the XAML source view to work with this file.</span></span>

1. <span data-ttu-id="82a43-134">Benzer şekilde, **L2XDBForm.xaml.cs** içindeki kaynağı [L2DBForm.xaml.cs kaynak kodu](l2dbform-xaml-cs-source-code.md)ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="82a43-134">Similarly, replace the source in **L2XDBForm.xaml.cs** with the [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

1. <span data-ttu-id="82a43-135">**App. xaml**dosyasında, **Window1. xaml** dizesinin tüm oluşumlarını **L2XDBForm. xaml**ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="82a43-135">In the file **App.xaml**, replace all occurrences of the string **Window1.xaml** with **L2XDBForm.xaml**.</span></span>

1. <span data-ttu-id="82a43-136">**Ctrl** +**SHIFT** +**B**'ye basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82a43-136">Build the solution by pressing **Ctrl**+**Shift**+**B**.</span></span>

### <a name="run-the-app"></a><span data-ttu-id="82a43-137">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="82a43-137">Run the app</span></span>

<span data-ttu-id="82a43-138">LinqToXmlDataBinding uygulaması, kullanıcının gömülü bir XML öğesi olarak depolanan bir kitap listesini görüntülemesini ve işlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a43-138">The LinqToXmlDataBinding app enables the user to view and manipulate a list of books that's stored as an embedded XML element.</span></span> <span data-ttu-id="82a43-139">**F5** tuşuna basarak uygulamayı çalıştırın (hata ayıklamayı Başlat) veya **CTRL**+**F5** (hata ayıklama olmadan Başlat).</span><span class="sxs-lookup"><span data-stu-id="82a43-139">Run the app by pressing **F5** (Start Debugging) or **Ctrl**+**F5** (Start Without Debugging).</span></span>

<span data-ttu-id="82a43-140">**LINQ to XML kullanarak WPF veri bağlama** başlıklı bir program penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="82a43-140">A program window with the title **WPF Data Binding using LINQ to XML** appears.</span></span>

<span data-ttu-id="82a43-141">Kullanıcı arabiriminin üst bölümü, kitap listesini temsil eden ham **XML** 'i görüntüler.</span><span class="sxs-lookup"><span data-stu-id="82a43-141">The top section of the UI displays the raw **XML** that represents the book list.</span></span> <span data-ttu-id="82a43-142">Bir WPF <xref:System.Windows.Controls.TextBlock> denetimi kullanılarak görüntülenir ve bu, fare veya klavye aracılığıyla etkileşimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="82a43-142">It is displayed using a WPF <xref:System.Windows.Controls.TextBlock> control, which does not enable interaction through the mouse or keyboard.</span></span>

<span data-ttu-id="82a43-143">**Kitap listesi**etiketli ikinci dikey bölüm, kitapları düz metin sıralı bir liste olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="82a43-143">The second vertical section, labeled **Book List**, displays the books as a plain text ordered list.</span></span> <span data-ttu-id="82a43-144">Fareyle veya klavyeden seçimi sağlayan <xref:System.Windows.Controls.ListBox> denetimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="82a43-144">It uses a <xref:System.Windows.Controls.ListBox> control that enables selection though the mouse or keyboard.</span></span>

### <a name="add-and-delete-books"></a><span data-ttu-id="82a43-145">Kitap ekleme ve silme</span><span class="sxs-lookup"><span data-stu-id="82a43-145">Add and delete books</span></span>

<span data-ttu-id="82a43-146">Listeye yeni bir kitap eklemek için son bölümdeki denetim <xref:System.Windows.Controls.TextBox>, **Yeni kitap ekle**' **ye ve ardından** **kitap ekle**' ye bir **değer** girin.</span><span class="sxs-lookup"><span data-stu-id="82a43-146">To add a new book to the list, enter values into the **ID** and **Value** <xref:System.Windows.Controls.TextBox> controls in the last section, **Add New Book**, and then select **Add Book**.</span></span> <span data-ttu-id="82a43-147">Kitap, hem kitap hem de XML listelerinde listeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="82a43-147">The book is appended to the list in both the book and XML listings.</span></span> <span data-ttu-id="82a43-148">Bu program giriş değerlerini doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="82a43-148">This program does not validate input values.</span></span>

<span data-ttu-id="82a43-149">Listeden mevcut bir kitabı silmek için **kitap listesi** bölümünde seçin ve ardından **Seçili kitabı kaldır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="82a43-149">To delete an existing book from the list, select it in the **Book List** section, and then select **Remove Selected Book**.</span></span> <span data-ttu-id="82a43-150">Kitap girişi hem defterden hem de ham XML kaynak listelerinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="82a43-150">The book entry is removed from both the book and the raw XML source listings.</span></span>

### <a name="edit-a-book-entry"></a><span data-ttu-id="82a43-151">Kitap girişini düzenleme</span><span class="sxs-lookup"><span data-stu-id="82a43-151">Edit a book entry</span></span>

1. <span data-ttu-id="82a43-152">İkinci **kitap listesi** bölümünde kitap girişini seçin.</span><span class="sxs-lookup"><span data-stu-id="82a43-152">Select the book entry in the second **Book List** section.</span></span>

   <span data-ttu-id="82a43-153">Geçerli değerleri **Seçili kitabı Düzenle** bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="82a43-153">Its current values are displayed in the **Edit Selected Book** section.</span></span>

1. <span data-ttu-id="82a43-154">Klavyeyi kullanarak değerleri düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="82a43-154">Edit the values using the keyboard.</span></span> <span data-ttu-id="82a43-155"><xref:System.Windows.Controls.TextBox> denetim odağı kaybettiğinde, değişiklikler otomatik olarak XML kaynağına ve kitap listelerine yayılır.</span><span class="sxs-lookup"><span data-stu-id="82a43-155">As soon as either <xref:System.Windows.Controls.TextBox> control loses focus, changes are automatically propagated to the XML source and book listings.</span></span>

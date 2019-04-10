---
title: 'İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: dfd0753895a937ccef9a8bc14b2f692219eb7f06
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230479"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1e468-102">İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma</span><span class="sxs-lookup"><span data-stu-id="1e468-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1e468-103">Temel alınan veri deposundan hataları işleme, veri girişi uygulama için gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1e468-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="1e468-104">Windows Forms <xref:System.Windows.Forms.DataGridView> denetim kolaylaştırır bu göstererek <xref:System.Windows.Forms.DataGridView.DataError> veri deposunu bir kısıtlama ihlali veya bir ihlal iş kuralı algıladığında gerçekleşmek üzereyken olay.</span><span class="sxs-lookup"><span data-stu-id="1e468-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>  
  
 <span data-ttu-id="1e468-105">Bu kılavuzda, tablosundan satırları alır `Customers` Northwind örnek veritabanındaki tablo ve bunları görüntüleme bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="1e468-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1e468-106">Yinelenen zaman `CustomerID` değeri, yeni bir satır veya düzenlenmiş bir var olan satır algılandığında <xref:System.Windows.Forms.DataGridView.DataError> olay gerçekleşir, hangi görüntüleyerek işlenecek bir <xref:System.Windows.Forms.MessageBox> özel durumu açıklayan.</span><span class="sxs-lookup"><span data-stu-id="1e468-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>  
  
 <span data-ttu-id="1e468-107">Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Windows veri girişi sırasında oluşan hataları ele Forms DataGridView denetiminde](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="1e468-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1e468-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1e468-108">Prerequisites</span></span>  
 <span data-ttu-id="1e468-109">Bu izlenecek yolu tamamlamak için şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="1e468-109">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="1e468-110">SQL Server Northwind örnek veritabanını bir sunucu erişim.</span><span class="sxs-lookup"><span data-stu-id="1e468-110">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="1e468-111">Form Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e468-111">Creating the Form</span></span>  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="1e468-112">DataGridView denetimine veri girişi sırasında oluşan hataları işlemek için</span><span class="sxs-lookup"><span data-stu-id="1e468-112">To handle data-entry errors in the DataGridView control</span></span>  
  
1.  <span data-ttu-id="1e468-113">Türetilen bir sınıf oluşturmanız <xref:System.Windows.Forms.Form> ve içeren bir <xref:System.Windows.Forms.DataGridView> denetimi ve bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="1e468-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     <span data-ttu-id="1e468-114">Aşağıdaki kod örneği içerir ve temel başlatma sağlar bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1e468-114">The following code example provides basic initialization and includes a `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  <span data-ttu-id="1e468-115">Veritabanına bağlanırken ayrıntılarını işlemek için form denetiminin sınıf tanımında bir yöntem uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1e468-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>  
  
     <span data-ttu-id="1e468-116">Bu kod örneği kullanan bir `GetData` doldurulmuş bir döndüren yöntem <xref:System.Data.DataTable> nesne.</span><span class="sxs-lookup"><span data-stu-id="1e468-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="1e468-117">Ayarladığınız mutlaka `connectionString` değişken veritabanınız için uygun olan bir değer.</span><span class="sxs-lookup"><span data-stu-id="1e468-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1e468-118">Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="1e468-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="1e468-119">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="1e468-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="1e468-120">Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="1e468-120">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  <span data-ttu-id="1e468-121">Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> başlatan olay <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.BindingSource> ve veri bağlamasını ayarlamak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1e468-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  <span data-ttu-id="1e468-122">Tanıtıcı <xref:System.Windows.Forms.DataGridView.DataError> olayda <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="1e468-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="1e468-123">Bir işleme hata bağlamı ise hata görüntüleme bir <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="1e468-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="1e468-124">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="1e468-124">Testing the Application</span></span>  
 <span data-ttu-id="1e468-125">Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e468-125">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="1e468-126">Formu sınamak için</span><span class="sxs-lookup"><span data-stu-id="1e468-126">To test the form</span></span>  
  
-   <span data-ttu-id="1e468-127">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="1e468-127">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="1e468-128">Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> denetim doldurulmuş Müşteriler tablosundan verileri.</span><span class="sxs-lookup"><span data-stu-id="1e468-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="1e468-129">İçin yinelenen bir değer girerseniz `CustomerID` ve Düzenle işleyin, hücre değerini otomatik olarak geri döner ve göreceğiniz bir <xref:System.Windows.Forms.MessageBox> görüntüleyen veri girişi hatası.</span><span class="sxs-lookup"><span data-stu-id="1e468-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1e468-130">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="1e468-130">Next Steps</span></span>  
 <span data-ttu-id="1e468-131">Bu uygulamayı size temel bir anlayış <xref:System.Windows.Forms.DataGridView> denetimin özellikleri.</span><span class="sxs-lookup"><span data-stu-id="1e468-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="1e468-132">Görünümünü ve davranışını özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> çeşitli şekillerde denetimi:</span><span class="sxs-lookup"><span data-stu-id="1e468-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="1e468-133">Kenarlık ve üstbilgi stilleri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1e468-133">Change border and header styles.</span></span> <span data-ttu-id="1e468-134">Daha fazla bilgi için [nasıl yapılır: Değiştirme kenarlık ve kılavuz çizgi stillerini Windows Forms DataGridView denetiminde](change-the-border-and-gridline-styles-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="1e468-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="1e468-135">Etkinleştirmek veya kısıtlamak için kullanıcı girişi <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="1e468-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1e468-136">Daha fazla bilgi için [nasıl yapılır: Önlemek satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md), ve [nasıl yapılır: Sütunları yapma salt okunur Windows Forms DataGridView denetiminde](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1e468-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="1e468-137">Kullanıcı girişini doğrulama <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="1e468-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1e468-138">Daha fazla bilgi için [izlenecek yol: Doğrulama verileri Windows Forms DataGridView denetiminde](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1e468-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="1e468-139">Çok büyük veri kümeleri ile sanal modu kullanarak işleyin.</span><span class="sxs-lookup"><span data-stu-id="1e468-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="1e468-140">Daha fazla bilgi için [izlenecek yol: Sanal modu uygulama içinde Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1e468-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="1e468-141">Hücrelerin görünüşünü özelleştirme.</span><span class="sxs-lookup"><span data-stu-id="1e468-141">Customize the appearance of cells.</span></span> <span data-ttu-id="1e468-142">Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: Windows Forms DataGridView denetimi için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1e468-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e468-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e468-143">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1e468-144">Windows Forms DataGridView Denetimindeki Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="1e468-144">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1e468-145">Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma</span><span class="sxs-lookup"><span data-stu-id="1e468-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="1e468-146">İzlenecek yol: Windows Forms DataGridView Denetimindeki Verileri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="1e468-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1e468-147">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="1e468-147">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)

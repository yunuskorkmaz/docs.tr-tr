---
title: "İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c602af6799da57fec904c87da7bed77c0040eff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="23ea2-102">İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma</span><span class="sxs-lookup"><span data-stu-id="23ea2-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="23ea2-103">Temel alınan veri deposundan hataları işleme, veri girişi uygulama için gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="23ea2-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="23ea2-104">Windows Forms <xref:System.Windows.Forms.DataGridView> denetim kolaylaştırır bu göstererek <xref:System.Windows.Forms.DataGridView.DataError> veri deposunda bir kısıtlama ihlali veya bozuk iş kuralı algıladığında oluşan olayı,.</span><span class="sxs-lookup"><span data-stu-id="23ea2-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>  
  
 <span data-ttu-id="23ea2-105">Bu kılavuzda, satırları alacak `Customers` tablo Northwind örnek veritabanında ve bunları görüntülemek bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="23ea2-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="23ea2-106">Yinelenen zaman `CustomerID` değeri, yeni bir satır veya düzenlenen varolan bir satır, algılandığında <xref:System.Windows.Forms.DataGridView.DataError> olay gerçekleşeceği, hangi görüntüleyerek işlenecek bir <xref:System.Windows.Forms.MessageBox> özel durumu açıklayan.</span><span class="sxs-lookup"><span data-stu-id="23ea2-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>  
  
 <span data-ttu-id="23ea2-107">Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: işlemek hatalar olduğunu ortaya sırasında veri girişi Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="23ea2-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="23ea2-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="23ea2-108">Prerequisites</span></span>  
 <span data-ttu-id="23ea2-109">Bu kılavuzu tamamlamak için gerekir:</span><span class="sxs-lookup"><span data-stu-id="23ea2-109">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="23ea2-110">Northwind SQL Server örnek veritabanı olan bir sunucuya erişim.</span><span class="sxs-lookup"><span data-stu-id="23ea2-110">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="23ea2-111">Form Oluşturma</span><span class="sxs-lookup"><span data-stu-id="23ea2-111">Creating the Form</span></span>  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="23ea2-112">DataGridView denetimindeki veri girişi sırasında oluşan hataları işlemek için</span><span class="sxs-lookup"><span data-stu-id="23ea2-112">To handle data-entry errors in the DataGridView control</span></span>  
  
1.  <span data-ttu-id="23ea2-113">Türeyen bir sınıf oluşturun <xref:System.Windows.Forms.Form> ve içeren bir <xref:System.Windows.Forms.DataGridView> denetim ve <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="23ea2-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     <span data-ttu-id="23ea2-114">Aşağıdaki kod örneğinde temel başlatma sağlar ve içeren bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="23ea2-114">The following code example provides basic initialization and includes a `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  <span data-ttu-id="23ea2-115">Veritabanına bağlanırken ayrıntılarını işlemek için formun sınıf tanımında yöntemi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23ea2-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>  
  
     <span data-ttu-id="23ea2-116">Bu kod örneği kullanan bir `GetData` doldurulan bir döndüren yöntem <xref:System.Data.DataTable> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="23ea2-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="23ea2-117">Ayarladığınız mutlaka `connectionString` değişken veritabanınız için uygun olan bir değer.</span><span class="sxs-lookup"><span data-stu-id="23ea2-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="23ea2-118">Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="23ea2-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="23ea2-119">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="23ea2-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="23ea2-120">Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="23ea2-120">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  <span data-ttu-id="23ea2-121">Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> başlatır olay <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.BindingSource> ve veri bağlamanın ayarlar.</span><span class="sxs-lookup"><span data-stu-id="23ea2-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  <span data-ttu-id="23ea2-122">İşleme <xref:System.Windows.Forms.DataGridView.DataError> olayı <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="23ea2-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="23ea2-123">Bağlamın hata için bir kaydetme işlemi ise, hatayı görüntüler bir <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="23ea2-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="23ea2-124">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="23ea2-124">Testing the Application</span></span>  
 <span data-ttu-id="23ea2-125">Artık formun beklendiği gibi davranır emin olmak için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23ea2-125">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="23ea2-126">Formu sınamak için</span><span class="sxs-lookup"><span data-stu-id="23ea2-126">To test the form</span></span>  
  
-   <span data-ttu-id="23ea2-127">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="23ea2-127">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="23ea2-128">Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> denetim doldurulmuş Müşteriler tablosundan gelen verilerle.</span><span class="sxs-lookup"><span data-stu-id="23ea2-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="23ea2-129">İçin yinelenen bir değer girerseniz, `CustomerID` ve düzenleme yürütme, hücre değeri otomatik olarak döner ve görürsünüz bir <xref:System.Windows.Forms.MessageBox> veri girişi hatasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="23ea2-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="23ea2-130">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="23ea2-130">Next Steps</span></span>  
 <span data-ttu-id="23ea2-131">Bu uygulama, temel bir anlayış sağlar <xref:System.Windows.Forms.DataGridView> denetimin özellikleri.</span><span class="sxs-lookup"><span data-stu-id="23ea2-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="23ea2-132">Görünümünü ve davranışını özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> çeşitli şekillerde denetimi:</span><span class="sxs-lookup"><span data-stu-id="23ea2-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="23ea2-133">Kenarlık ve üstbilgi stilleri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="23ea2-133">Change border and header styles.</span></span> <span data-ttu-id="23ea2-134">Daha fazla bilgi için bkz: [nasıl yapılır: kenarlık ve kılavuz çizgisi stilleri Windows Forms DataGridView denetiminde değiştirme](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="23ea2-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="23ea2-135">Etkinleştirmek veya kullanıcı girişini kısıtlamak <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="23ea2-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="23ea2-136">Daha fazla bilgi için bkz: [nasıl yapılır: önlemek satır ekleme ve silme Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), ve [nasıl yapılır: Windows Forms DataGridView denetiminde sütunları salt okunur hale](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="23ea2-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="23ea2-137">Kullanıcı girişini doğrulama <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="23ea2-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="23ea2-138">Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde verileri doğrulama](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="23ea2-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="23ea2-139">Sanal mod kullanarak çok büyük veri kümeleri işleyin.</span><span class="sxs-lookup"><span data-stu-id="23ea2-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="23ea2-140">Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="23ea2-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="23ea2-141">Hücrelerin görünüşünü özelleştirme.</span><span class="sxs-lookup"><span data-stu-id="23ea2-141">Customize the appearance of cells.</span></span> <span data-ttu-id="23ea2-142">Daha fazla bilgi için bkz [nasıl yapılır: görünümü hücre Windows Forms DataGridView denetiminde özelleştirme](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: ayarlama varsayılan hücre stilleri Windows Forms DataGridView denetimi için](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="23ea2-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ea2-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23ea2-143">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="23ea2-144">Veri girişi Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="23ea2-144">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="23ea2-145">Nasıl yapılır: Windows veri girişi sırasında oluşan hataları ele Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="23ea2-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="23ea2-146">İzlenecek yol: Windows Forms DataGridView denetiminde verileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="23ea2-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="23ea2-147">Bağlantı bilgileri koruma</span><span class="sxs-lookup"><span data-stu-id="23ea2-147">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)

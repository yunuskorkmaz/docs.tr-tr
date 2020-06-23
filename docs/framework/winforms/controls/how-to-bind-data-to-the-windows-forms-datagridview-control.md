---
title: Verileri DataGridView denetimine bağlama
ms.date: 02/08/2019
description: DataGridView denetiminin çeşitli veri kaynaklarına bağlanabilmesi için standart Windows Forms veri bağlama modelini nasıl desteklediğini öğrenin.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904422"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="43c8d-103">Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama</span><span class="sxs-lookup"><span data-stu-id="43c8d-103">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="43c8d-104"><xref:System.Windows.Forms.DataGridView>Denetim standart Windows Forms veri bağlama modelini destekler, bu nedenle çeşitli veri kaynaklarına bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="43c8d-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="43c8d-105">Genellikle, <xref:System.Windows.Forms.BindingSource> veri kaynağıyla etkileşimi yöneten bir öğesine bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="43c8d-105">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="43c8d-106">, <xref:System.Windows.Forms.BindingSource> Verilerinizin konumunu seçerken veya değiştirirken harika bir esneklik sağlayan herhangi bir Windows Forms veri kaynağı olabilir.</span><span class="sxs-lookup"><span data-stu-id="43c8d-106">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="43c8d-107">Denetimin desteklediği veri kaynakları hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> bkz. [DataGridView denetimine genel bakış](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="43c8d-107">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="43c8d-108">Visual Studio, DataGridView denetimine veri bağlama için kapsamlı destek içerir.</span><span class="sxs-lookup"><span data-stu-id="43c8d-108">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="43c8d-109">Daha fazla bilgi için bkz. [nasıl yapılır: Tasarımcıyı kullanarak verileri Windows Forms DataGridView denetimine bağlama](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="43c8d-109">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="43c8d-110">Bir DataGridView denetimini verilere bağlamak için:</span><span class="sxs-lookup"><span data-stu-id="43c8d-110">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="43c8d-111">Verileri alma ayrıntılarını işlemek için bir yöntem uygulayın.</span><span class="sxs-lookup"><span data-stu-id="43c8d-111">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="43c8d-112">Aşağıdaki kod örneği `GetData` , öğesini Başlatan bir yöntemi uygular <xref:System.Data.SqlClient.SqlDataAdapter> ve bunu doldurmak için kullanır <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="43c8d-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="43c8d-113">Daha sonra öğesini <xref:System.Data.DataTable> öğesine bağlar <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="43c8d-113">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="43c8d-114">Formun <xref:System.Windows.Forms.Form.Load> olay işleyicisinde, <xref:System.Windows.Forms.DataGridView> denetimini öğesine bağlayın <xref:System.Windows.Forms.BindingSource> ve `GetData` verileri almak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="43c8d-114">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="43c8d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="43c8d-115">Example</span></span>

<span data-ttu-id="43c8d-116">Bu kod örneği, bir Windows formundaki DataGridView denetimini doldurmak için bir veritabanından veri alır.</span><span class="sxs-lookup"><span data-stu-id="43c8d-116">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="43c8d-117">Formun Ayrıca verileri yeniden yükleme ve değişiklikleri veritabanına gönderme düğmeleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="43c8d-117">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="43c8d-118">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="43c8d-118">This example requires:</span></span>

- <span data-ttu-id="43c8d-119">Northwind SQL Server örnek veritabanına erişim.</span><span class="sxs-lookup"><span data-stu-id="43c8d-119">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="43c8d-120">Northwind örnek veritabanını yükleme hakkında daha fazla bilgi için bkz. [ADO.net Code örnekleri için örnek veritabanları edinme](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="43c8d-120">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="43c8d-121">Sisteme, System. Windows. Forms, System. Data ve System.Xml derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="43c8d-121">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="43c8d-122">Bu örneği derlemek ve çalıştırmak için, kodu yeni bir Windows Forms projesindeki *Form1* kod dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="43c8d-122">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="43c8d-123">C# veya Visual Basic komut satırından oluşturma hakkında bilgi için, bkz. [komut satırı oluşturma csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="43c8d-123">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="43c8d-124">`connectionString`Örnekteki değişkeni Northwind SQL Server örnek veritabanı bağlantınızın değerleriyle doldurun.</span><span class="sxs-lookup"><span data-stu-id="43c8d-124">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="43c8d-125">Tümleşik güvenlik olarak da bilinen Windows kimlik doğrulaması, veritabanına bağlanmak için bağlantı dizesinde parola depolamadan daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="43c8d-125">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="43c8d-126">Bağlantı güvenliği hakkında daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="43c8d-126">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="43c8d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43c8d-127">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="43c8d-128">Windows Forms DataGridView denetiminde verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="43c8d-128">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="43c8d-129">Bağlantı bilgilerini koruma</span><span class="sxs-lookup"><span data-stu-id="43c8d-129">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)

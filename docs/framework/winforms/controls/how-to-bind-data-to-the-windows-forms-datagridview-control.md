---
title: Verileri DataGridView Denetimine bağlama
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182270"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="39ddb-102">Nasıl yapılır: Verileri Windows Forms DataGridView denetimine bağlama</span><span class="sxs-lookup"><span data-stu-id="39ddb-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="39ddb-103">Denetim <xref:System.Windows.Forms.DataGridView> standart Windows Forms veri bağlama modelini destekler, böylece çeşitli veri kaynaklarına bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="39ddb-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="39ddb-104">Genellikle, veri kaynağı <xref:System.Windows.Forms.BindingSource> ile etkileşimi yöneten bir bağbağlanırsınız.</span><span class="sxs-lookup"><span data-stu-id="39ddb-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="39ddb-105">Verilerinizin <xref:System.Windows.Forms.BindingSource> konumunu seçerken veya değiştirirken size büyük esneklik sağlayan herhangi bir Windows Forms veri kaynağı olabilir.</span><span class="sxs-lookup"><span data-stu-id="39ddb-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="39ddb-106">Denetimin <xref:System.Windows.Forms.DataGridView> desteklediği veri kaynakları hakkında daha fazla bilgi için [DataGridView denetimine genel bakış'a](datagridview-control-overview-windows-forms.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="39ddb-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="39ddb-107">Visual Studio, DataGridView denetimine bağlanan veriler için kapsamlı bir desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="39ddb-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="39ddb-108">Daha fazla bilgi için [bkz: Verileri Tasarımcıyı kullanarak Windows Forms DataGridView denetimine bağla.](bind-data-to-the-datagrid-using-the-designer.md)</span><span class="sxs-lookup"><span data-stu-id="39ddb-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="39ddb-109">DataGridView denetimini verilere bağlamak için:</span><span class="sxs-lookup"><span data-stu-id="39ddb-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="39ddb-110">Verileri alma ayrıntılarını işlemek için bir yöntem uygulayın.</span><span class="sxs-lookup"><span data-stu-id="39ddb-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="39ddb-111">Aşağıdaki kod örneği, `GetData` a <xref:System.Data.SqlClient.SqlDataAdapter>' yı başlýlayan bir yöntem <xref:System.Data.DataTable>uygular ve bir .</span><span class="sxs-lookup"><span data-stu-id="39ddb-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="39ddb-112">Daha sonra <xref:System.Data.DataTable> bağlar <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="39ddb-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="39ddb-113">Formun olay <xref:System.Windows.Forms.Form.Load> <xref:System.Windows.Forms.DataGridView> işleyicisinde, denetimi <xref:System.Windows.Forms.BindingSource>,' ye bağla `GetData` ve verileri almak için yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="39ddb-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="39ddb-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="39ddb-114">Example</span></span>

<span data-ttu-id="39ddb-115">Bu tam kod örneği, Bir DataGridView denetimini Windows formunda doldurmak için veritabanından veri alır.</span><span class="sxs-lookup"><span data-stu-id="39ddb-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="39ddb-116">Formda ayrıca verileri yeniden yüklemek ve veritabanına değişiklik göndermek için düğmeler de vardır.</span><span class="sxs-lookup"><span data-stu-id="39ddb-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="39ddb-117">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="39ddb-117">This example requires:</span></span>

- <span data-ttu-id="39ddb-118">Northwind SQL Server örnek veritabanına erişim.</span><span class="sxs-lookup"><span data-stu-id="39ddb-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="39ddb-119">Northwind örnek veritabanını yükleme hakkında daha fazla bilgi için [ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="39ddb-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="39ddb-120">Sistem, System.Windows.Forms, System.Data ve System.Xml derlemelerine yapılan atıflar.</span><span class="sxs-lookup"><span data-stu-id="39ddb-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="39ddb-121">Bu örneği oluşturmak ve çalıştırmak için, kodu yeni bir Windows Forms projesinde *Form1* kod dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="39ddb-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="39ddb-122">C# veya Visual Basic komut satırından bina hakkında bilgi için [csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [Build komut satırına](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)sahip Komut satırı binasına bakın.</span><span class="sxs-lookup"><span data-stu-id="39ddb-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="39ddb-123">Örnekteki `connectionString` değişkeni Northwind SQL Server örnek veritabanı bağlantınızın değerleriyle doldurun.</span><span class="sxs-lookup"><span data-stu-id="39ddb-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="39ddb-124">Tümleşik güvenlik olarak da adlandırılan Windows Kimlik Doğrulama, veritabanına bağlanmanın bağlantı dizesinde parola depolamaktan daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="39ddb-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="39ddb-125">Bağlantı güvenliği hakkında daha fazla bilgi için [bkz.](../../data/adonet/protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="39ddb-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="39ddb-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39ddb-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="39ddb-127">Verileri Windows Forms DataGridView denetiminde görüntüleme</span><span class="sxs-lookup"><span data-stu-id="39ddb-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="39ddb-128">Bağlantı bilgilerini koruma</span><span class="sxs-lookup"><span data-stu-id="39ddb-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)

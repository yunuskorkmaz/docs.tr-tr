---
title: Verileri DataGridView denetimine bağlama
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: e2762bf363a469abf8c1e57b851d351c1cb41b62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745082"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="e0ee8-102">Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama</span><span class="sxs-lookup"><span data-stu-id="e0ee8-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="e0ee8-103"><xref:System.Windows.Forms.DataGridView> denetimi standart Windows Forms veri bağlama modelini destekler, bu nedenle çeşitli veri kaynaklarına bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="e0ee8-104">Genellikle, veri kaynağıyla etkileşimi yöneten bir <xref:System.Windows.Forms.BindingSource> bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="e0ee8-105"><xref:System.Windows.Forms.BindingSource>, verilerinizin konumunu seçerken veya değiştirirken size büyük bir esneklik sağlayan herhangi bir Windows Forms veri kaynağı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="e0ee8-106"><xref:System.Windows.Forms.DataGridView> denetiminin desteklediği veri kaynakları hakkında daha fazla bilgi için bkz. [DataGridView denetimine genel bakış](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e0ee8-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="e0ee8-107">Visual Studio, DataGridView denetimine veri bağlama için kapsamlı destek içerir.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="e0ee8-108">Daha fazla bilgi için bkz. [nasıl yapılır: Tasarımcıyı kullanarak verileri Windows Forms DataGridView denetimine bağlama](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e0ee8-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="e0ee8-109">Bir DataGridView denetimini verilere bağlamak için:</span><span class="sxs-lookup"><span data-stu-id="e0ee8-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="e0ee8-110">Verileri alma ayrıntılarını işlemek için bir yöntem uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="e0ee8-111">Aşağıdaki kod örneği, bir <xref:System.Data.SqlClient.SqlDataAdapter>Başlatan bir `GetData` yöntemi uygular ve <xref:System.Data.DataTable>doldurmak için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="e0ee8-112">Ardından <xref:System.Data.DataTable> <xref:System.Windows.Forms.BindingSource>bağlar.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span> 

2. <span data-ttu-id="e0ee8-113">Formun <xref:System.Windows.Forms.Form.Load> olay işleyicisinde, <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource>bağlayın ve verileri almak için `GetData` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="e0ee8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0ee8-114">Example</span></span>

<span data-ttu-id="e0ee8-115">Bu kod örneği, bir Windows formundaki DataGridView denetimini doldurmak için bir veritabanından veri alır.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="e0ee8-116">Formun Ayrıca verileri yeniden yükleme ve değişiklikleri veritabanına gönderme düğmeleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="e0ee8-117">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e0ee8-117">This example requires:</span></span> 

- <span data-ttu-id="e0ee8-118">Northwind SQL Server örnek veritabanına erişim.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="e0ee8-119">Northwind örnek veritabanını yükleme hakkında daha fazla bilgi için bkz. [ADO.net Code örnekleri için örnek veritabanları edinme](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e0ee8-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span> 

- <span data-ttu-id="e0ee8-120">Sisteme, System. Windows. Forms, System. Data ve System. xml derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="e0ee8-121">Bu örneği derlemek ve çalıştırmak için, kodu yeni bir Windows Forms projesindeki *Form1* kod dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="e0ee8-122">C# Veya Visual Basic komut satırından oluşturma hakkında bilgi için, bkz. [CSC. exe ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="e0ee8-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="e0ee8-123">Örnekteki `connectionString` değişkenini Northwind SQL Server örnek veritabanı bağlantınızın değerleriyle doldurun.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="e0ee8-124">Tümleşik güvenlik olarak da bilinen Windows kimlik doğrulaması, veritabanına bağlanmak için bağlantı dizesinde parola depolamadan daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="e0ee8-125">Bağlantı güvenliği hakkında daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="e0ee8-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e0ee8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0ee8-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="e0ee8-127">Windows Forms DataGridView denetiminde verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e0ee8-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e0ee8-128">Bağlantı bilgilerini koruma</span><span class="sxs-lookup"><span data-stu-id="e0ee8-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)

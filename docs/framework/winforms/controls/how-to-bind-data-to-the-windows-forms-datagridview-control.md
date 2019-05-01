---
title: 'Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama'
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e147109a64687177f201ad1e312fab56ea61d604
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010936"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="b0419-102">Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama</span><span class="sxs-lookup"><span data-stu-id="b0419-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="b0419-103"><xref:System.Windows.Forms.DataGridView> Denetimi, çeşitli veri kaynakları için bağlayabilirsiniz için standart Windows Forms veri bağlama modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="b0419-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="b0419-104">Genellikle, adlarınıza bir <xref:System.Windows.Forms.BindingSource> , veri kaynağı ile etkileşimi yönetir.</span><span class="sxs-lookup"><span data-stu-id="b0419-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="b0419-105"><xref:System.Windows.Forms.BindingSource> Seçerek ya da veri konumu değiştirirken büyük esneklik sağlayan bir Windows Forms veri kaynağı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b0419-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="b0419-106">Veri kaynakları hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> destekler, bkz [DataGridView denetimine genel bakış](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b0419-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="b0419-107">Visual Studio DataGridView denetimine veri bağlama için kapsamlı destek sunar.</span><span class="sxs-lookup"><span data-stu-id="b0419-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="b0419-108">Daha fazla bilgi için [nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetimine veri bağlama](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="b0419-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="b0419-109">DataGridView denetimine veri bağlama için:</span><span class="sxs-lookup"><span data-stu-id="b0419-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="b0419-110">Veri alma ayrıntılarını işlemek için bir yöntem uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b0419-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="b0419-111">Aşağıdaki kod örneğinde uygular bir `GetData` başlatan yöntem bir <xref:System.Data.SqlClient.SqlDataAdapter>ve doldurmak için kullandığı bir <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="b0419-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="b0419-112">Ardından bağlar <xref:System.Data.DataTable> için <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="b0419-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span> 

2. <span data-ttu-id="b0419-113">Formun <xref:System.Windows.Forms.Form.Load> olay işleyicisi, bağlama <xref:System.Windows.Forms.DataGridView> denetimini <xref:System.Windows.Forms.BindingSource>ve çağrı `GetData` verileri almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b0419-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="b0419-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0419-114">Example</span></span>

<span data-ttu-id="b0419-115">Bu tam kod örneği, bir Windows forma DataGridView denetiminde doldurmak için bir veritabanından verileri alır.</span><span class="sxs-lookup"><span data-stu-id="b0419-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="b0419-116">Form verileri yeniden yüklemek ve veritabanına değişiklikleri gönderme düğmeleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="b0419-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="b0419-117">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b0419-117">This example requires:</span></span> 

- <span data-ttu-id="b0419-118">Bir SQL Server Northwind örnek veritabanına erişim.</span><span class="sxs-lookup"><span data-stu-id="b0419-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="b0419-119">Northwind örnek veritabanını yükleme hakkında daha fazla bilgi için bkz. [örnek veritabanları ADO.NET için kod örneklerine](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="b0419-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span> 

- <span data-ttu-id="b0419-120">Sistem, System.Windows.Forms, System.Data ve System.Xml derlemesine ilişkin başvurular.</span><span class="sxs-lookup"><span data-stu-id="b0419-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="b0419-121">Derleme ve bu örneği çalıştırmak için kodun içine yapıştırın *Form1* kod dosyasına yeni bir Windows Forms projesi.</span><span class="sxs-lookup"><span data-stu-id="b0419-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="b0419-122">Binanın öğrenmek için C# veya bkz. Visual Basic komut satırı [csc.exe ile komut satırı derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="b0419-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="b0419-123">Doldurma `connectionString` örnekte SQL Server Northwind örnek veritabanı bağlantınız için değerleri değişken.</span><span class="sxs-lookup"><span data-stu-id="b0419-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="b0419-124">Windows kimlik doğrulama, tümleşik güvenlik olarak da bilinir, bağlantı dizesinde parola depolamak daha veritabanına bağlanmak için daha güvenli bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="b0419-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="b0419-125">Bağlantı güvenliği hakkında daha fazla bilgi için bkz: [bağlantı bilgilerini korumak](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="b0419-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b0419-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0419-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="b0419-127">Windows Forms DataGridView denetiminde veri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b0419-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b0419-128">Bağlantı bilgilerini koruma</span><span class="sxs-lookup"><span data-stu-id="b0419-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)

---
title: BindingSource bileşeniyle ADO.NET verilerini sıralama ve filtreleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742966"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="9c16c-102">Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="9c16c-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="9c16c-103"><xref:System.Windows.Forms.BindingSource> denetimin sıralama ve filtreleme özelliğini <xref:System.Windows.Forms.BindingSource.Sort%2A> ve <xref:System.Windows.Forms.BindingSource.Filter%2A> özellikleriyle kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c16c-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="9c16c-104">Temel alınan veri kaynağı bir <xref:System.ComponentModel.IBindingList>olduğunda basit sıralama uygulayabilir ve veri kaynağı bir <xref:System.ComponentModel.IBindingListView>olduğunda filtreleme ve gelişmiş sıralama uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c16c-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="9c16c-105"><xref:System.Windows.Forms.BindingSource.Sort%2A> özelliği için standart ADO.NET sözdizimi gerekir: veri kaynağındaki bir veri sütununun adını temsil eden bir dize ve sonra listenin artan veya azalan sırada sıralanması gerekip gerekmediğini belirtmek için `ASC` veya `DESC`.</span><span class="sxs-lookup"><span data-stu-id="9c16c-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard ADO.NET syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="9c16c-106">Her sütunu virgül ayırıcısıyla ayırarak gelişmiş sıralama veya birden çok sütunlu sıralama ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c16c-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="9c16c-107"><xref:System.Windows.Forms.BindingSource.Filter%2A> özelliği bir dize ifadesi alır.</span><span class="sxs-lookup"><span data-stu-id="9c16c-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c16c-108">Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="9c16c-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="9c16c-109">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="9c16c-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="9c16c-110">Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="9c16c-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="9c16c-111">BindingSource ile verileri filtrelemek için</span><span class="sxs-lookup"><span data-stu-id="9c16c-111">To filter data with the BindingSource</span></span>  
  
- <span data-ttu-id="9c16c-112"><xref:System.Windows.Forms.BindingSource.Filter%2A> özelliğini istediğiniz ifadeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9c16c-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="9c16c-113">Aşağıdaki kod örneğinde, ifadesi bir sütun adı ve ardından sütun için istediğiniz değeri izler.</span><span class="sxs-lookup"><span data-stu-id="9c16c-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="9c16c-114">BindingSource ile verileri sıralamak için</span><span class="sxs-lookup"><span data-stu-id="9c16c-114">To sort data with the BindingSource</span></span>  
  
1. <span data-ttu-id="9c16c-115"><xref:System.Windows.Forms.BindingSource.Sort%2A> özelliğini, ardından `ASC` veya `DESC` artan veya azalan sırada göstermek için istediğiniz sütun adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9c16c-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2. <span data-ttu-id="9c16c-116">Birden çok sütunu virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="9c16c-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="9c16c-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c16c-117">Example</span></span>  
 <span data-ttu-id="9c16c-118">Aşağıdaki kod örneği, Northwind örnek veritabanının Customers tablosundaki verileri bir <xref:System.Windows.Forms.DataGridView> denetimine yükler ve görünen verileri filtreleyerek sıralar.</span><span class="sxs-lookup"><span data-stu-id="9c16c-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9c16c-119">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="9c16c-119">Compiling the Code</span></span>  
 <span data-ttu-id="9c16c-120">Bu örneği çalıştırmak için kodu, `BindingSource1` adlı bir <xref:System.Windows.Forms.BindingSource> ve `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> içeren bir forma yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c16c-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="9c16c-121">Form için <xref:System.Windows.Forms.Form.Load> olayını işleyin ve Load olay işleyicisi yönteminde `InitializeSortedFilteredBindingSource` çağırın.</span><span class="sxs-lookup"><span data-stu-id="9c16c-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c16c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c16c-122">See also</span></span>

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- <span data-ttu-id="9c16c-123">[Nasıl yapılır: örnek veritabanları yüklemesi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9c16c-123">[How to: Install Sample Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span></span>
- [<span data-ttu-id="9c16c-124">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="9c16c-124">BindingSource Component</span></span>](bindingsource-component.md)

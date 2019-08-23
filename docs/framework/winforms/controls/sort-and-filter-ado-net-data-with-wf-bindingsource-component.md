---
title: 'Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme'
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
ms.openlocfilehash: ae331ca9e3fd2aed654659e11434454874eff8fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960420"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="ca22b-102">Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="ca22b-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="ca22b-103">Ve<xref:System.Windows.Forms.BindingSource.Sort%2A> <xref:System.Windows.Forms.BindingSource> özellikleriiledenetiminsıralamavefiltreleme<xref:System.Windows.Forms.BindingSource.Filter%2A> özelliğini kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca22b-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="ca22b-104">Temel alınan veri kaynağı bir <xref:System.ComponentModel.IBindingList>olduğunda basit sıralama uygulayabilir ve veri kaynağı bir <xref:System.ComponentModel.IBindingListView>olduğunda filtreleme ve gelişmiş sıralama uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca22b-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="ca22b-105">Özelliği için standart ADO.NET sözdizimi gerekir: veri kaynağındaki bir veri sütununun adını temsil eden bir dize ve `ASC` sonra `DESC` listenin artan veya azalan sırada sıralanması gerekip gerekmediğini belirtmek için. <xref:System.Windows.Forms.BindingSource.Sort%2A></span><span class="sxs-lookup"><span data-stu-id="ca22b-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard ADO.NET syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="ca22b-106">Her sütunu virgül ayırıcısıyla ayırarak gelişmiş sıralama veya birden çok sütunlu sıralama ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca22b-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="ca22b-107"><xref:System.Windows.Forms.BindingSource.Filter%2A> Özelliği bir dize ifadesi alır.</span><span class="sxs-lookup"><span data-stu-id="ca22b-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca22b-108">Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="ca22b-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="ca22b-109">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="ca22b-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="ca22b-110">Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="ca22b-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="ca22b-111">BindingSource ile verileri filtrelemek için</span><span class="sxs-lookup"><span data-stu-id="ca22b-111">To filter data with the BindingSource</span></span>  
  
- <span data-ttu-id="ca22b-112"><xref:System.Windows.Forms.BindingSource.Filter%2A> Özelliğini istediğiniz ifadeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ca22b-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="ca22b-113">Aşağıdaki kod örneğinde, ifadesi bir sütun adı ve ardından sütun için istediğiniz değeri izler.</span><span class="sxs-lookup"><span data-stu-id="ca22b-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="ca22b-114">BindingSource ile verileri sıralamak için</span><span class="sxs-lookup"><span data-stu-id="ca22b-114">To sort data with the BindingSource</span></span>  
  
1. <span data-ttu-id="ca22b-115">Özelliğini, daha `ASC` sonra istediğiniz sütun adı olarak ayarlayın veya `DESC` artan veya azalan sırayı belirtin. <xref:System.Windows.Forms.BindingSource.Sort%2A></span><span class="sxs-lookup"><span data-stu-id="ca22b-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2. <span data-ttu-id="ca22b-116">Birden çok sütunu virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="ca22b-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="ca22b-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca22b-117">Example</span></span>  
 <span data-ttu-id="ca22b-118">Aşağıdaki kod örneği, verileri Northwind örnek veritabanının Customers tablosundan bir <xref:System.Windows.Forms.DataGridView> denetime yükler ve görünen verileri filtreler ve sıralar.</span><span class="sxs-lookup"><span data-stu-id="ca22b-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca22b-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ca22b-119">Compiling the Code</span></span>  
 <span data-ttu-id="ca22b-120">Bu örneği çalıştırmak için, <xref:System.Windows.Forms.BindingSource> kodu Adlandırılmış `BindingSource1` ve <xref:System.Windows.Forms.DataGridView> adlı `dataGridView1`bir forma yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="ca22b-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="ca22b-121">Olay işleyicisini yükle yönteminde form ve çağrı `InitializeSortedFilteredBindingSource` için olayıişleyin.<xref:System.Windows.Forms.Form.Load></span><span class="sxs-lookup"><span data-stu-id="ca22b-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca22b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca22b-122">See also</span></span>

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- <span data-ttu-id="ca22b-123">[Nasıl yapılır: Örnek veritabanlarını yükler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="ca22b-123">[How to: Install Sample Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span></span>
- [<span data-ttu-id="ca22b-124">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ca22b-124">BindingSource Component</span></span>](bindingsource-component.md)

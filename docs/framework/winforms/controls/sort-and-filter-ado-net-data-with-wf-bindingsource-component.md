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
ms.openlocfilehash: d05cbdf63483c160603ee44f6b507edc2d13b170
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651936"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="6bd1d-102">Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="6bd1d-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="6bd1d-103">Sıralama ve filtreleme özelliğini kullanıma sunabileceğiniz <xref:System.Windows.Forms.BindingSource> aracılığıyla denetim <xref:System.Windows.Forms.BindingSource.Sort%2A> ve <xref:System.Windows.Forms.BindingSource.Filter%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="6bd1d-104">Temel alınan veri kaynağı olduğunda basit sıralama uygulayabileceğiniz bir <xref:System.ComponentModel.IBindingList>, ve gelişmiş veri kaynağı olduğunda sıralama ve filtreleme uygulayabilirsiniz bir <xref:System.ComponentModel.IBindingListView>.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="6bd1d-105"><xref:System.Windows.Forms.BindingSource.Sort%2A> Özelliği gerektiren standart [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] söz dizimi: bir veri kaynağındaki veri sütununun adını temsil eden bir dize tarafından izlenen `ASC` veya `DESC` listesini artan veya azalan olarak sıralanması gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="6bd1d-106">Gelişmiş sıralama veya bir virgül ayırıcısına ile her bir sütunun ayrılarak birden çok sütun sıralama ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="6bd1d-107"><xref:System.Windows.Forms.BindingSource.Filter%2A> Özelliği bir dize ifadesi alır.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bd1d-108">Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="6bd1d-109">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="6bd1d-110">Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="6bd1d-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="6bd1d-111">Verileri BindingSource ile filtreleme</span><span class="sxs-lookup"><span data-stu-id="6bd1d-111">To filter data with the BindingSource</span></span>  
  
- <span data-ttu-id="6bd1d-112">Ayarlama <xref:System.Windows.Forms.BindingSource.Filter%2A> özelliğini istediğiniz ifade.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="6bd1d-113">Aşağıdaki kod örneğinde sütun için istediğiniz değere göre ve ardından bir sütun adı bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="6bd1d-114">Verileri BindingSource ile sıralama</span><span class="sxs-lookup"><span data-stu-id="6bd1d-114">To sort data with the BindingSource</span></span>  
  
1. <span data-ttu-id="6bd1d-115">Ayarlama <xref:System.Windows.Forms.BindingSource.Sort%2A> özelliğini istediğiniz sütun adından `ASC` veya `DESC` artan veya azalan belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2. <span data-ttu-id="6bd1d-116">Birden çok sütun virgül ile ayırın.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="6bd1d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="6bd1d-117">Example</span></span>  
 <span data-ttu-id="6bd1d-118">Aşağıdaki kod örneği, Northwind örnek veritabanına, Müşteriler tablosundan verileri yükler. bir <xref:System.Windows.Forms.DataGridView> denetlemek, filtreler ve görüntülenen verileri sıralar.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6bd1d-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6bd1d-119">Compiling the Code</span></span>  
 <span data-ttu-id="6bd1d-120">Bu örneği çalıştırmak için kodu içeren bir biçime yapıştırın bir <xref:System.Windows.Forms.BindingSource> adlı `BindingSource1` ve <xref:System.Windows.Forms.DataGridView> adlı `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="6bd1d-121">Tanıtıcı <xref:System.Windows.Forms.Form.Load> olay formu ve çağrı `InitializeSortedFilteredBindingSource` yük olay işleyicisi yönteminde.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd1d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bd1d-122">See also</span></span>

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- <span data-ttu-id="6bd1d-123">[Nasıl yapılır: Örnek veritabanlarını yüklemek](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6bd1d-123">[How to: Install Sample Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span></span>
- [<span data-ttu-id="6bd1d-124">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="6bd1d-124">BindingSource Component</span></span>](bindingsource-component.md)

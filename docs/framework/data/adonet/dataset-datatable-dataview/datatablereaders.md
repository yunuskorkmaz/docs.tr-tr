---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785348"
---
# <a name="datatablereaders"></a><span data-ttu-id="ac8c5-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="ac8c5-102">DataTableReaders</span></span>
<span data-ttu-id="ac8c5-103">, <xref:System.Data.DataTableReader> Bir veya daha fazla salt <xref:System.Data.DataTable> okuma, <xref:System.Data.DataSet> yalnızca ileri bir sonuç kümesi biçiminde bir veya bir veya ' nin içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="ac8c5-104">**DataTable**'Dan bir **DataTableReader** oluşturduğunuzda, sonuçta elde edilen **DataTableReader** nesnesi, oluşturulduğu **DataTable** ile aynı verilere sahip bir sonuç kümesi içerir, ancak şu şekilde işaretlenmiş satırlar hariç miyor.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="ac8c5-105">Sütunlar, özgün **DataTable**ile aynı sırada görünür.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="ac8c5-106">**DataTableReader** , çağırarak <xref:System.Data.DataSet.CreateDataReader%2A>oluşturulduysa birden çok sonuç kümesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="ac8c5-107">Sonuçlar, **veri kümesi** nesnesinin <xref:System.Data.DataSet.Tables%2A> koleksiyonundaki **DataTable** ile aynı sıralardır.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac8c5-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ac8c5-108">In This Section</span></span>  
 [<span data-ttu-id="ac8c5-109">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac8c5-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="ac8c5-110">**DataTableReader** nesnesinin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="ac8c5-111">DataTable İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="ac8c5-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="ac8c5-112">**DataTableReader**içerikleri arasında gezinmek için **Read** yönteminin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8c5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac8c5-113">See also</span></span>

- [<span data-ttu-id="ac8c5-114">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ac8c5-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="ac8c5-115">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ac8c5-115">ADO.NET Overview</span></span>](../ado-net-overview.md)

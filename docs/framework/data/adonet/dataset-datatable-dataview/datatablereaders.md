---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1ff7868b59c6fdc4e6c443be1b831accc84f36a6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203822"
---
# <a name="datatablereaders"></a><span data-ttu-id="1e981-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="1e981-102">DataTableReaders</span></span>
<span data-ttu-id="1e981-103">, <xref:System.Data.DataTableReader> Bir veya daha fazla salt <xref:System.Data.DataTable> okuma, <xref:System.Data.DataSet> yalnızca ileri bir sonuç kümesi biçiminde bir veya bir veya ' nin içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e981-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="1e981-104">**DataTable**'Dan bir **DataTableReader** oluşturduğunuzda, sonuçta elde edilen **DataTableReader** nesnesi, oluşturulduğu **DataTable** ile aynı verilere sahip bir sonuç kümesi içerir, ancak şu şekilde işaretlenmiş satırlar hariç miyor.</span><span class="sxs-lookup"><span data-stu-id="1e981-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="1e981-105">Sütunlar, özgün **DataTable**ile aynı sırada görünür.</span><span class="sxs-lookup"><span data-stu-id="1e981-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="1e981-106">**DataTableReader** , çağırarak <xref:System.Data.DataSet.CreateDataReader%2A>oluşturulduysa birden çok sonuç kümesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1e981-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="1e981-107">Sonuçlar, **veri kümesi** nesnesinin <xref:System.Data.DataSet.Tables%2A> koleksiyonundaki **DataTable** ile aynı sıralardır.</span><span class="sxs-lookup"><span data-stu-id="1e981-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e981-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1e981-108">In This Section</span></span>  
 [<span data-ttu-id="1e981-109">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e981-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="1e981-110">**DataTableReader** nesnesinin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="1e981-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="1e981-111">DataTable İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="1e981-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="1e981-112">**DataTableReader**içerikleri arasında gezinmek için **Read** yönteminin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1e981-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e981-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e981-113">See also</span></span>

- [<span data-ttu-id="1e981-114">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1e981-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="1e981-115">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="1e981-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

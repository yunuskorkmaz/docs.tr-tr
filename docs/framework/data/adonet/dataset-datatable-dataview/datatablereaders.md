---
description: 'Daha fazla bilgi edinin: DataTableReaders'
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: b3e85ae05c07af18fe6219602b5b40f50a9fbc8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652607"
---
# <a name="datatablereaders"></a><span data-ttu-id="302ce-103">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="302ce-103">DataTableReaders</span></span>

<span data-ttu-id="302ce-104">, <xref:System.Data.DataTableReader> Bir veya <xref:System.Data.DataTable> <xref:System.Data.DataSet> daha fazla salt okuma, yalnızca ileri bir sonuç kümesi biçiminde bir veya bir veya ' nin içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="302ce-104">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="302ce-105">**DataTable**'Dan bir **DataTableReader** oluşturduğunuzda, sonuçta elde edilen **DataTableReader** nesnesi, silindiği **DataTable** ile aynı veriye sahip bir sonuç kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="302ce-105">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="302ce-106">Sütunlar, özgün **DataTable** ile aynı sırada görünür.</span><span class="sxs-lookup"><span data-stu-id="302ce-106">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="302ce-107">**DataTableReader** , çağırarak oluşturulduysa birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A> .</span><span class="sxs-lookup"><span data-stu-id="302ce-107">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="302ce-108">Sonuçlar, **veri kümesi** nesnesinin koleksiyonundaki **DataTable** ile aynı sıralardır <xref:System.Data.DataSet.Tables%2A> .</span><span class="sxs-lookup"><span data-stu-id="302ce-108">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="302ce-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="302ce-109">In This Section</span></span>  

 [<span data-ttu-id="302ce-110">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="302ce-110">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="302ce-111">**DataTableReader** nesnesinin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="302ce-111">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="302ce-112">DataTable İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="302ce-112">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="302ce-113">**DataTableReader** içerikleri arasında gezinmek için **Read** yönteminin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="302ce-113">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="302ce-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="302ce-114">See also</span></span>

- [<span data-ttu-id="302ce-115">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="302ce-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="302ce-116">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="302ce-116">ADO.NET Overview</span></span>](../ado-net-overview.md)

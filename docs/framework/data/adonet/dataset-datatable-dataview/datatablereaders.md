---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 911a45dad3d5d82ab5e5752b1c12f7d8a6ab1563
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202324"
---
# <a name="datatablereaders"></a><span data-ttu-id="f50cf-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="f50cf-102">DataTableReaders</span></span>

<span data-ttu-id="f50cf-103">, <xref:System.Data.DataTableReader> Bir veya <xref:System.Data.DataTable> <xref:System.Data.DataSet> daha fazla salt okuma, yalnızca ileri bir sonuç kümesi biçiminde bir veya bir veya ' nin içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f50cf-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="f50cf-104">**DataTable**'Dan bir **DataTableReader** oluşturduğunuzda, sonuçta elde edilen **DataTableReader** nesnesi, silindiği **DataTable** ile aynı veriye sahip bir sonuç kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="f50cf-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="f50cf-105">Sütunlar, özgün **DataTable**ile aynı sırada görünür.</span><span class="sxs-lookup"><span data-stu-id="f50cf-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="f50cf-106">**DataTableReader** , çağırarak oluşturulduysa birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A> .</span><span class="sxs-lookup"><span data-stu-id="f50cf-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="f50cf-107">Sonuçlar, **veri kümesi** nesnesinin koleksiyonundaki **DataTable** ile aynı sıralardır <xref:System.Data.DataSet.Tables%2A> .</span><span class="sxs-lookup"><span data-stu-id="f50cf-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f50cf-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f50cf-108">In This Section</span></span>  

 [<span data-ttu-id="f50cf-109">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f50cf-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="f50cf-110">**DataTableReader** nesnesinin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="f50cf-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="f50cf-111">DataTable İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="f50cf-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="f50cf-112">**DataTableReader**içerikleri arasında gezinmek için **Read** yönteminin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f50cf-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50cf-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f50cf-113">See also</span></span>

- [<span data-ttu-id="f50cf-114">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f50cf-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="f50cf-115">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f50cf-115">ADO.NET Overview</span></span>](../ado-net-overview.md)

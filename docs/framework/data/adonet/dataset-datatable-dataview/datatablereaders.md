---
title: DataTableReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0e3f3da6554239b4f04e244d3339a4280e1add85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="datatablereaders"></a><span data-ttu-id="caaf1-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="caaf1-102">DataTableReaders</span></span>
<span data-ttu-id="caaf1-103"><xref:System.Data.DataTableReader> İçeriğini sunan bir <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> bir veya daha fazla salt okunur, yalnızca ileri sonuç biçiminde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="caaf1-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="caaf1-104">Oluştururken bir **DataTableReader** gelen bir **DataTable**, elde edilen **DataTableReader** nesnesini içeren bir sonuç aynı veri kümesi  **DataTable** hangi, silinmiş olarak işaretlenmiş herhangi bir satır dışında oluşturulduğu gelen.</span><span class="sxs-lookup"><span data-stu-id="caaf1-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="caaf1-105">Özgün olduğu gibi aynı sırada sütunları görünmesi **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="caaf1-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="caaf1-106">A **DataTableReader** çağırarak oluşturulduysa, birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="caaf1-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="caaf1-107">Sonuçlar, aynı sırada bulunan **DataTables** içinde **DataSet** nesnenin <xref:System.Data.DataSet.Tables%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="caaf1-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="caaf1-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="caaf1-108">In This Section</span></span>  
 [<span data-ttu-id="caaf1-109">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="caaf1-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="caaf1-110">Nasıl oluşturulacağı açıklanır bir **DataTableReader** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="caaf1-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="caaf1-111">DataTable İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="caaf1-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="caaf1-112">Kullanımını açıklar **okuma** içeriğini taşımak için yöntemi bir **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="caaf1-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caaf1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="caaf1-113">See Also</span></span>  
 [<span data-ttu-id="caaf1-114">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="caaf1-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="caaf1-115">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="caaf1-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

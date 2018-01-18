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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b5160f5a2c68cab798dde154275c062e2bf31739
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="datatablereaders"></a><span data-ttu-id="70079-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="70079-102">DataTableReaders</span></span>
<span data-ttu-id="70079-103"><xref:System.Data.DataTableReader> İçeriğini sunan bir <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> bir veya daha fazla salt okunur, yalnızca ileri sonuç biçiminde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="70079-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="70079-104">Oluştururken bir **DataTableReader** gelen bir **DataTable**, elde edilen **DataTableReader** nesnesini içeren bir sonuç aynı veri kümesi  **DataTable** hangi, silinmiş olarak işaretlenmiş herhangi bir satır dışında oluşturulduğu gelen.</span><span class="sxs-lookup"><span data-stu-id="70079-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="70079-105">Özgün olduğu gibi aynı sırada sütunları görünmesi **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="70079-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="70079-106">A **DataTableReader** çağırarak oluşturulduysa, birden çok sonuç kümesi içerebilir <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="70079-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="70079-107">Sonuçlar, aynı sırada bulunan **DataTables** içinde **DataSet** nesnenin <xref:System.Data.DataSet.Tables%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="70079-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70079-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="70079-108">In This Section</span></span>  
 [<span data-ttu-id="70079-109">DataReader Oluşturma</span><span class="sxs-lookup"><span data-stu-id="70079-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="70079-110">Nasıl oluşturulacağı açıklanır bir **DataTableReader** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="70079-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="70079-111">DataTable İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="70079-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="70079-112">Kullanımını açıklar **okuma** içeriğini taşımak için yöntemi bir **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="70079-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70079-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70079-113">See Also</span></span>  
 [<span data-ttu-id="70079-114">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="70079-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="70079-115">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="70079-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

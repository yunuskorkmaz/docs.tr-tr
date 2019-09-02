---
title: DataTable İçinde Gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: b5837d647b72f8dd17c4a6d3664faf8976243d36
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204552"
---
# <a name="navigating-datatables"></a><span data-ttu-id="03e12-102">DataTable İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="03e12-102">Navigating DataTables</span></span>
<span data-ttu-id="03e12-103">, <xref:System.Data.DataTableReader> Bir veya daha fazla <xref:System.Data.DataTable> nesnenin içeriğini bir veya daha fazla salt okunurdur, salt ileri bir sonuç kümesi biçiminde edinir.</span><span class="sxs-lookup"><span data-stu-id="03e12-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="03e12-104"><xref:System.Data.DataTableReader> ,<xref:System.Data.DataSet.CreateDataReader%2A> Yöntemi kullanılarak oluşturulduysa, birden çok sonuç kümesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="03e12-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="03e12-105">Birden fazla sonuç kümesi olduğunda, <xref:System.Data.DataTableReader.NextResult%2A> yöntemi imleci bir sonraki sonuç kümesine ilerletir.</span><span class="sxs-lookup"><span data-stu-id="03e12-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="03e12-106">Bu yalnızca ileri bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="03e12-106">This is a forward-only process.</span></span> <span data-ttu-id="03e12-107">Önceki bir sonuç kümesine dönmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="03e12-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03e12-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="03e12-108">Example</span></span>  
 <span data-ttu-id="03e12-109">Aşağıdaki örnekte, `TestConstructor` yöntemi iki <xref:System.Data.DataTable> örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="03e12-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="03e12-110"><xref:System.Data.DataTableReader> Sınıf için bu oluşturucuyu göstermek amacıyla örnek, iki **DataTable**içeren bir diziyi temel alan yeni bir **DataTableReader** oluşturur ve basit bir işlem gerçekleştirir ve içeriği ilk birkaç kez yazdırıyor Konsol penceresine sütunlar.</span><span class="sxs-lookup"><span data-stu-id="03e12-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="03e12-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03e12-111">See also</span></span>

- [<span data-ttu-id="03e12-112">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="03e12-112">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="03e12-113">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="03e12-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

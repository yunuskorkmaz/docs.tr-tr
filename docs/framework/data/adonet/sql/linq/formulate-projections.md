---
title: "Projeksiyonlar düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bb22ddd4882d9885c55301a6fdc6a0eb336b49af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="formulate-projections"></a><span data-ttu-id="a2dea-102">Projeksiyonlar düzenleme</span><span class="sxs-lookup"><span data-stu-id="a2dea-102">Formulate Projections</span></span>
<span data-ttu-id="a2dea-103">Aşağıdaki örneklerde gösterildiği nasıl `select` deyimi C# ve `Select` deyiminde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] form sorgu tahminleri için diğer özelliklerle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2dea-103">The following examples show how the `select` statement in C# and `Select` statement in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2dea-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dea-104">Example</span></span>  
 <span data-ttu-id="a2dea-105">Aşağıdaki örnek kullanır `Select` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` yan tümcesinde C#) için kişi adı bir dizi döndürülecek `Customers`.</span><span class="sxs-lookup"><span data-stu-id="a2dea-105">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="a2dea-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dea-106">Example</span></span>  
 <span data-ttu-id="a2dea-107">Aşağıdaki örnek kullanır `Select` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` yan tümcesinde C#) ve *anonim türler* kişi adlarının dizisini döndürür ve telefon numaraları için `Customers`.</span><span class="sxs-lookup"><span data-stu-id="a2dea-107">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="a2dea-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dea-108">Example</span></span>  
 <span data-ttu-id="a2dea-109">Aşağıdaki örnek kullanır `Select` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` yan tümcesinde C#) ve *anonim türler* adlarının dizisini döndürür ve çalışanlar için telefonu numaraları.</span><span class="sxs-lookup"><span data-stu-id="a2dea-109">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="a2dea-110">`FirstName` Ve `LastName` alanları tek bir alana birleştirilir (`Name`) ve `HomePhone` alan yeniden adlandırılamaz `Phone` elde edilen sıralı.</span><span class="sxs-lookup"><span data-stu-id="a2dea-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="a2dea-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dea-111">Example</span></span>  
 <span data-ttu-id="a2dea-112">Aşağıdaki örnek kullanır `Select` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` yan tümcesinde C#) ve *anonim türler* tüm bir dizi döndürülecek `ProductID`s ve adlı hesaplanan değeri `HalfPrice`.</span><span class="sxs-lookup"><span data-stu-id="a2dea-112">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="a2dea-113">Bu değer ayarlanırsa `UnitPrice` 2 tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="a2dea-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="a2dea-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dea-114">Example</span></span>  
 <span data-ttu-id="a2dea-115">Aşağıdaki örnek kullanır `Select` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` yan tümcesinde C#) ve bir *koşullu ifade* bir dizi ürün adı ve ürün kullanılabilirlik dönün.</span><span class="sxs-lookup"><span data-stu-id="a2dea-115">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="a2dea-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dea-116">Example</span></span>  
 <span data-ttu-id="a2dea-117">Aşağıdaki örnek kullanan bir [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` yan tümcesi (`select` yan tümcesinde C#) ve bir *türü bilinen* bir dizi çalışanların adlarını döndürmek için (ad).</span><span class="sxs-lookup"><span data-stu-id="a2dea-117">The following example uses a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="a2dea-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dea-118">Example</span></span>  
 <span data-ttu-id="a2dea-119">Aşağıdaki örnek kullanır `Select` ve `Where` içinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` ve `where` C#) döndürmek için bir *sırası filtre* Londra müşteriler için kişi adları.</span><span class="sxs-lookup"><span data-stu-id="a2dea-119">The following example uses `Select` and `Where` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="a2dea-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dea-120">Example</span></span>  
 <span data-ttu-id="a2dea-121">Aşağıdaki örnek kullanan bir `Select` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` yan tümcesinde C#) ve *anonim türler* döndürmek için bir *alt şeklinde* müşteriler ilgili veriler.</span><span class="sxs-lookup"><span data-stu-id="a2dea-121">The following example uses a `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="a2dea-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2dea-122">Example</span></span>  
 <span data-ttu-id="a2dea-123">Aşağıdaki örnek, aşağıdaki sonuçları döndürmek için iç içe geçmiş sorgular kullanır:</span><span class="sxs-lookup"><span data-stu-id="a2dea-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="a2dea-124">Tüm siparişler ve bunların karşılık gelen bir dizi `OrderID`s.</span><span class="sxs-lookup"><span data-stu-id="a2dea-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="a2dea-125">Bir değişkene bir indirim siparişi öğeler.</span><span class="sxs-lookup"><span data-stu-id="a2dea-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="a2dea-126">Sevkiyat maliyetini dahil edilmezse kaydedilen para miktarı.</span><span class="sxs-lookup"><span data-stu-id="a2dea-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="a2dea-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2dea-127">See Also</span></span>  
 [<span data-ttu-id="a2dea-128">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="a2dea-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)

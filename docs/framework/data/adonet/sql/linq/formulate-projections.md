---
description: 'Daha fazla bilgi edinin: Bu projeksiyonlar'
title: Projeksiyonlar Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 591bc175426f08aa4273376e4c5efe370d2be756
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672081"
---
# <a name="formulate-projections"></a><span data-ttu-id="b9216-103">Projeksiyonlar Düzenleme</span><span class="sxs-lookup"><span data-stu-id="b9216-103">Formulate Projections</span></span>

<span data-ttu-id="b9216-104">Aşağıdaki örneklerde, `select` C# ve `Select` Visual Basic içindeki deyimin, sorgu projeksiyonlarını biçimlendirmek için diğer özelliklerle nasıl birleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9216-104">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9216-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9216-105">Example</span></span>  

 <span data-ttu-id="b9216-106">Aşağıdaki örnek, `Select` `select` için bir dizi iletişim adı döndürmek üzere Visual Basic (C# ' deki yan tümce) içinde yan tümcesini kullanır `Customers` .</span><span class="sxs-lookup"><span data-stu-id="b9216-106">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="b9216-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9216-107">Example</span></span>  

 <span data-ttu-id="b9216-108">Aşağıdaki örnek, `Select` `select` için bir dizi iletişim adı ve telefon numarası döndürmek üzere Visual Basic (C# ' deki yan tümce) ve *anonim türler* içinde yan tümcesini kullanır `Customers` .</span><span class="sxs-lookup"><span data-stu-id="b9216-108">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="b9216-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9216-109">Example</span></span>  

 <span data-ttu-id="b9216-110">Aşağıdaki örnek, `Select` `select` çalışanlar için bir ad ve telefon numarası sırası döndürmek üzere Visual Basic (C# ' deki yan tümce) ve *anonim türler* içinde yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9216-110">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="b9216-111">`FirstName`Ve `LastName` alanları tek bir alan () içinde birleştirilir `Name` ve alan, `HomePhone` `Phone` sonuçta elde edilen dizide olarak yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b9216-111">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="b9216-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9216-112">Example</span></span>  

 <span data-ttu-id="b9216-113">Aşağıdaki örnek, `Select` Visual Basic ( `select` C# ' deki yan tümce) ve *anonim türler* içindeki yan tümcesini ve ' nin bir dizisini `ProductID` ve adında bir hesaplanan değeri kullanır `HalfPrice` .</span><span class="sxs-lookup"><span data-stu-id="b9216-113">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="b9216-114">Bu değer `UnitPrice` 2 ile bölünmüş olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b9216-114">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="b9216-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9216-115">Example</span></span>  

 <span data-ttu-id="b9216-116">Aşağıdaki örnek, bir `Select` `select` ürün adı ve ürün kullanılabilirliği dizisi döndürmek için Visual Basic (C# ' deki yan tümce) ve *koşul deyimi* içinde yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9216-116">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="b9216-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9216-117">Example</span></span>  

 <span data-ttu-id="b9216-118">Aşağıdaki örnek, `Select` çalışanların adlarının bir dizisini döndürmek için bir Visual Basic yan tümcesini ( `select` C# içinde yan tümce) ve *bilinen bir türü* (adı) kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9216-118">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="b9216-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9216-119">Example</span></span>  

 <span data-ttu-id="b9216-120">Aşağıdaki örnek, `Select` `Where` `select` `where` Londra 'daki müşterilere yönelik olarak *filtrelenmiş bir dizi* iletişim adı döndürmek için Visual Basic (ve C# ' de) kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9216-120">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="b9216-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9216-121">Example</span></span>  

 <span data-ttu-id="b9216-122">Aşağıdaki örnek, `Select` `select` müşteriler hakkında verilerin *şekillendirilmiş bir alt kümesini* döndürmek için Visual Basic (C# ' deki yan tümce) ve *anonim türler* ' de bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9216-122">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="b9216-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9216-123">Example</span></span>  

 <span data-ttu-id="b9216-124">Aşağıdaki örnek, aşağıdaki sonuçları döndürmek için iç içe geçmiş sorguları kullanır:</span><span class="sxs-lookup"><span data-stu-id="b9216-124">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="b9216-125">Tüm siparişlerin ve bunlara karşılık gelen sözleşmelerinin sırası `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="b9216-125">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="b9216-126">Bir iskontonun bulunduğu sıradaki öğelerin alt sırası.</span><span class="sxs-lookup"><span data-stu-id="b9216-126">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="b9216-127">Sevkiyat maliyeti dahil değilse kaydedilen para miktarı.</span><span class="sxs-lookup"><span data-stu-id="b9216-127">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="b9216-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9216-128">See also</span></span>

- [<span data-ttu-id="b9216-129">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="b9216-129">Query Examples</span></span>](query-examples.md)

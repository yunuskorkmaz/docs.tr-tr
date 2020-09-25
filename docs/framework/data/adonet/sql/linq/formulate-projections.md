---
title: Projeksiyonlar Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f0bc6dfcff7778ebc7156cbb039e13570c90467b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194407"
---
# <a name="formulate-projections"></a><span data-ttu-id="8fbc2-102">Projeksiyonlar Düzenleme</span><span class="sxs-lookup"><span data-stu-id="8fbc2-102">Formulate Projections</span></span>

<span data-ttu-id="8fbc2-103">Aşağıdaki örneklerde, `select` C# ve `Select` Visual Basic içindeki deyimin, sorgu projeksiyonlarını biçimlendirmek için diğer özelliklerle nasıl birleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fbc2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fbc2-104">Example</span></span>  

 <span data-ttu-id="8fbc2-105">Aşağıdaki örnek, `Select` `select` için bir dizi iletişim adı döndürmek üzere Visual Basic (C# ' deki yan tümce) içinde yan tümcesini kullanır `Customers` .</span><span class="sxs-lookup"><span data-stu-id="8fbc2-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="8fbc2-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fbc2-106">Example</span></span>  

 <span data-ttu-id="8fbc2-107">Aşağıdaki örnek, `Select` `select` için bir dizi iletişim adı ve telefon numarası döndürmek üzere Visual Basic (C# ' deki yan tümce) ve *anonim türler* içinde yan tümcesini kullanır `Customers` .</span><span class="sxs-lookup"><span data-stu-id="8fbc2-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="8fbc2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fbc2-108">Example</span></span>  

 <span data-ttu-id="8fbc2-109">Aşağıdaki örnek, `Select` `select` çalışanlar için bir ad ve telefon numarası sırası döndürmek üzere Visual Basic (C# ' deki yan tümce) ve *anonim türler* içinde yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="8fbc2-110">`FirstName`Ve `LastName` alanları tek bir alan () içinde birleştirilir `Name` ve alan, `HomePhone` `Phone` sonuçta elde edilen dizide olarak yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="8fbc2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fbc2-111">Example</span></span>  

 <span data-ttu-id="8fbc2-112">Aşağıdaki örnek, `Select` Visual Basic ( `select` C# ' deki yan tümce) ve *anonim türler* içindeki yan tümcesini ve ' nin bir dizisini `ProductID` ve adında bir hesaplanan değeri kullanır `HalfPrice` .</span><span class="sxs-lookup"><span data-stu-id="8fbc2-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="8fbc2-113">Bu değer `UnitPrice` 2 ile bölünmüş olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="8fbc2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fbc2-114">Example</span></span>  

 <span data-ttu-id="8fbc2-115">Aşağıdaki örnek, bir `Select` `select` ürün adı ve ürün kullanılabilirliği dizisi döndürmek için Visual Basic (C# ' deki yan tümce) ve *koşul deyimi* içinde yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="8fbc2-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fbc2-116">Example</span></span>  

 <span data-ttu-id="8fbc2-117">Aşağıdaki örnek, `Select` çalışanların adlarının bir dizisini döndürmek için bir Visual Basic yan tümcesini ( `select` C# içinde yan tümce) ve *bilinen bir türü* (adı) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="8fbc2-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fbc2-118">Example</span></span>  

 <span data-ttu-id="8fbc2-119">Aşağıdaki örnek, `Select` `Where` `select` `where` Londra 'daki müşterilere yönelik olarak *filtrelenmiş bir dizi* iletişim adı döndürmek için Visual Basic (ve C# ' de) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="8fbc2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fbc2-120">Example</span></span>  

 <span data-ttu-id="8fbc2-121">Aşağıdaki örnek, `Select` `select` müşteriler hakkında verilerin *şekillendirilmiş bir alt kümesini* döndürmek için Visual Basic (C# ' deki yan tümce) ve *anonim türler* ' de bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="8fbc2-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fbc2-122">Example</span></span>  

 <span data-ttu-id="8fbc2-123">Aşağıdaki örnek, aşağıdaki sonuçları döndürmek için iç içe geçmiş sorguları kullanır:</span><span class="sxs-lookup"><span data-stu-id="8fbc2-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="8fbc2-124">Tüm siparişlerin ve bunlara karşılık gelen sözleşmelerinin sırası `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="8fbc2-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="8fbc2-125">Bir iskontonun bulunduğu sıradaki öğelerin alt sırası.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="8fbc2-126">Sevkiyat maliyeti dahil değilse kaydedilen para miktarı.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="8fbc2-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fbc2-127">See also</span></span>

- [<span data-ttu-id="8fbc2-128">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="8fbc2-128">Query Examples</span></span>](query-examples.md)

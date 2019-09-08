---
title: Projeksiyonlar Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793824"
---
# <a name="formulate-projections"></a><span data-ttu-id="cf87c-102">Projeksiyonlar Düzenleme</span><span class="sxs-lookup"><span data-stu-id="cf87c-102">Formulate Projections</span></span>
<span data-ttu-id="cf87c-103">Aşağıdaki örneklerde, içindeki Visual Basic `select` C# ve `Select` içindeki deyimin, sorgu projeksiyonlarını biçimlendirmek için diğer özelliklerle nasıl birleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cf87c-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf87c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf87c-104">Example</span></span>  
 <span data-ttu-id="cf87c-105">`Select` Aşağıdaki örnek, için`select` C# birdiziiletişimadıdöndürmeküzereVisualBasic(içindekiyantümce)içindeyantümcesini`Customers`kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf87c-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="cf87c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf87c-106">Example</span></span>  
 <span data-ttu-id="cf87c-107">Aşağıdaki örnek, için `Select` C#`select` bir`Customers`dizi iletişim adı ve telefon numarası döndürmek üzere Visual Basic (içindeki yan tümce) ve *anonim türlerde* yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf87c-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="cf87c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf87c-108">Example</span></span>  
 <span data-ttu-id="cf87c-109">Aşağıdaki örnek, çalışanlar için `Select` bir ad ve telefon`select` numarası sırası C#döndürmek üzere Visual Basic (içindeki yan tümce) ve *anonim türlerde* yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf87c-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="cf87c-110">`Name` `Phone` Ve alanları tek bir alan`HomePhone` () içinde birleştirilir ve alan, sonuçta elde edilen dizide olarak yeniden adlandırılır. `LastName` `FirstName`</span><span class="sxs-lookup"><span data-stu-id="cf87c-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="cf87c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf87c-111">Example</span></span>  
 <span data-ttu-id="cf87c-112">Aşağıdaki örnek, içinde `Select` C#Visual Basic (`select` yan tümce) ve *anonim türler* içindeki yan tümcesini kullanarak tüm `ProductID`s 'leri ve adlı `HalfPrice`bir hesaplanmış değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf87c-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="cf87c-113">Bu değer 2 ile `UnitPrice` bölünmüş olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cf87c-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="cf87c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf87c-114">Example</span></span>  
 <span data-ttu-id="cf87c-115">Aşağıdaki örnek, bir ürün `Select` adı ve ürün kullanılabilirliği`select` dizisi döndürmek C#için Visual Basic (içindeki yan tümce) ve *koşul deyimi* içinde yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf87c-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="cf87c-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf87c-116">Example</span></span>  
 <span data-ttu-id="cf87c-117">Aşağıdaki örnek, çalışanların adlarının bir `Select` dizisini döndürmek`select` için bir C#Visual Basic yan tümcesini (içinde yan tümce) ve *bilinen bir türü* (adı) kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf87c-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="cf87c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf87c-118">Example</span></span>  
 <span data-ttu-id="cf87c-119">Aşağıdaki örnek, Londra `Select` 'daki `Where` müşterilere yönelik olarak`select` filtrelenmiş `where` bir C#iletişim adları *dizisi* döndürmek için Visual Basic (ve içinde) kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf87c-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="cf87c-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf87c-120">Example</span></span>  
 <span data-ttu-id="cf87c-121">Aşağıdaki örnek, müşteriler hakkında `Select` verilerin *şekillendirilmiş bir alt kümesini* döndürmek C#için Visual Basic (`select` içindeki yan tümce) ve *anonim türlerde* bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf87c-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="cf87c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf87c-122">Example</span></span>  
 <span data-ttu-id="cf87c-123">Aşağıdaki örnek, aşağıdaki sonuçları döndürmek için iç içe geçmiş sorguları kullanır:</span><span class="sxs-lookup"><span data-stu-id="cf87c-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="cf87c-124">Tüm siparişlerin ve bunlara karşılık gelen `OrderID`sözleşmelerinin sırası.</span><span class="sxs-lookup"><span data-stu-id="cf87c-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="cf87c-125">Bir iskontonun bulunduğu sıradaki öğelerin alt sırası.</span><span class="sxs-lookup"><span data-stu-id="cf87c-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="cf87c-126">Sevkiyat maliyeti dahil değilse kaydedilen para miktarı.</span><span class="sxs-lookup"><span data-stu-id="cf87c-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="cf87c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf87c-127">See also</span></span>

- [<span data-ttu-id="cf87c-128">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="cf87c-128">Query Examples</span></span>](query-examples.md)

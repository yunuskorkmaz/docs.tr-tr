---
title: Projeksiyonlar düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 9b32ee4c7745fda482561311dc116e0e38b49ab7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599160"
---
# <a name="formulate-projections"></a><span data-ttu-id="ef1eb-102">Projeksiyonlar düzenleme</span><span class="sxs-lookup"><span data-stu-id="ef1eb-102">Formulate Projections</span></span>
<span data-ttu-id="ef1eb-103">Aşağıdaki örneklerde gösterildiği nasıl `select` deyiminde C# ve `Select` deyimi Visual Basic'te, form sorgu projeksiyonları diğer özellikleri ile birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef1eb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1eb-104">Example</span></span>  
 <span data-ttu-id="ef1eb-105">Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) için kişi adlarını bir dizisini döndürmek için `Customers`.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="ef1eb-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1eb-106">Example</span></span>  
 <span data-ttu-id="ef1eb-107">Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve *anonim türler* kişi adlarını bir dizisini döndürmek için telefon numaraları için `Customers`.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="ef1eb-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1eb-108">Example</span></span>  
 <span data-ttu-id="ef1eb-109">Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve *anonim türler* adları bir dizisini döndürmek ve çalışanlar için telefonu numaraları.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="ef1eb-110">`FirstName` Ve `LastName` alanları tek bir alana birleştirilir (`Name`) ve `HomePhone` alan yeniden adlandırılamaz `Phone` elde edilen sırada.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="ef1eb-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1eb-111">Example</span></span>  
 <span data-ttu-id="ef1eb-112">Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve *anonim türler* tüm bir dizisini döndürmek için `ProductID`s ve adlı hesaplanan değeri `HalfPrice`.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="ef1eb-113">Bu değeri şuna ayarlı `UnitPrice` 2 tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="ef1eb-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1eb-114">Example</span></span>  
 <span data-ttu-id="ef1eb-115">Aşağıdaki örnekte `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve bir *koşullu ifade* ürün adı ve ürün kullanılabilirliği bir dizisini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="ef1eb-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1eb-116">Example</span></span>  
 <span data-ttu-id="ef1eb-117">Aşağıdaki örnek bir Visual Basic kullanan `Select` yan tümcesi (`select` yan tümcesinde C#) ve bir *türü bilinen* çalışanlar adlarını bir dizisini döndürmek için (ad).</span><span class="sxs-lookup"><span data-stu-id="ef1eb-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="ef1eb-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1eb-118">Example</span></span>  
 <span data-ttu-id="ef1eb-119">Aşağıdaki örnekte `Select` ve `Where` Visual Basic'te (`select` ve `where` içinde C#) döndürülecek bir *dizisi filtrelenmiş* kişi adlarının Londra bulunan müşteriler için.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="ef1eb-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1eb-120">Example</span></span>  
 <span data-ttu-id="ef1eb-121">Aşağıdaki örnekte bir `Select` Visual Basic'te yan tümcesi (`select` yan tümcesinde C#) ve *anonim türler* döndürülecek bir *alt şeklinde* müşterilerle ilgili veri.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="ef1eb-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1eb-122">Example</span></span>  
 <span data-ttu-id="ef1eb-123">Aşağıdaki örnekte iç içe sorgu sonrasında şu sonuçların döndürülmesi için kullanır:</span><span class="sxs-lookup"><span data-stu-id="ef1eb-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="ef1eb-124">Tüm siparişleri ve bunlara karşılık gelen bir dizi `OrderID`s.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="ef1eb-125">İndirim siparişi öğeler bir alt dizi.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="ef1eb-126">Sevkiyat ücreti dahil edilmezse kaydedilmiş para miktarı.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="ef1eb-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef1eb-127">See also</span></span>
- [<span data-ttu-id="ef1eb-128">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ef1eb-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)

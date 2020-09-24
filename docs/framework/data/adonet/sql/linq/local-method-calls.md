---
title: Yerel Yöntem Çağrıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 25aded1aa961e182e8d2d472fca4c5a84b501af1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166176"
---
# <a name="local-method-calls"></a><span data-ttu-id="6a625-102">Yerel Yöntem Çağrıları</span><span class="sxs-lookup"><span data-stu-id="6a625-102">Local Method Calls</span></span>

<span data-ttu-id="6a625-103">Yerel bir yöntem çağrısı, nesne modeli içinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6a625-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="6a625-104">Uzak yöntem çağrısı, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL 'e çeviren ve yürütme için veritabanı altyapısına ileten bir veritabanıdır.</span><span class="sxs-lookup"><span data-stu-id="6a625-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="6a625-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ÇAĞRıYı SQL 'e çeviremez yerel Yöntem çağrıları gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6a625-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="6a625-106">Aksi takdirde, bir oluşturulur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="6a625-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="6a625-107">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="6a625-107">Example 1</span></span>  

 <span data-ttu-id="6a625-108">Aşağıdaki örnekte, bir `Order` sınıf Northwind örnek veritabanındaki Orders tablosuyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="6a625-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="6a625-109">Sınıfına bir yerel örnek yöntemi eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6a625-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="6a625-110">Sorgu 1 ' de, sınıf için Oluşturucu `Order` yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6a625-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="6a625-111">Sorgu 2 ' de, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL 'e çevrilmeye çalıştıysanız `LocalInstanceMethod()` , deneme başarısız olur ve bir <xref:System.InvalidOperationException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6a625-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="6a625-112">Ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , yerel Yöntem çağrıları için destek sağladığından, query2 bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="6a625-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6a625-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a625-113">See also</span></span>

- [<span data-ttu-id="6a625-114">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="6a625-114">Background Information</span></span>](background-information.md)

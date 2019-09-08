---
title: Yerel Yöntem Çağrıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: ec288d5ac2f6466860362be82c619c89204e8f31
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781426"
---
# <a name="local-method-calls"></a><span data-ttu-id="6bfe9-102">Yerel Yöntem Çağrıları</span><span class="sxs-lookup"><span data-stu-id="6bfe9-102">Local Method Calls</span></span>
<span data-ttu-id="6bfe9-103">Yerel bir yöntem çağrısı, nesne modeli içinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6bfe9-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="6bfe9-104">Uzak yöntem çağrısı, SQL 'e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çeviren ve yürütme için veritabanı altyapısına ileten bir veritabanıdır.</span><span class="sxs-lookup"><span data-stu-id="6bfe9-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="6bfe9-105">Çağrıyı SQL 'e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çeviremez yerel Yöntem çağrıları gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6bfe9-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="6bfe9-106">Aksi takdirde, <xref:System.InvalidOperationException> bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6bfe9-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="6bfe9-107">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="6bfe9-107">Example 1</span></span>  
 <span data-ttu-id="6bfe9-108">Aşağıdaki örnekte, bir `Order` sınıf Northwind örnek veritabanındaki Orders tablosuyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="6bfe9-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="6bfe9-109">Sınıfına bir yerel örnek yöntemi eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6bfe9-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="6bfe9-110">Sorgu 1 ' de, `Order` sınıf için Oluşturucu yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6bfe9-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="6bfe9-111">Sorgu 2 ' de, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL 'e çevrilmeye `LocalInstanceMethod()`çalıştıysanız, deneme başarısız olur ve bir <xref:System.InvalidOperationException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6bfe9-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="6bfe9-112">Ancak, yerel Yöntem çağrıları için destek sağladığından,query2birözeldurumoluşturmaz.[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bfe9-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6bfe9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bfe9-113">See also</span></span>

- [<span data-ttu-id="6bfe9-114">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="6bfe9-114">Background Information</span></span>](background-information.md)

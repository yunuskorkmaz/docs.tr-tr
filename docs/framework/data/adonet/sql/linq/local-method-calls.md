---
title: Yerel yöntem çağrıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 366c174a13e9a1a1928ef943febf199ae8485dfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352444"
---
# <a name="local-method-calls"></a><span data-ttu-id="b9e24-102">Yerel yöntem çağrıları</span><span class="sxs-lookup"><span data-stu-id="b9e24-102">Local Method Calls</span></span>
<span data-ttu-id="b9e24-103">Yerel yöntem çağrısı nesne modeli içindeki yürütülen biridir.</span><span class="sxs-lookup"><span data-stu-id="b9e24-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="b9e24-104">Uzak yöntem çağırma biridir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL dönüşür ve yürütme için veritabanı altyapısı iletir.</span><span class="sxs-lookup"><span data-stu-id="b9e24-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="b9e24-105">Yerel yöntem çağrılarını gerekiyor zaman [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL çağrısından çeviremez.</span><span class="sxs-lookup"><span data-stu-id="b9e24-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="b9e24-106">Aksi halde, bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b9e24-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="b9e24-107">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="b9e24-107">Example 1</span></span>  
 <span data-ttu-id="b9e24-108">Aşağıdaki örnekte, bir `Order` sınıfı, Northwind örnek veritabanı Siparişler tablosuna eşlendi.</span><span class="sxs-lookup"><span data-stu-id="b9e24-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="b9e24-109">Yerel örnek yöntemi sınıfı eklendi.</span><span class="sxs-lookup"><span data-stu-id="b9e24-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="b9e24-110">Sorgu 1 ' için oluşturucu `Order` sınıfı yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b9e24-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="b9e24-111">İçinde 2 ise sorgu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevrilemedi çalıştığınız `LocalInstanceMethod()`SQL denemesi başarısız olur ve bir <xref:System.InvalidOperationException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="b9e24-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="b9e24-112">Ancak çünkü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destek sağlayan yerel yöntem çağrıları için bir özel durum sorgu2 oluşturmayacaksa.</span><span class="sxs-lookup"><span data-stu-id="b9e24-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b9e24-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9e24-113">See Also</span></span>  
 [<span data-ttu-id="b9e24-114">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="b9e24-114">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

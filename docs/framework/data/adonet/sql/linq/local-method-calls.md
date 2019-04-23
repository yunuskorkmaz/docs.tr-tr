---
title: Yerel Yöntem Çağrıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: c8a4c29b1faa3c05f2cf32e9a60104b43a9b1c40
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074553"
---
# <a name="local-method-calls"></a><span data-ttu-id="40397-102">Yerel Yöntem Çağrıları</span><span class="sxs-lookup"><span data-stu-id="40397-102">Local Method Calls</span></span>
<span data-ttu-id="40397-103">Yerel yöntem çağrısı nesne modeli içinde yürütülen biridir.</span><span class="sxs-lookup"><span data-stu-id="40397-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="40397-104">Uzak yöntem çağırma biridir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL çevirir ve yürütme için veritabanı altyapısı iletir.</span><span class="sxs-lookup"><span data-stu-id="40397-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="40397-105">Yerel yöntem çağrıları gereklidir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL çağrısına çeviremez.</span><span class="sxs-lookup"><span data-stu-id="40397-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="40397-106">Aksi takdirde, bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="40397-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="40397-107">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="40397-107">Example 1</span></span>  
 <span data-ttu-id="40397-108">Aşağıdaki örnekte, bir `Order` sınıfı Northwind örnek veritabanındaki tablosuna eşlendi.</span><span class="sxs-lookup"><span data-stu-id="40397-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="40397-109">Yerel örnek yöntemi, sınıfa eklendi.</span><span class="sxs-lookup"><span data-stu-id="40397-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="40397-110">Sorgu 1 ' için oluşturucu `Order` sınıfı yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="40397-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="40397-111">İçinde 2, sorgu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çevir denedi `LocalInstanceMethod()`SQL denemesi başarısız olur ve bir <xref:System.InvalidOperationException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="40397-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="40397-112">Ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] desteği sağlayan yerel yöntem çağrıları için sorgu2 bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="40397-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="40397-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40397-113">See also</span></span>

- [<span data-ttu-id="40397-114">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="40397-114">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

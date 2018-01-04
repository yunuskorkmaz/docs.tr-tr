---
title: "Yerel yöntem çağrıları"
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
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 105814dd45bc8cd07bf25c4972d4d1b3aa93b1f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="local-method-calls"></a><span data-ttu-id="c9692-102">Yerel yöntem çağrıları</span><span class="sxs-lookup"><span data-stu-id="c9692-102">Local Method Calls</span></span>
<span data-ttu-id="c9692-103">Yerel yöntem çağrısı nesne modeli içindeki yürütülen biridir.</span><span class="sxs-lookup"><span data-stu-id="c9692-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="c9692-104">Uzak yöntem çağırma biridir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL dönüşür ve yürütme için veritabanı altyapısı iletir.</span><span class="sxs-lookup"><span data-stu-id="c9692-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="c9692-105">Yerel yöntem çağrılarını gerekiyor zaman [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL çağrısından çeviremez.</span><span class="sxs-lookup"><span data-stu-id="c9692-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="c9692-106">Aksi halde, bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c9692-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="c9692-107">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="c9692-107">Example 1</span></span>  
 <span data-ttu-id="c9692-108">Aşağıdaki örnekte, bir `Order` sınıfı, Northwind örnek veritabanı Siparişler tablosuna eşlendi.</span><span class="sxs-lookup"><span data-stu-id="c9692-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="c9692-109">Yerel örnek yöntemi sınıfı eklendi.</span><span class="sxs-lookup"><span data-stu-id="c9692-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="c9692-110">Sorgu 1 ' için oluşturucu `Order` sınıfı yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c9692-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="c9692-111">İçinde 2 ise sorgu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevrilemedi çalıştığınız `LocalInstanceMethod()`SQL denemesi başarısız olur ve bir <xref:System.InvalidOperationException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="c9692-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="c9692-112">Ancak çünkü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destek sağlayan yerel yöntem çağrıları için bir özel durum sorgu2 oluşturmayacaksa.</span><span class="sxs-lookup"><span data-stu-id="c9692-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c9692-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9692-113">See Also</span></span>  
 [<span data-ttu-id="c9692-114">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="c9692-114">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

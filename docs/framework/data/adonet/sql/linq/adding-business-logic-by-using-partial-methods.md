---
title: "Kısmi yöntemler kullanarak iş mantığı ekleme"
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
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9704ad7d4030ee85701f1f95f87c539c1fbd0122
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="6659f-102">Kısmi yöntemler kullanarak iş mantığı ekleme</span><span class="sxs-lookup"><span data-stu-id="6659f-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="6659f-103">Özelleştirebileceğiniz [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ve C# kodunda oluşturulan, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullanarak projeleri *kısmi yöntemler*.</span><span class="sxs-lookup"><span data-stu-id="6659f-103">You can customize [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="6659f-104">Kod, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturur imzaları kısmi yöntemi bir parçası olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6659f-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="6659f-105">Yöntem uygulamak istiyorsanız, kısmi yönteminizi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6659f-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="6659f-106">Kendi uygulama eklemezseniz derleyici kısmi yöntemler imza atar ve varsayılan yöntemlerini çağrıları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6659f-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6659f-107">Kullanıyorsanız [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] doğrulama ve diğer özelleştirmeleri varlık sınıfları eklemek için.</span><span class="sxs-lookup"><span data-stu-id="6659f-107">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="6659f-108">Örneğin, varsayılan eşleme için `Customer` Northwind örnek veritabanı sınıfında aşağıdaki kısmi yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="6659f-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="6659f-109">Kendi kısmi aşağıdaki gibi kod ekleyerek, kendi yönteminizi uygulayabileceğiniz `Customer` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="6659f-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="6659f-110">Bu yaklaşım genellikle kullanılan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için varsayılan yöntemleri geçersiz kılmak için `Insert`, `Update`, `Delete`ve nesne yaşam döngüsü olayları sırasında özellikleri doğrulanacak.</span><span class="sxs-lookup"><span data-stu-id="6659f-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="6659f-111">Daha fazla bilgi için bkz: [kısmi yöntemler](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) veya [partial (yöntem) (C# Başvurusu)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span><span class="sxs-lookup"><span data-stu-id="6659f-111">For more information, see [Partial Methods](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) or [partial (Method) (C# Reference)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6659f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6659f-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6659f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6659f-113">Description</span></span>  
 <span data-ttu-id="6659f-114">Aşağıdaki örnekte gösterildiği `ExampleClass` ilk SQLMetal ve ardından iki yöntemlerden sadece birini nasıl uygulayabilir gibi bir kod oluşturma aracı tarafından tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="6659f-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6659f-115">Kod</span><span class="sxs-lookup"><span data-stu-id="6659f-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="6659f-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="6659f-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6659f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6659f-117">Description</span></span>  
 <span data-ttu-id="6659f-118">Aşağıdaki örnek, arasındaki ilişkiyi kullanır `Shipper` ve `Order` varlıklar.</span><span class="sxs-lookup"><span data-stu-id="6659f-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="6659f-119">Kısmi yöntemler yöntemleri arasından Not `InsertShipper` ve `DeleteShipper`.</span><span class="sxs-lookup"><span data-stu-id="6659f-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="6659f-120">Bu yöntemleri tarafından sağlanan varsayılan kısmi yöntemlerini geçersiz kılın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşleme.</span><span class="sxs-lookup"><span data-stu-id="6659f-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6659f-121">Kod</span><span class="sxs-lookup"><span data-stu-id="6659f-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6659f-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6659f-122">See Also</span></span>  
 [<span data-ttu-id="6659f-123">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="6659f-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="6659f-124">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6659f-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)

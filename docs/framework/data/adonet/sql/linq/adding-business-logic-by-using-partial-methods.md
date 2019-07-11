---
title: Kısmi Yöntemler Kullanarak İş Mantığı Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: ed440f3315fc25e82b648f21410acb7a2c2a08f9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743672"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="cdb6d-102">Kısmi Yöntemler Kullanarak İş Mantığı Ekleme</span><span class="sxs-lookup"><span data-stu-id="cdb6d-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="cdb6d-103">Visual Basic özelleştirebilirsiniz ve C# oluşturulan kodda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullanarak projeleri *kısmi yöntemler*.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="cdb6d-104">Kod, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturur imzaları kısmi bir yöntemin bir parçası olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="cdb6d-105">Yöntemi uygulamak istiyorsanız, kendi kısmi yöntem ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="cdb6d-106">Kendi uygulamanız eklemezseniz derleyici kısmi yöntem imzası atar ve varsayılan yöntem çağrıları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cdb6d-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdb6d-107">Visual Studio kullanıyorsanız, Nesne İlişkisel Tasarımcısı varlık sınıflarına doğrulama ve diğer özelleştirmeleri eklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-107">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="cdb6d-108">Örneğin, varsayılan eşlemesini `Customer` Northwind örnek veritabanındaki sınıfı aşağıdaki kısmi yöntem içerir:</span><span class="sxs-lookup"><span data-stu-id="cdb6d-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="cdb6d-109">İçin kendi kısmi aşağıdaki gibi kod ekleyerek kendi bir yöntem uygulayabilirsiniz `Customer` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="cdb6d-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="cdb6d-110">Bu yaklaşım genellikle kullanılan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için varsayılan yöntemleri geçersiz kılmak için `Insert`, `Update`, `Delete`ve nesne yaşam döngüsü olayları sırasında özellikleri doğrulamak için.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="cdb6d-111">Daha fazla bilgi için [kısmi yöntemler](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) veya [partial (yöntem) (C# başvuru)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span><span class="sxs-lookup"><span data-stu-id="cdb6d-111">For more information, see [Partial Methods](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdb6d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="cdb6d-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cdb6d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cdb6d-113">Description</span></span>  
 <span data-ttu-id="cdb6d-114">Aşağıdaki örnekte gösterildiği `ExampleClass` ilk SQLMetal ve ardından iki yöntemden yalnızca biri nasıl uygulayabilir gibi bir kod oluşturma aracı tarafından tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cdb6d-115">Kod</span><span class="sxs-lookup"><span data-stu-id="cdb6d-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="cdb6d-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="cdb6d-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cdb6d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cdb6d-117">Description</span></span>  
 <span data-ttu-id="cdb6d-118">Aşağıdaki örnekte arasındaki ilişkiyi `Shipper` ve `Order` varlıklar.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="cdb6d-119">Kısmi yöntemler arasında yöntemleri Not `InsertShipper` ve `DeleteShipper`.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="cdb6d-120">Geçersiz kılma tarafından sağlanan varsayılan kısmi yöntemler bu yöntemleri [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşleme.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cdb6d-121">Kod</span><span class="sxs-lookup"><span data-stu-id="cdb6d-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cdb6d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdb6d-122">See also</span></span>

- [<span data-ttu-id="cdb6d-123">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="cdb6d-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="cdb6d-124">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cdb6d-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)

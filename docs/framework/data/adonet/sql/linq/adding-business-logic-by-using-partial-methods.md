---
title: Kısmi Yöntemler Kullanarak İş Mantığı Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: 251d7a05971ff7940f85ec9d555d26f2e57067c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248130"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="d25cf-102">Kısmi Yöntemler Kullanarak İş Mantığı Ekleme</span><span class="sxs-lookup"><span data-stu-id="d25cf-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="d25cf-103">C# Uygulamanızda[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Basic ve üretilen kodu, *kısmi Yöntemler*kullanarak özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d25cf-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="d25cf-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Üreten kod, imzaları kısmi bir metodun bir parçası olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d25cf-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="d25cf-105">Yöntemini uygulamak istiyorsanız, kendi kısmi yönteminizi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d25cf-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="d25cf-106">Kendi uygulamanızı eklemeyin, derleyici kısmi Yöntemler imzasını atar ve içinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]varsayılan yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="d25cf-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d25cf-107">Visual Studio kullanıyorsanız, varlık sınıflarına doğrulama ve diğer özelleştirmeler eklemek için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d25cf-107">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="d25cf-108">Örneğin, Northwind örnek veritabanındaki `Customer` sınıfının varsayılan eşlemesi aşağıdaki kısmi yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="d25cf-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="d25cf-109">Kendi kısmi `Customer` Sınıfınıza aşağıdaki gibi kod ekleyerek kendi yönteminizi uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d25cf-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="d25cf-110">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu yaklaşım genellikle, `Insert` `Update`nesne yaşam döngüsü olayları sırasında özellikleri doğrulamak için,,, ve için varsayılan yöntemleri geçersiz kılmak üzere ' de kullanılır. `Delete`</span><span class="sxs-lookup"><span data-stu-id="d25cf-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="d25cf-111">Daha fazla bilgi için bkz. [kısmi Yöntemler](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) veya [partial (Yöntem)C# (başvuru)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span><span class="sxs-lookup"><span data-stu-id="d25cf-111">For more information, see [Partial Methods](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d25cf-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d25cf-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d25cf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d25cf-113">Description</span></span>  
 <span data-ttu-id="d25cf-114">Aşağıdaki örnek, ilk `ExampleClass` olarak SqlMetal gibi kod oluşturma aracı tarafından tanımlandıkları ve sonra iki yöntemden yalnızca birini nasıl uygulayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d25cf-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d25cf-115">Kod</span><span class="sxs-lookup"><span data-stu-id="d25cf-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="d25cf-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d25cf-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d25cf-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d25cf-117">Description</span></span>  
 <span data-ttu-id="d25cf-118">Aşağıdaki örnek ve `Shipper` `Order` varlıkları arasındaki ilişkiyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d25cf-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="d25cf-119">Kısmi yöntemlerin `InsertShipper` ve `DeleteShipper`yöntemleri arasında aklınızda yer.</span><span class="sxs-lookup"><span data-stu-id="d25cf-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="d25cf-120">Bu yöntemler, eşleme tarafından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sağlanan varsayılan kısmi yöntemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="d25cf-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d25cf-121">Kod</span><span class="sxs-lookup"><span data-stu-id="d25cf-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d25cf-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d25cf-122">See also</span></span>

- [<span data-ttu-id="d25cf-123">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="d25cf-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="d25cf-124">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d25cf-124">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)

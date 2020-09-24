---
title: Kısmi Yöntemler Kullanarak İş Mantığı Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: 9ad3329c621b8bf8eaa0fd5f986ac7e8cff97d9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156166"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="ed3ba-102">Kısmi Yöntemler Kullanarak İş Mantığı Ekleme</span><span class="sxs-lookup"><span data-stu-id="ed3ba-102">Adding Business Logic By Using Partial Methods</span></span>

<span data-ttu-id="ed3ba-103">Uygulamanızda Visual Basic ve C# tarafından üretilen kodu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *kısmi Yöntemler*kullanarak özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ba-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="ed3ba-104">Üreten kod, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] imzaları kısmi bir metodun bir parçası olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed3ba-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="ed3ba-105">Yöntemini uygulamak istiyorsanız, kendi kısmi yönteminizi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ba-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="ed3ba-106">Kendi uygulamanızı eklemeyin, derleyici kısmi Yöntemler imzasını atar ve içinde varsayılan yöntemleri çağırır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ed3ba-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed3ba-107">Visual Studio kullanıyorsanız, varlık sınıflarına doğrulama ve diğer özelleştirmeler eklemek için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ba-107">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="ed3ba-108">Örneğin, `Customer` Northwind örnek veritabanındaki sınıfının varsayılan eşlemesi aşağıdaki kısmi yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="ed3ba-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="ed3ba-109">Kendi kısmi Sınıfınıza aşağıdaki gibi kod ekleyerek kendi yönteminizi uygulayabilirsiniz `Customer` :</span><span class="sxs-lookup"><span data-stu-id="ed3ba-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="ed3ba-110">Bu yaklaşım genellikle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert` , `Update` `Delete` nesne yaşam döngüsü olayları sırasında özellikleri doğrulamak için,,, ve için varsayılan yöntemleri geçersiz kılmak üzere ' de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ed3ba-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="ed3ba-111">Daha fazla bilgi için bkz. [kısmi Yöntemler](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) veya [partial (Yöntem) (c# başvurusu)](../../../../../csharp/language-reference/keywords/partial-method.md) (c#).</span><span class="sxs-lookup"><span data-stu-id="ed3ba-111">For more information, see [Partial Methods](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed3ba-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed3ba-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ed3ba-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed3ba-113">Description</span></span>  

 <span data-ttu-id="ed3ba-114">Aşağıdaki örnek, `ExampleClass` ilk olarak SQLMetal gibi kod oluşturma aracı tarafından tanımlandıkları ve sonra iki yöntemden yalnızca birini nasıl uygulayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed3ba-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed3ba-115">Kod</span><span class="sxs-lookup"><span data-stu-id="ed3ba-115">Code</span></span>  

 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="ed3ba-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed3ba-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ed3ba-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed3ba-117">Description</span></span>  

 <span data-ttu-id="ed3ba-118">Aşağıdaki örnek ve varlıkları arasındaki ilişkiyi kullanır `Shipper` `Order` .</span><span class="sxs-lookup"><span data-stu-id="ed3ba-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="ed3ba-119">Kısmi yöntemlerin ve yöntemleri arasında aklınızda yer `InsertShipper` `DeleteShipper` .</span><span class="sxs-lookup"><span data-stu-id="ed3ba-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="ed3ba-120">Bu yöntemler, eşleme tarafından sağlanan varsayılan kısmi yöntemleri geçersiz kılar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ed3ba-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed3ba-121">Kod</span><span class="sxs-lookup"><span data-stu-id="ed3ba-121">Code</span></span>  

 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ed3ba-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed3ba-122">See also</span></span>

- [<span data-ttu-id="ed3ba-123">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="ed3ba-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="ed3ba-124">Insert, Update ve Delete İşlemlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ed3ba-124">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)

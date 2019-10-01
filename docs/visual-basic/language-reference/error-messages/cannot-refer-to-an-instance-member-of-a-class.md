---
title: Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: a2a5ab99ff68e6dce783a2fd986ee6e8c15ae858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701171"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="05bae-102">Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz</span><span class="sxs-lookup"><span data-stu-id="05bae-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="05bae-103">Paylaşılan bir yordamın içinden bir sınıfın paylaşılmayan üyesine başvurmaya çalıştınız.</span><span class="sxs-lookup"><span data-stu-id="05bae-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="05bae-104">Aşağıdaki örnekte böyle bir durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05bae-104">The following example demonstrates such a situation.</span></span>  
  
```vb  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="05bae-105">Yukarıdaki örnekte, `x = 10` atama ifadesinde bu hata iletisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="05bae-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="05bae-106">Bunun nedeni, paylaşılan bir yordamın bir örnek değişkenine erişmeye çalışıyor olması.</span><span class="sxs-lookup"><span data-stu-id="05bae-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="05bae-107">@No__t-0 değişkeni, [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)olarak bildirildiği için bir örnek üyesidir.</span><span class="sxs-lookup"><span data-stu-id="05bae-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="05bae-108">@No__t-0 sınıfının her örneği kendi bağımsız değişkenini içerir `x`.</span><span class="sxs-lookup"><span data-stu-id="05bae-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="05bae-109">Bir örnek `x` değerini ayarladığında veya değiştirdiğinde, başka bir örnekteki `x` değerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="05bae-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="05bae-110">Ancak, `setX` yordamı, `sample` sınıfının tüm örnekleri arasında `Shared` ' dir.</span><span class="sxs-lookup"><span data-stu-id="05bae-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="05bae-111">Bu, sınıfın herhangi bir örneğiyle ilişkilendirilmediği, ancak tek tek örneklerden bağımsız olarak çalışan bir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="05bae-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="05bae-112">Belirli bir örneğe sahip hiçbir bağlantısı olmadığından, `setX` bir örnek değişkenine erişemez.</span><span class="sxs-lookup"><span data-stu-id="05bae-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="05bae-113">Yalnızca `Shared` değişkenlerinde çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="05bae-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="05bae-114">@No__t-0, paylaşılan bir değişkenin değerini ayarladığında veya değiştirdiğinde, bu yeni değer sınıfının tüm örnekleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05bae-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="05bae-115">**Hata kimliği:** BC30369</span><span class="sxs-lookup"><span data-stu-id="05bae-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="05bae-116">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="05bae-116">To correct this error</span></span>  
  
1. <span data-ttu-id="05bae-117">Üyenin sınıfın tüm örnekleri arasında paylaşılmasını mi yoksa her örnek için bir bireyin mı saklanacağını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="05bae-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2. <span data-ttu-id="05bae-118">Üyenin tek bir kopyasının tüm örnekler arasında paylaşılmasını istiyorsanız üye bildirimine `Shared` anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05bae-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="05bae-119">Yordam bildiriminde `Shared` anahtar sözcüğünü koruyun.</span><span class="sxs-lookup"><span data-stu-id="05bae-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3. <span data-ttu-id="05bae-120">Her bir örneğin üyenin tek bir kopyasına sahip olmasını istiyorsanız, üye bildirimi için `Shared` belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="05bae-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="05bae-121">Yordam bildiriminden `Shared` anahtar sözcüğünü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="05bae-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bae-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05bae-122">See also</span></span>

- [<span data-ttu-id="05bae-123">Shared</span><span class="sxs-lookup"><span data-stu-id="05bae-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)

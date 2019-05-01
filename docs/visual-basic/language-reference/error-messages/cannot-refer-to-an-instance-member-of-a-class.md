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
ms.openlocfilehash: aad068b5857eb956ded63fa2a57cb163d3cf5c58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013848"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="5a14a-102">Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz</span><span class="sxs-lookup"><span data-stu-id="5a14a-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="5a14a-103">Paylaşılan bir yordam içinde bir sınıftan paylaşılmayan üyesi başvurmak çalıştınız.</span><span class="sxs-lookup"><span data-stu-id="5a14a-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="5a14a-104">Aşağıdaki örnekte, böyle bir durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5a14a-104">The following example demonstrates such a situation.</span></span>  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="5a14a-105">Yukarıdaki örnekte, atama ifadesi `x = 10` bu hata iletisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a14a-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="5a14a-106">Paylaşılan bir yordam örneği bir değişkene erişmeye çalışıyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5a14a-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="5a14a-107">Değişken `x` olarak bildirilmediğinden, bir örnek üyesi olduğu [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="5a14a-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="5a14a-108">Sınıfın her örneğini `sample` kendi bağımsız değişkenini içeren `x`.</span><span class="sxs-lookup"><span data-stu-id="5a14a-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="5a14a-109">Ne zaman bir örneği ayarlar veya değerini değiştirir `x`, değerini etkilemez `x` herhangi bir örneğindeki.</span><span class="sxs-lookup"><span data-stu-id="5a14a-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="5a14a-110">Ancak, yordamın `setX` olduğu `Shared` sınıfın tüm örnekleri arasında `sample`.</span><span class="sxs-lookup"><span data-stu-id="5a14a-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="5a14a-111">Başka bir deyişle, herhangi bir sınıf örneği ile ilişkili değildir, ancak bunun yerine tek tek örnekleri bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="5a14a-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="5a14a-112">Belirli bir örneği ile bağlantı olduğundan `setX` bir örnek değişkeni erişemez.</span><span class="sxs-lookup"><span data-stu-id="5a14a-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="5a14a-113">Yalnızca çalışmalıdır `Shared` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="5a14a-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="5a14a-114">Zaman `setX` ayarlar veya yeni değeri sınıfın tüm örnekleri için kullanılabilir, paylaşılan bir değişkenin değerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5a14a-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="5a14a-115">**Hata Kimliği:** BC30369</span><span class="sxs-lookup"><span data-stu-id="5a14a-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5a14a-116">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5a14a-116">To correct this error</span></span>  
  
1. <span data-ttu-id="5a14a-117">Sınıfın tüm örnekleri arasında paylaşılan veya her örneği için tek tek tutulan üyesi için istediğinize karar verin.</span><span class="sxs-lookup"><span data-stu-id="5a14a-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2. <span data-ttu-id="5a14a-118">Üyenin tüm örnekleri arasında paylaşılması için tek bir kopyasını istiyorsanız ekleyin `Shared` üye bildirimi için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5a14a-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="5a14a-119">Korumak `Shared` yordamı bildirimindeki anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5a14a-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3. <span data-ttu-id="5a14a-120">Her örnek kendi ayrı üye kopyasına sahip istiyorsanız belirtmeyin `Shared` üye bildirimi için.</span><span class="sxs-lookup"><span data-stu-id="5a14a-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="5a14a-121">Kaldırma `Shared` yordam bildirimi from anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5a14a-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a14a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a14a-122">See also</span></span>

- [<span data-ttu-id="5a14a-123">Shared</span><span class="sxs-lookup"><span data-stu-id="5a14a-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)

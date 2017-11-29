---
title: "Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a15d36c0b3a4d6b1657d583de0dc61621da960d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="bd3d3-102">Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz</span><span class="sxs-lookup"><span data-stu-id="bd3d3-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="bd3d3-103">Paylaşılan bir yordam aynı sınıfın paylaşılmayan üye başvurmak denediniz.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="bd3d3-104">Aşağıdaki örnek, böyle bir durum gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-104">The following example demonstrates such a situation.</span></span>  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="bd3d3-105">Önceki örnekte, atama ifadesi `x = 10` bu hata iletisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="bd3d3-106">Paylaşılan bir yordam bir örnek değişkeni erişmeye çalışıyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="bd3d3-107">Değişkeni `x` olarak bildirilmedi örnek üyesine çünkü [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="bd3d3-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="bd3d3-108">Her sınıf örneği `sample` kendi bağımsız değişken içeriyor `x`.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="bd3d3-109">Ne zaman bir örnek ayarlar veya değerini değiştirir `x`, değerini etkilemez `x` başka bir örnek.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="bd3d3-110">Ancak, yordamı `setX` olan `Shared` sınıfın tüm örnekleri arasında `sample`.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="bd3d3-111">Başka bir deyişle, bir sınıfın örneklerini ile ilişkili değil, ancak bunun yerine tek tek örneklerini bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="bd3d3-112">Belirli bir örneği ile bağlantı içerdiğinden `setX` bir örnek değişkeni erişemiyor.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="bd3d3-113">Yalnızca üzerinde çalışmalıdır `Shared` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="bd3d3-114">Zaman `setX` ayarlar veya yeni bir değer sınıfın tüm örnekleri için kullanılabilir paylaşılan bir değişkenin değerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="bd3d3-115">**Hata Kimliği:** BC30369</span><span class="sxs-lookup"><span data-stu-id="bd3d3-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd3d3-116">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bd3d3-116">To correct this error</span></span>  
  
1.  <span data-ttu-id="bd3d3-117">Sınıfın tüm örnekleri arasında paylaşılabilir veya her örneği için tek tek tutulan üyesi isteyip istemediğinize karar verin.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2.  <span data-ttu-id="bd3d3-118">Tüm örnekler arasında paylaşılacak üye tek bir kopyasını istiyorsanız ekleyin `Shared` üye bildirimi anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="bd3d3-119">Korumak `Shared` yordamı bildiriminde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3.  <span data-ttu-id="bd3d3-120">Her örnek üyesinin tek tek kendi kopyasına sahip istiyorsanız belirtmeyin `Shared` üye bildirimi için.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="bd3d3-121">Kaldırma `Shared` yordamı bildirimi anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd3d3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd3d3-122">See Also</span></span>  
 [<span data-ttu-id="bd3d3-123">Paylaşılan</span><span class="sxs-lookup"><span data-stu-id="bd3d3-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)

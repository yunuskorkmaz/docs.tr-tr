---
title: '&#39;&lt;TypeName&gt; &#39; temsilci türü'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 6676328d0c1ea459f5934b5f9e2cb66580adad40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737208"
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="41868-102">&#39;&lt;TypeName&gt; &#39; temsilci türü</span><span class="sxs-lookup"><span data-stu-id="41868-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="41868-103">'\<typename >' temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="41868-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="41868-104">Temsilci oluşturma yalnızca tek bir AddressOf ifade bir bağımsız değişken listesi olarak izin verir.</span><span class="sxs-lookup"><span data-stu-id="41868-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="41868-105">Genellikle bir AddressOf ifadesi, bir temsilci oluşturma yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41868-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="41868-106">A `New` yan tümcesi bir temsilci sınıfı örneğini oluşturma temsilci Oluşturucu için geçersiz bağımsız değişken listesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="41868-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="41868-107">Yalnızca tek bir sağladığınız `AddressOf` yeni bir temsilci örneğini oluştururken ifade.</span><span class="sxs-lookup"><span data-stu-id="41868-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="41868-108">Bu hata, herhangi bir bağımsız değişken temsilci Oluşturucu için birden fazla bağımsız değişken geçirmeniz ya da tek bir bağımsız değişken geçirirseniz, geçerli değil geçirmezseniz sonuçlanabilir `AddressOf` ifade.</span><span class="sxs-lookup"><span data-stu-id="41868-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="41868-109">**Hata Kimliği:** BC32008</span><span class="sxs-lookup"><span data-stu-id="41868-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41868-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="41868-110">To correct this error</span></span>  
  
-   <span data-ttu-id="41868-111">Tek kullanımlık `AddressOf` ifade'temsilci sınıfında bağımsız değişken listesinde `New` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="41868-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41868-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41868-112">See also</span></span>
- [<span data-ttu-id="41868-113">New İşleci</span><span class="sxs-lookup"><span data-stu-id="41868-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="41868-114">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="41868-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="41868-115">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="41868-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="41868-116">Nasıl yapılır: Bir temsilci yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="41868-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

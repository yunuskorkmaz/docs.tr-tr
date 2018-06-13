---
title: '&#39;&lt;TypeName&gt; &#39; bir temsilci türü'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c6d4244ce72dedee50b65ba19978149ce86b9e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595654"
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="abacb-102">&#39;&lt;TypeName&gt; &#39; bir temsilci türü</span><span class="sxs-lookup"><span data-stu-id="abacb-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="abacb-103">'\<typename >' temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="abacb-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="abacb-104">Temsilci yapım yalnızca tek bir AddressOf ifade bir değişken listesi olarak verir.</span><span class="sxs-lookup"><span data-stu-id="abacb-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="abacb-105">Genellikle bir AddressOf ifade temsilci yapım yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="abacb-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="abacb-106">A `New` yan tümcesi bir temsilci sınıfının bir örneğini oluşturma sağlayan bir temsilci Oluşturucu geçersiz bağımsız değişken listesi.</span><span class="sxs-lookup"><span data-stu-id="abacb-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="abacb-107">Yalnızca tek bir sağlayabilir `AddressOf` yeni bir temsilci örneği oluşturulurken ifade.</span><span class="sxs-lookup"><span data-stu-id="abacb-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="abacb-108">Bu hata, herhangi bir bağımsız değişken temsilci Oluşturucu için birden fazla bağımsız değişken geçirmek ya da tek bir bağımsız değişken geçirirseniz bir geçerli olmayan geçirmezseniz sonuçlanabilir `AddressOf` ifade.</span><span class="sxs-lookup"><span data-stu-id="abacb-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="abacb-109">**Hata Kimliği:** BC32008</span><span class="sxs-lookup"><span data-stu-id="abacb-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="abacb-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="abacb-110">To correct this error</span></span>  
  
-   <span data-ttu-id="abacb-111">Tek kullanımlık `AddressOf` temsilci sınıfında için bağımsız değişken listesi ifadesinde `New` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="abacb-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abacb-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="abacb-112">See Also</span></span>  
 [<span data-ttu-id="abacb-113">New İşleci</span><span class="sxs-lookup"><span data-stu-id="abacb-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="abacb-114">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="abacb-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="abacb-115">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="abacb-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="abacb-116">Nasıl yapılır: Temsilci Yöntemi Çağırma</span><span class="sxs-lookup"><span data-stu-id="abacb-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

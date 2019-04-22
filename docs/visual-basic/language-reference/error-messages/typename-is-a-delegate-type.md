---
title: "'<typename>' bir temsilci türü değil"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c308805f5e73d740ff18a40d95b9cc2576ac95fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841280"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="fcf55-102">'\<typename >' bir temsilci türü</span><span class="sxs-lookup"><span data-stu-id="fcf55-102">'\<typename>' is a delegate type</span></span>
<span data-ttu-id="fcf55-103">'\<typename >' temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="fcf55-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="fcf55-104">Temsilci oluşturma yalnızca tek bir AddressOf ifade bir bağımsız değişken listesi olarak izin verir.</span><span class="sxs-lookup"><span data-stu-id="fcf55-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="fcf55-105">Genellikle bir AddressOf ifadesi, bir temsilci oluşturma yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fcf55-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="fcf55-106">A `New` yan tümcesi bir temsilci sınıfı örneğini oluşturma temsilci Oluşturucu için geçersiz bağımsız değişken listesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcf55-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="fcf55-107">Yalnızca tek bir sağladığınız `AddressOf` yeni bir temsilci örneğini oluştururken ifade.</span><span class="sxs-lookup"><span data-stu-id="fcf55-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="fcf55-108">Bu hata, herhangi bir bağımsız değişken temsilci Oluşturucu için birden fazla bağımsız değişken geçirmeniz ya da tek bir bağımsız değişken geçirirseniz, geçerli değil geçirmezseniz sonuçlanabilir `AddressOf` ifade.</span><span class="sxs-lookup"><span data-stu-id="fcf55-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="fcf55-109">**Hata Kimliği:** BC32008</span><span class="sxs-lookup"><span data-stu-id="fcf55-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fcf55-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fcf55-110">To correct this error</span></span>  
  
-   <span data-ttu-id="fcf55-111">Tek kullanımlık `AddressOf` ifade'temsilci sınıfında bağımsız değişken listesinde `New` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fcf55-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf55-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcf55-112">See also</span></span>

- [<span data-ttu-id="fcf55-113">New İşleci</span><span class="sxs-lookup"><span data-stu-id="fcf55-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="fcf55-114">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="fcf55-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="fcf55-115">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="fcf55-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="fcf55-116">Nasıl yapılır: Bir temsilci yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="fcf55-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

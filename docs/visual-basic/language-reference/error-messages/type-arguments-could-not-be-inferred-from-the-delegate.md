---
title: Tür bağımsız değişkenleri temsilciden gösterilemedi
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 17b65a39082ddaf54aabf12ca9b95e49af80f5f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666312"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="c2468-102">Tür bağımsız değişkenleri temsilciden gösterilemedi</span><span class="sxs-lookup"><span data-stu-id="c2468-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="c2468-103">Atama ifadesi kullanan `AddressOf` genel adresi atamak için yordamı bir temsilci, ancak genel yordam herhangi bir türü bağımsız değişken sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="c2468-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="c2468-104">Normalde, genel tür çağırdığınızda, bir tür bağımsız değişkeni genel tür tanımlar. her tür parametresi için sağlayın.</span><span class="sxs-lookup"><span data-stu-id="c2468-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="c2468-105">Herhangi bir tür bağımsız değişkeni sağlamazsanız derleyici için tür parametreleri geçirilecek türlerini çıkarması çalışır.</span><span class="sxs-lookup"><span data-stu-id="c2468-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="c2468-106">İçerik türlerini çıkarması derleyici için yeterli bilgi sağlamazsa bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c2468-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="c2468-107">**Hata Kimliği:** BC36564</span><span class="sxs-lookup"><span data-stu-id="c2468-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c2468-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c2468-108">To correct this error</span></span>  
  
-   <span data-ttu-id="c2468-109">Yordamı genel tür bağımsız değişkenleri belirtin `AddressOf` ifade.</span><span class="sxs-lookup"><span data-stu-id="c2468-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2468-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2468-110">See also</span></span>
- [<span data-ttu-id="c2468-111">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="c2468-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="c2468-112">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="c2468-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="c2468-113">Visual Basic'de genel yordamlar</span><span class="sxs-lookup"><span data-stu-id="c2468-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="c2468-114">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="c2468-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="c2468-115">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="c2468-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

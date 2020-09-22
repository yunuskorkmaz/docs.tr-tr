---
title: Tür bağımsız değişkenleri temsilciden gösterilemedi
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 51b0bbf2e346acdd84a1bc2283db4a71adc9f7dc
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870436"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="b5535-102">Tür bağımsız değişkenleri temsilciden gösterilemedi</span><span class="sxs-lookup"><span data-stu-id="b5535-102">Type arguments could not be inferred from the delegate</span></span>

<span data-ttu-id="b5535-103">Atama ekstresi `AddressOf` , bir temsilciye genel yordamın adresini atamak için kullanır, ancak genel yordamda herhangi bir tür bağımsız değişkeni sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b5535-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="b5535-104">Normal olarak, genel bir tür çağırdığınızda, genel türün tanımladığı her tür parametresi için bir tür bağımsız değişkeni sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="b5535-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="b5535-105">Herhangi bir tür bağımsız değişkeni belirtmezseniz, derleyici tür parametrelerine geçirilecek türleri çıkarması için girişimde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b5535-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="b5535-106">Bağlam derleyicinin türleri çıkarması için yeterli bilgi sağlamıyorsa bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b5535-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="b5535-107">**Hata kimliği:** BC36564</span><span class="sxs-lookup"><span data-stu-id="b5535-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5535-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b5535-108">To correct this error</span></span>  
  
- <span data-ttu-id="b5535-109">İfadedeki genel yordamın tür bağımsız değişkenlerini belirtin `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="b5535-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5535-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5535-110">See also</span></span>

- [<span data-ttu-id="b5535-111">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="b5535-111">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="b5535-112">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="b5535-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="b5535-113">Visual Basic'de Genel Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b5535-113">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="b5535-114">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="b5535-114">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="b5535-115">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="b5535-115">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)

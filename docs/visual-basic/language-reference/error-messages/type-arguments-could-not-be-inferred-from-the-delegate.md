---
title: "Tür bağımsız değişkenleri temsilciden gösterilemedi"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="0a78e-102">Tür bağımsız değişkenleri temsilciden gösterilemedi</span><span class="sxs-lookup"><span data-stu-id="0a78e-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="0a78e-103">Atama deyimini kullanan `AddressOf` genel adresi atamak için yordamı bir temsilci, ancak genel yordam için herhangi bir tür bağımsız değişkeni sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="0a78e-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="0a78e-104">Normalde, genel bir tür çağırdığınızda, genel tür tanımlar her tür parametresi için bir tür bağımsız değişken sağlayın.</span><span class="sxs-lookup"><span data-stu-id="0a78e-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="0a78e-105">Herhangi bir tür bağımsız değişkeni belirtmezseniz, derleyici tür parametreleri geçirilecek türleri Infer dener.</span><span class="sxs-lookup"><span data-stu-id="0a78e-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="0a78e-106">İçerik türlerini anlamak derleyici için yeterli bilgi sağlamıyorsa, bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0a78e-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="0a78e-107">**Hata Kimliği:** BC36564</span><span class="sxs-lookup"><span data-stu-id="0a78e-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a78e-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0a78e-108">To correct this error</span></span>  
  
-   <span data-ttu-id="0a78e-109">Genel yordamda tür bağımsız değişkenleri belirtin `AddressOf` ifade.</span><span class="sxs-lookup"><span data-stu-id="0a78e-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a78e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a78e-110">See Also</span></span>  
 [<span data-ttu-id="0a78e-111">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="0a78e-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="0a78e-112">AddressOf işleci</span><span class="sxs-lookup"><span data-stu-id="0a78e-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="0a78e-113">Visual Basic'de genel yordamlar</span><span class="sxs-lookup"><span data-stu-id="0a78e-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [<span data-ttu-id="0a78e-114">Tür listesi</span><span class="sxs-lookup"><span data-stu-id="0a78e-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="0a78e-115">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0a78e-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

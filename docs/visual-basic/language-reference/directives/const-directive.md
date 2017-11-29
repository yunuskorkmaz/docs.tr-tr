---
title: "#<a name=\"const-directive\"></a>Const yönergesi"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6e162b01dc5c99fb7708337d259f9e66ddd6b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="const-directive"></a><span data-ttu-id="5a673-102">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5a673-102">#Const Directive</span></span>
<span data-ttu-id="5a673-103">Koşullu derleme sabitleri için Visual Basic tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a673-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a673-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a673-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="5a673-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5a673-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="5a673-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5a673-106">Required.</span></span> <span data-ttu-id="5a673-107">Tanımlanan sabiti adı.</span><span class="sxs-lookup"><span data-stu-id="5a673-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="5a673-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5a673-108">Required.</span></span> <span data-ttu-id="5a673-109">Değişmez değeri, diğer koşullu derleme sabiti ya da tüm aritmetik veya mantıksal işleçler dışında içeren herhangi bir birleşimini `Is`.</span><span class="sxs-lookup"><span data-stu-id="5a673-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a673-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a673-110">Remarks</span></span>  
 <span data-ttu-id="5a673-111">Koşullu derleme sabitleri her zaman göründükleri dosyasına özeldir.</span><span class="sxs-lookup"><span data-stu-id="5a673-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="5a673-112">Genel derleyici sabitleri kullanarak oluşturulamıyor `#Const` yönerge; oluşturabileceğiniz bunları yalnızca kullanıcı arabiriminde veya ile `/define` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5a673-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="5a673-113">Yalnızca koşullu derleyici sabit ve değişmez değerlerine kullanabilirsiniz `expression`.</span><span class="sxs-lookup"><span data-stu-id="5a673-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="5a673-114">İle tanımlanan bir standart sabit kullanarak `Const` bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="5a673-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="5a673-115">Buna karşılık, tanımlanmış sabitleri kullanabilirsiniz `#Const` anahtar sözcüğü yalnızca koşullu derleme için.</span><span class="sxs-lookup"><span data-stu-id="5a673-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="5a673-116">Sabitleri ayrıca tanımlanmamış, bu durumda bunlar değerine sahip `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5a673-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a673-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a673-117">Example</span></span>  
 <span data-ttu-id="5a673-118">Bu örnekte `#Const` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="5a673-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5a673-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a673-119">See Also</span></span>  
 [<span data-ttu-id="5a673-120">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a673-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)  
 [<span data-ttu-id="5a673-121">#If... Then... #Else yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5a673-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="5a673-122">Const deyimi</span><span class="sxs-lookup"><span data-stu-id="5a673-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="5a673-123">Koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="5a673-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="5a673-124">If... Then... Else deyimi</span><span class="sxs-lookup"><span data-stu-id="5a673-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

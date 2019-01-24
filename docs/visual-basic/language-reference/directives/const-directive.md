---
title: '##Const yönergesi (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 7e855f76a0fa8e6c06fd557a944c518641415f09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710605"
---
# <a name="const-directive"></a><span data-ttu-id="5b456-102">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5b456-102">#Const Directive</span></span>
<span data-ttu-id="5b456-103">Visual Basic için koşullu derleyici sabitlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5b456-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b456-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b456-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="5b456-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5b456-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="5b456-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5b456-106">Required.</span></span> <span data-ttu-id="5b456-107">Tanımlanan sabitin adı.</span><span class="sxs-lookup"><span data-stu-id="5b456-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="5b456-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5b456-108">Required.</span></span> <span data-ttu-id="5b456-109">Değişmez değeri, diğer koşullu derleyici sabiti ya da içeren tüm aritmetik veya mantıksal işleçleri dışında herhangi bir birleşimini `Is`.</span><span class="sxs-lookup"><span data-stu-id="5b456-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b456-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b456-110">Remarks</span></span>  
 <span data-ttu-id="5b456-111">Koşullu derleyici sabitleri, göründükleri dosyaya her zaman özeldir.</span><span class="sxs-lookup"><span data-stu-id="5b456-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="5b456-112">Genel derleyici sabitlerini kullanarak oluşturulamıyor `#Const` yönergesi; oluşturup bunları yalnızca kullanıcı arabirimi veya ile `/define` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5b456-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="5b456-113">Yalnızca koşullu derleyici sabitlerini ve sabit değerlerde kullanabileceğiniz `expression`.</span><span class="sxs-lookup"><span data-stu-id="5b456-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="5b456-114">İle tanımlanan bir standart sabit kullanarak `Const` bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="5b456-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="5b456-115">Buna karşılık, tanımlı sabitler kullanabileceğiniz `#Const` koşullu derleme için yalnızca anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5b456-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="5b456-116">Sabitler de tanımlanmamışsa, bu durumda bunlar değerine sahip `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5b456-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b456-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b456-117">Example</span></span>  
 <span data-ttu-id="5b456-118">Bu örnekte `#Const` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="5b456-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5b456-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b456-119">See also</span></span>
- [<span data-ttu-id="5b456-120">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b456-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
- [<span data-ttu-id="5b456-121">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5b456-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="5b456-122">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="5b456-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="5b456-123">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="5b456-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="5b456-124">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="5b456-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

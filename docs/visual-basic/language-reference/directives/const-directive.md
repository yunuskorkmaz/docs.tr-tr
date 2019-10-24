---
title: '#Const yönergesi (Visual Basic)'
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
ms.openlocfilehash: 031f35df24fd52aeeafcb7b4c0208806d7fc5fc4
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774749"
---
# <a name="const-directive"></a><span data-ttu-id="56147-102">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="56147-102">#Const Directive</span></span>
<span data-ttu-id="56147-103">Visual Basic için koşullu derleyici sabitleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="56147-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56147-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56147-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="56147-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="56147-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="56147-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="56147-106">Required.</span></span> <span data-ttu-id="56147-107">Tanımlanmakta olan sabitin adı.</span><span class="sxs-lookup"><span data-stu-id="56147-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="56147-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="56147-108">Required.</span></span> <span data-ttu-id="56147-109">Değişmez değer, diğer koşullu derleyici sabiti veya `Is` dışında herhangi bir ya da tüm aritmetik veya mantıksal işleçleri içeren herhangi bir bileşim.</span><span class="sxs-lookup"><span data-stu-id="56147-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56147-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56147-110">Remarks</span></span>  
 <span data-ttu-id="56147-111">Koşullu derleyici sabitleri, her zaman göründükleri dosya için özeldir.</span><span class="sxs-lookup"><span data-stu-id="56147-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="56147-112">@No__t_0 yönergesini kullanarak ortak derleyici sabitleri oluşturamazsınız; Onları yalnızca Kullanıcı arabiriminde veya `/define` derleyici seçeneğiyle oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56147-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="56147-113">@No__t_0 yalnızca koşullu derleyici sabitlerini ve sabit değerlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56147-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="56147-114">@No__t_0 ile tanımlanmış standart bir sabit kullanmak hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="56147-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="56147-115">Buna karşılık, yalnızca koşullu derleme için `#Const` anahtar sözcüğüyle tanımlanmış sabitleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56147-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="56147-116">Sabitler de tanımsız olabilir ve bu durumda `Nothing` değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="56147-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56147-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="56147-117">Example</span></span>  
 <span data-ttu-id="56147-118">Bu örnek `#Const` yönergesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="56147-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="56147-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56147-119">See also</span></span>

- [<span data-ttu-id="56147-120">-tanımla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56147-120">-define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
- [<span data-ttu-id="56147-121">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="56147-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="56147-122">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="56147-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="56147-123">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="56147-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="56147-124">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="56147-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

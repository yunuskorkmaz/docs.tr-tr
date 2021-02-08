---
description: 'Daha fazla bilgi edinin: #Const Yönergesi'
title: '#Const Yönergesi'
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
ms.openlocfilehash: 9597666ee1320f5dfda226040f93a84eb60a3deb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797282"
---
# <a name="const-directive"></a><span data-ttu-id="0f6cb-103">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0f6cb-103">#Const Directive</span></span>

<span data-ttu-id="0f6cb-104">Visual Basic için koşullu derleyici sabitleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-104">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f6cb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0f6cb-105">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="0f6cb-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0f6cb-106">Parts</span></span>  

 `constname`  
 <span data-ttu-id="0f6cb-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-107">Required.</span></span> <span data-ttu-id="0f6cb-108">Tanımlanmakta olan sabitin adı.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-108">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="0f6cb-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-109">Required.</span></span> <span data-ttu-id="0f6cb-110">Değişmez değer, diğer koşullu derleyici sabiti veya hariç herhangi bir ya da tüm aritmetik ya da mantıksal işleçleri içeren herhangi bir bileşim `Is` .</span><span class="sxs-lookup"><span data-stu-id="0f6cb-110">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f6cb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f6cb-111">Remarks</span></span>  

 <span data-ttu-id="0f6cb-112">Koşullu derleyici sabitleri, her zaman göründükleri dosya için özeldir.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-112">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="0f6cb-113">Yönergesini kullanarak genel derleyici sabitleri oluşturamazsınız `#Const` ; bunları yalnızca Kullanıcı arabiriminde veya `/define` derleyici seçeneğiyle oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-113">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="0f6cb-114">Yalnızca koşullu derleyici sabitlerini ve sabit değerlerini kullanabilirsiniz `expression` .</span><span class="sxs-lookup"><span data-stu-id="0f6cb-114">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="0f6cb-115">İle tanımlanmış standart bir sabit kullanılması `Const` hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-115">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="0f6cb-116">Buna karşılık, `#Const` yalnızca koşullu derleme için anahtar sözcükle tanımlanmış sabitleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-116">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="0f6cb-117">Sabitler de tanımsız olabilir ve bu durumda bir değeri olur `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="0f6cb-117">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f6cb-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f6cb-118">Example</span></span>  

 <span data-ttu-id="0f6cb-119">Bu örnek, `#Const` yönergesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-119">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0f6cb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-120">See also</span></span>

- [<span data-ttu-id="0f6cb-121">-tanımla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f6cb-121">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
- [<span data-ttu-id="0f6cb-122">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="0f6cb-122">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="0f6cb-123">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="0f6cb-123">Const Statement</span></span>](../statements/const-statement.md)
- [<span data-ttu-id="0f6cb-124">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="0f6cb-124">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="0f6cb-125">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="0f6cb-125">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)

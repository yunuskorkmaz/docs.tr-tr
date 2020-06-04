---
title: '#If...Then...#Else Yönergeleri'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 7054a6ada4583c5d89e020437eb622a59d3eb17a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410016"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="0082e-102">#If...Then...#Else Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0082e-102">#If...Then...#Else Directives</span></span>

<span data-ttu-id="0082e-103">Seçili Visual Basic kodu bloklarını koşullu olarak derler.</span><span class="sxs-lookup"><span data-stu-id="0082e-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="0082e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0082e-104">Syntax</span></span>

```vb
#If expression Then
   statements
[ #ElseIf expression Then
   [ statements ]
...
#ElseIf expression Then
   [ statements ] ]
[ #Else
   [ statements ] ]
#End If
```

## <a name="parts"></a><span data-ttu-id="0082e-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0082e-105">Parts</span></span>

`expression`  
<span data-ttu-id="0082e-106">`#If`Ve deyimleri için gerekli `#ElseIf` , başka bir yerde.</span><span class="sxs-lookup"><span data-stu-id="0082e-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="0082e-107">Veya olarak değerlendirilen bir veya daha fazla koşullu derleyici sabiti, sabit değer ve işleçlerden oluşan herhangi bir ifade `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="0082e-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="0082e-108">For deyimleri için gerekli `#If` , başka bir yerde.</span><span class="sxs-lookup"><span data-stu-id="0082e-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="0082e-109">İlişkili ifade olarak değerlendirildiğinde derlenen program satırları veya derleyici yönergeleri Visual Basic `True` .</span><span class="sxs-lookup"><span data-stu-id="0082e-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="0082e-110">`#If`Ekstre bloğunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="0082e-110">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="0082e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0082e-111">Remarks</span></span>

<span data-ttu-id="0082e-112">Yüzeyde, `#If...Then...#Else` yönergelerin davranışı deyimlerle aynı şekilde görünür `If...Then...Else` .</span><span class="sxs-lookup"><span data-stu-id="0082e-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="0082e-113">Ancak, `#If...Then...#Else` yönergeler derleyici tarafından derlendiğini değerlendirir, ancak `If...Then...Else` deyimler çalışma zamanında koşulları değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="0082e-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="0082e-114">Koşullu derleme genellikle farklı platformlar için aynı programı derlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0082e-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="0082e-115">Hata ayıklama kodunun yürütülebilir bir dosyada görünmesini engellemek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0082e-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="0082e-116">Koşullu derleme sırasında dışlanan kod, son yürütülebilir dosyadan tamamen atlandığından, boyut veya performans üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="0082e-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="0082e-117">Herhangi bir değerlendirmenin sonucuna bakılmaksızın, tüm ifadeler kullanılarak değerlendirilir `Option Compare Binary` .</span><span class="sxs-lookup"><span data-stu-id="0082e-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="0082e-118">`Option Compare`Deyimi `#If` ve `#ElseIf` deyimlerindeki ifadeleri etkilemez.</span><span class="sxs-lookup"><span data-stu-id="0082e-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="0082e-119">`#If`,, `#Else` `#ElseIf` Ve yönergelerinin tek satırlık formu yoktur `#End If` .</span><span class="sxs-lookup"><span data-stu-id="0082e-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="0082e-120">Diğer hiçbir kod, yönergelerden biriyle aynı satırda görünemez.</span><span class="sxs-lookup"><span data-stu-id="0082e-120">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="0082e-121">Koşullu derleme bloğunun içindeki deyimler, tamamlanmış Mantıksal deyimler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0082e-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="0082e-122">Örneğin, yalnızca bir işlevin özniteliklerini koşullu olarak derlenemez, ancak işlevi öznitelikleri ile birlikte koşullu olarak bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0082e-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="0082e-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="0082e-123">Example</span></span>

<span data-ttu-id="0082e-124">Bu örnek, `#If...Then...#Else` belirli deyimlerin derlenip derlenmeyeceğini anlamak için yapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0082e-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="0082e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0082e-125">See also</span></span>

- [<span data-ttu-id="0082e-126">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="0082e-126">#Const Directive</span></span>](const-directive.md)
- [<span data-ttu-id="0082e-127">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="0082e-127">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="0082e-128">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="0082e-128">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>

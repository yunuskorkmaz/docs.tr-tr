---
title: '#If... Then... #Else yönergeleri (Visual Basic)'
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
ms.openlocfilehash: 8c0aece749edf144fdd5c8ede9ec7e2e4c96ad54
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823395"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="8e95d-102">#If...Then...#Else Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8e95d-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="8e95d-103">Seçili Visual Basic kod bloklarını koşullu biçimde derler.</span><span class="sxs-lookup"><span data-stu-id="8e95d-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e95d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e95d-104">Syntax</span></span>  
  
```  
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
  
## <a name="parts"></a><span data-ttu-id="8e95d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8e95d-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="8e95d-106">Gerekli `#If` ve `#ElseIf` deyimleri, isteğe bağlı başka bir yerde.</span><span class="sxs-lookup"><span data-stu-id="8e95d-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="8e95d-107">Bir veya daha fazla koşullu derleyici sabitleri, sabit değerleri ve değerlendiren işleçler, özel olarak oluşan herhangi bir ifade `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="8e95d-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="8e95d-108">Gerekli `#If` deyim bloğu isteğe bağlı başka bir yerde.</span><span class="sxs-lookup"><span data-stu-id="8e95d-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="8e95d-109">Visual Basic program satırları veya ilişkili ifadenin değerlendirdiği, derlenmiş derleyici yönergeleri `True`.</span><span class="sxs-lookup"><span data-stu-id="8e95d-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="8e95d-110">Sonlandırır `#If` deyim bloğu.</span><span class="sxs-lookup"><span data-stu-id="8e95d-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e95d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e95d-111">Remarks</span></span>  
 <span data-ttu-id="8e95d-112">Yüzeysel olarak, davranışını `#If...Then...#Else` yönergeleri görünür aynı şekilde `If...Then...Else` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="8e95d-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="8e95d-113">Ancak, `#If...Then...#Else` yönergeleri değerlendirmek derleyici tarafından derlenmiş ise `If...Then...Else` deyimleri, çalışma zamanında koşulları değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="8e95d-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="8e95d-114">Koşullu derleme, genellikle aynı programın farklı platformlar için derlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e95d-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="8e95d-115">Önlemek için de kullanılan bir yürütülebilir dosya olarak görüntülenmesini kodda hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="8e95d-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="8e95d-116">Boyutu veya performans üzerinde hiçbir etkisi olmaz şekilde koşullu derleme sırasında dışlanan kod tamamen son yürütülebilir dosyadan atlandı.</span><span class="sxs-lookup"><span data-stu-id="8e95d-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="8e95d-117">Tüm değerlendirme sonucunu bağımsız olarak kullanarak tüm ifadeler değerlendirilir `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="8e95d-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="8e95d-118">`Option Compare` Deyimi ifadelerinde etkilemez `#If` ve `#ElseIf` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="8e95d-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e95d-119">Hiçbir tek satır biçiminde `#If`, `#Else`, `#ElseIf`, ve `#End If` yönergeler bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e95d-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="8e95d-120">Başka bir kod tüm yönergeleri ile aynı satırda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="8e95d-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="8e95d-121">Koşullu derleme bloğundaki ifadeleri tam mantıksal ifadeler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e95d-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="8e95d-122">Örneğin, yalnızca bir işlev özniteliklerini koşullu olarak derlenemez, ancak işlev özniteliklerini birlikte koşullu olarak bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8e95d-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="8e95d-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e95d-123">Example</span></span>
 <span data-ttu-id="8e95d-124">Bu örnekte `#If...Then...#Else` belirli deyimleri derleme belirlemek için yapı.</span><span class="sxs-lookup"><span data-stu-id="8e95d-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8e95d-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e95d-125">See also</span></span>

- [<span data-ttu-id="8e95d-126">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="8e95d-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="8e95d-127">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="8e95d-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="8e95d-128">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="8e95d-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>

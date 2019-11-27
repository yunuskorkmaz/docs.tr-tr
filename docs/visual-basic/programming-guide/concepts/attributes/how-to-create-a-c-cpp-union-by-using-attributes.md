---
title: 'Nasıl yapılır: öznitelikleri kullanarak CC++ birleşimi oluşturma'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: acb8dc781e2872ae46e5aa058a98b3dd98f3e064
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349493"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="bb47b-102">Nasıl yapılır: öznitelikleri kullanarak C/C++ Union oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb47b-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>

<span data-ttu-id="bb47b-103">Öznitelikleri kullanarak yapıların bellekte nasıl düzenlendiğini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb47b-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="bb47b-104">Örneğin, `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` özniteliklerini kullanarak C/C++ içinde birleşim olarak bilinen öğeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb47b-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="bb47b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb47b-105">Example</span></span>

<span data-ttu-id="bb47b-106">Bu kod kesiminde, tüm `TestUnion` alanları bellekte aynı konumda başlar.</span><span class="sxs-lookup"><span data-stu-id="bb47b-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a><span data-ttu-id="bb47b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb47b-107">Example</span></span>

<span data-ttu-id="bb47b-108">Aşağıda, alanların farklı bir açık küme konumlarında başlayacağı başka bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bb47b-108">The following is another example where fields start at different explicitly set locations.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

<span data-ttu-id="bb47b-109">İki tamsayı alanı `i1` ve `i2`, `lg`ile aynı bellek konumlarını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="bb47b-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="bb47b-110">Yapı düzeni üzerinde bu denetim sıralaması, platform çağırma kullanılırken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="bb47b-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb47b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb47b-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="bb47b-112">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bb47b-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="bb47b-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bb47b-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="bb47b-114">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb47b-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="bb47b-115">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb47b-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="bb47b-116">Özel öznitelikler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb47b-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="bb47b-117">Yansıma kullanarak özniteliklere erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb47b-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

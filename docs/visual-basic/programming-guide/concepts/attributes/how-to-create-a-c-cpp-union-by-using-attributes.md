---
title: 'Nasıl yapılır: (Visual Basic) öznitelikleri kullanarak C / C++ birleşimi oluşturma'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: e37aac03db7a24e6519acb4eb843b46b8c60b4f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663290"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="de7e0-102">Nasıl yapılır: Öznitelikler (Visual Basic) kullanarak bir C/C++ birleşimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="de7e0-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>
<span data-ttu-id="de7e0-103">Öznitelikleri kullanarak yapı birimleri bellekte nasıl düzenlenmiştir özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de7e0-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="de7e0-104">Örneğin, olarak C/C++'ta bir birleşim kullanarak Bilineni oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="de7e0-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de7e0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="de7e0-105">Example</span></span>  
 <span data-ttu-id="de7e0-106">Bu kesimdeki kod, tüm alanları `TestUnion` bellekte aynı konuma başlangıç.</span><span class="sxs-lookup"><span data-stu-id="de7e0-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="de7e0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="de7e0-107">Example</span></span>  
 <span data-ttu-id="de7e0-108">Başka bir örnek farklı alanları başlangıcında konumları açıkça ayarlandığı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="de7e0-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="de7e0-109">İki tamsayı alanları `i1` ve `i2`, aynı bellek konumları olarak paylaşma `lg`.</span><span class="sxs-lookup"><span data-stu-id="de7e0-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="de7e0-110">Platform çağırma kullanırken, bu tür bir yapı yerleşimi üzerinde denetim yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="de7e0-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7e0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de7e0-111">See also</span></span>
- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="de7e0-112">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="de7e0-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="de7e0-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de7e0-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="de7e0-114">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de7e0-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="de7e0-115">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de7e0-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="de7e0-116">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="de7e0-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="de7e0-117">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="de7e0-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

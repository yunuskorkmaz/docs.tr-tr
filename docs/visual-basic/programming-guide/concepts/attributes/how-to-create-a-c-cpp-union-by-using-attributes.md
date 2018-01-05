---
title: "Nasıl yapılır: öznitelikleri (Visual Basic) kullanarak C C++ birleşimi oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51d04c573e91a351c48edefebdb3d32fce1d306f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="804f1-102">Nasıl yapılır: öznitelikleri (Visual Basic) kullanarak C/C++ birleşimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="804f1-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>
<span data-ttu-id="804f1-103">Öznitelikleri kullanarak yapılar bellekte nasıl düzenlenmiştir özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="804f1-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="804f1-104">Örneğin, kullanarak C/c++ birleşimi olarak Bilineni oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="804f1-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="804f1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="804f1-105">Example</span></span>  
 <span data-ttu-id="804f1-106">Bu kesimdeki kod, tüm alanları `TestUnion` bellek aynı konumda başlatın.</span><span class="sxs-lookup"><span data-stu-id="804f1-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="804f1-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="804f1-107">Example</span></span>  
 <span data-ttu-id="804f1-108">Başka bir örnek farklı alanları başlangıcında açıkça konumları belirlendiği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="804f1-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="804f1-109">İki tamsayı alanlarının `i1` ve `i2`, aynı bellek konumları olarak paylaşma `lg`.</span><span class="sxs-lookup"><span data-stu-id="804f1-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="804f1-110">Platform çağırma kullanırken bu tür bir yapı düzeni denetime yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="804f1-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804f1-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="804f1-111">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="804f1-112">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="804f1-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="804f1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="804f1-113">Attributes</span></span>](../../../../standard/attributes/index.md)  
 [<span data-ttu-id="804f1-114">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="804f1-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="804f1-115">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="804f1-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="804f1-116">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="804f1-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="804f1-117">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="804f1-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

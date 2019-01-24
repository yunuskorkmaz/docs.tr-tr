---
title: 'Nasıl yapılır: Öznitelikleri kullanarak C / C++ birleşimi oluşturma (C#)'
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: a8b902536cd09ac732bf2144536605a66b5bbc56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599042"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="e7db6-102">Nasıl yapılır: Öznitelikleri kullanarak C/C++ birleşimi oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="e7db6-102">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>
<span data-ttu-id="e7db6-103">Öznitelikleri kullanarak yapı birimleri bellekte nasıl düzenlenmiştir özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7db6-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="e7db6-104">Örneğin, olarak C/C++'ta bir birleşim kullanarak Bilineni oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="e7db6-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7db6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7db6-105">Example</span></span>  
 <span data-ttu-id="e7db6-106">Bu kesimdeki kod, tüm alanları `TestUnion` bellekte aynı konuma başlangıç.</span><span class="sxs-lookup"><span data-stu-id="e7db6-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestUnion  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public byte b;  
       }  
```  
  
## <a name="example"></a><span data-ttu-id="e7db6-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7db6-107">Example</span></span>  
 <span data-ttu-id="e7db6-108">Başka bir örnek farklı alanları başlangıcında konumları açıkça ayarlandığı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7db6-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestExplicit  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public long lg;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i1;  
  
           [System.Runtime.InteropServices.FieldOffset(4)]  
           public int i2;  
  
           [System.Runtime.InteropServices.FieldOffset(8)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(12)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(14)]  
           public byte b;  
       }  
```  
  
 <span data-ttu-id="e7db6-109">İki tamsayı alanları `i1` ve `i2`, aynı bellek konumları olarak paylaşma `lg`.</span><span class="sxs-lookup"><span data-stu-id="e7db6-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="e7db6-110">Platform çağırma kullanırken, bu tür bir yapı yerleşimi üzerinde denetim yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="e7db6-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7db6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7db6-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="e7db6-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e7db6-112">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e7db6-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7db6-113">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="e7db6-114">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="e7db6-114">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="e7db6-115">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="e7db6-115">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="e7db6-116">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7db6-116">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="e7db6-117">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="e7db6-117">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

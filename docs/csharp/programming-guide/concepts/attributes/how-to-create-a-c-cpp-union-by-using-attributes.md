---
title: 'Nasıl yapılır: Öznitelikleri (C#) kullanarakC++ C birleşimi oluşturma'
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: fdadc9505b93f40c66001ac36345efada2edd270
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595365"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="b096c-102">Nasıl yapılır: Öznitelikleri kullanarak C/C++ Union oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="b096c-102">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>
<span data-ttu-id="b096c-103">Öznitelikleri kullanarak yapıların bellekte nasıl düzenlendiğini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b096c-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="b096c-104">Örneğin,C++ `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` özniteliklerini kullanarak C/içinde birleşim olarak bilinen öğeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b096c-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b096c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b096c-105">Example</span></span>  
 <span data-ttu-id="b096c-106">Bu kod kesiminde, tüm alanları `TestUnion` bellekte aynı konumda başlar.</span><span class="sxs-lookup"><span data-stu-id="b096c-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b096c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b096c-107">Example</span></span>  
 <span data-ttu-id="b096c-108">Aşağıda, alanların farklı bir açık küme konumlarında başlayacağı başka bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b096c-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="b096c-109">İki tamsayı alanı `i1` ve `i2`aynı bellek konumlarını `lg`ile paylaşır.</span><span class="sxs-lookup"><span data-stu-id="b096c-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="b096c-110">Yapı düzeni üzerinde bu denetim sıralaması, platform çağırma kullanılırken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b096c-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b096c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b096c-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="b096c-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b096c-112">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="b096c-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b096c-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="b096c-114">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="b096c-114">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="b096c-115">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="b096c-115">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="b096c-116">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="b096c-116">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
- [<span data-ttu-id="b096c-117">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="b096c-117">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)

---
title: "Nasıl yapılır: öznitelikleri (C#) kullanarak C C++ birleşimi oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 450fb922079ca6737b8db7754f25435b9c3b884b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="a91b3-102">Nasıl yapılır: öznitelikleri (C#) kullanarak C/C++ birleşimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a91b3-102">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>
<span data-ttu-id="a91b3-103">Öznitelikleri kullanarak yapılar bellekte nasıl düzenlenmiştir özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a91b3-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="a91b3-104">Örneğin, kullanarak C/c++ birleşimi olarak Bilineni oluşturabilirsiniz `StructLayout(LayoutKind.Explicit)` ve `FieldOffset` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="a91b3-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a91b3-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a91b3-105">Example</span></span>  
 <span data-ttu-id="a91b3-106">Bu kesimdeki kod, tüm alanları `TestUnion` bellek aynı konumda başlatın.</span><span class="sxs-lookup"><span data-stu-id="a91b3-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a91b3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a91b3-107">Example</span></span>  
 <span data-ttu-id="a91b3-108">Başka bir örnek farklı alanları başlangıcında açıkça konumları belirlendiği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a91b3-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="a91b3-109">İki tamsayı alanlarının `i1` ve `i2`, aynı bellek konumları olarak paylaşma `lg`.</span><span class="sxs-lookup"><span data-stu-id="a91b3-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="a91b3-110">Platform çağırma kullanırken bu tür bir yapı düzeni denetime yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a91b3-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91b3-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a91b3-111">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="a91b3-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a91b3-112">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a91b3-113">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="a91b3-113">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="a91b3-114">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="a91b3-114">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="a91b3-115">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="a91b3-115">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="a91b3-116">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="a91b3-116">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="a91b3-117">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="a91b3-117">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

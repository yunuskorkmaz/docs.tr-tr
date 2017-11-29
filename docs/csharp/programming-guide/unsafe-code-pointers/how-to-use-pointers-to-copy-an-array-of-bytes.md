---
title: "Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="ddd6e-102">Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ddd6e-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>
<span data-ttu-id="ddd6e-103">Aşağıdaki örnek, bir diziden bayt kopyalamak için işaretçiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddd6e-103">The following example uses pointers to copy bytes from one array to another.</span></span>  
  
 <span data-ttu-id="ddd6e-104">Bu örnekte [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) içinde işaretçileri kullanmanıza olanak tanır anahtar sözcüğü `Copy` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ddd6e-104">This example uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="ddd6e-105">[Sabit](../../../csharp/language-reference/keywords/fixed-statement.md) deyimi, kaynak ve hedef diziler işaretçiler bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ddd6e-105">The [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="ddd6e-106">Bu *PIN'ler* kaynak ve hedef konumu, böylece atık toplama tarafından taşınmayacak bellekte dizi.</span><span class="sxs-lookup"><span data-stu-id="ddd6e-106">This *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="ddd6e-107">Bellek blokları dizileri ne zaman sabitlenmemiş `fixed` blok tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ddd6e-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="ddd6e-108">Çünkü `Copy` Bu örnekte bir yöntem `unsafe` anahtar sözcüğü, onu derlenmelidir **/ unsafe** derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ddd6e-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the **/unsafe** compiler option.</span></span> <span data-ttu-id="ddd6e-109">Visual Studio'da seçeneğini ayarlamak için proje adına sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="ddd6e-109">To set the option in Visual Studio, right-click the project name, and then click **Properties**.</span></span> <span data-ttu-id="ddd6e-110">Üzerinde **yapı** sekmesine **güvenli olmayan kod izin**.</span><span class="sxs-lookup"><span data-stu-id="ddd6e-110">On the **Build** tab, select **Allow unsafe code**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddd6e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddd6e-111">Example</span></span>  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ddd6e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ddd6e-112">See Also</span></span>  
 [<span data-ttu-id="ddd6e-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ddd6e-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ddd6e-114">Güvenli olmayan kod ve işaretçiler</span><span class="sxs-lookup"><span data-stu-id="ddd6e-114">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="ddd6e-115">/ unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ddd6e-115">/unsafe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [<span data-ttu-id="ddd6e-116">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="ddd6e-116">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

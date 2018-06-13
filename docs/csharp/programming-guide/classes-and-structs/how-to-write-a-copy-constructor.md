---
title: 'Nasıl yapılır: Kopya Oluşturucu Yazma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 8a7cc85d40272918f4839d13fcccb79b558eeac7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322503"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="07eb7-102">Nasıl yapılır: Kopya Oluşturucu Yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="07eb7-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="07eb7-103">C# kopya Oluşturucu nesneler için sağlamaz, ancak kendiniz yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07eb7-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07eb7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="07eb7-104">Example</span></span>  
 <span data-ttu-id="07eb7-105">Aşağıdaki örnekte, `Person` [sınıfı](../../../csharp/language-reference/keywords/class.md) alır, bir kopya oluşturucu bağımsız değişken olarak, bir örneğini tanımlar `Person`.</span><span class="sxs-lookup"><span data-stu-id="07eb7-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="07eb7-106">Bağımsız değişken özelliklerinin değerleri yeni bir örneğini özelliklerine atanan `Person`.</span><span class="sxs-lookup"><span data-stu-id="07eb7-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="07eb7-107">Gönderen bir alternatif kopya Oluşturucu kodu içeren `Name` ve `Age` sınıfının örneği oluşturucusu kopyalamak istediğiniz örneğinin özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="07eb7-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="07eb7-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07eb7-108">See Also</span></span>  
 <xref:System.ICloneable>  
 [<span data-ttu-id="07eb7-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="07eb7-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="07eb7-110">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="07eb7-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="07eb7-111">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="07eb7-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="07eb7-112">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="07eb7-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

---
title: 'Nasıl yapılır: -Kopya Oluşturucu yazma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 169bdfc53d0c30ffc14e5a9525920679a94fbf23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651785"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="37c28-102">Nasıl yapılır: Kopya Oluşturucu yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="37c28-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="37c28-103">C# nesneler için bir kopya Oluşturucusu sağlamaz, ancak kendiniz bir tane yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37c28-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37c28-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="37c28-104">Example</span></span>  
 <span data-ttu-id="37c28-105">Aşağıdaki örnekte, `Person` [sınıfı](../../../csharp/language-reference/keywords/class.md) alan, bir kopya oluşturucu bağımsız değişken olarak, bir örneğini tanımlar `Person`.</span><span class="sxs-lookup"><span data-stu-id="37c28-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="37c28-106">Bağımsız değişken özelliklerinin değerleri, yeni bir örneğini özelliklerine atanan `Person`.</span><span class="sxs-lookup"><span data-stu-id="37c28-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="37c28-107">Gönderen bir alternatif bir kopya Oluşturucu kodunu içeren `Name` ve `Age` sınıfın örnek oluşturucusuna kopyalamak istediğiniz örneğin özellikleri.</span><span class="sxs-lookup"><span data-stu-id="37c28-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="37c28-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37c28-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="37c28-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="37c28-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="37c28-110">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="37c28-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="37c28-111">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="37c28-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="37c28-112">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="37c28-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

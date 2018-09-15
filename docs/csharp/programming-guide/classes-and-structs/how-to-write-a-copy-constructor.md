---
title: 'Nasıl yapılır: Kopya Oluşturucu Yazma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: d6ecfc3659dcf533db0f4e7b67fdffd620a584fd
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638116"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="64ce6-102">Nasıl yapılır: Kopya Oluşturucu Yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="64ce6-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="64ce6-103">C# nesneler için bir kopya Oluşturucusu sağlamaz, ancak kendiniz bir tane yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64ce6-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64ce6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="64ce6-104">Example</span></span>  
 <span data-ttu-id="64ce6-105">Aşağıdaki örnekte, `Person` [sınıfı](../../../csharp/language-reference/keywords/class.md) alan, bir kopya oluşturucu bağımsız değişken olarak, bir örneğini tanımlar `Person`.</span><span class="sxs-lookup"><span data-stu-id="64ce6-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="64ce6-106">Bağımsız değişken özelliklerinin değerleri, yeni bir örneğini özelliklerine atanan `Person`.</span><span class="sxs-lookup"><span data-stu-id="64ce6-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="64ce6-107">Gönderen bir alternatif bir kopya Oluşturucu kodunu içeren `Name` ve `Age` sınıfın örnek oluşturucusuna kopyalamak istediğiniz örneğin özellikleri.</span><span class="sxs-lookup"><span data-stu-id="64ce6-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="64ce6-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64ce6-108">See Also</span></span>

- <xref:System.ICloneable>  
- [<span data-ttu-id="64ce6-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="64ce6-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="64ce6-110">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="64ce6-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="64ce6-111">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="64ce6-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="64ce6-112">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="64ce6-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

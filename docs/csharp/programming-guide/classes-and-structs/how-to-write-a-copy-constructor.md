---
title: 'Nasıl yapılır: Kopya Oluşturucu yazma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: bdc352566052f4cec1686176131e9b1e1b768794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596609"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="8d8ce-102">Nasıl yapılır: Kopya Oluşturucu yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8d8ce-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="8d8ce-103">C#nesneler için bir kopya Oluşturucu sağlamaz, ancak kendiniz bir tane yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d8ce-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d8ce-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d8ce-104">Example</span></span>  
 <span data-ttu-id="8d8ce-105">Aşağıdaki örnekte `Person` [sınıfı](../../language-reference/keywords/class.md) , bir örneği `Person`olan bağımsız değişkeni olarak alan bir kopya Oluşturucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8d8ce-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="8d8ce-106">Bağımsız değişkeninin özelliklerinin değerleri, yeni örneğinin `Person`özelliklerine atanır.</span><span class="sxs-lookup"><span data-stu-id="8d8ce-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="8d8ce-107">Kod, sınıfının örnek oluşturucusuna kopyalamak istediğiniz örneğin `Name` ve `Age` özelliklerini gönderen alternatif bir kopya Oluşturucu içerir.</span><span class="sxs-lookup"><span data-stu-id="8d8ce-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="8d8ce-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d8ce-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="8d8ce-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8d8ce-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8d8ce-110">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="8d8ce-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="8d8ce-111">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="8d8ce-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="8d8ce-112">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="8d8ce-112">Finalizers</span></span>](./destructors.md)

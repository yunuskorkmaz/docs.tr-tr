---
title: Kopya oluşturucu nasıl yazılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714848"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="a8c07-102">Kopya oluşturucu nasıl yazılır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a8c07-102">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="a8c07-103">C# nesneler için bir kopya oluşturucu sağlamaz, ancak kendiniz yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8c07-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8c07-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8c07-104">Example</span></span>  
 <span data-ttu-id="a8c07-105">Aşağıdaki örnekte, `Person` [sınıf,](../../language-reference/keywords/class.md) bağımsız değişkeni olarak `Person`bir kopyasını alan bir kopya oluşturucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a8c07-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="a8c07-106">Bağımsız değişkenin özelliklerinin değerleri yeni örneğin in özelliklerine `Person`atanır.</span><span class="sxs-lookup"><span data-stu-id="a8c07-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="a8c07-107">Kod, kopyalamak istediğiniz örneğin `Name` özelliklerini `Age` ve özelliklerini sınıfın örnek oluşturucuya gönderen alternatif bir kopya oluşturucu içerir.</span><span class="sxs-lookup"><span data-stu-id="a8c07-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="a8c07-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8c07-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="a8c07-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a8c07-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a8c07-110">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="a8c07-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="a8c07-111">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a8c07-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="a8c07-112">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="a8c07-112">Finalizers</span></span>](./destructors.md)

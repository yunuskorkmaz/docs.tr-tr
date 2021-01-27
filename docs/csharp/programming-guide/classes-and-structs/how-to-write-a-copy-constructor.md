---
title: Kopya Oluşturucu yazma-C# Programlama Kılavuzu
description: Sınıfının bir örneğini alan ve girişin değerleriyle yeni bir örnek döndüren C# ' de bir kopya Oluşturucu yazmayı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: db26b26ebcc51b57fdbe58ddaf92e5019cb69659
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899392"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="6b32d-103">Kopya Oluşturucu yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6b32d-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="6b32d-104">C# nesneler için bir kopya Oluşturucu sağlamaz, ancak kendiniz bir tane yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b32d-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b32d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b32d-105">Example</span></span>  

 <span data-ttu-id="6b32d-106">Aşağıdaki örnekte `Person` [sınıfı](../../language-reference/keywords/class.md) , bir örneği olan bağımsız değişkeni olarak alan bir kopya Oluşturucu tanımlar `Person` .</span><span class="sxs-lookup"><span data-stu-id="6b32d-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="6b32d-107">Bağımsız değişkeninin özelliklerinin değerleri, yeni örneğinin özelliklerine atanır `Person` .</span><span class="sxs-lookup"><span data-stu-id="6b32d-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="6b32d-108">Kod, `Name` `Age` sınıfının örnek oluşturucusuna kopyalamak istediğiniz örneğin ve özelliklerini gönderen alternatif bir kopya Oluşturucu içerir.</span><span class="sxs-lookup"><span data-stu-id="6b32d-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]
  
## <a name="see-also"></a><span data-ttu-id="6b32d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b32d-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="6b32d-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6b32d-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6b32d-111">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="6b32d-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="6b32d-112">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="6b32d-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="6b32d-113">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="6b32d-113">Finalizers</span></span>](./destructors.md)

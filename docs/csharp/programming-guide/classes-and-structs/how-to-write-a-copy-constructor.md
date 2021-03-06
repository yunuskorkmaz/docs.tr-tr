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
ms.openlocfilehash: c61018444dd600d6f33765b104034355d0301667
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255242"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="c0691-103">Kopya Oluşturucu yazma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c0691-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="c0691-104">C# [kayıtları](records.md) nesneler için bir kopya Oluşturucusu sağlar, ancak sınıflar için kendiniz yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0691-104">C# [records](records.md) provide a copy constructor for objects, but for classes you have to write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0691-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0691-105">Example</span></span>  

 <span data-ttu-id="c0691-106">Aşağıdaki örnekte `Person` [sınıfı](../../language-reference/keywords/class.md) , bir örneği olan bağımsız değişkeni olarak alan bir kopya Oluşturucu tanımlar `Person` .</span><span class="sxs-lookup"><span data-stu-id="c0691-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="c0691-107">Bağımsız değişkeninin özelliklerinin değerleri, yeni örneğinin özelliklerine atanır `Person` .</span><span class="sxs-lookup"><span data-stu-id="c0691-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="c0691-108">Kod, `Name` `Age` sınıfının örnek oluşturucusuna kopyalamak istediğiniz örneğin ve özelliklerini gönderen alternatif bir kopya Oluşturucu içerir.</span><span class="sxs-lookup"><span data-stu-id="c0691-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]

## <a name="see-also"></a><span data-ttu-id="c0691-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0691-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="c0691-110">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="c0691-110">Records</span></span>](records.md)
- [<span data-ttu-id="c0691-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c0691-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c0691-112">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="c0691-112">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="c0691-113">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="c0691-113">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="c0691-114">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="c0691-114">Finalizers</span></span>](./destructors.md)

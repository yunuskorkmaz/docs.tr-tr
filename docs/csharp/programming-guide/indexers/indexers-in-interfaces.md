---
title: Arabirimlerde Dizin oluşturucular-C# Programlama Kılavuzu
description: Dizin oluşturucular C# içindeki bir arabirimde bildirilemez. Arabirim dizin oluşturucular erişimcilerinin sınıf dizin oluşturucularının Erişimcilerden farklı olduğunu öğrenin.
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303107"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="9fd1b-104">Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9fd1b-104">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="9fd1b-105">Dizin oluşturucular bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-105">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="9fd1b-106">Arabirim dizin oluşturucularının erişimcileri, [sınıf](../../language-reference/keywords/class.md) dizin oluşturucularının erişimcilerine aşağıdaki yollarla göre farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="9fd1b-106">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="9fd1b-107">Arabirim erişimcileri değiştiriciler kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-107">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="9fd1b-108">Arabirim erişimcisinin genellikle gövdesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-108">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="9fd1b-109">Erişimcinin amacı, dizin oluşturucunun okuma-yazma, salt okunurdur veya salt yazılır olduğunu belirtsağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-109">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="9fd1b-110">Bir arabirimde tanımlanmış bir Dizin Oluşturucu için uygulama sağlayabilirsiniz, ancak bu nadir bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-110">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="9fd1b-111">Dizin oluşturucular genellikle veri alanlarına erişmek için bir API tanımlar ve veri alanları bir arabirimde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-111">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="9fd1b-112">Arabirim dizin oluşturucu erişimcisine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9fd1b-112">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="9fd1b-113">Bir dizin oluşturucunun imzası aynı arabirimde belirtilen diğer tüm dizin oluşturucularının imzalarından farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-113">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="9fd1b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fd1b-114">Example</span></span>

<span data-ttu-id="9fd1b-115">Aşağıdaki örnek, arabirim dizin oluşturucularının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-115">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="9fd1b-116">Yukarıdaki örnekte, arabirim üyesinin tam adını kullanarak açık arabirim üye uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-116">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="9fd1b-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9fd1b-117">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="9fd1b-118">Ancak, tam adı yalnızca, sınıf aynı Dizin Oluşturucu imzasına sahip birden fazla arabirim uygularken karışıklığı önlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-118">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="9fd1b-119">Örneğin, bir `Employee` Sınıf iki arabirim uygusa ve `ICitizen` `IEmployee` her iki arabirimde de aynı Dizin Oluşturucu imzası varsa, açık arabirim üye uygulaması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-119">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="9fd1b-120">Diğer bir deyişle, aşağıdaki Dizin Oluşturucu bildirimi:</span><span class="sxs-lookup"><span data-stu-id="9fd1b-120">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="9fd1b-121">arabirim üzerinde dizin oluşturucuyu uygular `IEmployee` , aşağıdaki bildirim:</span><span class="sxs-lookup"><span data-stu-id="9fd1b-121">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="9fd1b-122">arabirimindeki Dizin oluşturucuyu uygular `ICitizen` .</span><span class="sxs-lookup"><span data-stu-id="9fd1b-122">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fd1b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fd1b-123">See also</span></span>

- [<span data-ttu-id="9fd1b-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9fd1b-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9fd1b-125">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="9fd1b-125">Indexers</span></span>](./index.md)
- [<span data-ttu-id="9fd1b-126">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9fd1b-126">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="9fd1b-127">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="9fd1b-127">Interfaces</span></span>](../interfaces/index.md)

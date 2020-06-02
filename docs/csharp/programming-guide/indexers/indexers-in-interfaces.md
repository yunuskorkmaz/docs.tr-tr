---
title: Arabirimlerde Dizin oluşturucular-C# Programlama Kılavuzu
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 9ce6e4f0e0533c2880c6241f44409435248a336a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287486"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="60934-102">Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="60934-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="60934-103">Dizin oluşturucular bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="60934-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="60934-104">Arabirim dizin oluşturucularının erişimcileri, [sınıf](../../language-reference/keywords/class.md) dizin oluşturucularının erişimcilerine aşağıdaki yollarla göre farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="60934-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="60934-105">Arabirim erişimcileri değiştiriciler kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="60934-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="60934-106">Arabirim erişimcisinin genellikle gövdesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="60934-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="60934-107">Erişimcinin amacı, dizin oluşturucunun okuma-yazma, salt okunurdur veya salt yazılır olduğunu belirtsağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="60934-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="60934-108">Bir arabirimde tanımlanmış bir Dizin Oluşturucu için uygulama sağlayabilirsiniz, ancak bu nadir bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="60934-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="60934-109">Dizin oluşturucular genellikle veri alanlarına erişmek için bir API tanımlar ve veri alanları bir arabirimde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="60934-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="60934-110">Arabirim dizin oluşturucu erişimcisine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="60934-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="60934-111">Bir dizin oluşturucunun imzası aynı arabirimde belirtilen diğer tüm dizin oluşturucularının imzalarından farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60934-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="60934-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="60934-112">Example</span></span>

<span data-ttu-id="60934-113">Aşağıdaki örnek, arabirim dizin oluşturucularının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="60934-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="60934-114">Yukarıdaki örnekte, arabirim üyesinin tam adını kullanarak açık arabirim üye uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60934-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="60934-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="60934-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="60934-116">Ancak, tam adı yalnızca, sınıf aynı Dizin Oluşturucu imzasına sahip birden fazla arabirim uygularken karışıklığı önlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="60934-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="60934-117">Örneğin, bir `Employee` Sınıf iki arabirim uygusa ve `ICitizen` `IEmployee` her iki arabirimde de aynı Dizin Oluşturucu imzası varsa, açık arabirim üye uygulaması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="60934-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="60934-118">Diğer bir deyişle, aşağıdaki Dizin Oluşturucu bildirimi:</span><span class="sxs-lookup"><span data-stu-id="60934-118">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="60934-119">arabirim üzerinde dizin oluşturucuyu uygular `IEmployee` , aşağıdaki bildirim:</span><span class="sxs-lookup"><span data-stu-id="60934-119">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="60934-120">arabirimindeki Dizin oluşturucuyu uygular `ICitizen` .</span><span class="sxs-lookup"><span data-stu-id="60934-120">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="60934-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60934-121">See also</span></span>

- [<span data-ttu-id="60934-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="60934-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="60934-123">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="60934-123">Indexers</span></span>](./index.md)
- [<span data-ttu-id="60934-124">Özellikler</span><span class="sxs-lookup"><span data-stu-id="60934-124">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="60934-125">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="60934-125">Interfaces</span></span>](../interfaces/index.md)

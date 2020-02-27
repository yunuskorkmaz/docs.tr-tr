---
title: Arabirimlerde Dizin oluşturucular- C# Programlama Kılavuzu
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627844"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="74cb7-102">Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="74cb7-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="74cb7-103">Dizin oluşturucular bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="74cb7-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="74cb7-104">Arabirim dizin oluşturucularının erişimcileri, [sınıf](../../language-reference/keywords/class.md) dizin oluşturucularının erişimcilerine aşağıdaki yollarla göre farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="74cb7-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="74cb7-105">Arabirim erişimcileri değiştiriciler kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="74cb7-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="74cb7-106">Arabirim erişimcisinin genellikle gövdesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="74cb7-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="74cb7-107">Erişimcinin amacı, dizin oluşturucunun okuma-yazma, salt okunurdur veya salt yazılır olduğunu belirtsağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="74cb7-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="74cb7-108">Bir arabirimde tanımlanmış bir Dizin Oluşturucu için uygulama sağlayabilirsiniz, ancak bu nadir bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="74cb7-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="74cb7-109">Dizin oluşturucular genellikle veri alanlarına erişmek için bir API tanımlar ve veri alanları bir arabirimde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="74cb7-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="74cb7-110">Arabirim dizin oluşturucu erişimcisine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="74cb7-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="74cb7-111">Bir dizin oluşturucunun imzası aynı arabirimde belirtilen diğer tüm dizin oluşturucularının imzalarından farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74cb7-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="74cb7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="74cb7-112">Example</span></span>

<span data-ttu-id="74cb7-113">Aşağıdaki örnek, arabirim dizin oluşturucularının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="74cb7-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="74cb7-114">Yukarıdaki örnekte, arabirim üyesinin tam adını kullanarak açık arabirim üye uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74cb7-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="74cb7-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="74cb7-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="74cb7-116">Ancak, tam adı yalnızca, sınıf aynı Dizin Oluşturucu imzasına sahip birden fazla arabirim uygularken karışıklığı önlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="74cb7-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="74cb7-117">Örneğin, bir `Employee` sınıfı iki arabirim uygusa, `ICitizen` ve `IEmployee`ve her iki arabirimde de aynı Dizin Oluşturucu imzası varsa, açık arabirim üye uygulaması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="74cb7-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="74cb7-118">Diğer bir deyişle, aşağıdaki Dizin Oluşturucu bildirimi:</span><span class="sxs-lookup"><span data-stu-id="74cb7-118">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
``

implements the indexer on the `IEmployee` interface, while the following declaration:

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="74cb7-119">`ICitizen` arabirimindeki Dizin oluşturucuyu uygular.</span><span class="sxs-lookup"><span data-stu-id="74cb7-119">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="74cb7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74cb7-120">See also</span></span>

- [<span data-ttu-id="74cb7-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="74cb7-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="74cb7-122">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="74cb7-122">Indexers</span></span>](./index.md)
- [<span data-ttu-id="74cb7-123">Özellikler</span><span class="sxs-lookup"><span data-stu-id="74cb7-123">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="74cb7-124">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="74cb7-124">Interfaces</span></span>](../interfaces/index.md)

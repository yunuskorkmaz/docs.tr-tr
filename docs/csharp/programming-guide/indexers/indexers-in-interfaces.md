---
title: Arayüzlerde Dizinleyiciler - C# Programlama Kılavuzu
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627844"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="96a4f-102">Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="96a4f-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="96a4f-103">Dizin leyiciler bir [arabirimde](../../language-reference/keywords/interface.md)bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="96a4f-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="96a4f-104">Arabirim dizinleyicilerinin erişenleri [sınıf](../../language-reference/keywords/class.md) dizinleyicilerinin erişimcilerinden aşağıdaki şekillerde farklıdır:</span><span class="sxs-lookup"><span data-stu-id="96a4f-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="96a4f-105">Arabirim erişimcileri değiştirici kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="96a4f-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="96a4f-106">Arabirim erişimcisi genellikle bir gövdeye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="96a4f-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="96a4f-107">Erişimamacının amacı, dizin leyicinin okuma-yazma, salt okuma veya yalnızca yazma olup olmadığını belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="96a4f-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="96a4f-108">Arabirimde tanımlanan bir dizinleyici için bir uygulama sağlayabilirsiniz, ancak bu nadirdir.</span><span class="sxs-lookup"><span data-stu-id="96a4f-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="96a4f-109">Dizin leyiciler genellikle veri alanlarına erişmek için bir API tanımlar ve veri alanları bir arabirimde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="96a4f-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="96a4f-110">Aşağıda bir arabirim dizinleyici erişime yenisi örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="96a4f-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="96a4f-111">Bir dizinleyicinin imzası, aynı arabirimde bildirilen diğer tüm dizinleyicilerin imzalarından farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="96a4f-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="96a4f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="96a4f-112">Example</span></span>

<span data-ttu-id="96a4f-113">Aşağıdaki örnek, arabirim dizinleyicilerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96a4f-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="96a4f-114">Önceki örnekte, arabirim üyesinin tam nitelikli adını kullanarak açık arabirim üyesi uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96a4f-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="96a4f-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="96a4f-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="96a4f-116">Ancak, tam nitelikli ad yalnızca sınıf aynı dizinleyici imzası ile birden fazla arabirim uygularken belirsizliği önlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="96a4f-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="96a4f-117">Örneğin, bir `Employee` sınıf iki arabirim uyguluyorsa `ICitizen` ve `IEmployee`her iki arabirim de aynı dizinleyici imzaya sahipse, açık arabirim üyesi uygulaması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="96a4f-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="96a4f-118">Diğer bir şey, aşağıdaki dizinleyici bildirimi:</span><span class="sxs-lookup"><span data-stu-id="96a4f-118">That is, the following indexer declaration:</span></span>

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

<span data-ttu-id="96a4f-119">arabirim deki dizinleyiciyi `ICitizen` uygular.</span><span class="sxs-lookup"><span data-stu-id="96a4f-119">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="96a4f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96a4f-120">See also</span></span>

- [<span data-ttu-id="96a4f-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="96a4f-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="96a4f-122">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="96a4f-122">Indexers</span></span>](./index.md)
- [<span data-ttu-id="96a4f-123">Özellikler</span><span class="sxs-lookup"><span data-stu-id="96a4f-123">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="96a4f-124">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="96a4f-124">Interfaces</span></span>](../interfaces/index.md)

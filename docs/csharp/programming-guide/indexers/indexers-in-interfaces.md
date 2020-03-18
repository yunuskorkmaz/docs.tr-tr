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
# <a name="indexers-in-interfaces-c-programming-guide"></a>Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)

Dizin leyiciler bir [arabirimde](../../language-reference/keywords/interface.md)bildirilebilir. Arabirim dizinleyicilerinin erişenleri [sınıf](../../language-reference/keywords/class.md) dizinleyicilerinin erişimcilerinden aşağıdaki şekillerde farklıdır:

- Arabirim erişimcileri değiştirici kullanmaz.
- Arabirim erişimcisi genellikle bir gövdeye sahip değildir.

Erişimamacının amacı, dizin leyicinin okuma-yazma, salt okuma veya yalnızca yazma olup olmadığını belirtmektir. Arabirimde tanımlanan bir dizinleyici için bir uygulama sağlayabilirsiniz, ancak bu nadirdir. Dizin leyiciler genellikle veri alanlarına erişmek için bir API tanımlar ve veri alanları bir arabirimde tanımlanamaz.

Aşağıda bir arabirim dizinleyici erişime yenisi örneği verilmiştir:

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

Bir dizinleyicinin imzası, aynı arabirimde bildirilen diğer tüm dizinleyicilerin imzalarından farklı olmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, arabirim dizinleyicilerin nasıl uygulanacağını gösterir.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

Önceki örnekte, arabirim üyesinin tam nitelikli adını kullanarak açık arabirim üyesi uygulamasını kullanabilirsiniz. Örneğin:

```csharp
string IIndexInterface.this[int index]
{
}
```

Ancak, tam nitelikli ad yalnızca sınıf aynı dizinleyici imzası ile birden fazla arabirim uygularken belirsizliği önlemek için gereklidir. Örneğin, bir `Employee` sınıf iki arabirim uyguluyorsa `ICitizen` ve `IEmployee`her iki arabirim de aynı dizinleyici imzaya sahipse, açık arabirim üyesi uygulaması gereklidir. Diğer bir şey, aşağıdaki dizinleyici bildirimi:

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

arabirim deki dizinleyiciyi `ICitizen` uygular.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Özellikler](../classes-and-structs/properties.md)
- [Arabirimler](../interfaces/index.md)

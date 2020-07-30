---
title: İfade-Bodied Üyeler-C# Programlama Kılavuzu
description: İfade-Bodied Üyeler hakkında bilgi edinin. Özellikler, oluşturucular, sonlandırıcılar ve daha fazlası için ifade gövdesi tanımı kullanan kod örneklerine bakın.
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: e68e96e4aa3ff6a64590459a7197da1833e1a275
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381664"
---
# <a name="expression-bodied-members-c-programming-guide"></a>İfade-Bodied Üyeler (C# Programlama Kılavuzu)

İfade gövdesi tanımları, üyenin uygulamasını çok kısa, okunabilir bir biçimde sağlamanıza olanak tanır. Bir yöntem veya özellik gibi desteklenen herhangi bir üyenin mantığı tek bir ifadeden oluşuyorsa, bir ifade gövdesi tanımı kullanabilirsiniz. Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:

```csharp
member => expression;
```

Burada *ifadesi* geçerli bir ifadedir.

C# 6 ' da Yöntemler ve salt okunurdur özellikler için ifade gövdesi tanımları desteği sunuldu ve c# 7,0 ' de genişletilmişti. İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri ile birlikte kullanılabilir:

|Üye  |İtibariyle destekleniyor... |
|---------|---------|
|[Yöntem](#methods)  |C# 6 |
|[Salt okunurdur özelliği](#read-only-properties)   |C# 6  |
|[Özellik](#properties)  |C# 7.0 |
|[Oluşturucu](#constructors)   |C# 7.0 |
|[Sonlandırıcı](#finalizers)     |C# 7.0 |
|[Dizin Oluşturucu](#indexers)       |C# 7.0 |

## <a name="methods"></a>Yöntemler

Bir ifade-Bodied yöntemi, türü yöntemin dönüş türüyle eşleşen bir değer döndüren tek bir ifadeden oluşur veya döndürülen yöntemler için `void` bazı işlemleri gerçekleştirir. Örneğin, yöntemi geçersiz kılan türler, <xref:System.Object.ToString%2A> genellikle geçerli nesnenin dize gösterimini döndüren tek bir ifade içerir.

Aşağıdaki örnek, `Person` <xref:System.Object.ToString%2A> bir ifade gövdesi tanımıyla yöntemi geçersiz kılan bir sınıfı tanımlar. Ayrıca `DisplayName` , konsola bir ad görüntüleyen bir yöntemi tanımlar. `return`Anahtar sözcüğünün `ToString` ifade gövdesi tanımında kullanılmadığını unutmayın.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Daha fazla bilgi için bkz. [Yöntemler (C# Programlama Kılavuzu)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Salt okunurdur özellikleri

C# 6 ' dan itibaren, salt okunurdur bir özellik uygulamak için ifade gövdesi tanımı kullanabilirsiniz. Bunu yapmak için aşağıdaki sözdizimini kullanın:

```csharp
PropertyType PropertyName => expression;
```

Aşağıdaki örnek, `Location` salt okunurdur `Name` özelliği özel alanın değerini döndüren bir ifade gövdesi tanımı olarak uygulanan bir sınıfı tanımlar `locationName` :

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Özellikler hakkında daha fazla bilgi için bkz. [Özellikler (C# Programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="properties"></a>Özellikler

C# 7,0 ' den başlayarak, özellik ve erişimcileri uygulamak için ifade gövdesi tanımları `get` kullanabilirsiniz `set` . Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Özellikler hakkında daha fazla bilgi için bkz. [Özellikler (C# Programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Oluşturucular

Bir oluşturucunun ifade gövdesi tanımı genellikle tek bir atama ifadesi veya oluşturucunun bağımsız değişkenlerini işleyen veya örnek durumunu Başlatan bir yöntem çağrısından oluşur.

Aşağıdaki örnek, `Location` oluşturucusunun *adı*adlı tek bir dize parametresine sahip olan bir sınıfı tanımlar. İfade gövdesi tanımı bağımsız değişkeni `Name` özelliğine atar.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Daha fazla bilgi için bkz. [oluşturucular (C# Programlama Kılavuzu)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Sonlandırıcılar

Sonlandırıcı için bir ifade gövdesi tanımı tipik olarak, yönetilmeyen kaynakları serbest bırakma deyimleri gibi temizleme deyimlerini içerir.

Aşağıdaki örnek, sonlandırıcının çağrıldığını göstermek için bir ifade gövde tanımı kullanan sonlandırıcıyı tanımlar.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Daha fazla bilgi için bkz. [sonlandırıcılar (C# Programlama Kılavuzu)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Dizin Oluşturucular

Özellikler ile olduğu gibi, `get` `set` `get` erişimci bir değer döndüren tek bir ifadeden oluşuyorsa veya `set` erişimci basit bir atama gerçekleştirdiğinde, Dizin Oluşturucu ve erişimciler ifade gövdesi tanımlarından oluşur.

Aşağıdaki örnek adlı bir sınıfı tanımlar `Sports` . Bu, bir dizi <xref:System.String> spor adını içeren bir iç dizi içerir. Dizin Oluşturucu `get` ve `set` erişimciler, ifade gövdesi tanımları olarak uygulanır.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Daha fazla bilgi için bkz. [Dizin oluşturucular (C# Programlama Kılavuzu)](../indexers/index.md).

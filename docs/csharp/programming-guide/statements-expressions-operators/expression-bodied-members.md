---
title: İfade-Bodied Üyeler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: 45dcc58b252963e80798ba86ca5c4f461d493fac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120143"
---
# <a name="expression-bodied-members-c-programming-guide"></a>İfade-Bodied Üyeler (C# Programlama Kılavuzu)

İfade gövdesi tanımları, üyenin uygulamasını çok kısa, okunabilir bir biçimde sağlamanıza olanak tanır. Bir yöntem veya özellik gibi desteklenen herhangi bir üyenin mantığı tek bir ifadeden oluşuyorsa, bir ifade gövdesi tanımı kullanabilirsiniz. Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:

```csharp
member => expression;
```

Burada *ifadesi* geçerli bir ifadedir.

6 ' C# da Yöntemler ve salt okunurdur özellikler için ifade gövdesi tanımları desteği sunuldu ve 7,0 ' de C# genişletildi. İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri ile birlikte kullanılabilir:

|Üye  |İtibariyle destekleniyor... |
|---------|---------|
|[Yöntemidir](#methods)  |C# 6 |
|[Salt okunurdur özelliği](#read-only-properties)   |C# 6  |
|[Özelliði](#properties)  |C# 7.0 |
|[Constructor](#constructors)   |C# 7.0 |
|[Sonlandırıcı](#finalizers)     |C# 7.0 |
|[Dizinleyic](#indexers)       |C# 7.0 |

## <a name="methods"></a>Yöntemler

İfade-Bodied yöntemi, türü yöntemin dönüş türüyle eşleşen bir değer döndüren tek bir ifadeden oluşur veya `void`döndüren yöntemler için bazı işlemleri gerçekleştirir. Örneğin, <xref:System.Object.ToString%2A> yöntemini geçersiz kılan türler, genellikle geçerli nesnenin dize gösterimini döndüren tek bir ifade içerir.

Aşağıdaki örnek, bir ifade gövdesi tanımıyla <xref:System.Object.ToString%2A> yöntemini geçersiz kılan bir `Person` sınıfını tanımlar. Ayrıca, konsola bir ad görüntüleyen bir `DisplayName` yöntemi tanımlar. `return` anahtar sözcüğünün `ToString` ifadesi gövde tanımında kullanılmadığını unutmayın.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Daha fazla bilgi için bkz. [YöntemlerC# (Programlama Kılavuzu)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Salt okunurdur özellikleri

C# 6 ' dan itibaren, salt okunurdur bir özellik uygulamak için ifade gövdesi tanımı kullanabilirsiniz. Bunu yapmak için aşağıdaki sözdizimini kullanın:

```csharp
PropertyType PropertyName => expression;
```

Aşağıdaki örnek, salt okunurdur `Name` özelliği özel `locationName` alanının değerini döndüren bir ifade gövdesi tanımı olarak uygulanan bir `Location` sınıfını tanımlar:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Özellikler hakkında daha fazla bilgi için bkz. [ÖzelliklerC# (Programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="properties"></a>Özellikler

7,0 ' C# den başlayarak, özellik`get`ve`set`erişimcileri uygulamak için ifade gövdesi tanımlarını kullanabilirsiniz. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Özellikler hakkında daha fazla bilgi için bkz. [ÖzelliklerC# (Programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Oluşturucular

Bir oluşturucunun ifade gövdesi tanımı genellikle tek bir atama ifadesi veya oluşturucunun bağımsız değişkenlerini işleyen veya örnek durumunu Başlatan bir yöntem çağrısından oluşur.

Aşağıdaki örnek, oluşturucusunun *adı*adlı tek bir dize parametresine sahip bir `Location` sınıfını tanımlar. İfade gövdesi tanımı, bağımsız değişkeni `Name` özelliğine atar.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Daha fazla bilgi için bkz. [oluşturucularC# (Programlama Kılavuzu)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Sonlandırıcılar

Sonlandırıcı için bir ifade gövdesi tanımı tipik olarak, yönetilmeyen kaynakları serbest bırakma deyimleri gibi temizleme deyimlerini içerir.

Aşağıdaki örnek, sonlandırıcının çağrıldığını göstermek için bir ifade gövde tanımı kullanan sonlandırıcıyı tanımlar.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Daha fazla bilgi için bkz. [sonlandırıcılarC# (Programlama Kılavuzu)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Dizin Oluşturucular

Özellikler ile benzer şekilde, `get` erişimci bir değer döndüren tek bir ifadeden oluşuyorsa veya `set` erişimcisi basit bir atama gerçekleştirdiğinden, Dizin Oluşturucu `get` ve `set` erişimcileri ifade gövdesi tanımlarından oluşur.

Aşağıdaki örnek, bir dizi spor adını içeren bir iç <xref:System.String> dizisi içeren `Sports` adlı bir sınıfı tanımlar. Dizin Oluşturucu `get` ve `set` erişimcileri, ifade gövdesi tanımları olarak uygulanır.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Daha fazla bilgi için bkz. [DizinC# oluşturucular (Programlama Kılavuzu)](../indexers/index.md).

---
title: İfade gövdeli üyeler - C# Programlama Kılavuzu
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711993"
---
# <a name="expression-bodied-members-c-programming-guide"></a>İfade gövdeli üyeler (C# programlama kılavuzu)

İfade gövdesi tanımları, bir üyenin uygulamasını çok kısa ve okunabilir bir biçimde sağlamanıza izin sağlar. Bir yöntem veya özellik gibi desteklenen herhangi bir üyenin mantığı tek bir ifadeden oluştuğunda bir ifade gövdesi tanımı kullanabilirsiniz. Bir ifade gövdesi tanımı aşağıdaki genel sözdizimine sahiptir:

```csharp
member => expression;
```

*ifadenin* geçerli bir ifade olduğu yerde.

C# 6'daki yöntemler ve salt okunur özellikler için ifade gövdesi tanımları desteği tanıtıldı ve C# 7.0'da genişletildi. İfade gövdesi tanımları aşağıdaki tabloda listelenen tür üyeleri ile kullanılabilir:

|Üye  |Itibariyle desteklenen ... |
|---------|---------|
|[Yöntem](#methods)  |C# 6 |
|[Salt okunur özellik](#read-only-properties)   |C# 6  |
|[Özellik](#properties)  |C# 7.0 |
|[Oluşturucu](#constructors)   |C# 7.0 |
|[Sonlandırıcıyı](#finalizers)     |C# 7.0 |
|[Dizin Oluşturucu](#indexers)       |C# 7.0 |

## <a name="methods"></a>Yöntemler

İfade gövdeli yöntem, türü yöntemin dönüş türüyle eşleşen bir değer döndüren veya bazı `void`işlemleri gerçekleştiren dönen yöntemler için tek bir ifadeden oluşur. Örneğin, <xref:System.Object.ToString%2A> yöntemi geçersiz kılınan türler genellikle geçerli nesnenin dize temsilini döndüren tek bir ifade içerir.

Aşağıdaki örnek, `Person` <xref:System.Object.ToString%2A> bir ifade gövdesi tanımı ile yöntemi geçersiz kılan bir sınıf tanımlar. Ayrıca konsola `DisplayName` bir ad gösteren bir yöntem tanımlar. Anahtar kelimenin `return` ifade gövdesi tanımında `ToString` kullanılmadığını unutmayın.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Daha fazla bilgi için [Bkz. Yöntemler (C# Programlama Kılavuzu).](../classes-and-structs/methods.md)

## <a name="read-only-properties"></a>Salt okunur özellikler

C# 6 ile başlayarak, salt okunur özelliği uygulamak için ifade gövdesi tanımını kullanabilirsiniz. Bunu yapmak için aşağıdaki sözdizimini kullanın:

```csharp
PropertyType PropertyName => expression;
```

Aşağıdaki örnekte, `Location` salt `Name` okunur özelliği özel `locationName` alanın değerini döndüren bir ifade gövdesi tanımı olarak uygulanan bir sınıf tanımlanır:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Özellikler hakkında daha fazla bilgi için [Özellikler (C# Programlama Kılavuzu)](../classes-and-structs/properties.md)bakın.

## <a name="properties"></a>Özellikler

C# 7.0 ile başlayarak, özellik `get` ve `set` erişimciuygulamak için ifade gövdesi tanımlarını kullanabilirsiniz. Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Özellikler hakkında daha fazla bilgi için [Özellikler (C# Programlama Kılavuzu)](../classes-and-structs/properties.md)bakın.

## <a name="constructors"></a>Oluşturucular

Bir oluşturucu için bir ifade gövdesi tanımı genellikle tek bir atama ifadesi veya oluşturucunun bağımsız değişkenlerini işleyen veya örnek durumunu ilke açan bir yöntem çağrısından oluşur.

Aşağıdaki örnek, oluşturucu `Location` *adı*adlı tek bir dize parametresi olan bir sınıf tanımlar. İfade gövdesi tanımı bağımsız değişkeni `Name` özelliğe atar.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Daha fazla bilgi için [Constructors (C# Programlama Kılavuzu)](../classes-and-structs/constructors.md)bakın.

## <a name="finalizers"></a>Sonlandırıcılar

Sonlandırıcı için bir ifade gövdesi tanımı genellikle yönetilmeyen kaynakları serbest bırakmak ifadeler gibi temizleme deyimleri içerir.

Aşağıdaki örnek, sonlandırıcının çağrıldığını belirtmek için ifade gövdesi tanımını kullanan bir sonlandırıcı tanımlar.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Daha fazla bilgi için [Finalizers (C# Programlama Kılavuzu)](../classes-and-structs/destructors.md)bakın.

## <a name="indexers"></a>Dizin Oluşturucular

Özelliklerde olduğu gibi, `get` indeksleyici ve `set` erişimci, `get` erişimci bir değer döndüren tek `set` bir ifadeden oluşuyorsa veya erişimci basit bir atama gerçekleştiriyorsa ifade gövdesi tanımlarından oluşur.

Aşağıdaki örnek, bir dizi `Sports` sporun <xref:System.String> adlarını içeren dahili bir dizi içeren bir sınıf tanımlar. Hem `get` dizinleyici `set` hem de erişime girenler ifade gövdesi tanımları olarak uygulanır.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Daha fazla bilgi için [Bkz. Dizinleyiciler (C# Programlama Kılavuzu)](../indexers/index.md).

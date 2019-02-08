---
title: İfade gövdeli üyeler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7c282157639a6a60270ce8dbebbc91dd0e0a3f3
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826622"
---
# <a name="expression-bodied-members-c-programming-guide"></a>İfade gövdeli üyeler (C# programlama Kılavuzu)

İfade gövdesi tanımları çok kısa, okunabilir bir form uygulamasında bir üyenin sağlamanıza izin veren. Mantığı herhangi bir yöntemi veya özelliği gibi desteklenen bir üyesi için tek bir ifadeye oluşur. her bir deyim gövdesi tanımına kullanabilirsiniz. Bir ifade gövdesi tanımına genel sözdizimi aşağıdaki gibidir:

```csharp
member => expression;
```

Burada *ifade* geçerli bir ifadedir.

Yöntem ve salt okunur özellikler için ifade gövdesi tanımları için destek sunulmuştur C# 6 ve içinde genişletilmiş C# 7.0. İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri birlikte kullanılabilir:

|Üye  |Sürümünden desteklenen... |
|---------|---------|
|[Yöntemi](#methods)  |C# 6 |
|[Salt okunur özelliği](#read-only-properties)   |C# 6  |
|[Özelliği](#properties)  |C# 7.0 |
|[Oluşturucusu](#constructors)   |C# 7.0 |
|[Sonlandırıcı](#finalizers)     |C# 7.0 |
|[Dizin Oluşturucu](#indexers)       |C# 7.0 |

## <a name="methods"></a>Yöntemler

Bir ifade gövdeli yöntem türü yöntemin dönüş türü ile eşleşen bir değer döndüren tek bir ifade ya da, döndüren yöntemler oluşur `void`, olan bazı işlemi gerçekleştirir. Örneğin, bu geçersiz kılma türleri <xref:System.Object.ToString%2A> yöntemi genellikle geçerli nesnenin dize gösterimini döndürür, tek bir ifade içerir.

Aşağıdaki örnekte tanımlayan bir `Person` kılan sınıf <xref:System.Object.ToString%2A> yöntemi bir deyim gövdesi tanımına sahip. Ayrıca tanımlar bir `DisplayName` adını konsolda görüntüler yöntemi. Unutmayın `return` anahtar sözcüğü kullanılan değil `ToString` ifade gövdesi tanımı.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Daha fazla bilgi için [yöntemler (C# programlama Kılavuzu)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Salt okunur özellikler

İle başlayarak C# 6, salt okunur özelliği uygulamak için ifade gövdesi tanımına kullanabilirsiniz. Bunu yapmak için aşağıdaki sözdizimini kullanın:

```csharp
PropertyType PropertyName => expression;
```

Aşağıdaki örnekte tanımlayan bir `Location` sınıfının salt okunur `Name` özel değerini döndüren bir ifade gövdesi tanımını olarak gerçekleştirilen özellik `locationName` alan:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Özellikleri hakkında daha fazla bilgi için bkz. [özellikleri (C# Programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="properties"></a>Özellikler

İle başlayarak C# 7.0 özelliği uygulamak için ifade gövdesi tanımları kullanabilirsiniz `get` ve `set` erişimcileri. Aşağıdaki örnek bunu nasıl yapacağınız gösterilmiştir:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Özellikleri hakkında daha fazla bilgi için bkz. [özellikleri (C# Programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Oluşturucular

Bir oluşturucu için bir ifade gövdesi tanımına, genellikle tek bir atama ifadesi veya Oluşturucunun bağımsız değişkenleri işleme veya örnek durumu başlatan bir yöntem çağrısı oluşur.

Aşağıdaki örnekte tanımlayan bir `Location` sınıfı, Oluşturucusu olan tek bir dize parametresi adlı *adı*. Bağımsız değişkeni için ifade gövdesi tanımına atar `Name` özelliği.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Daha fazla bilgi için [oluşturucular (C# programlama Kılavuzu)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Sonlandırıcılar

Bir sonlandırıcı için ifade gövdesi tanımına, genellikle, yönetilmeyen kaynakları serbest deyimleri gibi temizleme ifadeleri içerir.

Aşağıdaki örnek, sonlandırıcı adı belirtmek için bir ifade gövdesi tanımı kullanan bir sonlandırıcı tanımlar.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Daha fazla bilgi için [sonlandırıcılar (C# programlama Kılavuzu)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Dizin Oluşturucular

Özellikleri gibi bir oluşturucunun get ve set erişimcileri değer döndüren tek bir deyimde get erişimcisinin oluşur veya set erişimcisi basit atama gerçekleştirir ifade gövdesi tanımlarını oluşur.

Aşağıdaki örnek adlı bir sınıf tanımlar `Sports` bir iç içeren <xref:System.String> Spor sayısını adlarını içeren bir dizi. İfade gövdesi tanımlarla hem oluşturucunun get ve set erişimcileri uygulanır.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Daha fazla bilgi için [dizin oluşturucular (C# programlama Kılavuzu)](../indexers/index.md).

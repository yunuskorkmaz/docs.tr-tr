---
title: İfade gövdeli üyeler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36f71352dca584c107af4f45850ce21bb016ba01
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238123"
---
# <a name="expression-bodied-members-c-programming-guide"></a>İfade gövdeli üyeler (C# programlama Kılavuzu)
İfade gövdesi tanımları çok kısa, okunabilir bir form uygulamasında bir üyenin sağlamanıza izin veren. Mantığı herhangi bir yöntemi veya özelliği gibi desteklenen bir üyesi için tek bir ifadeye oluşur. her bir deyim gövdesi tanımına kullanabilirsiniz. Bir ifade gövdesi tanımına genel sözdizimi aşağıdaki gibidir:

```csharp
member => expression;
```

Burada *ifade* geçerli bir ifadedir. 

Yöntemleri için ifade gövdesi tanımları için destek eklenmiştir ve özellik erişimcileri, C# 6'da Al ve C# 7.0 genişletildi. İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri birlikte kullanılabilir: 

|Üye  |Sürümünden desteklenen... |
|---------|---------|
|[Yöntemi](#methods)  |C# 6 |
|[Oluşturucusu](#constructors)   |C# 7.0 |
|[Sonlandırıcı](#finalizers)     |C# 7.0 |
|[Özellik Al](#property-get-statements)  |C# 6 |
|[Özellik kümesi](#property-set-statements)  |C# 7.0 |
|[Dizin Oluşturucu](#indexers)       |C# 7.0 |

## <a name="methods"></a>Yöntemler

Bir ifade gövdeli yöntem türü yöntemin dönüş türü ile eşleşen bir değer döndüren tek bir ifade ya da, döndüren yöntemler oluşur `void`, olan bazı işlemi gerçekleştirir. Örneğin, bu geçersiz kılma türleri <xref:System.Object.ToString%2A> yöntemi genellikle geçerli nesnenin dize gösterimini döndürür, tek bir ifade içerir. 

Aşağıdaki örnekte tanımlayan bir `Person` kılan sınıf <xref:System.Object.ToString%2A> yöntemi bir deyim gövdesi tanımına sahip. Ayrıca tanımlar bir `DisplayName` adını konsolda görüntüler yöntemi. Unutmayın `return` anahtar sözcüğü kullanılan değil `ToString` ifade gövdesi tanımı.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Daha fazla bilgi için [yöntemler (C# programlama Kılavuzu)](../classes-and-structs/methods.md).
 
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

## <a name="property-get-statements"></a>Özellik get deyimleri

Uygulamak seçerseniz bir alma erişimcisi kendiniz, özellik değeri yalnızca döndüren tek ifadeler için bir ifade gövdesi tanımına kullanabilirsiniz. Unutmayın `return` deyimi kullanılmaz.

Aşağıdaki örnekte tanımlayan bir `Location.Name` özelliği olan özellik get erişimcisi özel değerini döndürür `locationName` özelliği yedekleyen alan. 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Bir ifade gövdesi tanımına kullanan salt okunur özellikler uygulanabilir açık bir `set` deyimi. Sözdizimi şöyledir:

```csharp
PropertyName => returnValue;
```

Aşağıdaki örnekte tanımlayan bir `Location` sınıfının salt okunur `Name` özel değerini döndüren bir ifade gövdesi tanımını olarak gerçekleştirilen özellik `locationName` alan.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Daha fazla bilgi için [özellikler (C# programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="property-set-statements"></a>Özellik kümesi ifadeleri

Bir özellik kümesi erişimcisi kendi başınıza uygulamak isterseniz, özelliği yedekleyen alana değer atayan bir tek satır ifadesi için bir ifade gövdesi tanımına kullanabilirsiniz.

Aşağıdaki örnekte tanımlayan bir `Location.Name` özelliği, özelliği ayarlanmış deyimi, giriş bağımsız değişkeni özel atar `locationName` özelliği yedekleyen alan.

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Daha fazla bilgi için [özellikler (C# programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="indexers"></a>Dizin Oluşturucular

Özellikleri gibi bir oluşturucunun get ve set erişimcileri değer döndüren tek bir deyimde get erişimcisinin oluşur veya set erişimcisi basit atama gerçekleştirir ifade gövdesi tanımlarını oluşur.

Aşağıdaki örnek adlı bir sınıf tanımlar `Sports` bir iç içeren <xref:System.String> Spor sayısını adlarını içeren bir dizi. İfade gövdesi tanımlarla hem oluşturucunun get ve set erişimcileri uygulanır.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

Daha fazla bilgi için [dizin oluşturucular (C# programlama Kılavuzu)](../indexers/index.md).


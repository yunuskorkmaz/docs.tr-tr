---
title: İfade bodied üyeleri (C# programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5690a2ddb9127bb0c9b06d3607e3d105fca9a2e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="expression-bodied-members-c-programming-guide"></a>İfade bodied üyeleri (C# programlama Kılavuzu)
İfade gövdesi tanımları çok kısa, okunabilir bir form bir üyenin uygulamasında sağlamanıza olanak tanır. Tek bir ifade yöntemi veya özelliği gibi herhangi bir desteklenen üyesi mantığını oluşur her bir ifade gövdesi tanımı kullanabilirsiniz. Bir ifade gövdesi tanımı genel sözdizimi aşağıdaki gibidir:

```csharp
member => expression;
```

Burada *ifade* geçerli bir ifade değil. 

İfade gövdesi tanımları için destek yöntemleri için sunulmuştur ve özellik get Erişimciler C# 6've C# 7. 0'genişletildi. İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri ile birlikte kullanılabilir: 

|Üye  |Sürümünden itibaren desteklenen... |
|---------|---------|
|[Yöntemi](#methods)  |C# 6 |
|[Oluşturucusu](#constructors)   |C# 7.0 |
|[Sonlandırıcı](#finalizers)     |C# 7.0 |
|[Özellik Get](#property-get-statements)  |C# 6 |
|[Özellik kümesi](#property-set-statements)  |C# 7.0 |
|[Dizin Oluşturucu](#indexers)       |C# 7.0 |

## <a name="methods"></a>Yöntemler

Tek bir ifade türü yöntemin dönüş türü ile eşleşen bir değeri döndürür veya, döndüren yöntemler için bir ifade bodied yöntemi oluşur `void`, bazı işlemi gerçekleştirir. Örneğin, bu geçersiz kılma türleri <xref:System.Object.ToString%2A> yöntemi genellikle geçerli nesnenin dize gösterimini döndürür tek bir ifade içerir. 

Aşağıdaki örnek tanımlayan bir `Person` geçersiz kılmaları sınıf <xref:System.Object.ToString%2A> bir ifade gövdesi tanımıyla yöntemi. Ayrıca tanımlayan bir `Show` bir ad konsola görüntüler yöntemi. Unutmayın `return` anahtar sözcüğü kullanılan değil `ToString` ifade gövdesi tanımı.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Daha fazla bilgi için bkz: [yöntemler (C# programlama Kılavuzu)](../classes-and-structs/methods.md).
 
## <a name="constructors"></a>Oluşturucular

Bir oluşturucu için bir ifade gövdesi tanımı genellikle tek bir atama ifadesi veya Oluşturucusu'nın bağımsız değişkenleri işleme veya örnek durum başlatır yöntem çağrısı oluşur. 

Aşağıdaki örnek tanımlayan bir `Location` sınıfı, bir oluşturucuya sahip tek bir dize adlı parametre *adı*. Bağımsız değişkeni ifadesi gövde tanımı atar `Name` özelliği.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Daha fazla bilgi için bkz: [oluşturucular (C# programlama Kılavuzu)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Sonlandırıcılar

Bir sonlandırıcı için bir ifade gövdesi tanımı genellikle, yönetilmeyen kaynakları serbest deyimleri gibi temizleme ifadeleri içerir.

Aşağıdaki örnek, sonlandırıcıyı çağrıldı belirtmek için bir ifade gövdesi tanımını kullanan bir sonlandırıcı tanımlar.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Daha fazla bilgi için bkz: [sonlandırıcılar (C# programlama Kılavuzu)](../classes-and-structs/destructors.md).

## <a name="property-get-statements"></a>Özellik get deyimleri

Uygulamak isterseniz bir özellik get erişimcisi kendiniz, bir ifade gövdesi tanımı yalnızca özellik değeri döndüren tek ifadeler için kullanabilirsiniz. Unutmayın `return` değil deyimi kullanılır.

Aşağıdaki örnek tanımlayan bir `Location.Name` özelliği, özellik get erişimcisi özel değerini döndürür `locationName` özelliği yedekler alan. 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Bir ifade gövdesi tanımı kullanmak salt okunur özellikler uygulanabilir açık bir `set` deyimi. Sözdizimi şöyledir:

```csharp
PropertyName => returnValue;
```

Aşağıdaki örnek tanımlayan bir `Location` sınıfının salt okunur `Name` özelliği özel değerini döndüren bir ifade gövdesi tanımı olarak uygulanan `locationName` alan.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Daha fazla bilgi için bkz: [özellikler (C# programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="property-set-statements"></a>Özellik set deyimleri

Bir özellik set erişimcisi kendiniz uygulamak isterseniz özelliği yedekler alan için değer atayan bir tek satırlı deyim için bir ifade gövdesi tanımı kullanabilirsiniz.

Aşağıdaki örnek tanımlayan bir `Location.Name` özelliği, özelliği ayarlanmış deyimi özel kendi giriş bağımsız değişkenine atar `locationName` özelliği yedekler alan.

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Daha fazla bilgi için bkz: [özellikler (C# programlama Kılavuzu)](../classes-and-structs/properties.md).

## <a name="indexers"></a>Dizin Oluşturucular

Özellikler gibi bir oluşturucunun get ve set erişimcileri get erişimcisine bir değer döndüren bir tek deyiminden oluşan ya da basit atama set erişimcisine gerçekleştirir ifade gövdesi tanımlarını oluşur.

Aşağıdaki örnek adlı bir sınıf tanımlar `Sports` iç içeren <xref:System.String> Spor sayısı adlarını içeren bir dizi. Oluşturucunun get ve set erişimcileri ifade gövdesi tanımları uygulanır.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

Daha fazla bilgi için bkz: [dizin oluşturucular (C# programlama Kılavuzu)](../indexers/index.md).


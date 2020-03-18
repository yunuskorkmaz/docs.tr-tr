---
title: Constructors - C# Programlama Kılavuzu
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8eedfaed111f01cc2ec55a2f42df66d4588bd42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399793"
---
# <a name="constructors-c-programming-guide"></a>Oluşturucular (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md) veya [yapı](../../language-reference/builtin-types/struct.md) oluşturulduğunda, oluşturucusu çağrılır. Bir sınıf veya yapı, farklı bağımsız değişkenler alan birden çok oluşturucuya sahip olabilir. Oluşturucular, programcının varsayılan değerleri ayarlamasını, anlık değeri sınırlamasını ve esnek ve okunması kolay kod yazmasını sağlar. Daha fazla bilgi ve örnekler için, Yapı [oluşturucuları](./using-constructors.md) ve Örnek [Oluşturucuları](./instance-constructors.md)Kullanma'ya bakın.  

## <a name="parameterless-constructors"></a>Parametresiz yapıcılar
  
Sınıfınız için bir oluşturucu sağlamazsanız, C# varsayılan olarak nesneyi anında belirleyen ve üye değişkenleri [C# türlerinin varsayılan değerlerinde](../../language-reference/builtin-types/default-values.md) listelenen varsayılan değerlere ayarlayan bir tane oluşturur. Yapınız için bir oluşturucu sağlamazsanız, C# her alanı varsayılan değerine otomatik olarak başlatması için *örtük bir parametresiz oluşturucuya* güvenir. Daha fazla bilgi ve örnekler için [Bkz. Örnek oluşturucular.](instance-constructors.md)  

## <a name="constructor-syntax"></a>Yapıcı sözdizimi

Oluşturucu, adı türünün adıile aynı olan bir yöntemdir. Yöntem imzası yalnızca yöntem adını ve parametre listesini içerir; bir iade türü içermez. Aşağıdaki örnek, adlı bir sınıfın `Person`oluşturucusu gösterir.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Bir oluşturucu tek bir deyim olarak uygulanabilirse, bir [ifade gövdesi tanımı](../statements-expressions-operators/expression-bodied-members.md)kullanabilirsiniz. Aşağıdaki örnek, oluşturucu `Location` *adı*adlı tek bir dize parametresi olan bir sınıf tanımlar. İfade gövdesi tanımı bağımsız değişkeni `locationName` alana atar.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Statik yapıcılar

Önceki örneklerin tümü, yeni bir nesne oluşturan örnek oluşturucuları göstermiştir. Bir sınıf veya yapı, türün statik üyelerini baş harfe çeken statik bir oluşturucuya da sahip olabilir.  Statik yapıcılar parametresizdir. Statik alanları başlatmak için statik bir oluşturucu sağlamazsanız, C# derleyicisi statik alanları [C# türleri makalesinin Varsayılan değerlerinde](../../language-reference/builtin-types/default-values.md) listelenen varsayılan değerlerine amerler.

Aşağıdaki örnek, statik bir alanı başlatmak için statik bir oluşturucu kullanır.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Aşağıdaki örnekte görüldüğü gibi, ifade gövdesi tanımına sahip statik bir oluşturucu da tanımlayabilirsiniz.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Daha fazla bilgi ve örnekler için [Statik Oluşturucular'a](./static-constructors.md)bakın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Oluşturucuları Kullanma](./using-constructors.md)  
  
 [Örnek Oluşturucuları](./instance-constructors.md)  
  
 [Özel Oluşturucular](./private-constructors.md)  
  
 [Statik Oluşturucular](./static-constructors.md)  
  
 [Kopya oluşturucu nasıl yazılır?](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Sonlandırıcılar](./destructors.md)
- [Statik](../../language-reference/keywords/static.md)
- [Neden Başharfler yapıcılar olarak Ters Sırada Çalışır? Birinci Bölüm](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)

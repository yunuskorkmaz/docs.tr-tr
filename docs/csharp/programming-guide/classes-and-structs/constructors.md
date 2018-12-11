---
title: Oluşturucular - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 79b000952ed03e5dc28d1c33bd2cba14708fb26a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235338"
---
# <a name="constructors-c-programming-guide"></a>Oluşturucular (C# Programlama Kılavuzu)
Her bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md) olan oluşturulan, kendi Oluşturucu çağrılır. Farklı bağımsız değişkenler almayan birden çok Oluşturucu, bir sınıf veya yapı olabilir. Oluşturucular, esnek ve kolay okunur kod yazma, örnekleme sınırlandırmak ve varsayılan değerlerini ayarlamak Programcı etkinleştirin. Daha fazla bilgi ve örnekler için bkz. [oluşturucuları kullanarak](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) ve [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="default-constructors"></a>Varsayılan Oluşturucu
  
Sınıfınız için bir oluşturucu sağlamazsanız, C# nesnesini başlatır ve üye değişkenleri için varsayılan değerleri, bağlantısında listelendiği gibi ayarlar. varsayılan olarak bir tane oluşturur [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). Yapınızı için bir oluşturucu sağlamazsanız, C# dayanan bir *örtülü varsayılan bir oluşturucuya* listelenen her alanda bir değer türü varsayılan değerine otomatik olarak başlatmak için [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). Daha fazla bilgi ve örnekler için bkz. [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="constructor-syntax"></a>Oluşturucu sözdizimi

Bir oluşturucu kendi türünün adı ile aynı adı olan bir yöntemdir. Yöntem imzası yöntem adı ve kendi parametre listesi ' dönüş türü içermez. Aşağıdaki örnekte adlı bir sınıf için oluşturucu `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Tek bir deyimde bir oluşturucu uygulanabilir, kullanabileceğiniz bir [ifade gövdesi tanımına](../statements-expressions-operators/expression-bodied-members.md). Aşağıdaki örnekte tanımlayan bir `Location` sınıfı, Oluşturucusu olan tek bir dize parametresi adlı *adı*. Bağımsız değişkeni için ifade gövdesi tanımına atar `locationName` alan.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Statik oluşturucular

Önceki örneklerde, yeni nesne oluşturma tüm gösterilen örnek oluşturucuları vardır. Bir sınıf veya yapı, türün statik üyeleri başlatan bir statik Oluşturucu da olabilir.  Statik oluşturucular parametresiz. Statik alanları başlatmak için bir statik Oluşturucu sağlamazsanız, C# derleyicisi bağlantısında listelendiği gibi statik alanları varsayılan değerlerine başlatır varsayılan statik Oluşturucu sağlayacak [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). 

Aşağıdaki örnek, statik bir alanı başlatmak için bir statik Oluşturucu kullanır.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Aşağıdaki örnekte gösterildiği gibi bir statik Oluşturucu bir ifade gövdesi tanımıyla de tanımlayabilirsiniz. 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Daha fazla bilgi ve örnekler için bkz. [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Oluşturucuları Kullanma](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [Örnek Oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [Özel Oluşturucular](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [Statik Oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [Nasıl yapılır: Kopya Oluşturucu yazma](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [static](../../../csharp/language-reference/keywords/static.md)  
- [Başlatıcılar neden olarak oluşturucular ters sırada çalıştırılır? Bölüm bir](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)

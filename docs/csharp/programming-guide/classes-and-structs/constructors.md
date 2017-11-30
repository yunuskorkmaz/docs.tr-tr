---
title: "Oluşturucular (C# Programlama Kılavuzu)"
ms.date: 05/05/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 65c50311548667ab5fdc685b70b6ab9e88376067
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="constructors-c-programming-guide"></a>Oluşturucular (C# Programlama Kılavuzu)
Her bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md) olan oluşturulan kurucusu çağrılır. Sınıfta veya yapı farklı bağımsız değişkenler almayan birden çok oluşturucular olabilir. Oluşturucular örneklemesi sınırlamak ve esnek ve kolay okumak kod yazma varsayılan değerlerini ayarlamak Programcı etkinleştirin. Daha fazla bilgi ve örnekler için bkz: [kullanarak oluşturucular](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) ve [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="default-constructors"></a>Varsayılan Oluşturucu
  
Sınıfı için bir oluşturucu sağlamazsanız, C# bir nesne oluşturur ve üye değişkenleri için varsayılan değerleri içinde listelenen ayarlar varsayılan olarak oluşturur [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). Yapı için bir oluşturucu sağlamazsanız, C# dayanan bir *örtük varsayılan oluşturucu* içinde listelenen her bir alan bir değer türü için varsayılan değer otomatik olarak başlatmak için [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). Daha fazla bilgi ve örnekler için bkz: [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="constructor-syntax"></a>Oluşturucu sözdizimi

Bir oluşturucu kendi türünün adı ile aynı adı olan bir yöntemdir. Yöntem imzası yalnızca yöntemi adı ve parametre listesi içerir; dönüş türü içermez. Aşağıdaki örnek adlı bir sınıf oluşturucusu gösterir `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Bir oluşturucu tek bir deyimde uygulanabilir, kullanabileceğiniz bir [ifade gövdesi tanımı](../statements-expressions-operators/expression-bodied-members.md). Aşağıdaki örnek tanımlayan bir `Location` sınıfı, bir oluşturucuya sahip tek bir dize adlı parametre *adı*. Bağımsız değişkeni ifadesi gövde tanımı atar `locationName` alan.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Statik oluşturucular

Önceki örneklerde, yeni nesne oluşturma tüm gösterilen örnek oluşturucuları vardır. Ayrıca bir sınıf veya yapı türün statik üyeleri başlatır statik Oluşturucu olabilir.  Statik oluşturucular parametresiz. Statik alanları başlatmak için statik bir oluşturucu sağlamazsanız, C# Derleyici içinde listelenen statik alanları varsayılan değerlerine başlatır varsayılan statik Oluşturucu sağlayacak [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). 

Aşağıdaki örnek, statik bir alanı başlatmak için bir statik oluşturucusunu kullanır.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Ayrıca aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı statik bir oluşturucu tanımlayabilirsiniz. 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Daha fazla bilgi ve örnekler için bkz: [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Oluşturucular Kullanma](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [Örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [Özel oluşturucular](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [Statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [Nasıl yapılır: kopya Oluşturucu yazma](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [statik](../../../csharp/language-reference/keywords/static.md)  
 [Başlatıcılar neden oluşturucular ters sırada çalışır? Bölüm bir](http://go.microsoft.com/fwlink/?LinkId=112374)

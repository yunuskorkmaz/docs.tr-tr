---
title: Oluşturucular- C# Programlama Kılavuzu
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 9c57ff6dd9acd8a8bcff6de4fce7d898f1135703
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714963"
---
# <a name="constructors-c-programming-guide"></a>Oluşturucular (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/keywords/struct.md) oluşturulduğunda, Oluşturucusu çağırılır. Bir sınıf veya yapının farklı bağımsız değişkenler alan birden çok Oluşturucusu olabilir. Oluşturucular, programcının varsayılan değerleri ayarlama, örnek oluşturmayı sınırlandırma ve esnek ve okunması kolay bir kod yazma olanağı sağlar. Daha fazla bilgi ve örnek için bkz. oluşturucular ve [örnek oluşturucular](./instance-constructors.md) [kullanma](./using-constructors.md) .  

## <a name="parameterless-constructors"></a>Parametresiz oluşturucular
  
Sınıfınız için bir Oluşturucu sağlamazsanız, C# nesneyi örnekleyen ve varsayılan [değerler tablosunda](../../language-reference/keywords/default-values-table.md)listelenen üye değişkenlerini varsayılan değerlere ayarlayan varsayılan olarak bir tane oluşturur. Struct için bir Oluşturucu sağlamazsanız, C# [varsayılan değerler tablosunda](../../language-reference/keywords/default-values-table.md)listelenen bir değer türünün her alanını varsayılan değerine otomatik olarak başlatmak için *örtük parametresiz bir oluşturucuya* bağımlıdır. Daha fazla bilgi ve örnek için bkz. [örnek oluşturucular](./instance-constructors.md).  

## <a name="constructor-syntax"></a>Oluşturucu sözdizimi

Oluşturucu, adı türünün adı ile aynı olan bir yöntemdir. Yöntemi imzasında yalnızca Yöntem adı ve parametre listesi bulunur; dönüş türü içermez. Aşağıdaki örnek, `Person`adlı bir sınıf için oluşturucuyu gösterir.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Bir Oluşturucu tek bir deyim olarak uygulan, bir [ifade gövdesi tanımı](../statements-expressions-operators/expression-bodied-members.md)kullanabilirsiniz. Aşağıdaki örnek, oluşturucusunun *adı*adlı tek bir dize parametresine sahip bir `Location` sınıfını tanımlar. İfade gövdesi tanımı, `locationName` alanına bağımsız değişkenini atar.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Statik oluşturucular

Önceki örneklerde, yeni bir nesne oluşturan tüm gösterilen örnek oluşturucuları vardır. Bir sınıf veya yapı, türün statik üyelerini Başlatan statik bir oluşturucuya de sahip olabilir.  Statik oluşturucular parametresiz. Statik alanları başlatmak için statik bir Oluşturucu sağlamazsanız, C# derleyici [varsayılan değerler tablosunda](../../language-reference/keywords/default-values-table.md)listelenen statik alanları varsayılan değerlerine başlatır.

Aşağıdaki örnek, statik bir alanı başlatmak için statik bir Oluşturucu kullanır.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Aşağıdaki örnekte gösterildiği gibi, bir ifade gövdesi tanımıyla bir statik oluşturucu da tanımlayabilirsiniz. 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Daha fazla bilgi ve örnek için bkz. [statik oluşturucular](./static-constructors.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Oluşturucuları Kullanma](./using-constructors.md)  
  
 [Örnek Oluşturucuları](./instance-constructors.md)  
  
 [Özel Oluşturucular](./private-constructors.md)  
  
 [Statik Oluşturucular](./static-constructors.md)  
  
 [Kopya Oluşturucu yazma](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Sonlandırıcılar](./destructors.md)
- [static](../../language-reference/keywords/static.md)
- [Başlatıcılar neden oluşturucular olarak ters sırada çalışıyor? Birinci bölüm](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)

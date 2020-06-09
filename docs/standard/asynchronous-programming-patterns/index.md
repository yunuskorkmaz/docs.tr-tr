---
title: Asenkron programlama desenleri
description: Görev tabanlı zaman uyumsuz model (TAP), olay tabanlı zaman uyumsuz model (EAP), .NET 'te & zaman uyumsuz programlama modeli (APM) hakkında bilgi edinin.
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: bd4d44d8de8a64be82e9ce6af593a86719b59fcf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583511"
---
# <a name="asynchronous-programming-patterns"></a>Asenkron programlama desenleri

.NET, zaman uyumsuz işlemleri gerçekleştirmek için üç model sağlar:  

- Zaman uyumsuz bir işlemin başlatılması ve tamamlanmasını temsil etmek için tek bir yöntem kullanan **görev tabanlı zaman uyumsuz model (TAP)**. .NET Framework 4 ' te dokunma eklendi. **.NET ' te zaman uyumsuz programlama için önerilen yaklaşımdır.** C# ' deki [Async](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/operators/await.md) anahtar sözcükleri ve Visual Basic ' deki [Async](../../visual-basic/language-reference/modifiers/async.md) ve [await](../../visual-basic/language-reference/operators/await-operator.md) işleçleri, TAP için dil desteği Ekle ' ye tıklayın. Daha fazla bilgi için bkz. [görev tabanlı zaman uyumsuz model (TAP)](task-based-asynchronous-pattern-tap.md).  

- Zaman uyumsuz davranış sağlamaya yönelik olay tabanlı eski model olan **olay tabanlı zaman uyumsuz model (EAP)**. `Async`Son ek ve bir veya daha fazla olay, olay işleyicisi temsilci türleri ve-türetilmiş türler içeren bir yöntem gerektirir `EventArg` . EAP .NET Framework 2,0 ' de tanıtılmıştı. Artık yeni geliştirme için önerilmez. Daha fazla bilgi için bkz. [olay tabanlı zaman uyumsuz model (EAP)](event-based-asynchronous-pattern-eap.md).  

- Zaman uyumsuz davranış sağlamak için arabirimi kullanan eski model olan **zaman uyumsuz programlama modeli (APM)** modeli (Ayrıca, model olarak da bilinir <xref:System.IAsyncResult> ) <xref:System.IAsyncResult> . Bu düzende, zaman uyumlu işlemler `Begin` ve `End` yöntemleri gerektirir (örneğin, `BeginWrite` ve `EndWrite` bir zaman uyumsuz yazma işlemi uygulamak için). Bu model artık yeni geliştirme için önerilmez. Daha fazla bilgi için bkz. [zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md).  
  
## <a name="comparison-of-patterns"></a>Desenlerin karşılaştırması

Üç desenin zaman uyumsuz işlemlerin nasıl modellendiği hakkında hızlı bir karşılaştırma için, `Read` belirtilen bir uzaklığa göre belirtilen bir veri miktarını belirtilen bir arabellekte okuyan bir yöntemi göz önünde bulundurun:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

Bu yöntemin karşılık gelen DOKUNMASı, aşağıdaki tek yöntemi kullanıma sunar `ReadAsync` :  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

EAP karşılığı aşağıdaki tür ve üye kümesini kullanıma sunar:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
APM karşılığı, `BeginRead` ve yöntemlerini kullanıma sunar `EndRead` :  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz, derinlemesine](../async-in-depth.md)
- [C 'de zaman uyumsuz programlama #](../../csharp/async.md)
- [F 'de zaman uyumsuz programlama #](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)

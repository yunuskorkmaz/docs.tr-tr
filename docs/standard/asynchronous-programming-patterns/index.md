---
title: Zaman uyumsuz programlama desenleri
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50d76aef201fead37923a65cfeead16638b09842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031180"
---
# <a name="asynchronous-programming-patterns"></a>Zaman uyumsuz programlama desenleri

.NET, zaman uyumsuz işlemleri gerçekleştirmek için üç desen sağlar:  

- **Görev tabanlı zaman uyumsuz desen (TAP)**, başlangıcını ve tamamlanmasını zaman uyumsuz bir işlemin temsil etmek için tek bir yöntem kullanır. DOKUNUN, .NET Framework 4'te tanıtıldı. **. NET'te zaman uyumsuz programlama için önerilen yaklaşımdır.** [Zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) anahtar sözcükleri C# ve [zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) Visual Basic'de işleçler DOKUNUN için dil desteği ekleyin. Daha fazla bilgi için [görev tabanlı zaman uyumsuz desen (TAP)](task-based-asynchronous-pattern-tap.md).  

- **Olay tabanlı zaman uyumsuz desen (EAP)**, zaman uyumsuz davranış sağlamak için olay-tabanlı eski model olduğu. Bir yöntemin gerektirir `Async` soneki ve bir veya daha fazla olaylar, olay işleyicisi temsilci türleri ve `EventArg`-türetilmiş türler. EAP .NET Framework 2.0 sürümünde kullanıma sunulmuştur. Artık yeni geliştirme projeleri için tavsiye edilir. Daha fazla bilgi için [olay tabanlı zaman uyumsuz desen (EAP)](event-based-asynchronous-pattern-eap.md).  

- **Zaman uyumsuz programlama modeli (APM)** desen (olarak da adlandırılan <xref:System.IAsyncResult> deseni), kullanan eski model olduğu <xref:System.IAsyncResult> zaman uyumsuz davranışı sağlamak için arabirim. Bu düzende, zaman uyumlu işlemler gerektiren `Begin` ve `End` yöntemleri (örneğin, `BeginWrite` ve `EndWrite` bir zaman uyumsuz yazma işlemini uygulamak için). Bu düzen, artık yeni geliştirme projeleri için tavsiye edilir. Daha fazla bilgi için [zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md).  
  
## <a name="comparison-of-patterns"></a>Desenler karşılaştırması

Nasıl üç model zaman uyumsuz işlemler desenleri hızlı karşılaştırma için göz önünde bir `Read` belirtilen uzaklıkta başlayan sağlanan arabellek içine belirtilen miktarda veri okuyan yöntemi:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

Bu yöntemin DOKUNUN karşılığı aşağıdaki tek kullanılabilmesini `ReadAsync` yöntemi:  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

EAP karşılığı türleri ve üyeleri aşağıdaki kümesini kullanıma:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
APM karşılığı kullanılabilmesini `BeginRead` ve `EndRead` yöntemleri:  
  
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

- [Zaman uyumsuz derinlemesine](../async-in-depth.md)
- [C# zaman uyumsuz programlama](~/docs/csharp/async.md)
- [Zaman uyumsuz programlamaF#](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)

---
title: Asenkron programlama desenleri
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: e1efe9c3eb57f317def91e527506c358eb086679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160059"
---
# <a name="asynchronous-programming-patterns"></a>Asenkron programlama desenleri

.NET, eşzamanlı işlemler gerçekleştirmek için üç desen sağlar:  

- **Görev tabanlı Eşenkron Desen (TAP),** bir eşzamanlı işlemin başlatılmasını ve tamamlanmasını temsil etmek için tek bir yöntem kullanır. TAP ,.NET Framework 4'te tanıtıldı. **.NET'te eşzamanlı programlamaiçin önerilen yaklaşımdır.** C# [ve](../../csharp/language-reference/keywords/async.md) Visual Basic'teki [Async](../../visual-basic/language-reference/modifiers/async.md) ve [Await](../../visual-basic/language-reference/operators/await-operator.md) işleçleri, [await](../../csharp/language-reference/operators/await.md) TAP için dil desteği ekler. Daha fazla bilgi için [Görev Tabanlı Eşzamanlı Desen (TAP)](task-based-asynchronous-pattern-tap.md)'ye bakın.  

- **Olay tabanlı Asynchronous Pattern (EAP)**, asynchronous davranış sağlamak için olay tabanlı eski modeldir. `Async` Soneki ve bir veya daha fazla olay, olay işleyicisi `EventArg`temsilci türleri ve -türetilmiş türleri olan bir yöntem gerektirir. EAP .NET Framework 2.0'da tanıtıldı. Artık yeni bir gelişme için tavsiye edilmez. Daha fazla bilgi için olay [tabanlı Eşzamanlı Desen (EAP)](event-based-asynchronous-pattern-eap.md)bakın.  

- **Asynchronous Programming Model (APM)** <xref:System.IAsyncResult> deseni (desen olarak da adlandırılır), asynchronous davranış sağlamak için <xref:System.IAsyncResult> arabirimi kullanan eski modeldir. Bu desende, senkron `Begin` işlemler `End` gerektirir ve `BeginWrite` yöntemleri `EndWrite` (örneğin, ve bir eşzamanlı yazma işlemi uygulamak için). Bu desen artık yeni geliştirme için önerilmez. Daha fazla bilgi için, [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)bakın.  
  
## <a name="comparison-of-patterns"></a>Desenlerin karşılaştırılması

Üç modelin eşzamanlı işlemleri nasıl modellediğinin hızlı `Read` bir karşılaştırması için, belirli bir ofsetten başlayarak sağlanan bir arabellekte belirli miktarda veriyi okuyan bir yöntemi düşünün:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

Bu yöntemin TAP karşılığı aşağıdaki `ReadAsync` tek yöntemi ortaya çıkarır:  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

EAP muadili aşağıdaki tür ve üye kümesini ortaya çıkar:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
APM muadili `BeginRead` ve `EndRead` yöntemleri ortaya çıkaracak:  
  
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

- [Derinlemesine Async](../async-in-depth.md)
- [C'de asynchronous programlama #](../../csharp/async.md)
- [F'de Async Programlama #](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Async ve Await ile Asynchronous Programlama (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)

---
title: Zaman Uyumsuz Programlama Desenleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e399a512d2bee636aec35e008c0632ce9c5fa781
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068410"
---
# <a name="asynchronous-programming-patterns"></a>Zaman Uyumsuz Programlama Desenleri

.NET Framework zaman uyumsuz işlemleri gerçekleştirmek için üç desen sağlar:  
  
- **Zaman uyumsuz programlama modeli (APM)** desen (olarak da adlandırılan <xref:System.IAsyncResult> deseni), burada zaman uyumsuz işlemleri gerektirir `Begin` ve `End` yöntemleri (örneğin, `BeginWrite` ve `EndWrite` için zaman uyumsuz işlemleri yazın). Bu düzen, artık yeni geliştirme projeleri için tavsiye edilir. Daha fazla bilgi için [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
- **Olay tabanlı zaman uyumsuz desen (EAP)**, bir yöntemin gerektiren `Async` sonek ve ayrıca bir veya daha fazla olay, olay işleyicisi temsilci türleri gerektirir ve `EventArg`-türetilmiş türler. EAP .NET Framework 2.0 sürümünde kullanıma sunulmuştur. Artık yeni geliştirme projeleri için tavsiye edilir. Daha fazla bilgi için [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
- **Görev tabanlı zaman uyumsuz desen (TAP)**, başlangıcını ve tamamlanmasını zaman uyumsuz bir işlemin temsil etmek için tek bir yöntem kullanır. DOKUNUN .NET Framework 4'te kullanıma sunulmuştur ve zaman uyumsuz için önerilen yaklaşım, .NET Framework programlama. [Zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) C# anahtar sözcükleri ve [zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) Visual Basic dili işleçleri DOKUNUN için dil desteği ekleyin. Daha fazla bilgi için [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
## <a name="comparing-patterns"></a>Desenleri karşılaştırma  

Nasıl üç model zaman uyumsuz işlemler desenleri hızlı karşılaştırma için göz önünde bir `Read` belirtilen uzaklıkta başlayan sağlanan arabellek içine belirtilen miktarda veri okuyan yöntemi:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
Bu yöntemin APM karşılığı kullanılabilmesini `BeginRead` ve `EndRead` yöntemleri:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
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
  
DOKUNUN karşılığı aşağıdaki tek kullanılabilmesini `ReadAsync` yöntemi:  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
Sonraki bölümde verilen bağlantıları DOKUNUN, APM ve EAP kapsamlı bir tartışma için bkz.  
  
## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| ----- | ----------- |
| [Zaman Uyumsuz Programlama Modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | Kullanan eski model açıklar <xref:System.IAsyncResult> zaman uyumsuz davranışı sağlamak için arabirim. Bu model, artık yeni geliştirme projeleri için tavsiye edilir. |
| [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | Zaman uyumsuz davranış sağlamak için olay-tabanlı eski modelini açıklar. Bu model, artık yeni geliştirme projeleri için tavsiye edilir. |
| [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | Temel yeni zaman uyumsuz deseni açıklar <xref:System.Threading.Tasks> ad alanı. Bu model, .NET Framework 4 ve sonraki sürümlerde zaman uyumsuz programlama için önerilen yaklaşımdır. |

## <a name="see-also"></a>Ayrıca bkz.

- [C# zaman uyumsuz programlama](~/docs/csharp/async.md)   
- [F # zaman uyumsuz programlama](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)

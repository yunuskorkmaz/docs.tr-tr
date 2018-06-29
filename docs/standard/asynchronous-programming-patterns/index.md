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
ms.openlocfilehash: 809385bda48c6fb8dae125fe348228aaee375a6c
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071311"
---
# <a name="asynchronous-programming-patterns"></a>Zaman Uyumsuz Programlama Desenleri

.NET Framework zaman uyumsuz işlemleri gerçekleştirmek için üç desenleri sağlar:  
  
- **Zaman uyumsuz programlama modeli (APM)** deseni (olarak da bilinir <xref:System.IAsyncResult> desen), burada zaman uyumsuz işlemleri gerektirir `Begin` ve `End` yöntemleri (örneğin, `BeginWrite` ve `EndWrite` için zaman uyumsuz işlemleri yazma). Bu desen artık yeni geliştirme projeleri için önerilir. Daha fazla bilgi için bkz: [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
- **Olay tabanlı zaman uyumsuz desen (EAP)**, içeren bir yöntem gerektirir `Async` sonek ve de gerektiren bir veya daha fazla olaylar, olay işleyici temsilci türleri ve `EventArg`-türetilmiş tür. EAP, .NET Framework 2. 0 ' sunulmuştur. Artık yeni geliştirme projeleri için önerilir. Daha fazla bilgi için bkz: [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
- **Görev tabanlı zaman uyumsuz desen (TAP)**, başlatma ve zaman uyumsuz bir işlemin tamamlanmasını temsil etmek için tek bir yöntem kullanır. DOKUNUN .NET Framework 4'te tanıtılan ve .NET Framework önerilen yaklaşım zaman uyumsuz programlama. [Zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) C# anahtar sözcükleri ve [zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [bekleme](~/docs/visual-basic/language-reference/operators/await-operator.md) Visual Basic Dil işleçleri DOKUNUN için dil desteği ekleyin. Daha fazla bilgi için bkz: [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
## <a name="comparing-patterns"></a>Desenler karşılaştırma  

Üç model zaman uyumsuz işlemleri nasıl düzenleri hızlı karşılaştırma için göz önünde bulundurun bir `Read` belirtilen uzaklıkta başlayan sağlanan arabellek içine belirtilen miktarda veri okuyan yöntemi:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
Bu yöntemin APM karşılık gelen kullanılabilmesini `BeginRead` ve `EndRead` yöntemleri:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
EAP karşılık gelen türleri ve üyeleri aşağıdaki kümesini kullanıma:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
DOKUNUN karşılık gelen aşağıdaki tek kullanılabilmesini `ReadAsync` yöntemi:  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
DOKUNUN, APM ve EAP kapsamlı bir tartışma için sonraki bölümde sağlanan bağlantılara bakın.  
  
## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| ----- | ----------- |
| [Zaman Uyumsuz Programlama Modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | Kullanan eski modeli açıklayan <xref:System.IAsyncResult> zaman uyumsuz davranışı sağlamak için arabirim. Bu model, artık yeni geliştirme projeleri için önerilir. |
| [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | Zaman uyumsuz davranışı sağlamak için olay tabanlı eski modeli açıklar. Bu model, artık yeni geliştirme projeleri için önerilir. |
| [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | Temel yeni zaman uyumsuz deseni açıklar <xref:System.Threading.Tasks> ad alanı. Bu model, .NET Framework 4 ve sonraki sürümlerde zaman uyumsuz programlama için önerilen yaklaşımdır. |

## <a name="see-also"></a>Ayrıca bkz.

[C# zaman uyumsuz programlama](~/docs/csharp/async.md)   
[F # zaman uyumsuz programlama](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
[Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)

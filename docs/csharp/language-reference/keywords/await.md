---
title: await (C# Başvurusu)
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: e32c7007ca98ce2153386665b60c45ff9e90cc3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218926"
---
# <a name="await-c-reference"></a>await (C# Başvurusu)
`await` İşleci awaited görevi tamamlanana kadar yönteminin yürütülmesi askıya noktası eklemek için zaman uyumsuz bir yöntem göreve uygulanır. Görev devam eden iş temsil eder.  
  
`await` yalnızca zaman uyumsuz bir yöntem değiştiren kullanılabilir [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) anahtar sözcüğü. Kullanılarak tanımlanmış böyle bir yöntemi, `async` değiştiricisini ve genellikle bir veya daha fazla içeren `await` ifadeleri olarak adlandırılır bir *async yöntemi*.  
  
> [!NOTE]
>  `async` Ve `await` anahtar sözcükler, C# 5'te sunulmuştu. Zaman uyumsuz programlamaya giriş için bkz: [zaman uyumsuz programlama ile async ve await](../../../csharp/programming-guide/concepts/async/index.md).  
  
Göreve `await` işleci uygulanır genellikle uygulayan bir yöntemine yapılan bir çağrı tarafından döndürülen [görev tabanlı zaman uyumsuz desen](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Döndüren yöntemler içerirler <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, ve `System.Threading.Tasks.ValueType<TResult>` nesneleri.  

  
 Aşağıdaki örnekte, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> yöntemi döndürür bir `Task<byte[]>`. Görev tamamlandığında gerçek bayt dizisi oluşturmak için bir promise görevidir. `await` İşleci yürütme çalışmanın kadar bekletir <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> yöntemi tamamlanmıştır. Bu arada, Denetim çağırana döndürülen `GetPageSizeAsync`. Görev yürütme tamamlandığında `await` ifadeyi hesaplar bir bayt dizisi.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
>  Tam bir örnek için bkz: [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme tarafından erişme](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Örnekten indirebilirsiniz [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) Microsoft Web sitesinde. AsyncWalkthrough_HttpClient projesinde örnektir.  
  
Önceki örnekte gösterildiği gibi `await` döndüren bir yöntem çağrısının sonucunu uygulanan bir `Task<TResult>`, ardından türünü `await` ifade `TResult`. Varsa `await` döndüren bir yöntem çağrısının sonucunu uygulanan bir `Task`, ardından türünü `await` ifade `void`. Aşağıdaki örnek fark gösterilmektedir.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
Bir `await` ifade üzerinde onu Yürütülüyor iş parçacığı engellemez. Bunun yerine, zaman uyumsuz yöntem rest awaited görev devamlılığı olarak imzalamak derleyici neden olur. Denetim ardından async yöntemi çağırana döndürür. Görev tamamlandığında, devamlılık ve kaldığı yerden zaman uyumsuz yöntem sürdürür yürütülmesi çağırır.  
  
Bir `await` ifade kendi kapsayan, yalnızca gövdesinde oluşabilir yöntemi, lambda ifadesi veya ile işaretlenmelidir anonim yöntemi bir `async` değiştiricisi. Terim *await* bu bağlamda yalnızca bir anahtar sözcük görevi görür. Başka bir yerde bir tanımlayıcı olarak yorumlanır. Yöntemi, lambda ifadesi veya anonim yöntemi, içinde bir `await` ifadesi, bir sorgu ifadesinde bloğunun zaman uyumlu bir işlev gövdesine gerçekleşemez bir [lock deyimi](../../../csharp/language-reference/keywords/lock-statement.md), veya bir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlamı.  
  
## <a name="exceptions"></a>Özel Durumlar  
Çoğu zaman uyumsuz yöntemleri döndürür bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Döndürülen görev özelliklerini durumunu ve görevin tam olup, async yöntemi bir özel durum nedeniyle veya iptal edildi ve son sonucu gibi geçmişi hakkında bilgi taşır. `await` İşleci tarafından döndürülen nesne üzerinde yöntemlerini çağırarak bu özellikleri erişen `GetAwaiter` yöntemi.  
  
Bir özel duruma neden olan görev döndüren bir zaman uyumsuz yöntem bekleme durumunda `await` işleci özel durumu yeniden oluşturur.  
  
İptal edilir, bir görev döndüren zaman uyumsuz yöntem bekleme durumunda `await` işleci bloğunu bir <xref:System.OperationCanceledException>.  
  
Hatalı durumda tek bir görevi birden fazla özel yansıtabilirsiniz. Örneğin, görev için bir çağrı sonucunu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Bu tür bir görev bekleme zaman bekleme işlemi yalnızca bir özel durum yeniden oluşturur. Ancak, özel durumlar hangisinin işlenemezse tahmin edilemez.  
  
Zaman uyumsuz yöntemleri işleme hatası örnekleri için bkz: [try-catch](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, URL'leri için komut satırı bağımsız değişken olarak geçirilen sayfaları toplam karakter sayısı döndürür. Örnek aramalar `GetPageLengthsAsync` ile işaretlenen yöntemi `async` anahtar sözcüğü. `GetPageLengthsAsync` Yöntemi sırayla kullanan `await` çağrıları bekleme için anahtar sözcüğü <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> yöntemi.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

Çünkü kullanımını `async` ve `await` bir uygulama giriş noktası desteklenmiyor, uygulayamıyoruz `async` özniteliğini `Main` yöntemi ya da can biz await `GetPageLengthsAsync` yöntem çağrısı. Biz emin olabilirsiniz `Main` yöntemi bekleyeceği zaman uyumsuz işlemin değerini alarak tamamlanmasını <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> özelliği. Bir değer döndürmeyen görevlerde çağırabilirsiniz <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemi. 

## <a name="see-also"></a>Ayrıca bkz.  
[Zaman uyumsuz programlama ile zaman uyumsuz ve bekleme](../../../csharp/programming-guide/concepts/async/index.md)   
[İzlenecek yol: Async kullanarak Web'e erişme ve bekler](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
[async](../../../csharp/language-reference/keywords/async.md)

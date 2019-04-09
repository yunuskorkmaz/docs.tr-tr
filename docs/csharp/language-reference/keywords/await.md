---
title: await - C# başvurusu
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 91d76309fedb2a6f3d877a47f230fda74060107e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122895"
---
# <a name="await-c-reference"></a>await (C# Başvurusu)
`await` İşleci awaited görevi tamamlanıncaya kadar yöntemin yürütülmesine askıya alma noktası eklemek için bir zaman uyumsuz yöntemdeki bir göreve uygulanır. Görev, devam eden çalışmayı temsil eder.  
  
`await` yalnızca zaman uyumsuz bir yöntem değiştiren kullanılabilir [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) anahtar sözcüğü. Tarafından tanımlanan tür bir yöntem, `async` değiştiricisi ve genellikle bir veya daha fazla içeren `await` ifadeleri olarak adlandırılır bir *zaman uyumsuz yöntem*.  
  
> [!NOTE]
> `async` Ve `await` anahtar sözcükler C# 5'te kullanıma sunulmuştur. Zaman uyumsuz programlamaya giriş için bkz [Asynchronous Programming with async ve await](../../../csharp/programming-guide/concepts/async/index.md).  
  
Görev `await` işleci uygulanır genellikle uygulayan bir yönteme bir çağrı tarafından döndürülen [görev tabanlı zaman uyumsuz desen](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Döndüren yöntemler içerirler <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, ve <xref:System.Threading.Tasks.ValueTask%601> nesneleri.  

Aşağıdaki örnekte, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> yöntemi döndürür bir `Task<byte[]>`. Görev, görev tamamlandığında gerçek bayt dizisini üretmek için bir vaattir. `await` İşleci çalışması kadar yürütmeyi askıya alır <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> yöntemi tamamlanmıştır. Bu sırada, Denetim çağırana döndürülmeden `GetPageSizeAsync`. Görev yürütme tamamlandığında `await` ifadesi bir bayt dizisine değerlendirir.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
> Tam bir örnek için bkz [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). İçinden örneği karşıdan yükleyebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) Microsoft Web sitesinde. Örnek AsyncWalkthrough_HttpClient projesindedir.  
  
Önceki örnekte gösterildiği gibi `await` getiren bir metot çağrısının sonucuna uygulanan bir `Task<TResult>`, sonra türünü `await` ifade `TResult`. Varsa `await` getiren bir metot çağrısının sonucuna uygulanan bir `Task`, sonra türünü `await` ifade `void`. Fark aşağıdaki örnekte gösterilmiştir.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
Bir `await` ifadesi, üzerinde yürütme yaptığı iş parçacığını engellemez. Bunun yerine, derleyicinin zaman uyumsuz yöntemin geri kalanını imzalamasına devamı olarak oturum neden olur. Denetim, ardından zaman uyumsuz yöntemini çağırana döner. Görev tamamlandığında, devamlılık ve yürütülmesi kaldığı zaman uyumsuz yöntem sürdürür çağırır.  
  
Bir `await` ifade, kapsayan, yalnızca gövdesinde oluşabilir yöntem, lambda ifadesi veya ile işaretlenmelidir anonim yöntem bir `async` değiştiricisi. Terim *await* yalnızca bu bağlamda bir anahtar sözcük görevi görür. Başka bir yerde, tanımlayıcı olarak yorumlanır. Yöntem, lambda ifadesi veya adsız yöntemle, içinde bir `await` deyim bloğunda, bir sorgu ifadesinde, zaman uyumlu bir işlevin gövdesinde gerçekleşemez bir [kilit deyimi](../../../csharp/language-reference/keywords/lock-statement.md), veya bir [güvenli](../../../csharp/language-reference/keywords/unsafe.md) bağlamı.  
  
## <a name="exceptions"></a>Özel Durumlar  
Çoğu zaman uyumsuz yöntemlerin dönüş bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Döndürülen görevin özelliklerini, durumunu ve geçmişini, görevin tam olup olmadığı, zaman uyumsuz yöntemin bir özel duruma neden oldu veya iptal edildi ve nihai sonucun ne olduğu gibi hakkında bilgi getirir. `await` İşleci tarafından döndürülen nesne üzerinde yöntemleri çağırarak bu özelliklere erişir `GetAwaiter` yöntemi.  
  
Bir özel durum neden olan bir görev döndüren zaman uyumsuz yöntem, `await` işleci özel durumu yeniden oluşturur.  
  
İptal edilen bir görev döndüren zaman uyumsuz yöntem, `await` işleci beklerseniz bir <xref:System.OperationCanceledException>.  
  
Hatalı bir durumda olan tek bir görev birden çok özel durumu yansıtabilir. Örneğin, görev yapılan bir çağrının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Böyle bir görevi beklerken, bekleme işlemi özel durumlardan yalnızca birini yeniden oluşturur. Ancak, özel durumların fırlatılan tahmin edemezsiniz.  
  
Zaman uyumsuz yöntemlerdeki hata işleme örnekleri için bkz: [try-catch](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, URL'leri için komut satırı bağımsız değişkenleri geçirilir sayfalarında toplam karakter sayısı döndürür. Örnek aramalar `GetPageLengthsAsync` ile işaretlenmiş yöntemi `async` anahtar sözcüğü. `GetPageLengthsAsync` Sırayla kullanmaktadır `await` çağrıları await anahtar sözcüğünü <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> yöntemi.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

Önceki örnekte C# destekleyen 7.1 [ `async` `Main` yöntemi](../../programming-guide/main-and-command-args/index.md). Çünkü daha önceki C# sürümleri döndüren uygulama giriş noktaları desteklemez <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, uygulayamazsınız `async` değiştiriciyi `Main` yöntemi ve await `GetPageLengthsAsync` yöntem çağrısı. Bu durumda, işaretlenmesini sağlayabilir `Main` yöntemi zaman uyumsuz işlemin değerini alarak bekler <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> özelliği. Bir değeri döndürmeyen görev çağırabilirsiniz <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemi. Dil sürümü seçme hakkında daha fazla bilgi için bkz: [seçin C# dil sürümü](../configure-language-version.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile Zaman Uyumsuz Programlama](../../../csharp/programming-guide/concepts/async/index.md)
- [İzlenecek yol: Async ve Await Kullanarak Web'e Erişme](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [async](../../../csharp/language-reference/keywords/async.md)

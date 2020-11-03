---
title: Zamanlayıcılar
description: Çok iş parçacıklı bir ortamda kullanılacak .NET zamanlayıcıları hakkında bilgi edinin.
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.openlocfilehash: c9d0b085285705af79f0fafa212867b5571863ba
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188724"
---
# <a name="timers"></a>Zamanlayıcılar

.NET, çok iş parçacıklı bir ortamda kullanmak için iki Zamanlayıcı sağlar:

- <xref:System.Threading.Timer?displayProperty=nameWithType>düzenli aralıklarla bir iş parçacığında tek bir geri çağırma yöntemi yürüten <xref:System.Threading.ThreadPool> .
- <xref:System.Timers.Timer?displayProperty=nameWithType>Bu, varsayılan olarak <xref:System.Threading.ThreadPool> düzenli aralıklarla bir iş parçacığında bir olay oluşturur.

> [!NOTE]
> Bazı .NET uygulamaları ek zamanlayıcılar içerebilir:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: düzenli aralıklarla bir olayı harekete uygulayan Windows Forms bileşen. Bileşen Kullanıcı arabirimine sahip değildir ve tek iş parçacıklı bir ortamda kullanılmak üzere tasarlanmıştır.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: düzenli bir aralıkta zaman uyumsuz veya zaman uyumlu Web sayfası geri gönderileri gerçekleştiren bir ASP.NET bileşeni.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: <xref:System.Windows.Threading.Dispatcher> belirli bir zaman aralığında ve belirtilen öncelikte işlenen kuyrukla tümleştirilmiş bir zamanlayıcı.

## <a name="the-systemthreadingtimer-class"></a>System. Threading. Timer sınıfı

<xref:System.Threading.Timer?displayProperty=nameWithType>Sınıfı, belirli zaman aralıklarında bir temsilciyi sürekli olarak çağırmanızı sağlar. Bu sınıfı, belirli bir zaman aralığındaki bir temsilciye tek bir çağrı zamanlamak için de kullanabilirsiniz. Temsilci bir <xref:System.Threading.ThreadPool> iş parçacığında yürütülür.

Bir nesne oluşturduğunuzda, geri <xref:System.Threading.Timer?displayProperty=nameWithType> <xref:System.Threading.TimerCallback> çağırma yöntemini, geri çağrıya geçirilen isteğe bağlı bir durum nesnesini, geri aramanın ilk çağrısından önce gecikme süresini ve geri çağırma çağırmaları arasındaki zaman aralığını tanımlayan bir temsilci belirtirsiniz. Bekleyen bir zamanlayıcıyı iptal etmek için yöntemini çağırın <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> .

Aşağıdaki örnek, belirtilen temsilciyi bir saniyeden sonra ilk kez çağıran bir zamanlayıcı oluşturur (1000 milisaniye) ve ardından iki saniyede bir çağırır. Örnekteki durum nesnesi, temsilcinin kaç kez çağrıldığını saymak için kullanılır. Temsilci, en az 10 kez çağrıldığında Zamanlayıcı durdurulur.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Daha fazla bilgi ve örnek için bkz <xref:System.Threading.Timer?displayProperty=nameWithType> ..

## <a name="the-systemtimerstimer-class"></a>System. süreölçerler. Timer sınıfı

Çoklu iş parçacıklı bir ortamda kullanılabilen bir zamanlayıcı, <xref:System.Timers.Timer?displayProperty=nameWithType> Varsayılan olarak bir iş parçacığında bir olay oluşturur <xref:System.Threading.ThreadPool> .

Bir <xref:System.Timers.Timer?displayProperty=nameWithType> nesne oluşturduğunuzda, bir olayın tetikkaydedileceği zaman aralığını belirtebilirsiniz <xref:System.Timers.Timer.Elapsed> . <xref:System.Timers.Timer.Enabled%2A>Bir zamanlayıcının bir olayı oluşturup tetiklemeyeceğini göstermek için özelliğini kullanın <xref:System.Timers.Timer.Elapsed> . Bir <xref:System.Timers.Timer.Elapsed> olayın yalnızca belirtilen Aralık geçtikten sonra bir kez ortaya çıkarılmasının gerekmesi durumunda, öğesini <xref:System.Timers.Timer.AutoReset%2A> olarak ayarlayın `false` . Özelliğinin varsayılan değeri, <xref:System.Timers.Timer.AutoReset%2A> `true` bir <xref:System.Timers.Timer.Elapsed> olayın özelliği tarafından tanımlanan aralıkta düzenli olarak oluşturulduğu anlamına gelir <xref:System.Timers.Timer.Interval%2A> .

Daha fazla bilgi ve örnek için bkz <xref:System.Timers.Timer?displayProperty=nameWithType> ..
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)

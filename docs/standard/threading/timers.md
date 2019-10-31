---
title: Süreölçerler
description: Çok iş parçacıklı bir ortamda kullanılacak .NET zamanlayıcıları hakkında bilgi edinin.
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.openlocfilehash: d7d1fa13b02fe7425fa9b4cb81ba20297a23fe4b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128945"
---
# <a name="timers"></a>Süreölçerler

.NET, çok iş parçacıklı bir ortamda kullanmak için iki Zamanlayıcı sağlar:

- düzenli aralıklarla <xref:System.Threading.ThreadPool> iş parçacığında tek bir geri çağırma yöntemi yürüten <xref:System.Threading.Timer?displayProperty=nameWithType>.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, varsayılan olarak düzenli aralıklarla bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde bir olay oluşturur.

> [!NOTE]
> Bazı .NET uygulamaları ek zamanlayıcılar içerebilir:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: düzenli aralıklarla bir olayı harekete uygulayan Windows Forms bir bileşen. Bileşen Kullanıcı arabirimine sahip değildir ve tek iş parçacıklı bir ortamda kullanılmak üzere tasarlanmıştır.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: düzenli bir aralıkta zaman uyumsuz veya zaman uyumlu Web sayfası geri göndermeler gerçekleştiren bir ASP.NET bileşeni.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: belirli bir zaman aralığında ve belirtilen öncelikte işlenen <xref:System.Windows.Threading.Dispatcher> kuyruğu ile tümleştirilmiş bir zamanlayıcı.

## <a name="the-systemthreadingtimer-class"></a>System. Threading. Timer sınıfı

<xref:System.Threading.Timer?displayProperty=nameWithType> sınıfı, belirli zaman aralıklarında bir temsilciyi sürekli olarak çağırmanızı sağlar. Bu sınıfı, belirli bir zaman aralığındaki bir temsilciye tek bir çağrı zamanlamak için de kullanabilirsiniz. Temsilci <xref:System.Threading.ThreadPool> bir iş parçacığında yürütülür.

<xref:System.Threading.Timer?displayProperty=nameWithType> nesnesi oluşturduğunuzda, geri çağırma yöntemini, geri çağrıya geçirilen isteğe bağlı bir durum nesnesini, geri aramanın ilk çağrısından önce gecikme süresini ve arasındaki zaman aralığını tanımlayan bir <xref:System.Threading.TimerCallback> temsilcisi belirtirsiniz. geri çağırma çağırmaları. Bekleyen bir zamanlayıcıyı iptal etmek için <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek, belirtilen temsilciyi bir saniyeden sonra ilk kez çağıran bir zamanlayıcı oluşturur (1000 milisaniye) ve ardından iki saniyede bir çağırır. Örnekteki durum nesnesi, temsilcinin kaç kez çağrıldığını saymak için kullanılır. Temsilci, en az 10 kez çağrıldığında Zamanlayıcı durdurulur.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Daha fazla bilgi ve örnek için bkz. <xref:System.Threading.Timer?displayProperty=nameWithType>.

## <a name="the-systemtimerstimer-class"></a>System. süreölçerler. Timer sınıfı

Çoklu iş parçacıklı bir ortamda kullanılabilen başka bir zamanlayıcı, varsayılan olarak bir <xref:System.Threading.ThreadPool> iş parçacığında bir olay harekete geçirirse <xref:System.Timers.Timer?displayProperty=nameWithType>.

Bir <xref:System.Timers.Timer?displayProperty=nameWithType> nesnesi oluşturduğunuzda, bir <xref:System.Timers.Timer.Elapsed> olayının tetikkaydedileceği zaman aralığını belirtebilirsiniz. Bir zamanlayıcının bir <xref:System.Timers.Timer.Elapsed> olayı oluşturup yükseltmeyeceğini göstermek için <xref:System.Timers.Timer.Enabled%2A> özelliğini kullanın. Bir <xref:System.Timers.Timer.Elapsed> olayının, belirtilen Aralık geçtikten sonra yalnızca bir kez ortaya çıkarıldıktan sonra, <xref:System.Timers.Timer.AutoReset%2A> `false`olarak ayarlayın. <xref:System.Timers.Timer.AutoReset%2A> özelliğinin varsayılan değeri `true`ve bu, <xref:System.Timers.Timer.Elapsed> bir olayın <xref:System.Timers.Timer.Interval%2A> özelliği tarafından tanımlanan aralıkta düzenli olarak oluşturulduğu anlamına gelir.

Daha fazla bilgi ve örnek için bkz. <xref:System.Timers.Timer?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [İş Parçacığı Nesneleri ve Özellikleri](threading-objects-and-features.md)

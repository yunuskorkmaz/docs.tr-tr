---
title: Zamanlayıcılar
description: .NET zamanlayıcıların çok iş parçacığı ortamında ne kullanacağını öğrenin.
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
ms.openlocfilehash: d463eb2a8d598dc5ba9b2fb51a6fc08c563e6fe4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739494"
---
# <a name="timers"></a>Zamanlayıcılar

.NET, çok iş parçacığı bir ortamda kullanmak üzere iki zamanlayıcı sağlar:

- <xref:System.Threading.Timer?displayProperty=nameWithType>, düzenli aralıklarla bir iş <xref:System.Threading.ThreadPool> parçacığı üzerinde tek bir geri arama yöntemi yürütür.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, varsayılan olarak düzenli aralıklarla bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde bir olay yükseltir.

> [!NOTE]
> Bazı .NET uygulamaları ek zamanlayıcılar içerebilir:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: bir olayı düzenli aralıklarla ateşleyen bir Windows Forms bileşeni. Bileşenin kullanıcı arabirimi yoktur ve tek iş parçacığı ortamında kullanılmak üzere tasarlanmıştır.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: düzenli aralıklarla eşzamanlı veya senkron web sayfası postback'leri gerçekleştiren ASP.NET bir bileşendir.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: <xref:System.Windows.Threading.Dispatcher> belirli bir zaman aralığında ve belirli bir öncelikte işlenen sıraya entegre edilmiş bir zamanlayıcı.

## <a name="the-systemthreadingtimer-class"></a>System.Threading.Timer sınıfı

Sınıf, <xref:System.Threading.Timer?displayProperty=nameWithType> belirli zaman aralıklarında sürekli olarak temsilci çağırmanızı sağlar. Bu sınıfı, belirli bir zaman aralığında bir temsilciye tek bir çağrı zamanlamak için de kullanabilirsiniz. Temsilci bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde yürütülür.

Bir <xref:System.Threading.Timer?displayProperty=nameWithType> nesne oluşturduğunuzda, <xref:System.Threading.TimerCallback> geri arama yöntemini, geri arama için geçirilen isteğe bağlı durum nesnesini, geri aramanın ilk çağrılmadan önce geciktirilmesi gereken süreyi ve geri arama çağrıları arasındaki zaman aralığını tanımlayan bir temsilci belirtirsiniz. Bekleyen bir zamanlayıcıyı iptal <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> etmek için yöntemi arayın.

Aşağıdaki örnek, sağlanan temsilciyi bir saniyeden (1000 milisaniye) sonra ilk kez çağıran ve ardından her iki saniyede bir çağıran bir zamanlayıcı oluşturur. Örnekteki durum nesnesi, temsilcinin kaç kez çağrıldığını saymak için kullanılır. Temsilci en az 10 kez çağrıldığında zamanlayıcı durdurulur.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Daha fazla bilgi ve <xref:System.Threading.Timer?displayProperty=nameWithType>örnekler için bkz.

## <a name="the-systemtimerstimer-class"></a>System.Timers.Timer sınıfı

Çok iş parçacığı ortamında kullanılabilecek başka bir <xref:System.Timers.Timer?displayProperty=nameWithType> zamanlayıcı, varsayılan olarak <xref:System.Threading.ThreadPool> bir iş parçacığı üzerinde bir olay yükseltir olmasıdır.

Bir <xref:System.Timers.Timer?displayProperty=nameWithType> nesne oluşturduğunuzda, bir <xref:System.Timers.Timer.Elapsed> olayı yükseltmek için zaman aralığını belirtebilirsiniz. Bir <xref:System.Timers.Timer.Enabled%2A> zamanlayıcının bir <xref:System.Timers.Timer.Elapsed> olayı yükseltmesi gerekip gerekmediğini belirtmek için özelliği kullanın. Belirtilen aralık <xref:System.Timers.Timer.Elapsed> geçtikten sonra yalnızca bir kez yükseltilecek bir olay <xref:System.Timers.Timer.AutoReset%2A> `false`gerekiyorsa, 'yi ' ye ayarlayın. <xref:System.Timers.Timer.AutoReset%2A> Özelliğin varsayılan `true`değeri, bir <xref:System.Timers.Timer.Elapsed> olayın <xref:System.Timers.Timer.Interval%2A> özellik tarafından tanımlanan aralıkta düzenli olarak yükseltildiği anlamına gelir.

Daha fazla bilgi ve <xref:System.Timers.Timer?displayProperty=nameWithType>örnekler için bkz.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [İş Parçacığı Nesneleri ve Özellikleri](threading-objects-and-features.md)

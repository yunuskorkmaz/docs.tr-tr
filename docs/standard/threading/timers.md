---
title: Süreölçerler
description: Çok iş parçacıklı bir ortamda kullanmak için hangi .NET zamanlayıcılar hakkında bilgi edinin.
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
ms.author: ronpet
ms.openlocfilehash: 63f9b759621689c129fc356fe38d7e7c5ee41f30
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878567"
---
# <a name="timers"></a>Süreölçerler

.NET, çok iş parçacıklı bir ortamda kullanmak için iki zamanlayıcılar sağlar:

- <xref:System.Threading.Timer?displayProperty=nameWithType>, üzerinde tek bir geri çağırma yöntemini yürütür bir <xref:System.Threading.ThreadPool> düzenli aralıklarla iş parçacığı.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, varsayılan olarak yükselten bir olay hakkında bir <xref:System.Threading.ThreadPool> düzenli aralıklarla iş parçacığı.

> [!NOTE]
> Bazı .NET uygulamalarında ek zamanlayıcılar şunları içerebilir:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: bir Windows Forms bileşeni düzenli aralıklarla bir olayı tetikler. Bileşen herhangi bir kullanıcı arabirimi olan ve tek iş parçacıklı bir ortamda kullanılmak üzere tasarlanmıştır.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: düzenli aralıkla web sayfası zaman uyumlu veya zaman uyumsuz Geri göndermeler gerçekleştiren bir ASP.NET bileşeni.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: tümleştirilmiş bir zamanlayıcı <xref:System.Windows.Threading.Dispatcher> işlenen belirtilen bir zaman aralığı ve belirtilen bir öncelik sırası.

## <a name="the-systemthreadingtimer-class"></a>Süre System.Threading.Timer sınıfı

<xref:System.Threading.Timer?displayProperty=nameWithType> Sınıfı temsilci belirtilen aralıklarla sürekli olarak çağırmanızı sağlar. Bu sınıf, belirtilen zaman aralığı içinde bir temsilci tek bir çağrı zamanlamak için de kullanabilirsiniz. Temsilci üzerinde yürütülen bir <xref:System.Threading.ThreadPool> iş parçacığı.

Oluştururken bir <xref:System.Threading.Timer?displayProperty=nameWithType> nesne, belirttiğiniz bir <xref:System.Threading.TimerCallback> geri çağırma yöntemi tanımlayan bir temsilci, geri çağırma ve zaman aralığını ilk çağrısıysa önce gecikme süresini geri çağırma geçirilen bir isteğe bağlı durum nesnesi geri çağırmaları arasında. Bekleyen bir zamanlayıcı iptal etmek için çağrı <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> yöntemi.

Aşağıdaki örnek, bir saniye (1000 milisaniye cinsinden) sonra ilk kez sağlanan temsilci çağırır ve ardından her iki saniye çağıran bir zamanlayıcı oluşturur. Örnekte durum nesnesi, bir temsilci çağrılır kaç kez saymak için kullanılır. En az 10 kez temsilci çağrıldığında Zamanlayıcı durduruldu.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Daha fazla bilgi ve örnekler için bkz. <xref:System.Threading.Timer?displayProperty=nameWithType>.

## <a name="the-systemtimerstimer-class"></a>System.Timers.Timer sınıfı

Çok iş parçacıklı bir ortamda kullanılabilen başka bir süre ölçer <xref:System.Timers.Timer?displayProperty=nameWithType> varsayılan olarak oluşturan bir olay hakkında bir <xref:System.Threading.ThreadPool> iş parçacığı.

Oluştururken bir <xref:System.Timers.Timer?displayProperty=nameWithType> nesnesi, yükseltmek istediğiniz zaman aralığını belirtin bir <xref:System.Timers.Timer.Elapsed> olay. Kullanım <xref:System.Timers.Timer.Enabled%2A> Zamanlayıcı oluşturması gerektiğini belirtmek için özelliği bir <xref:System.Timers.Timer.Elapsed> olay. Gerekirse bir <xref:System.Timers.Timer.Elapsed> belirtilen zaman aralığı geçtikten sonra yalnızca bir kez tetiklenecek olayı <xref:System.Timers.Timer.AutoReset%2A> için `false`. Varsayılan değer olan <xref:System.Timers.Timer.AutoReset%2A> özelliği `true`, anlamına gelecek şekilde, bir <xref:System.Timers.Timer.Elapsed> olayı oluşturulur düzenli olarak tarafından tanımlanan aralıkta <xref:System.Timers.Timer.Interval%2A> özelliği.

Daha fazla bilgi ve örnekler için bkz. <xref:System.Timers.Timer?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Timer?displayProperty=nameWithType>  
- <xref:System.Timers.Timer?displayProperty=nameWithType>  
- [İş Parçacığı Nesneleri ve Özellikleri](threading-objects-and-features.md)

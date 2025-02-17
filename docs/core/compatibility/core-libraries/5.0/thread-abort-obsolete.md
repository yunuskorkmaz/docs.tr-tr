---
title: 'Son değişiklik: Thread. Abort artık kullanılmıyor'
description: Iş parçacığı. Abort API 'Lerinin artık kullanılmayan çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 29c688250593801bab9b32b9e787911e561ec000
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257069"
---
# <a name="threadabort-is-obsolete"></a>Thread.Abort kullanımdan kaldırıldı

<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>API 'ler artık kullanılmıyor. .NET 5 veya sonraki bir sürümü hedefleyen projeler, bu yöntemler çağrılırsa derleme zamanı uyarısıyla karşılaşacaktır `SYSLIB0006` .

## <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, ' <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> a yapılan çağrılar derleme zamanı uyarıları üretmedi, ancak yöntem çalışma zamanında bir oluşturma işlemi gerçekleştiriyordu <xref:System.PlatformNotSupportedException> .

.NET 5 ' den başlayarak, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> uyarı olarak kullanımdan kalkmış olarak işaretlenir. Bu yöntemin çağrılması derleyici uyarısı oluşturur `SYSLIB0006` . Yönteminin uygulanması değiştirilmez ve bir oluşturma işlemi devam eder <xref:System.PlatformNotSupportedException> .

## <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Her zaman <xref:System.PlatformNotSupportedException> , .NET Framework hariç tüm .NET uygulamalarında her zaman bir şekilde oluşturulan, <xref:System.ObsoleteAttribute> çağrıldığı yerlere dikkat çekmek için yönteme eklenmiştir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

- <xref:System.Threading.CancellationToken>Çağırmak yerine bir iş birimi işlemesini durdurmak için bir kullanın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> . Aşağıdaki örnek öğesinin kullanımını gösterir <xref:System.Threading.CancellationToken> .

  ```csharp
  void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
  {
      if (QueryIsMoreWorkPending())
      {
          // If the CancellationToken is marked as "needs to cancel",
          // this will throw the appropriate exception.
          cancellationToken.ThrowIfCancellationRequested();

          WorkItem work = DequeueWorkItem();
          ProcessWorkItem(work);
      }
  }
  ```

  Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında iptal](../../../../standard/threading/cancellation-in-managed-threads.md).

- Derleme zamanı uyarısını bastırmak için uyarı kodunu gizleyin `SYSLIB0006` . Uyarı kodu öğesine özeldir <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ve bu kod, kodunuzun diğer kullanımdan kaldırma uyarılarını göstermez. Ancak, uyarıları kaldırmak yerine ' a yapılan çağrıları kaldırmanızı öneririz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  Ayrıca, proje dosyasında uyarıyı da gizleyebilirsiniz.

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->

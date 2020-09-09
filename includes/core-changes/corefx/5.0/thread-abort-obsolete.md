---
ms.openlocfilehash: 85488de561a2298f2ff4009ec78b9a6e294053f3
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598183"
---
### <a name="threadabort-is-obsolete"></a>Thread. Abort artık kullanılmıyor

<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>API 'ler artık kullanılmıyor. .NET 5,0 veya sonraki bir sürümü hedefleyen projeler, bu yöntemler çağrılırsa derleme zamanı uyarılarıyla karşılaşacaktır. Uyarıları bastırdığınızda, çalışma zamanında bir <xref:System.PlatformNotSupportedException> oluşturulur.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, ' <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> a yapılan çağrılar derleme zamanı uyarıları üretmedi, ancak yöntem çalışma zamanında bir oluşturma işlemi gerçekleştiriyordu <xref:System.PlatformNotSupportedException> .

.NET 5,0 ' den itibaren, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> artık uyarı olarak kullanılmıyor olarak işaretlenir. Bu yöntemin çağrılması derleyici uyarısı oluşturur `SYSLIB0006` . Yönteminin uygulanması değiştirilmez ve bir oluşturma işlemi devam eder <xref:System.PlatformNotSupportedException> .

#### <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Her zaman <xref:System.PlatformNotSupportedException> , .NET Framework hariç tüm .NET uygulamalarında her zaman bir şekilde oluşturulan, <xref:System.ObsoleteAttribute> çağrıldığı yerlere dikkat çekmek için yönteme eklenmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 RC 1

#### <a name="recommended-action"></a>Önerilen eylem

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

  Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında iptal](../../../../docs/standard/threading/cancellation-in-managed-threads.md).

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

#### <a name="category"></a>Kategori

- Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->

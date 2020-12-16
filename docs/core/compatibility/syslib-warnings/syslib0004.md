---
title: SYSLIB0004 uyarısı
description: Derleme zamanı uyarı SYSLIB0004 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 03be8bb54f71f74ed94ee2c3f8489397ae1e99b5
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596561"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a>SYSLIB0004: kısıtlanmış yürütme bölgesi (CER) özelliği desteklenmiyor

[Kısıtlı yürütme bölgeleri (cer)](../../../framework/performance/constrained-execution-regions.md) özelliği yalnızca .NET Framework desteklenir. Bu nedenle, CER ile ilgili çeşitli API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Bu API 'Lerin kullanılması, `SYSLIB0004` derleme zamanında uyarı oluşturur.

Aşağıdaki CER ile ilgili API 'Ler artık kullanılmıyor:

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="workarounds"></a>Geçici Çözümler

- Bir metoda bir CER özniteliği uyguladıysanız, özniteliğini kaldırın. Bu özniteliklerin, .NET 5,0 ve sonraki sürümlerinde hiçbir etkisi yoktur.

  ```csharp
  // REMOVE the attribute below.
  [ReliabilityContract(Consistency.WillNotCorruptState, Cer.Success)]
  public void DoSomething()
  {
  }

  // REMOVE the attribute below.
  [PrePrepareMethod]
  public void DoSomething()
  {
  }
  ```

- Veya öğesini çağırıyorsanız `RuntimeHelpers.ProbeForSufficientStack` `RuntimeHelpers.PrepareContractedDelegate` , çağrıyı kaldırın. Bu çağrıların, .NET 5,0 ve sonraki sürümlerde hiçbir etkisi yoktur.

  ```csharp
  public void DoSomething()
  {
      // REMOVE the call below.
      RuntimeHelpers.ProbeForSufficientStack();

      // (Remainder of your method logic here.)
  }
  ```

- Öğesini çağırıyorsanız `RuntimeHelpers.PrepareConstrainedRegions` , çağrıyı kaldırın. Bu çağrının, .NET 5,0 ve sonraki sürümlerde hiçbir etkisi yoktur.

  ```csharp
  public void DoSomething_Old()
  {
      // REMOVE the call below.
      RuntimeHelpers.PrepareConstrainedRegions();
      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }

  public void DoSomething_Corrected()
  {
      // There is no call to PrepareConstrainedRegions. It's a normal try / finally block.

      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

- Öğesini çağırıyorsanız `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup` , çağrıyı standart bir _try/catch/finally_ bloğu ile değiştirin.

  ```csharp
  // The sample below produces warning SYSLIB0004.
  public void DoSomething_Old()
  {
      RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(MyTryCode, MyCleanupCode, null);
  }
  public void MyTryCode(object state) { /* try code */ }
  public void MyCleanupCode(object state, bool exceptionThrown) { /* cleanup code */ }

  // The corrected sample below does not produce warning SYSLIB0004.
  public void DoSomething_Corrected()
  {
      try
      {
          // try code
      }
      catch (Exception ex)
      {
          // exception handling code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Kısıtlı yürütme bölgeleri](../../../framework/performance/constrained-execution-regions.md)

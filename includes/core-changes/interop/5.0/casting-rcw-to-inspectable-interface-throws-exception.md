---
ms.openlocfilehash: 8693c1fdef5fa194b16127d4f1dd87e23ad68f2d
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438055"
---
### <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a>Bir arabirime RCW atama `InterfaceIsIInspectable` PlatformNotSupportedException oluşturur

Çalışma zamanı çağrılabilir sarmalayıcı (RCW) ' i şu şekilde işaretlenen bir arabirime atama, <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> bir oluşturur <xref:System.PlatformNotSupportedException> . Bu değişiklik, [.net 'Ten WinRT desteğinin kaldırılmasına](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net)yönelik bir izdir.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 RC2

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET 5,0 Preview 6 ' dan önceki .NET sürümlerinde, bir RCW 'yı beklenen şekilde işaretlenen bir arabirime atama <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> . .NET 5,0 önizlemeleri 6-8 ve RC1 'de, bir RCW 'ı bir arabirime başarıyla çevirebilirsiniz <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> . Ancak, çalışma zamanındaki temeldeki destek [.net 5,0 Preview 6 ' da kaldırıldığından](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net), arabirim üzerinde Yöntemler yürüttüğünüzde erişim ihlalleri alabilirsiniz.

.NET 5,0 RC2 ve sonraki sürümlerinde, bir RCW 'yı olarak işaretlenen bir arabirime atama, <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> atama zamanında oluşturur <xref:System.PlatformNotSupportedException> .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Desteği <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> [önceki bir .NET 5,0 önizlemesinde kaldırılmıştır](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net). Ancak, bir arabirime atama <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> yanlışlıkla daha fazla baktık. Çalışma zamanındaki temel alınan destek artık mevcut olmadığından, bir oluşturma düzgün bir <xref:System.PlatformNotSupportedException> hata yolu sunar. Özel durum oluşturmak, bu özelliğin artık desteklenmediğini daha fazla bulunabilir hale getirir.

#### <a name="recommended-action"></a>Önerilen eylem

- Arabirimi bir Windows çalışma zamanı meta verileri (WinMD) dosyasında tanımlayabiliyorsanız bunun yerine C#/wınrt aracını kullanın.

- Aksi takdirde, arabirimini yerine olarak işaretleyin <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> ve bu yöntemlerin arayüzünün başına üç sözde giriş ekleyin <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> . Aşağıdaki kod parçacığı bir örnek gösterir.

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

#### <a name="category"></a>Kategori

Interop

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

-->

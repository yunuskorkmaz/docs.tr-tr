---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614714"
---
### <a name="long-path-support"></a>Uzun yol desteği

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 hedeflenen uygulamalardan başlayarak, uzun yollar (en fazla 32K karakter) desteklenir ve yol uzunlukları 260 karakterlik (veya `MAX_PATH` ) sınırlaması kaldırılmıştır. .NET Framework 4.6.2 hedeflemek üzere yeniden derlenen uygulamalar için, bir yol 260 karakteri aştığından daha önce bir olan kod yolları <xref:System.IO.PathTooLongException?displayProperty=fullName> Şimdi <xref:System.IO.PathTooLongException?displayProperty=fullName> yalnızca aşağıdaki koşullarda bir oluşturacak:

- Yolun uzunluğu <xref:System.Int16.MaxValue> (32.767) karakterden fazla.
- İşletim sistemi, `COR_E_PATHTOOLONG` eşdeğerini döndürür.
.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen uygulamalar için, bir <xref:System.IO.PathTooLongException?displayProperty=fullName> yol 260 karakteri aştığında çalışma zamanı otomatik olarak bir oluşturur.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.6.2 hedefleyen uygulamalar için, dosyanızın bölümüne aşağıdakiler eklenerek uzun yol desteğini devre dışı bırakabilirsiniz `<runtime>` `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

.NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.2 veya sonraki sürümlerde çalışan uygulamalar için, dosyanızın bölümüne aşağıdakileri ekleyerek uzun yol desteğini tercih edebilirsiniz `<runtime>` `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

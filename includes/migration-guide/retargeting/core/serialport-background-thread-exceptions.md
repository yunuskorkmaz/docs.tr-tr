---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614750"
---
### <a name="serialport-background-thread-exceptions"></a>SerialPort arka plan iş parçacığı özel durumları

#### <a name="details"></a>Ayrıntılar

Akışlarla oluşturulan arka plan iş parçacıkları <xref:System.IO.Ports.SerialPort> artık işletim sistemi özel durumları oluştuğunda işlemi sonlandırır. <br/>.NET Framework 4,7 ve önceki sürümlerini hedefleyen uygulamalarda, bir akış ile oluşturulan arka plan iş parçacığında bir işletim sistemi özel durumu oluştuğunda bir işlem sonlandırılır <xref:System.IO.Ports.SerialPort> . <br/>.NET Framework 4.7.1 veya sonraki bir sürümü hedefleyen uygulamalarda, arka plan iş parçacıkları etkin seri bağlantı noktasıyla ilgili işletim sistemi olaylarını bekler ve seri bağlantı noktasının ani kaldırılması gibi bazı durumlarda kilitlenebilir.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.7.1 ' i hedefleyen uygulamalar için, aşağıdaki, dosyanızın bölümüne aşağıdakileri ekleyerek özel durum işlemesini devre dışı bırakabilirsiniz `<runtime>` `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

.NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.7.1 veya sonraki sürümlerde çalışan uygulamalar için, dosyanızın bölümüne aşağıdakini ekleyerek özel durum işlemeye geçebilirsiniz `<runtime>` `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>

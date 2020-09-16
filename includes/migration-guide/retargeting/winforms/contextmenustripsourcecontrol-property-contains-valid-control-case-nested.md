---
ms.openlocfilehash: 5529b8379c5cb9f1bc525e0c2340f6b885e35822
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606700"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>ContextMenuStrip. SourceControl özelliği, iç içe ToolStripMenuItems durumunda geçerli bir denetim içeriyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.1 ve önceki sürümlerde <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliği, Kullanıcı menüyü iç içe geçmiş denetimlerden açtığında yanlış bir değer döndürür <xref:System.Windows.Forms.ToolStripMenuItem> . .NET Framework 4.7.2 ve sonrasında, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> özelliği her zaman gerçek kaynak denetimine ayarlanır.

#### <a name="suggestion"></a>Öneri

**Bu değişiklikleri kabul etme veya devre dışı bırakma** Bir uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.2 veya sonraki bir sürümde çalışmalıdır. Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:

- .NET Framework 4.7.2 ' i hedefliyor. Bu değişiklik, .NET Framework 4.7.2 veya üstünü hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilir.
- Aşağıdaki örnekte gösterildiği gibi, .NET Framework 4.7.1 veya daha önceki bir sürümü hedefler ve eski erişilebilirlik davranışlarından yararlanarak, aşağıdaki [AppContext anahtarını](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` app.config dosyasının bölümüne ekleyerek ve öğesini olarak ayarlayarak eski erişilebilirlik davranışlarından daha fazla bilgi sağlar `false` .

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

.NET Framework 4.7.2 veya üstünü hedefleyen ve eski davranışı korumak isteyen uygulamalar, bu AppContext anahtarını açıkça olarak ayarlayarak eski kaynak denetimi değerinin kullanımını kabul edebilir `true` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

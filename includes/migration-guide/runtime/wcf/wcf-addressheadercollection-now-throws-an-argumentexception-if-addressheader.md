---
ms.openlocfilehash: e8b98e465228afd07432e737bb16aefb1b979973
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770890"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>Bir addressHeader öğesi null ise, WCF AddressHeaderCollection şimdi bir ArgumentException oluşturur

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.1 ' den başlayarak, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Oluşturucu <xref:System.ArgumentException> öğelerinden biri ise bir tane oluşturur `null` . .NET Framework 4,7 ve önceki sürümlerde, hiçbir özel durum oluşturulmaz.

#### <a name="suggestion"></a>Öneri

Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunlarıyla karşılaşırsanız, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek devre dışı bırakabilirsiniz `<runtime>` :

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->

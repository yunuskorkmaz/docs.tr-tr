---
ms.openlocfilehash: fa2a856911c7dcf81a39b7682a62a86c35328037
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274965"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>WCF AddressHeaderCollection şimdi bir addressHeader öğesi null ise bir ArgumentException atar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> başlayarak, yapıcı <xref:System.ArgumentException> bir öğe <code>null</code>atar. .NET Framework 4.7 ve önceki sürümlerinde hiçbir istisna atılmaz.|
|Öneri|.NET Framework 4.7.1 veya daha sonraki bir sürümde bu değişiklikle uyumluluk sorunlarıyla karşılaşırsanız, app.config dosyasının <code>&lt;runtime&gt;</code> bölümüne aşağıdaki satırı ekleyerek bu değişikliği devre dışı kabilirsiniz::<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|

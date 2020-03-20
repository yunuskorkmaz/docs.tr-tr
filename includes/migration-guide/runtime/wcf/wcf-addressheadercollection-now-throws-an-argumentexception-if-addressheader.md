---
ms.openlocfilehash: d8c9cec723ec4e57fb4868cc95881be8eb4001b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857233"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>WCF AddressHeaderCollection şimdi bir addressHeader öğesi null ise bir ArgumentException atar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> başlayarak, yapıcı <xref:System.ArgumentException> bir öğe <code>null</code>atar. .NET Framework 4.7 ve önceki sürümlerinde hiçbir istisna atılmaz.|
|Öneri|.NET Framework 4.7.1 veya daha sonraki bir sürümde bu değişiklikle uyumluluk sorunlarıyla karşılaşırsanız, app.config dosyasının <code>&lt;runtime&gt;</code> bölümüne aşağıdaki satırı ekleyerek bu değişikliği devre dışı kabilirsiniz::<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})?displayProperty=nameWithType></li></ul>|

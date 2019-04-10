---
ms.openlocfilehash: 01c0689bbfb102f8f4d9455f9d258e8ea5515d9e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235020"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>MemberDescriptor.Equals yanlış uygulaması

|   |   |
|---|---|
|Ayrıntılar|Asıl uygulamasına <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> yöntemi karşılaştırılan nesneleri iki farklı dize özelliklerinden karşılaştırır: kategori adı ve açıklama dizesi. Karşılaştırılacak düzeltmesidir <xref:System.ComponentModel.MemberDescriptor.Category> ilk nesnenin <xref:System.ComponentModel.MemberDescriptor.Category> ikinci biri ve <xref:System.ComponentModel.MemberDescriptor.Description> ilk için <xref:System.ComponentModel.MemberDescriptor.Description> saniye.|
|Öneri|Uygulamanızın bağımlı değilse <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> bazen döndüren <code>false</code> zaman tanımlayıcıları eşdeğerdir ve hedeflediğiniz .NET Framework 4.6.2 veya sonraki sürümlerde, birkaç seçeneğiniz vardır:<ol><li>Karşılaştırmak için kod değişiklikleri yapabilir <xref:System.ComponentModel.MemberDescriptor.Category> ve <xref:System.ComponentModel.MemberDescriptor.Description> alanlara el ile ek arama <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> yöntemi.</li><li>Bu değişikliğin dışında aşağıdaki değeri app.config dosyasına ekleyerek iyileştirilmiş:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Uygulamanız .NET Framework 4.6.1 hedefliyorsa veya önceki bir sürümü ve .NET Framework 4.6.2 üzerinde çalışıyor veya üzeri ve bu değişiklik etkin istediğiniz, uyumluluk anahtarı ayarlayabileceğiniz <code>false</code> şu değeri app.config dosyasına ekleyerek:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

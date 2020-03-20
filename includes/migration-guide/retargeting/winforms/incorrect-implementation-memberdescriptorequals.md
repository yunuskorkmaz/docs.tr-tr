---
ms.openlocfilehash: 01c0689bbfb102f8f4d9455f9d258e8ea5515d9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859306"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>ÜyeTanımlayıcının yanlış uygulanması.Eşittir

|   |   |
|---|---|
|Ayrıntılar|Yöntemin <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> özgün uygulaması, karşılaştırılan nesnelerden iki farklı dize özelliğini karşılaştırır: kategori adı ve açıklama dizesi. Düzeltme, ilk <xref:System.ComponentModel.MemberDescriptor.Category> nesnenin <xref:System.ComponentModel.MemberDescriptor.Category> ikinci nesneyle, <xref:System.ComponentModel.MemberDescriptor.Description> ilkinini <xref:System.ComponentModel.MemberDescriptor.Description> ikincinesneyle karşılaştırmaktır.|
|Öneri|Uygulamanız <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> bazen tanımlayıcılar eşdeğer <code>false</code> olduğunda geri dönmeye bağlıysa ve .NET Framework 4.6.2 veya daha sonrasını hedefliyorsanız, birkaç seçeneğiniz vardır:<ol><li>Yöntemi çağırmanın yanı <xref:System.ComponentModel.MemberDescriptor.Category> <xref:System.ComponentModel.MemberDescriptor.Description> sıra, alanları ve alanları el ile karşılaştırmak için kod değişiklikleri yapın. <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType></li><li>App.config dosyasına aşağıdaki değeri ekleyerek bu değişikliği devre dışı bırakma:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Uygulamanız .NET Framework 4.6.1 veya daha öncesini hedefliyorsa ve .NET Framework 4.6.2 veya daha sonra <code>false</code> üzerinde çalışıyorsa ve bu değişikliğin etkin olmasını istiyorsanız, app.config dosyasına aşağıdaki değeri ekleyerek uyumluluk anahtarını ayarlayabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

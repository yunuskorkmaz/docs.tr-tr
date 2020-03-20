---
ms.openlocfilehash: e08b78b49cab88d4435d75b04bd446b413a61340
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859373"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current, bir kullanım yan tümcesi çağrıldığında null dönebilir

|   |   |
|---|---|
|Ayrıntılar|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>geri <code>null</code> dönebilir <xref:System.NullReferenceException> ve aşağıdaki koşulların tümü doğruysa ortaya çıkabilir:<ul><li>Bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> döndüren bir yöntemde özelliğin değerini alırsınız</li><li>Nesneyi <xref:System.ServiceModel.OperationContextScope> bir <code>using</code> yan tümcede anında alarsınız.</li><li>Içindeki özelliğin <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> değerini <code>using statement</code>alırsınız. Örnek:</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Öneri|Bu sorunu gidermek için aşağıdakileri yapabilirsiniz:<ul><li>Yeni bir<code>null</code> <xref:System.ServiceModel.OperationContext.Current%2A> nesne olmayan ı anında anımsamak için kodunuzu aşağıdaki gibi değiştirin:</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>.NET Framework 4.6.2'ye en son güncelleştirmeyi yükleyin veya .NET Framework'ün sonraki bir sürümüne yükseltin. Bu, <xref:System.Threading.ExecutionContext> giriş <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> akışını devre dışı kılabilir ve .NET Framework 4.6.1 ve önceki sürümlerde WCF uygulamalarının davranışını geri yükler. Bu davranış yapılandırılabilir; yapılandırma dosyanıza aşağıdaki uygulama ayarını eklemeye eşdeğerdir:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Bu değişiklik istenmeyen bir durumsa ve uygulamanız işlem bağlamları arasında akan yürütme bağlamına bağlıysa, akışını aşağıdaki gibi etkinleştirebilirsiniz:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|

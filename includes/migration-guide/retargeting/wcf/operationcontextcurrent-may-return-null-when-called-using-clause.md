---
ms.openlocfilehash: e08b78b49cab88d4435d75b04bd446b413a61340
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59234966"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current using çağrıldığında null döndürebilir yan tümcesi

|   |   |
|---|---|
|Ayrıntılar|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> döndürebilir <code>null</code> ve <xref:System.NullReferenceException> aşağıdaki koşulların tümü doğruysa, neden olabilir:<ul><li>Değerini alma <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> döndüren bir yöntem özelliğinde bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</li><li>Örneği <xref:System.ServiceModel.OperationContextScope> nesnesine bir <code>using</code> yan tümcesi.</li><li>Değerini alma <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> özelliği içinde <code>using statement</code>. Örneğin:</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Öneri|Bu sorunu gidermek için aşağıdakileri yapabilirsiniz:<ul><li>Şu şekilde yeni bir örneğini oluşturmak için kodunuzu değiştirmeniz olmayan<code>null</code> <xref:System.ServiceModel.OperationContext.Current%2A> nesnesi:</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>.NET Framework 4.6.2 en son güncelleştirmesi veya .NET Framework'ün daha sonraki bir sürüme yükseltin. Bu akışı devre dışı bırakır <xref:System.Threading.ExecutionContext> içinde <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> ve WCF uygulamaları .NET Framework 4.6.1 ve önceki sürümlerinde davranışını geri yükler. Bu davranışı yapılandırılabilir değildir; yapılandırma dosyanız aşağıdaki uygulama ayarı ekleme ile eşdeğerdir:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Bu değişiklik istenmeyen bir durumdur ve işlem bağlamları arasında akan yürütme bağlamı uygulamanızın bağımlı, kendi akış şu şekilde etkinleştirebilirsiniz:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|

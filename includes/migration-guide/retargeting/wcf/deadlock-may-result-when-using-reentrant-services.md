### <a name="deadlock-may-result-when-using-reentrant-services"></a>Kilitlenme desteklemeyeceğini hizmetlerini kullanırken neden olabilir

|   |   |
|---|---|
|Ayrıntılar|Bir kilitlenme hizmeti örneklerini tek bir iş parçacığı aynı anda yürütme kısıtlayan bir desteklemeyeceğini hizmeti neden olabilir. Bu sorunla karşılaşırsanız eğilimlidir Hizmetleri aşağıdaki olacaktır <xref:System.ServiceModel.ServiceBehaviorAttribute> kodlarında:<pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|Öneri|Bu sorunu gidermek için aşağıdakileri yapabilirsiniz:<ul><li>Hizmetin eşzamanlılık modu ayarlamak <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> veya &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;. Örneğin:</li></ul><pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>.NET Framework 4.6.2 en son güncelleştirmesi veya .NET Framework'ün daha sonraki bir sürüme yükseltin. Bu akışı devre dışı bırakır <xref:System.Threading.ExecutionContext> içinde <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>. Bu davranışı yapılandırılabilir değildir; yapılandırma dosyanız aşağıdaki uygulama ayarı ekleme ile eşdeğerdir:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Değerini <code>Switch.System.ServiceModel.DisableOperationContextAsyncFlow</code> hiçbir zaman ayarlanmalıdır <code>false</code> Rentrant Hizmetleri.|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|


---
ms.openlocfilehash: 2f960942bda54505690cbac3151ef74ec0ab5ebb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235611"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>Reentrant hizmetlerini kullanırken kilitlenme oluşabilir

|   |   |
|---|---|
|Ayrıntılar|Kilitlenme, hizmetin örneklerini aynı anda bir yürütme iş parçacığıyla sınırlayan bir Reentrant hizmetiyle sonuçlanabilir. Bu sorunla karşılaşmaya yatkın hizmetlerin <xref:System.ServiceModel.ServiceBehaviorAttribute> kodlarında aşağıdakiler olacaktır:<pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|Öneri|Bu sorunu gidermek için aşağıdakileri yapabilirsiniz:<ul><li>Hizmetin eşzamanlılık modunu <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> veya &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;'a ayarlayın. Örnek:</li></ul><pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>.NET Framework 4.6.2'ye en son güncelleştirmeyi yükleyin veya .NET Framework'ün sonraki bir sürümüne yükseltin. <xref:System.Threading.ExecutionContext> Bu, in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>akışını devre dışı kılabilir. Bu davranış yapılandırılabilir; yapılandırma dosyanıza aşağıdaki uygulama ayarını eklemeye eşdeğerdir:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Değeri asla <code>Switch.System.ServiceModel.DisableOperationContextAsyncFlow</code> Rentrant hizmetleri <code>false</code> için ayarlanamamalıdır.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|

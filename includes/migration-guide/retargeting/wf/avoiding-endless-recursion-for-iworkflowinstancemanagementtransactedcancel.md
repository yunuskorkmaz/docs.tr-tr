---
ms.openlocfilehash: ab9431780422dfece5dcf8007d13e6d584f5118f
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96477428"
---
### <a name="avoiding-endless-recursion-for-iworkflowinstancemanagementtransactedcancel-and-iworkflowinstancemanagementtransactedterminate"></a>IWorkflowInstanceManagement. TransactedCancel ve IWorkflowInstanceManagement. TransactedTerminate için sonsuz özyineleme önleme

#### <a name="details"></a>Ayrıntılar

<xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedCancel%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedTerminate%2A?displayProperty=nameWithType> Bir iş akışı hizmet örneğini iptal etmek veya sonlandırmak için veya API 'leri kullanırken veya işlerken, iş akışı örneği, `Workflow` isteği işlemenin bir parçası olarak hizmet örneğini kalıcı hale getirmeye çalıştığında, sonsuz özyineleme nedeniyle bir yığın taşmasıyla karşılaşabilir. Bu sorun, iş akışı örneği başka bir hizmetin tamamlanması için başka bir bekleyen WCF isteğinin beklediği bir durumdaysa oluşur. `TransactedCancel`Ve `TransactedTerminate` işlemleri, iş akışı hizmeti örneği için sıraya alınan iş öğeleri oluşturur. Bu iş öğeleri, isteğin işlenmesinin bir parçası olarak yürütülmez `TransactedCancel/TransactedTerminate` . İş akışı hizmeti örneği, diğer bekleyen WCF isteğinin tamamlanmasını beklerken meşgul olduğundan, oluşturulan iş öğesi sıraya alınır. `TransactedCancel/TransactedTerminate`İşlem tamamlanır ve denetim istemciye geri döndürülür. İşlemle ilişkili işlem `TransactedCancel/TransactedTerminate` işlemeye çalıştığında, iş akışı hizmeti örneğinin durumunu kalıcı hale getirmek gerekir. Ancak `WCF` örnek için bekleyen bir istek olduğundan, Iş akışı çalışma zamanı iş akışı hizmeti örneğini sürdüremiyor ve sonsuz bir özyineleme döngüsü yığın taşmasına neden olabilir. `TransactedCancel` `TransactedTerminate` Yalnızca bellekte bir iş öğesi oluşturduğundan, bir işlemin mevcut olması herhangi bir etkiye sahip değildir. İşlemin geri alınması iş öğesini atlamaz. .NET Framework 4.7.2 ' den başlayarak bu sorunu gidermek için, `AppSetting` `web.config/app.config` iş akışı hizmetine eklenebilecek ve bu işlemi ve için işlemleri yoksaydığını bildiren bir sunduk `TransactedCancel` `TransactedTerminate` . Bu işlem, iş akışı örneğinin kalıcı hale getirilmeksizin işlemin çalışmasına izin verir. Bu özelliğin AppSetting 'i olarak adlandırılmıştır `microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate` . Değeri, `true` işlemin yoksayılması gerektiğini belirtir ve bu nedenle yığın taşmasını önler. Bu AppSetting 'in varsayılan değeri, bu `false` nedenle mevcut iş akışı hizmet örnekleri etkilenmez.

#### <a name="suggestion"></a>Öneri

<xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>Bir iş akışı örneğini iptal etmeyi veya sonlandırmayı denerken, AppFabric veya başka bir istemci kullanıyorsanız ve iş akışı hizmet örneğinde bir yığın taşmasıyla karşılaşdıysanız, `<appSettings>` iş akışı hizmeti için web.config/app.config dosyasının bölümüne aşağıdakileri ekleyebilirsiniz:

<pre><code class="lang-xml">&lt;add key=&quot;microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate&quot; value=&quot;true&quot;/&gt;&#13;&#10;</code></pre>

Sorunla karşılaşmayın, bunu yapmanız gerekmez.

| Ad    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

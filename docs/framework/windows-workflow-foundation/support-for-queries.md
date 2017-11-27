---
title: "Sorgular için destek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4f338f9ae5cc6967885d0518eb573d9f9535fc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="support-for-queries"></a>Sorgular için destek
SQL iş akışı örneği deposuna iyi bilinen bir özellik kümesi depolama alanına kaydeder. Kullanıcılar için Sorgulayabileceğiniz çıkarak bu özellikleri. Aşağıdaki listede bu iyi bilinen özelliklerini içerir:  
  
-   **Site adı.** Hizmet içeren Web sitesi adı.  
  
-   **Göreli uygulama yolu.** Web sitesi göre uygulamanın yolu.  
  
-   **Göreli hizmet yolu.** Hizmet uygulaması göreli yolu.  
  
-   **Hizmet adı.** Hizmetin adı.  
  
-   **Hizmet Namespace.** Hizmetin kullandığı ad alanının adı.  
  
-   **Geçerli makineye.**  
  
-   **Son makine**. İş akışı hizmeti örneği en son ne zaman çalıştırıldığı bilgisayar.  
  
> [!NOTE]
>  İş akışı hizmeti ana bilgisayarı kullanarak kendini barındıran senaryolar için yalnızca son dört özellikleri doldurulur. İş akışı uygulama senaryoları için yalnızca en son özellik doldurulur.  
  
 İş akışı çalışma zamanı ilk üç özellikleri için değer sağlıyor. İş akışı hizmeti ana bilgisayarı için değer sağlıyor **askıya neden** özelliği. SQL iş akışı örneği deposuna kendisi için değer sağlıyor **son güncelleştirilen makine** özelliği.  
  
 SQL iş akışı örneği depolama özelliğini de Kalıcılık veritabanı ve belirttiğiniz değerleri depolamak istediğiniz özel özellikler sorgularda kullanmak istediğiniz belirtmenize olanak sağlar. Özel promosyonlar hakkında daha fazla bilgi için bkz: [deposu genişletilebilirlik](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).  
  
## <a name="views"></a>Görünümler  
 Örnek deposuna aşağıdaki görünümleri içerir. Bkz: [Kalıcılık veritabanı şeması](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) daha ayrıntılı bilgi için.  
  
### <a name="the-instances-view"></a>Örnek görünümü  
 Örnekleri görünüm aşağıdaki alanları içerir:  
  
1.  **Kimliği**  
  
2.  **PendingTimer**  
  
3.  **CreationTime**  
  
4.  **LastUpdatedTime**  
  
5.  **ServiceDeploymentId**  
  
6.  **SuspensionExceptionName**  
  
7.  **SuspensionReason**  
  
8.  **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **Isınitialized**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>ServiceDeployments görünümü  
 ServiceDeployments görünüm aşağıdaki alanları içerir:  
  
1.  **SiteName**  
  
2.  **RelativeServicePath**  
  
3.  **RelativeApplicationPath**  
  
4.  **ServiceName**  
  
5.  **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>InstancePromotedProperties görünümü  
 InstancePromotedProperties görünüm aşağıdaki alanları içerir. Yükseltilen özellikleri hakkında daha fazla bilgi için bkz: [deposu genişletilebilirlik](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) konu.  
  
1.  **Örnek kimliği**  
  
2.  **EncodingOption**  
  
3.  **PromotionName**  
  
4.  **Değer #** (alanlardan çeşitli **Value1** için **Value64**).

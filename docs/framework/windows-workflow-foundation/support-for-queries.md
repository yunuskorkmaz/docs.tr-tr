---
title: Sorgu Desteği
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641521"
---
# <a name="support-for-queries"></a>Sorgu Desteği
SQL iş akışı örneği Store iyi bilinen özellikler kümesi deposuna kaydeder. Kullanıcılar için sorgulayabilir örnekleri, bu özellikleri bağlı. Aşağıdaki liste, bazı iyi bilinen bu özellikleri içerir:  
  
- **Site adı.** Hizmeti içeren Web sitesinin adı.  
  
- **Uygulama göreli yolu.** Uygulamanın Web sitesini göreli yolu.  
  
- **Hizmet göreli yolu.** Hizmet uygulaması göreli yolu.  
  
- **Hizmet adı.** Hizmetin adı.  
  
- **Hizmet Namespace.** Hizmetin kullandığı ad alanının adı.  
  
- **Geçerli makine.**  
  
- **Son makine**. İş akışı hizmet örneği son kez çalıştırıldığı bir bilgisayar.  
  
> [!NOTE]
>  İş akışı hizmeti konağı kullanarak şirket içinde barındırılan senaryoları için yalnızca son dört özellikleri doldurulur. İş akışı uygulama senaryoları için yalnızca en son özellik doldurulur.  
  
 İş akışı çalışma zamanı ilk üç özellikleri için değer sağlıyor. İş akışı hizmeti konağı için değer sağlayan **askıya alma nedeni** özelliği. SQL iş akışı örneği Store kendisi için değer sağlıyor **son güncelleştirilen makine** özelliği.  
  
 SQL iş akışı örneği Store özellik de Kalıcılık veritabanı ve belirttiğiniz değerleri depolamak kullanmak istediğiniz özel özellikler sorgularda kullanmak istediğinizi belirtmek olanak sağlar. Özel promosyonlar hakkında daha fazla bilgi için bkz: [Store genişletilebilirlik](store-extensibility.md).  
  
## <a name="views"></a>Görünümler  
 Örnek depo, aşağıdaki görünümleri içerir. Bkz: [Kalıcılık veritabanı şeması](persistence-database-schema.md) daha ayrıntılı bilgi için.  
  
### <a name="the-instances-view"></a>Örnekleri görüntüle  
 Örnekler görünümü, aşağıdaki alanları içerir:  
  
1. **Kimlik**  
  
2. **PendingTimer**  
  
3. **CreationTime**  
  
4. **lastUpdatedTime**  
  
5. **ServiceDeploymentId**  
  
6. **SuspensionExceptionName**  
  
7. **SuspensionReason**  
  
8. **ActiveBookmarks**  
  
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
  
### <a name="the-servicedeployments-view"></a>ServiceDeployments görüntüle  
 ServiceDeployments görünümü, aşağıdaki alanları içerir:  
  
1. **Site adı**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **serviceName**  
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>InstancePromotedProperties görüntüle  
 InstancePromotedProperties görünümü, aşağıdaki alanları içerir. Yükseltilen özellikleri hakkında ayrıntılı bilgi için bkz. [Store genişletilebilirlik](store-extensibility.md) konu.  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **PromotionName**  
  
4. **Değer #** (alanlardan bir dizi **Value1** için **Value64**).

---
title: Sorgu Desteği
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: e281b5ae7a41bd282f8e7c7eb9db6f99ef5487f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948934"
---
# <a name="support-for-queries"></a>Sorgu Desteği
SQL Iş akışı örneği deposu depodaki bir dizi iyi bilinen özelliği kaydeder. Kullanıcılar, bu özelliklere göre örnekleri sorgulayabilir. Aşağıdaki listede, bu iyi bilinen özelliklerden bazıları yer almaktadır:  
  
- **Site adı.** Hizmeti içeren Web sitesinin adı.  
  
- **Göreli uygulama yolu.** Web sitesine göre uygulamanın yolu.  
  
- **Göreli hizmet yolu.** Uygulamaya göre hizmetin yolu.  
  
- **Hizmet adı.** Hizmetin adı.  
  
- **Hizmet ad alanı.** Hizmetin kullandığı ad alanının adı.  
  
- **Geçerli makine.**  
  
- **Son makine**. İş akışı hizmeti örneğinin son çalıştırıldığı bilgisayar.  
  
> [!NOTE]
> Iş akışı hizmeti ana bilgisayarı kullanan şirket içinde barındırılan senaryolar için yalnızca son dört Özellik doldurulur. Iş akışı uygulama senaryolarında yalnızca son özellik doldurulur.  
  
 İş akışı çalışma zamanı, ilk üç özellik için değerler sağlar. İş akışı hizmeti Konağı, **askıya alma nedeni** özelliğinin değerini sağlar. SQL Iş akışı örneği deposunun kendisi, **son güncelleştirilmiş makine** özelliği için değerler sağlar.  
  
 SQL Iş akışı örneği deposu özelliği ayrıca, değerlerini Kalıcılık veritabanında depolamak istediğiniz ve sorgularda kullanmak istediğiniz özel özellikleri belirtmenize imkan tanır. Özel promosyonlar hakkında daha fazla bilgi için bkz. [depolama genişletilebilirliği](store-extensibility.md).  
  
## <a name="views"></a>Görünümler  
 Örnek deposu aşağıdaki görünümleri içerir. Daha fazla ayrıntı için bkz. [Kalıcılık veritabanı şeması](persistence-database-schema.md) .  
  
### <a name="the-instances-view"></a>Örnekler görünümü  
 Örnekler görünümü aşağıdaki alanları içerir:  
  
1. **Kimlik**  
  
2. **PendingTimer**  
  
3. **CreationTime**  
  
4. **LastUpdatedTime**  
  
5. **ServiceDeploymentId**  
  
6. **SuspensionExceptionName**  
  
7. **SuspensionReason**  
  
8. **Activeyer Işaretleri**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **Isaskıya alındı**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>Servicedağıtımlar görünümü  
 Servicedağıtımlar görünümü aşağıdaki alanları içerir:  
  
1. **SiteName**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **HizmetAdı**  
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>InstancePromotedProperties görünümü  
 InstancePromotedProperties görünümü aşağıdaki alanları içerir. Yükseltilen özelliklerle ilgili ayrıntılar için bkz. [depolama genişletilebilirliği](store-extensibility.md) konusu.  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **PromotionName**  
  
4. **Değer #** ( **değer1** ile **Value64**arasında bir alan aralığı).

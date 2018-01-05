---
title: "Kalıcılık veritabanı şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc758f85b4f8b0bec5c00979f42d3f7b2ea7b182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-database-schema"></a>Kalıcılık veritabanı şeması
Bu konuda SQL iş akışı örneği mağaza tarafından desteklenen ortak görünümler açıklanmaktadır.  
  
## <a name="instances-view"></a>Örnekleri görüntüleyin  
 **Örnekleri** görünümü veritabanındaki tüm iş akışı örnekleri hakkında genel bilgiler içerir.  
  
|Sütun adı|Sütun türü|Açıklama|  
|-----------------|-----------------|-----------------|  
|örnek kimliği|Benzersiz tanımlayıcı|Bir iş akışı örneği kimliği.|  
|PendingTimer|DateTime|İş akışı bir gecikme faaliyete engellenir ve Zamanlayıcı dolduktan sonra sürdürülecek gösterir. Bu değer iş akışı süresi dolacak şekilde bir süreölçer bekleyen engellenmeyen null olabilir.|  
|CreationTime|DateTime|İş akışının ne zaman oluşturulduğunu gösterir.|  
|LastUpdatedTime|DateTime|İş akışı veritabanına kalıcı son zamanı gösterir.|  
|ServiceDeploymentId|BigInt|[ServiceDeployments] görüntülemek için yabancı anahtar olarak görev yapar. Geçerli iş akışı örneği web barındırılan bir hizmet örneği varsa, bu sütun NULL olarak ayarlanmış bir değer, aksi takdirde vardır.|  
|SuspensionExceptionName|Nvarchar(450)|İş akışını askıya almak neden (örneğin InvalidOperationException) özel durum türünü belirtir.|  
|SuspensionReason|nvarchar(max)|İş akışı örneği neden askıya alındı gösterir. Askıya almak örnek bir özel durum neden olursa, bu sütun özel durumla ilgili ileti içerir.<br /><br /> Örnek el ile askıya alınırsa, bu sütun örneği askıya almak için kullanıcı tarafından belirtilen neden içerir.|  
|ActiveBookmarks|nvarchar(max)|İş akışı örneği boş ise, bu özellik örneği üzerinde engellendi hangi yer işaretleri gösterir. Örnek boş değilse, bu sütun NULL olur.|  
|CurrentMachine|Nvarchar(128)|Bilgisayarın adını şu anda iş akışı örneği bellekte yüklü olduğunu gösterir.|  
|LastMachine|Nvarchar(450)|İş akışı örneği yüklenen son bilgisayarı gösterir.|  
|ExecutionStatus|Nvarchar(450)|Geçerli iş akışı yürütme durumunu gösterir. Olası durumlar şunlardır **Executing**, **boşta**, **kapalı**.|  
|Isınitialized|bit|İş akışı örneği başlatılmış olup olmadığını gösterir. Başlatılan iş akışı örneği en az bir kez kalıcı bir iş akışı örneği ' dir.|  
|IsSuspended|bit|İş akışı örneği askıya olup olmadığını gösterir.|  
|IsCompleted|bit|İş akışı örneği yürütülmesi tamamlandı olup olmadığını gösterir. **Not:** IIf **InstanceCompletionAction** özelliği ayarlanmış **DeleteAll**, örnekleri tamamlanmasından sonra görünümünden kaldırılır.|  
|EncodingOption|Mini tamsayı|Veri özellikleri serileştirmek için kullanılan kodlama açıklar.<br /><br /> -0 – hiçbir kodlama<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|varbinary(max)|Örnek yüklendiğinde, geri iş akışı çalışma zamanı sağlanan serileştirilmiş örnek veri özelliklerini içerir.<br /><br /> Her bir ilkel özellik hiçbir özel derlemeler blob serisini kaldırmak için gerekli olduğu anlamına gelir yerel bir CLR türü ' dir.|  
|WriteOnlyPrimitiveDataProperties|varbinary(max)|Örnek yüklendiğinde, geri iş akışı çalışma zamanı sağlanmayan serileştirilmiş örnek veri özellikleri içerir.<br /><br /> Her bir ilkel özellik hiçbir özel derlemeler blob serisini kaldırmak için gerekli olduğu anlamına gelir yerel bir CLR türü ' dir.|  
|ReadWriteComplexDataProperties|varbinary(max)|Örnek yüklendiğinde, geri iş akışı çalışma zamanı için sağlanan serileştirilmiş örnek veri özelliklerini içerir.<br /><br /> Seri kaldırıcı bu blob depolanan tüm nesne türlerinin bilgi gerektirir.|  
|WriteOnlyComplexDataProperties|varbinary(max)|Örnek yüklendiğinde, geri iş akışı çalışma zamanı sağlanmayan serileştirilmiş örnek veri özellikleri içerir.<br /><br /> Seri kaldırıcı bu blob depolanan tüm nesne türlerinin bilgi gerektirir.|  
|IdentityName|nvarchar(max)|İş akışı tanımı adı.|  
|IdentityPackage|nvarchar(max)|İş akışı (derleme adı gibi) oluşturulduğunda verilen paket bilgileri.|  
|Derleme|BigInt|İş akışı sürümünün yapı numarası.|  
|Ana|BigInt|İş akışı sürümü ana sayısı.|  
|Küçük|BigInt|İş akışı sürümü küçük sayısı.|  
|Gözden geçirme|BigInt|İş akışı sürümü düzeltme sayısı.|  
  
> [!CAUTION]
>  **Örnekleri** görünümü silme tetikleyicisi de içerir. Uygun izinlere sahip kullanıcılar, iş akışı örnekleri veritabanından zorla kaldıracak bu görünüm delete deyimini yürütebilir. İş akışı çalışma zamanı altında bir örnekten silme istenmeyen sonuçlara neden olabilir çünkü son çare olarak doğrudan görünümünden silme öneririz. Bunun yerine, iş akışı örneği yönetim uç noktası örneği sonlandırılacak iş akışı çalışma zamanı için kullanın. Çok sayıda örneği görünümden silmek istiyorsanız, bu örnekleri üzerinde çalışan hiçbir etkin çalışma zamanları vardır emin olun.  
  
## <a name="servicedeployments-view"></a>ServiceDeployments görünümü  
 **ServiceDeployments** görünümü tüm Web dağıtım bilgilerini içerir (IIS / edildi) iş akışı hizmetleri barındırılan. Web barındırılan her iş akışı örneği içerecek bir **ServiceDeploymentId** bu görünümde bir satır için başvuruyor.  
  
|Sütun adı|Sütun türü|Açıklama|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|Bu görünüm için birincil anahtar.|  
|SiteName|nvarchar(max)|İş akışı hizmeti içeren sitenin adını temsil eder (örneğin **varsayılan Web sitesi**).|  
|RelativeServicePath|nvarchar(max)|İş akışı hizmeti noktaları site göre sanal yolu temsil eder. (örn.  **/app1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|nvarchar(max)|İş akışı hizmeti içeren bir uygulama için işaret site göre sanal yolu temsil eder. (örneğin **sitesinde/App1 adlı**).|  
|ServiceName|nvarchar(max)|İş akışı hizmeti adını temsil eder. (örneğin **PurchaseOrderService**).|  
|ServiceNamespace|nvarchar(max)|İş akışı hizmeti ad alanı temsil eder. (örneğin **Şirketim**).|  
  
 ServiceDeployments görünüm da Delete tetikleyicisi içeriyor. Uygun izinlere sahip kullanıcılar ServiceDeployment girişler veritabanından kaldırmak için bu görünümü delete deyimini yürütebilir. Aşağıdakilere dikkat edin:  
  
1.  Bu işlemi gerçekleştirmeden önce tüm veritabanını kilitlenip gerekir beri bu görünümden girdileri silme maliyetlidir. Bu iş akışı örneği mevcut olmayan ServiceDeployment girişe burada başvurabileceğiniz senaryo önlemek gereklidir. Kapalı kaldıkları yalnızca sırasında bu görünümden silme / bakım pencereleri.  
  
2.  Tüm girişleri tarafından başvuruluyor ServiceDeployment satır silme dener **örnekleri** görünüm yok op neden olur. Yalnızca sıfır başvuruları ServiceDeployment satırlarla silebilirsiniz.  
  
## <a name="instancepromotedproperties-view"></a>InstancePromotedProperties görünümü  
 **InstancePromotedProperties** görünümü kullanıcı tarafından belirtilen tüm yükseltilen özellikleri için bilgiler içerir. Yükseltilen bir özellik olan bir kullanıcı örneği almak için sorguları kullanabilirsiniz birinci sınıf bir özellik olarak çalışır.  Örneğin, bir kullanıcı her zaman bir sırada maliyetini depolayan bir PurchaseOrder yükseltmenin ekleyebilirsiniz **Value1** sütun. Bu kullanıcı sorgulamak için belirli bir değere maliyeti aşıyor tüm satın alma siparişleri etkinleştirir.  
  
|Sütun türü|Sütun türü|Açıklama|  
|-|-|-|  
|örnek kimliği|Benzersiz tanımlayıcı|İş akışı örneği kimliği|  
|EncodingOption|Mini tamsayı|Yükseltilen ikili özellikleri serileştirmek için kullanılan kodlama açıklar.<br /><br /> -0 – hiçbir kodlama<br />-1 – GZipStream|  
|PromotionName|nvarchar(400)|Bu örnekle ilişkili yükseltme adı. PromotionName genel sütunları bu satırda içerik eklemek için gereklidir.<br /><br /> Örneğin, bir PromotionName PurchaseOrder Value1 sırasını maliyetini içerir, Value2 siparişin müşterinin adını içerir, müşteri vb. adresini değeri 3 içerir gösterebilir.|  
|Değer [1-32]|SqlVariant|Değer [1-32] SqlVariant sütununda depolanan değerleri içerir. Tek bir yükseltme 32'den fazla SqlVariants içeremez.|  
|Değer [33-64]|varbinary(max)|Değer [33-64] serileştirilmiş değerlerini içerir. Örneğin, Value33 bir JPEG, satın alınan bir maddenin içerebilir. Tek bir yükseltme 32'den fazla ikili özelliklerini içeremez.|  
  
 Şemaya bağlı, kullanıcıların bu görünüm sorguları en iyi duruma getirmek için bir veya daha fazla sütun dizinleri ekleyebileceğiniz anlamına gelir InstancePromotedProperties görünümdür.  
  
> [!NOTE]
>  Bir dizini oluşturulmuş görünüm daha fazla depolama alanı gerektirir ve ek işlem yükü ekler. Lütfen [SQL Server 2008 dizin oluşturulmuş görünümler ile performans geliştirme](http://go.microsoft.com/fwlink/?LinkId=179529) daha fazla bilgi için.

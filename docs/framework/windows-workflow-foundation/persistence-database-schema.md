---
title: Kalıcılık Veritabanı Şeması
ms.date: 03/30/2017
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
ms.openlocfilehash: 65d8b2f7a6283d65823e1a186239d398ee4a530a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038329"
---
# <a name="persistence-database-schema"></a>Kalıcılık Veritabanı Şeması
Bu konuda, SQL Iş akışı örnek deposu tarafından desteklenen genel görünümler açıklanmaktadır.  
  
## <a name="instances-view"></a>Örnek görünümü  
 **Örnekler** görünümü veritabanındaki tüm Iş akışı örnekleri hakkında genel bilgiler içerir.  
  
|Sütun adı|Sütun türü|Açıklama|  
|-----------------|-----------------|-----------------|  
|InstanceId|Benzersiz tanımlayıcı|Bir iş akışı örneğinin KIMLIĞI.|  
|PendingTimer|DateTime|Bir gecikme etkinliğinde iş akışının engellenip engellenmediğini ve Zamanlayıcının süresi dolduktan sonra devam edecek olduğunu gösterir. İş akışı, bir zamanlayıcının süre sonu beklenememesi durumunda bu değer null olabilir.|  
|CreationTime|DateTime|İş akışının ne zaman oluşturulduğunu gösterir.|  
|LastUpdatedTime|DateTime|İş akışının veritabanına son ne zaman kalıcı olduğunu gösterir.|  
|ServiceDeploymentId|BigInt|[Servicedağıtımlar] görünümüne yabancı anahtar işlevi görür. Geçerli iş akışı örneği, Web 'de barındırılan bir hizmetin bir örneğidir, bu sütunda bir değer bulunur, aksi takdirde NULL olarak ayarlanır.|  
|SuspensionExceptionName|Nvarchar (450)|İş akışının askıya alınmasına neden olan özel durumun türünü (örn. InvalidOperationException) belirtir.|  
|SuspensionReason|Nvarchar (max)|Iş akışı örneğinin neden askıya alındığını gösterir. Bir özel durum örneğin askıya alınmasına neden olursa, bu sütun özel durumla ilişkili iletiyi içerir.<br /><br /> Örnek el ile askıya alınmışsa, bu sütun örneği askıya almak için Kullanıcı tarafından belirtilen nedeni içerir.|  
|Activeyer Işaretleri|Nvarchar (max)|İş akışı örneği boşta ise, bu özellik örneğin hangi yer işaretlerinin engellendiğini gösterir. Örnek boşta değilse, bu sütun NULL olur.|  
|CurrentMachine|Nvarchar (128)|Bilgisayar adının şu anda bellekte yüklü iş akışı örneği olduğunu gösterir.|  
|LastMachine|Nvarchar (450)|İş akışı örneğini yükleyen son bilgisayarı gösterir.|  
|ExecutionStatus|Nvarchar (450)|Iş akışının geçerli yürütme durumunu gösterir. Olası durumlar **yürütme**, **Boşta**ve **kapalı**durumlarını içerir.|  
|IsInitialized|bit|İş akışı örneğinin başlatılmış olup olmadığını gösterir. Başlatılmış bir iş akışı örneği, en az bir kez kalıcı olan bir iş akışı örneğidir.|  
|Isaskıya alındı|bit|İş akışı örneğinin askıya alınıp alınmadığını gösterir.|  
|IsCompleted|bit|Iş akışı örneğinin yürütülmesinin tamamlanıp bitmediğini belirtir. **Not:**  IIF, **InstanceCompletionAction** özelliği **DeleteAll**olarak ayarlanmış, örnekler tamamlandıktan sonra görünümden kaldırılır.|  
|EncodingOption|Iç|Veri özelliklerini seri hale getirmek için kullanılan kodlamayı açıklar.<br /><br /> -0 – kodlama yok<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|Varbinary (max)|Örnek yüklendiğinde iş akışı çalışma zamanına geri sağlanacak serileştirilmiş örnek veri özelliklerini içerir.<br /><br /> Her ilkel özellik yerel bir CLR türüdür ve bu, Blobun serisini kaldırmak için özel derlemeler gerekmediği anlamına gelir.|  
|WriteOnlyPrimitiveDataProperties|Varbinary (max)|Örnek yüklendiğinde iş akışı çalışma zamanına geri sağlanmayan serileştirilmiş örnek veri özelliklerini içerir.<br /><br /> Her ilkel özellik yerel bir CLR türüdür ve bu, Blobun serisini kaldırmak için özel derlemeler gerekmediği anlamına gelir.|  
|ReadWriteComplexDataProperties|Varbinary (max)|Örnek yüklendiğinde iş akışı çalışma zamanına geri sağlanacak serileştirilmiş örnek veri özelliklerini içerir.<br /><br /> Seri hale getirici, bu bloba depolanan tüm nesne türleri hakkında bilgi gerektirir.|  
|WriteOnlyComplexDataProperties|Varbinary (max)|Örnek yüklendiğinde iş akışı çalışma zamanına geri sağlanmayan serileştirilmiş örnek veri özelliklerini içerir.<br /><br /> Seri hale getirici, bu bloba depolanan tüm nesne türleri hakkında bilgi gerektirir.|  
|IdentityName|Nvarchar (max)|İş akışı tanımının adı.|  
|IdentityPackage|Nvarchar (max)|İş akışı oluşturulduğunda verilen paket bilgileri (örneğin, derleme adı).|  
|Yapı|BigInt|İş akışı sürümünün yapı numarası.|  
|Ana|BigInt|İş akışı sürümünün ana numarası.|  
|İkincil|BigInt|İş akışı sürümünün küçük sayısı.|  
|Gözden geçirme|BigInt|İş akışı sürümünün düzeltme numarası.|  
  
> [!CAUTION]
> **Örnekler** görünümü bir Delete tetikleyicisi de içerir. Uygun izinlere sahip kullanıcılar, iş akışı örneklerini veritabanından zorla kaldıracak bu görünüme karşı delete deyimlerini yürütebilir. İş akışı çalışma zamanının altındaki bir örneği silmek istenmeden sonuçlara neden olabileceğinden, doğrudan görünümden yalnızca son çare olarak silinmesini öneririz. Bunun yerine, iş akışı çalışma zamanının örneği sonlandırmayı sağlamak için Iş akışı örneği yönetim uç noktasını kullanın. Görünümden çok sayıda örnek silmek istiyorsanız, bu örneklerde çalışan etkin çalışma zamanları olmadığından emin olun.  
  
## <a name="servicedeployments-view"></a>Servicedağıtımlar görünümü  
 **Servicedağıtımlar** görünümü tüm Web (IIS/WAS) barındırılan iş akışı hizmetleri için dağıtım bilgilerini içerir. Web 'de barındırılan her iş akışı örneği, bu görünümdeki bir satıra başvuran bir **ServiceDeploymentId** içerir.  
  
|Sütun adı|Sütun türü|Açıklama|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|Bu görünüm için birincil anahtar.|  
|Site adı|Nvarchar (max)|İş akışı hizmetini içeren sitenin adını temsil eder (örneğin, **varsayılan Web sitesi**).|  
|RelativeServicePath|Nvarchar (max)|İş akışı hizmetine işaret eden siteyle ilişkili sanal yolu temsil eder. DomainName.  **/APP1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|Nvarchar (max)|İş akışı hizmetini içeren bir uygulamayı işaret eden siteyle ilişkili sanal yolu temsil eder. (ör. **/APP1**).|  
|ServiceName|Nvarchar (max)|İş akışı hizmetinin adını temsil eder. (örn. **PurchaseOrderService**).|  
|ServiceNamespace|Nvarchar (max)|İş akışı hizmetinin ad alanını temsil eder. (ör. **şirketim**).|  
  
 Servicedağıtımlar görünümü bir silme tetikleyicisi de içerir. Uygun izinlere sahip kullanıcılar, Service Deployment girişlerini veritabanından kaldırmak için bu görünüme karşı delete deyimlerini yürütebilir. Aşağıdakilere dikkat edin:  
  
1. Bu işlemi gerçekleştirmeden önce tüm veritabanının kilitlenmesi gerektiğinden, bu görünümden girişlerin silinmesi maliyetlidir. Bu, bir iş akışı örneğinin var olmayan bir ServiceDeployment girdisine başvurabileceği senaryoya engel olmak için gereklidir. Bu görünümden yalnızca saat/bakım pencereleri sırasında silin.  
  
2. **Örnekler** görünümündeki girişler tarafından başvurulan bir ServiceDeployment satırını silme girişimleri, işlem olmadan sonuçlanır. ServiceDeployment satırlarını yalnızca sıfır başvuru ile silebilirsiniz.  
  
## <a name="instancepromotedproperties-view"></a>InstancePromotedProperties görünümü  
 **InstancePromotedProperties** görünümü, Kullanıcı tarafından belirtilen tüm yükseltilen özelliklerle ilgili bilgiler içerir. Yükseltilen bir özellik, bir kullanıcının örnekleri almak için sorgularda kullanabileceği birinci sınıf bir özellik olarak çalışır.  Örneğin, bir Kullanıcı her zaman **değer1** sütununda bir siparişin maliyetini depolayan bir PurchaseOrder yükseltmesi ekleyebilir. Bu, bir kullanıcının maliyeti belirli bir değeri aşan tüm satın alma siparişlerinin sorgulanbilmesini sağlar.  
  
|Sütun türü|Sütun türü|Açıklama|  
|-|-|-|  
|InstanceId|Benzersiz tanımlayıcı|Iş akışı örneğinin KIMLIĞI|  
|EncodingOption|Iç|Yükseltilen ikili özellikleri seri hale getirmek için kullanılan kodlamayı açıklar.<br /><br /> -0 – kodlama yok<br />-1 – GZipStream|  
|PromotionName|Nvarchar (400)|Bu örnekle ilişkili yükseltmenin adı. Bu satırdaki genel sütunlara bağlam eklemek için PromotionName gereklidir.<br /><br /> Örneğin, PurchaseOrder 'nin PromotionName değeri, değer1 'in sipariş maliyetini içerdiğini, değer2 'nin siparişi veren müşterinin adını içerdiğini, 1. değerin müşterinin adresini içerdiğini vb. gösterir.|  
|Değer [1-32]|SqlVariant|[1-32] değeri, bir SQLVARIANT sütununda depolanabilecek değerler içeriyor. Tek bir promosyon 32 taneden fazla SQLVARIANT içeremez.|  
|Değer [33-64]|Varbinary (max)|[33-64] değeri serileştirilmiş değerler içeriyor. Örneğin, Value33, satın alınan bir öğenin JPEG içerebilir. Tek bir promosyon 32 taneden fazla ikili özellik içeremez|  
  
 InstancePromotedProperties Görünümü şemaya bağlıdır, bu da kullanıcıların bu görünüme yönelik sorguları iyileştirmek için bir veya daha fazla sütuna dizinler ekleyebileceği anlamına gelir.  
  
> [!NOTE]
> Dizinli bir görünüm daha fazla depolama alanı gerektirir ve ek işleme yükü ekler. Daha fazla bilgi için lütfen [SQL Server 2008 dizinli görünümlerle performansı artırma](https://go.microsoft.com/fwlink/?LinkId=179529) bölümüne bakın.

---
title: Kalıcılık Veritabanı Şeması
ms.date: 03/30/2017
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
ms.openlocfilehash: 38df4b3d629840f1b5def2eafa0d074a2b2397a2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331071"
---
# <a name="persistence-database-schema"></a>Kalıcılık Veritabanı Şeması
Bu konuda, SQL iş akışı örneği Store tarafından desteklenen ortak görünümler açıklanmaktadır.  
  
## <a name="instances-view"></a>Örnekleri görüntüle  
 **Örnekleri** görünümü veritabanındaki tüm iş akışı örnekleri hakkında genel bilgiler içerir.  
  
|Sütun adı|Sütun türü|Açıklama|  
|-----------------|-----------------|-----------------|  
|InstanceId|Benzersiz tanımlayıcı|Bir iş akışı örneği kimliği.|  
|PendingTimer|DateTime|İş akışı bir gecikme faaliyete engellenir ve Zamanlayıcı dolduktan sonra devam edecek gösterir. Bu değer, bekleme süresi dolacak şekilde bir zamanlayıcıyı temel iş akışı engellenip engellenmediğini null olabilir.|  
|CreationTime|DateTime|İş akışının ne zaman oluşturulduğunu gösterir.|  
|LastUpdatedTime|DateTime|İş akışı veritabanına yazılan son zamanı gösterir.|  
|ServiceDeploymentId|BigInt|[ServiceDeployments] görünümü için yabancı anahtar görevi görür. Geçerli iş akışı örneği web barındırılan hizmetinin bir örneği ise, bu sütun NULL olarak ayarlanmış bir değer, aksi takdirde sahiptir.|  
|SuspensionExceptionName|Nvarchar(450)|Neden iş akışını askıya almak (örneğin InvalidOperationException) özel durumun türünü gösterir.|  
|SuspensionReason|nvarchar(max)|Neden iş akışı örneği askıya alındı gösterir. Askıya almak örnek bir özel durum neden olursa, bu sütun özel durumla ilişkili ileti içerir.<br /><br /> Örnek el ile askıya alınırsa, bu sütun kullanıcı tarafından belirtilen nedenini örneği askıya alma içerir.|  
|ActiveBookmarks|nvarchar(max)|İş akışı örneği boş ise, bu özellik örneği üzerinde engellenir hangi yer işaretlerini gösterir. Örneği boş değilse, bu sütun NULL olur.|  
|CurrentMachine|nvarchar(128)|Bilgisayar adı şu anda iş akışı örneği belleğe sahip gösterir.|  
|LastMachine|Nvarchar(450)|İş akışı örneği yüklendi son bilgisayarı gösterir.|  
|ExecutionStatus|Nvarchar(450)|İş akışının geçerli yürütme durumunu gösterir. Olası durumlar şunlardır **Executing**, **boşta**, **kapalı**.|  
|Isınitialized|Bit|İş akışı örneği başlatılmış olup olmadığını gösterir. Başlatılan iş akışı örneği en az bir kez kalıcı bir iş akışı örneği ' dir.|  
|IsSuspended|Bit|İş akışı örneği askıya olup olmadığını gösterir.|  
|IsCompleted|Bit|İş akışı örneği yürütmesini bitirene olup olmadığını gösterir. **Not:**  IIf **InstanceCompletionAction** özelliği **DeleteAll**, örnekleri tamamlandıktan sonra görünümünden kaldırılır.|  
|EncodingOption|Mini tamsayı|Veri özellikleri serileştirmek için kullanılan kodlama açıklar.<br /><br /> -0 – hiçbir kodlama<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|VARBINARY(max)|Örnek yüklendiğinde, geri iş akışı çalışma zamanı sağlanan serileştirilmiş bir örnek veri özelliklerini içerir.<br /><br /> Özel bütünleştirilmiş kod yok blob serisini kaldırmak için gerekli olup olmadığını anlamına gelir. yerel bir CLR türü her temel özelliğidir.|  
|WriteOnlyPrimitiveDataProperties|VARBINARY(max)|Örnek yüklendiğinde, geri iş akışı çalışma zamanı için sağlanan değil serileştirilmiş bir örnek veri özelliklerini içerir.<br /><br /> Özel bütünleştirilmiş kod yok blob serisini kaldırmak için gerekli olup olmadığını anlamına gelir. yerel bir CLR türü her temel özelliğidir.|  
|ReadWriteComplexDataProperties|VARBINARY(max)|Örnek yüklendiğinde, geri iş akışı çalışma zamanı için sağlanan serileştirilmiş bir örnek veri özelliklerini içerir.<br /><br /> Bir seri durumdan çıkarıcı bu blobu'nda depolanan tüm nesne türlerinin bilgi gerektirir.|  
|WriteOnlyComplexDataProperties|VARBINARY(max)|Örnek yüklendiğinde, geri iş akışı çalışma zamanı için sağlanan değil serileştirilmiş bir örnek veri özelliklerini içerir.<br /><br /> Bir seri durumdan çıkarıcı bu blobu'nda depolanan tüm nesne türlerinin bilgi gerektirir.|  
|IdentityName|nvarchar(max)|İş akışı tanımının adı.|  
|IdentityPackage|nvarchar(max)|İş akışı (derleme adı gibi) oluşturulduğunda verilen paket bilgileri.|  
|Yapı|BigInt|İş akışı sürümünün derleme numarası.|  
|Ana|BigInt|İş akışı sürümü ana sayısı.|  
|İkincil|BigInt|İş akışı sürümü küçük sayısı.|  
|Gözden geçirme|BigInt|İş akışı sürümünün düzeltme numarası.|  
  
> [!CAUTION]
>  **Örnekleri** görünümü de Delete tetikleyicisi içeriyor. Uygun izne sahip kullanıcılar zorla iş akışı örnekleri veritabanından kaldırır bu görünüm delete deyimini yürütebilir. İş akışı çalışma zamanı altında örneğini silmek, istenmeyen sonuçlara neden olabilir çünkü yalnızca son çare olarak doğrudan görünümden silme öneririz. İş akışı çalışma zamanı örneği sonlandırmak için bunun yerine, iş akışı örneği yönetim uç noktasını kullanın. Çok sayıda örneği görünümden silmek istiyorsanız, bu örnekler üzerinde çalışıyor olabilir hiçbir etkin çalışma zamanları olmadığından emin olun.  
  
## <a name="servicedeployments-view"></a>ServiceDeployments görüntüle  
 **ServiceDeployments** görünümü, tüm Web dağıtım bilgilerini içerir (IIS / WAS'da) barındırılan iş akışı hizmetleri. Web barındırılan her iş akışı örneği içerecek bir **ServiceDeploymentId** bu görünümde bir satıra başvuruyor.  
  
|Sütun adı|Sütun türü|Açıklama|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|Bu görünüm için birincil anahtar.|  
|Site adı|nvarchar(max)|İş akışı hizmeti içeren sitenin adını temsil eder (örneğin **varsayılan Web sitesi**).|  
|RelativeServicePath|nvarchar(max)|İş akışı hizmetine işaret eden site göreli sanal yolu temsil eder. (örn.)  **/app1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|nvarchar(max)|İş akışı hizmeti içeren bir uygulamaya işaret eden site göreli sanal yolu temsil eder. (örneğin **/app1**).|  
|ServiceName|nvarchar(max)|İş akışı hizmeti adını temsil eder. (örneğin **PurchaseOrderService**).|  
|ServiceNamespace|nvarchar(max)|İş akışı hizmet ad alanını temsil eder. (örneğin **Şirketim**).|  
  
 ServiceDeployments görünüm de Delete tetikleyicisi içeriyor. Uygun izinlere sahip kullanıcılar delete deyimleri ServiceDeployment girişler veritabanından kaldırmak için bu görünümü karşı çalıştırabilirsiniz. Aşağıdakilere dikkat edin:  
  
1. Tüm veritabanını, bu işlemi gerçekleştirmeden önce kilitlenmelidir olduğundan, bu görünümden girdileri silme maliyetlidir. Bu, bir iş akışı örneği var olmayan ServiceDeployment girişe burada başvurabileceğiniz senaryo önlemek gereklidir. Kapalı kaldıkları süreleri sırasında yalnızca bu görünümden silme / bakım pencereleri.  
  
2. Tüm girdiler tarafından başvuruluyor bir ServiceDeployment satır silme girişiminde **örnekleri** görünüm yok op neden olur. Yalnızca sıfır başvuruları ServiceDeployment satırlarla silebilirsiniz.  
  
## <a name="instancepromotedproperties-view"></a>InstancePromotedProperties görüntüle  
 **InstancePromotedProperties** görünümü kullanıcı tarafından belirtilen yükseltilen özellikleri için bilgiler içerir. Yükseltilen özellik sorgularda örnekleri almak için kullanabileceğiniz bir kullanıcı bir birinci sınıf özellik olarak işlev görür.  Örneğin, bir kullanıcı her zaman sırayla maliyetini depolayan bir PurchaseOrder promosyon ekleyebilirsiniz **Value1** sütun. Bu kullanıcı için tüm satın alma siparişleri maliyeti belirli bir değere aştığı için sorgu etkinleştirir.  
  
|Sütun türü|Sütun türü|Açıklama|  
|-|-|-|  
|InstanceId|Benzersiz tanımlayıcı|İş akışı örneği kimliği|  
|EncodingOption|Mini tamsayı|Yükseltilen ikili özellikleri serileştirmek için kullanılan kodlama açıklar.<br /><br /> -0 – hiçbir kodlama<br />-1 – GZipStream|  
|PromotionName|Nvarchar(400)|Bu örnekle ilişkili yükseltme adı. PromotionName genel sütunları bu satırda bağlam eklemek için gereklidir.<br /><br /> Örneğin, bir PromotionName PurchaseOrder Value1 sırasını maliyetini içerir, değer2 siparişi veren müşteri adını içeren, müşteri ve benzeri adresini değeri 3'ü içerip gösterebilir.|  
|Değeri [1-32]|SqlVariant|Değeri [1-32] SqlVariant sütunda depolanabilen değerlerini içerir. Tek bir yükseltme 32'den fazla SqlVariants içeremez.|  
|Değer [33-64]|VARBINARY(max)|Değer 33-64 seri değerlerini içerir. Örneğin, Value33 bir JPEG, satın alınan bir maddenin içerebilir. Tek bir yükseltme 32'den fazla ikili özellikleri içeremez|  
  
 Şemaya bağlı, kullanıcıları bu görünüm sorguları iyileştirmek için bir veya daha fazla sütuna dizinleri ekleyebilirsiniz anlamına gelir InstancePromotedProperties görünümdür.  
  
> [!NOTE]
>  Dizinli bir görünüm, daha fazla depolama alanı gerektirir ve ek işlem yükü ekler. Lütfen [SQL Server 2008 dizin oluşturulmuş görünümler ile performansı iyileştirme](https://go.microsoft.com/fwlink/?LinkId=179529) daha fazla bilgi için.

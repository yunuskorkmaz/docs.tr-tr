---
title: Yansıma sağlayıcısı (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: 12a23970b059e338df05a2f0b58ca67ad6fae6d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582571"
---
# <a name="reflection-provider-wcf-data-services"></a>Yansıma sağlayıcısı (WCF Data Services)
Entity Framework Veri modeliyle verileri kullanıma sunduğundan yanı sıra [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kesinlikle bir varlık tabanlı modelde tanımlı değil verilerini açığa çıkarabilir. Yansıma sağlayıcısı, dönüş türleri uygulayan sınıflar verileri kullanıma sunar <xref:System.Linq.IQueryable%601> arabirimi. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Bu sınıflar için bir veri modeli çıkarsamak için yansıtma kullanır ve adresi tabanlı sorgular kaynaklarda dil ile tümleşik sorgu (LINQ) çevirebilir-sorguları sunulan temel <xref:System.Linq.IQueryable%601> türleri.  
  
> [!NOTE]
>  Kullanabileceğiniz <xref:System.Linq.Queryable.AsQueryable%2A> döndürülecek yöntemi bir <xref:System.Linq.IQueryable%601> arabirimi uygulayan herhangi bir sınıftan <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Bu veri hizmetiniz için bir veri kaynağı olarak kullanılacak en genel koleksiyon türleri sağlar.  
  
 Yansıma sağlayıcısı türü hiyerarşileri destekler. Daha fazla bilgi için [nasıl yapılır: Yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
## <a name="inferring-the-data-model"></a>Veri modeli çıkarımını yapma  
 Veri Hizmeti oluşturduğunuzda, sağlayıcı yansıma kullanarak veri modelini algılar. Aşağıdaki liste, yansıma sağlayıcısı veri modeli nasıl çıkarsar gösterir:  
  
-   Varlık kapsayıcı - veri döndüren özellikler gösteren sınıf bir <xref:System.Linq.IQueryable%601> örneği. Yansıma tabanlı veri modeline yönlendirirken, varlık kapsayıcı hizmetinin kökü temsil eder. Tek bir varlık kapsayıcı sınıfı, belirtilen bir ad alanı için desteklenir.  
  
-   Varlık kümeleri - döndüren Özellikler <xref:System.Linq.IQueryable%601> örnekleri varlık kümeleri kabul edilir. Varlık kümeleri, doğrudan sorgu kaynakları olarak ele alınır. Varlık kapsayıcısının yalnızca bir özellikte döndürebilir bir <xref:System.Linq.IQueryable%601> belirli bir türden.  
  
-   Varlık türleri - tür `T` , <xref:System.Linq.IQueryable%601> varlık döndürür kümesi. Devralma Hiyerarşisi parçası olan sınıfları yansıma sağlayıcısı tarafından bir eşdeğer varlık türü hiyerarşiye çevrilir.  
  
-   Varlık anahtarları - varlık türü olduğu her veri sınıfı bir anahtarı özelliği olması gerekir. Bu özellik ile öznitelendirilen <xref:System.Data.Services.Common.DataServiceKeyAttribute> özniteliği (`[DataServiceKeyAttribute]`).  
  
    > [!NOTE]
    >  Yalnızca uygulamalıdır <xref:System.Data.Services.Common.DataServiceKeyAttribute> varlık türünün örneğini benzersiz şekilde tanımlamak için kullanılan bir özelliği için öznitelik. Bu öznitelik, bir gezinti özelliğine uygulandığında dikkate alınmaz.  
  
-   Varlık türü özellikleri - Varlık anahtarı dışında bir varlık türü gibi bir sınıfı erişilebilir, dizin oluşturucu olmayan özelliklerini yansıma sağlayıcısı değerlendirir:  
  
    -   Özelliğin türü basit tür döndürürse, özelliği bir özellik bir varlık türü olduğu varsayılır.  
  
    -   Özelliği bir varlık türü olan bir türü döndürürse, özelliği "bir" çoktan çoka bir veya birebir ilişkisi sonunu temsil eden bir gezinti özelliği olduğu varsayılır.  
  
    -   Özellik döndürürse bir <xref:System.Collections.Generic.IEnumerable%601> bir varlık türü, ardından özellik bire çok veya çoktan çoğa bir ilişki "many" sonunu temsil eden bir gezinti özelliği olarak kabul edilir.  
  
    -   Özelliğinin dönüş türü bir değer türü ise özelliği karmaşık bir türü temsil eder.  
  
> [!NOTE]
>  Varlık ilişkisel modelini temel alan bir veri modeli farklı olarak, ilişkisel veri yansıma sağlayıcısını temel modelleri anlaşılmıyor. İlişkisel veriler aracılığıyla kullanıma sunmak için Entity Framework kullanmalısınız [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
## <a name="data-type-mapping"></a>Veri türü eşlemesi  
 Bir veri modeli, .NET Framework sınıflarını çıkarıldığında, veri modeli ilkel türlerini .NET Framework veri türleri için şu şekilde eşlenir:  
  
|.NET framework veri türü|Veri modeli türü|  
|------------------------------|---------------------|  
|<xref:System.Byte>`[]`|`Edm.Binary`|  
|<xref:System.Boolean>|`Edm.Boolean`|  
|<xref:System.Byte>|`Edm.Byte`|  
|<xref:System.DateTime>|`Edm.DateTime`|  
|<xref:System.Decimal>|`Edm.Decimal`|  
|<xref:System.Double>|`Edm.Double`|  
|<xref:System.Guid>|`Edm.Guid`|  
|<xref:System.Int16>|`Edm.Int16`|  
|<xref:System.Int32>|`Edm.Int32`|  
|<xref:System.Int64>|`Edm.Int64`|  
|<xref:System.SByte>|`Edm.SByte`|  
|<xref:System.Single>|`Edm.Single`|  
|<xref:System.String>|`Edm.String`|  
  
> [!NOTE]
>  .NET framework boş değer atanabilen değer türleri null atanamaz karşılık gelen bir değer türleri aynı veri modeli türlerine eşlenir.  
  
## <a name="enabling-updates-in-the-data-model"></a>Veri modelindeki güncelleştirmeleri etkinleştirme  
 Bu tür bir veri modeli kullanıma sunulan veri güncelleştirmelere izin verecek şekilde yansıma sağlayıcısını tanımlayan bir <xref:System.Data.Services.IUpdatable> arabirimi. Bu arabirim, güncelleştirmeleri kullanıma sunulan türlerine kalıcı hale getirmek nasıl veri hizmeti bildirir. Varlık kapsayıcı sınıfı veri modeli tarafından tanımlanan kaynakları için güncelleştirmeleri etkinleştirecek şekilde uygulamalıdır <xref:System.Data.Services.IUpdatable> arabirimi. Uygulaması örneği için <xref:System.Data.Services.IUpdatable> arabirim için bkz: [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 <xref:System.Data.Services.IUpdatable> Arabirimi gerektirir böylece yansıma sağlayıcısını kullanarak, güncelleştirmeleri veri kaynağına yayılamaz aşağıdaki üyeleri uygulanabilir:  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Navigation özelliğinden erişilen birbiriyle ilgili nesnelerden oluşan bir koleksiyon için bir nesne eklemek için gereken işlevleri sağlar.|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Bekleyen verilerde yapılan değişiklikleri iptal eder işlevlerini sağlar.|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Belirtilen kapsayıcı içinde yeni bir kaynak oluşturmak için gereken işlevleri sağlar.|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Bir kaynağı silmek için gereken işlevleri sağlar.|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Belirli bir sorgu ve tür adıyla belirlenen bir kaynağı almak için gereken işlevleri sağlar.|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Bir kaynak özelliğinin değeri döndürmek için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Gezinti özelliğine erişinceye birbiriyle ilgili nesnelerden oluşan bir koleksiyon için bir nesne kaldırmak için gereken işlevleri sağlar.|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Belirtilen kaynak güncelleştirme için gereken işlevleri sağlar.|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Belirli bir nesne örneği tarafından temsil edilen kaynak döndürülecek işlevlerini sağlar.|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Tüm bekleyen değişiklikleri kaydetmek için gereken işlevleri sağlar.|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|İlgili nesne başvurusu bir gezinti özelliği'ni kullanarak ayarlamak için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Bir kaynak özelliğinin değeri ayarlamak için işlevsellik sağlar.|  
  
## <a name="handling-concurrency"></a>Eşzamanlılığı İşleme  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir varlık için eşzamanlı bir simge tanımlamak olanak tanıyarak bir iyimser eşzamanlılık modelini destekler. Bir veya daha fazla varlık özelliklerini içerir, bu eşzamanlılık belirteci, bir değişiklik, güncellenen veya silinen istenen verileri oluşup oluşmadığını belirlemek için veri hizmeti tarafından kullanılır. Varlığın geçerli değerlere eTag istekte alınan belirteç değerleri farklı olduğunda, bir özel durum veri hizmeti tarafından oluşturulur. <xref:System.Data.Services.ETagAttribute> Yansıma sağlayıcısı eşzamanlı bir simge tanımlamak için bir varlık türü için uygulanır. Eşzamanlılık belirteci, bir anahtar özellik ya da bir gezinti özelliği dahil edemezsiniz. Daha fazla bilgi için [veri hizmetini güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Yansıma sağlayıcısı ile LINQ to SQL kullanma  
 Varsayılan olarak Entity Framework yerel olarak desteklendiğinden, ilişkisel verilerle kullanmak için önerilen veri sağlayıcısı olan [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Ancak LINQ to SQL sınıfları data service ile kullanılacak yansıma sağlayıcısını kullanabilirsiniz. <xref:System.Data.Linq.Table%601> Sonucu üzerinde yöntemleri tarafından döndürülen kümeleri <xref:System.Data.Linq.DataContext> LINQ to SQL Object Relational Designer (O/R Tasarımcısı) uygulama tarafından oluşturulan <xref:System.Linq.IQueryable%601> arabirimi. Bu, bu yöntemlere erişmek ve oluşturulan LINQ to SQL sınıfları kullanarak varlık verilerini SQL Server'dan döndürmek yansıma sağlayıcısı sağlar. Ancak LINQ to SQL uygulamadığından <xref:System.Data.Services.IUpdatable> arabirimi, gereken varolan genişleten kısmi bir sınıf eklemek <xref:System.Data.Linq.DataContext> eklemek için kısmi sınıf <xref:System.Data.Services.IUpdatable> uygulaması. Daha fazla bilgi için [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

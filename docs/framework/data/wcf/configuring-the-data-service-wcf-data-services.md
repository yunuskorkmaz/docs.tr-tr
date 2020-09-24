---
title: Veri hizmetini yapılandırma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 59efd4c8-cc7a-4800-a0a4-d3f8abe6c55c
ms.openlocfilehash: a30a8c2c731e8c5cb2b22c8d7f34ec32d149803c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152799"
---
# <a name="configuring-the-data-service-wcf-data-services"></a>Veri hizmetini yapılandırma (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, açık veri Protokolü (OData) akışlarını kullanıma sunan veri hizmetleri oluşturabilirsiniz. Bu akışlardaki veriler, çeşitli veri kaynaklarından gelebilir. WCF Veri Hizmetleri, bu verileri OData akışı olarak göstermek için veri sağlayıcılarını kullanır. Bu sağlayıcılar bir Entity Framework sağlayıcısı, bir yansıma sağlayıcısı ve bir dizi özel veri hizmeti sağlayıcısı arabirimlerini içerir. Sağlayıcı uygulama, hizmet için veri modelini tanımlar. Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).  
  
 WCF Veri Hizmetleri veri hizmeti, sınıfından devralan bir sınıftır <xref:System.Data.Services.DataService%601> . burada veri hizmetinin türü, veri modelinin varlık kapsayıcısıdır. Bu varlık kapsayıcısının <xref:System.Linq.IQueryable%601> , veri modelindeki varlık kümelerine erişmek için kullanılan bir veya daha fazla özelliği olan bir veya daha fazla özelliği vardır.  
  
 Veri hizmetinin davranışları, sınıfının üyeleri tarafından <xref:System.Data.Services.DataServiceConfiguration> ve sınıfının <xref:System.Data.Services.DataServiceBehavior> özelliğinden erişilen sınıfının üyeleri tarafından tanımlanır <xref:System.Data.Services.DataServiceConfiguration.DataServiceBehavior%2A> <xref:System.Data.Services.DataServiceConfiguration> ... <xref:System.Data.Services.DataServiceConfiguration>Sınıfı, `InitializeService` Northwind veri hizmeti 'nin aşağıdaki uygulamasında olduğu gibi veri hizmeti tarafından uygulanan yöntemine sağlanır:  
  
[!code-csharp[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigcomplete)]  
[!code-vb[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigcomplete)]  
  
## <a name="data-service-configuration-settings"></a>Veri hizmeti yapılandırma ayarları  

 <xref:System.Data.Services.DataServiceConfiguration>Sınıfı, aşağıdaki veri hizmeti davranışlarını belirtmenizi sağlar:  
  
|Üye|Davranış|  
|------------|--------------|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptCountRequests%2A>|`$count`Yol kesimini ve sorgu seçeneğini kullanarak veri hizmetine gönderilen sayma isteklerini devre dışı bırakmanızı sağlar `$inlinecount` . Daha fazla bilgi için bkz. [OData: URI kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptProjectionRequests%2A>|Sorgu seçeneği kullanılarak veri hizmetine gönderilen isteklerde veri projeksiyonu desteğini devre dışı bırakmanızı sağlar `$select` . Daha fazla bilgi için bkz. [OData: URI kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeAccess%2A>|Arabirimi kullanılarak tanımlanan dinamik meta veri sağlayıcısının meta verilerinde bir veri türünün gösterilmesini sağlar <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> .|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeConversion%2A>|Veri hizmeti çalışma zamanının, yükte bulunan türü, istekte belirtilen gerçek özellik türüne dönüştürüp dönüştürmeyeceğini belirtmenize olanak sağlar.|  
|<xref:System.Data.Services.DataServiceBehavior.InvokeInterceptorsOnLinkDelete%2A>|İki varlık arasında bir ilişki bağlantısı silindiğinde ilgili varlıklarda kayıtlı değişiklik yakalayıcılar yapılıp yapılmayacağını belirtmenize olanak sağlar.|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxBatchCount%2A>|Tek bir toplu işte izin verilen değişiklik kümesi sayısını ve sorgu işlemlerini sınırlamanıza olanak sağlar. Daha fazla bilgi için bkz. [OData: Batch ve toplu](https://www.odata.org/documentation/odata-version-2-0/batch-processing/) [işlem işlemleri](batching-operations-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxChangesetCount%2A>|Tek bir değişiklik kümesine dahil edilebilir değişiklik sayısını sınırlamanıza olanak sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti sonuçlarının sayfalamayı etkinleştirme](how-to-enable-paging-of-data-service-results-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandCount%2A>|Sorgu işlecini kullanarak, tek bir istekte yer alan ilgili varlıkların sayısını sınırlayarak bir yanıtın boyutunu sınırlandırmanıza olanak sağlar `$expand` . Daha fazla bilgi için bkz. [OData: URI kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) ve [ertelenmiş içerik yükleme](loading-deferred-content-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandDepth%2A>|Sorgu işlecini kullanarak, tek bir istekte yer alan ilgili varlıkların grafiğinin derinliğini sınırlayarak bir yanıtın boyutunu sınırlandırmanıza olanak sağlar `$expand` . Daha fazla bilgi için bkz. [OData: URI kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) ve [ertelenmiş içerik yükleme](loading-deferred-content-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxObjectCountOnInsert%2A>|, Tek bir POST isteğinde bulunabilecek eklenecek varlık sayısını sınırlamanıza olanak sağlar.|  
|<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>|Veri hizmeti tarafından kullanılan atom protokolünün sürümünü tanımlar. Değeri <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> en büyük değerinden küçük bir değere ayarlandığında <xref:System.Data.Services.Common.DataServiceProtocolVersion> , WCF veri hizmetleri en son işlevselliği veri hizmetine erişen istemciler için kullanılamaz. Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxResultsPerCollection%2A>|Bir veri akışı olarak döndürülen her bir varlık kümesindeki varlık sayısını sınırlayarak bir yanıtın boyutunu sınırlandırmanıza olanak sağlar.|  
|<xref:System.Data.Services.DataServiceConfiguration.RegisterKnownType%2A>|Veri hizmeti tarafından tanınan türler listesine bir veri türü ekler.|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetAccessRule%2A>|Veri hizmetinde kullanılabilir olan varlık kümesi kaynakları için erişim haklarını ayarlar. `*`Ad parametresinin, kalan tüm varlık kümelerine erişimi aynı düzeye ayarlaması için bir yıldız işareti () değeri sağlanabilir. İstemci uygulamaları için gerekli olan veri hizmeti kaynaklarına en az ayrıcalık erişimi sağlamak için varlık kümelerine erişim ayarlamanızı öneririz. Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md). Belirli bir URI ve HTTP eylemi için gereken en düşük erişim haklarına örnek olarak, [En düşük kaynak erişim gereksinimleri](configuring-the-data-service-wcf-data-services.md#accessRequirements) bölümünde tablosuna bakın.|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetPageSize%2A>|Bir varlık kümesi kaynağı için maksimum sayfa boyutunu ayarlar. Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti sonuçlarının sayfalamayı etkinleştirme](how-to-enable-paging-of-data-service-results-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.SetServiceOperationAccessRule%2A>|Veri hizmetinde tanımlanan hizmet işlemlerine yönelik erişim haklarını ayarlar. Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md). `*`Ad parametresinin, tüm hizmet işlemlerine yönelik erişimi aynı düzeye ayarlaması için bir yıldız işareti () değeri sağlanabilir. İstemci uygulamaları için gerekli olan veri hizmeti kaynaklarına en az ayrıcalık erişimi sağlamak için hizmet işlemlerine erişim ayarlamanızı öneririz. Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A>|Bu yapılandırma özelliği, hata yanıtı iletisinde daha fazla bilgi döndürerek bir veri hizmetini daha kolay bir şekilde gidermenize olanak sağlar. Bu seçenek, bir üretim ortamında kullanılmak üzere tasarlanmamıştır. Daha fazla bilgi için bkz. [WCF veri Hizmetleri geliştirme ve dağıtma](developing-and-deploying-wcf-data-services.md).|  
  
<a name="accessRequirements"></a>

## <a name="minimum-resource-access-requirements"></a>En düşük kaynak erişimi gereksinimleri  

 Aşağıdaki tabloda, belirli bir işlemi yürütmek için verilmesi gereken en düşük varlık kümesi haklarının ayrıntıları verilmiştir. Yol örnekleri, [hızlı](quickstart-wcf-data-services.md)başlangıcı tamamladığınızda oluşturulan Northwind veri hizmetini temel alır. Hem <xref:System.Data.Services.EntitySetRights> numaralandırma hem de <xref:System.Data.Services.ServiceOperationRights> numaralandırma kullanılarak tanımlandığından <xref:System.FlagsAttribute> , tek bir varlık kümesi veya işlemi için birden çok izin belirtmek üzere bir mantıksal or işleci kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmetine erişimi etkinleştirme](how-to-enable-access-to-the-data-service-wcf-data-services.md).  
  
|Yol/eylem|`GET`|`DELETE`|`MERGE`|`POST`|`PUT`|  
|------------------|-----------|--------------|-------------|------------|-----------|  
|`/Customers`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmez|Desteklenmez|<xref:System.Data.Services.EntitySetRights.WriteAppend>|Desteklenmez|  
|`/Customers('ALFKI')`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteMerge>|yok|<xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmez|Desteklenmez|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteMerge> veya <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> '<br /><br /> `Orders``:`ve<xref:System.Data.Services.EntitySetRights.WriteAppend>|Desteklenmez|  
|`/Customers('ALFKI')/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteDelete>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteMerge>|Desteklenmez|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Orders(10643)/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteDelete><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteMerge> ;<br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.WriteAppend> ve <xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmez|  
|`/Customers('ALFKI')/$links/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmez|Desteklenmez|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteMerge> veya <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmez|  
|`/Customers('ALFKI')/$links/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteMerge> veya <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmez|Desteklenmez|Desteklenmez|  
|`/Orders(10643)/$links/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteMerge> veya <xref:System.Data.Services.EntitySetRights.WriteReplace>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteMerge>|Desteklenmez|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle>;<br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers/$count`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmez|Desteklenmez|Desteklenmez|Desteklenmez|  
|`/Customers('ALFKI')/ContactName`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmez|<xref:System.Data.Services.EntitySetRights.WriteMerge>|Desteklenmez|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Address/StreetAddress/$value`<sup>1</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.WriteDelete>|Desteklenmez|Desteklenmez|Desteklenmez|  
|`/Customers('ALFKI')/ContactName/$value`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.WriteMerge>|Desteklenmez|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/$value`<sup>2</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmez|Desteklenmez|Desteklenmez|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmez|Desteklenmez|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend>|Desteklenmez|  
|`/Customers('ALFKI')?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> '<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmez|Desteklenmez|Desteklenmez|Desteklenmez|  
  
 <sup>1</sup> Bu örnekte, `Address` adında bir özelliği olan varlığın karmaşık tür özelliğini temsil eder `Customers` `StreetAddress` . Northwind veri Hizmetleri tarafından kullanılan model, bu karmaşık türü açıkça tanımlamaz. Veri modeli Entity Framework sağlayıcısı kullanılarak tanımlandığında, bu tür karmaşık bir tür tanımlamak için Varlık Veri Modeli araçlarını kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: karmaşık türler oluşturma ve değiştirme](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
 <sup>2</sup> bu URI, bir ikili büyük nesne (blob) döndüren bir özellik, bu örnekte olduğu gibi bir medya bağlantısı girişi olan bir varlığa ait olan medya kaynağı olarak tanımlandığında desteklenir `Customers` . Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md).  
  
<a name="versioning"></a>

## <a name="versioning-requirements"></a>Sürüm oluşturma gereksinimleri  

 Aşağıdaki veri hizmeti yapılandırma davranışları OData protokolünün 2 veya sonraki sürümlerinin sürümlerini gerektirir:  
  
- Count istekleri için destek.  
  
- Projeksiyon için $select sorgu seçeneği için destek.  
  
 Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [Veri Hizmeti Barındırma](hosting-the-data-service-wcf-data-services.md)

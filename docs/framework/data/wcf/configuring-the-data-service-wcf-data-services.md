---
title: Veri Hizmetinin Yapılandırılması (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 59efd4c8-cc7a-4800-a0a4-d3f8abe6c55c
ms.openlocfilehash: 6f73fa43bcb99e53adabe8b49ffee75c65802eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399891"
---
# <a name="configuring-the-data-service-wcf-data-services"></a>Veri Hizmetinin Yapılandırılması (WCF Veri Hizmetleri)
WCF Veri Hizmetleri ile Açık Veri Protokolü (OData) akışlarını ortaya çıkaran veri hizmetleri oluşturabilirsiniz. Bu akışlarda veri çeşitli veri kaynaklarından gelebilir. WCF Veri Hizmetleri, bu verileri OData akışı olarak ortaya çıkarmak için veri sağlayıcılarını kullanır. Bu sağlayıcılar arasında Varlık Çerçevesi sağlayıcısı, bir yansıtma sağlayıcısı ve bir dizi özel veri hizmeti sağlayıcısı arabirimi bulunur. Sağlayıcı uygulaması hizmet için veri modelini tanımlar. Daha fazla bilgi için [Bkz. Veri Hizmetleri Sağlayıcıları.](data-services-providers-wcf-data-services.md)  
  
 WCF Veri Hizmetleri'nde veri hizmeti, <xref:System.Data.Services.DataService%601> veri hizmetinin türü veri modelinin varlık kapsayıcısı olan sınıftan devralan bir sınıftır. Bu varlık kapsayıcısı, veri modelindeki varlık kümelerine erişmek için kullanılan bir <xref:System.Linq.IQueryable%601>veya daha fazla özelme sahiptir.  
  
 Veri hizmetinin davranışları <xref:System.Data.Services.DataServiceConfiguration> sınıfın üyeleri ve <xref:System.Data.Services.DataServiceBehavior> <xref:System.Data.Services.DataServiceConfiguration.DataServiceBehavior%2A> <xref:System.Data.Services.DataServiceConfiguration> sınıfın özelliğinden erişilen sınıf üyeleri tarafından tanımlanır. Sınıf, <xref:System.Data.Services.DataServiceConfiguration> northwind veri `InitializeService` hizmetinin aşağıdaki uygulamasında olduğu gibi, veri hizmeti tarafından uygulanan yönteme verilir:  
  
[!code-csharp[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigcomplete)]  
[!code-vb[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigcomplete)]  
  
## <a name="data-service-configuration-settings"></a>Veri Hizmeti Yapılandırma Ayarları  
 Sınıf, <xref:System.Data.Services.DataServiceConfiguration> aşağıdaki veri hizmeti davranışlarını belirtmenizi sağlar:  
  
|Üye|Davranış|  
|------------|--------------|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptCountRequests%2A>|`$count` Yol kesimini ve sorgu seçeneğini kullanarak veri hizmetine gönderilen sayı isteklerini `$inlinecount` devre dışı etmenizi sağlar. Daha fazla bilgi için [Bkz. OData: URI Kuralları.](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptProjectionRequests%2A>|`$select` Sorgu seçeneğini kullanarak veri hizmetine gönderilen isteklerde veri projeksiyonu desteğini devre dışı etmenizi sağlar. Daha fazla bilgi için [Bkz. OData: URI Kuralları.](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeAccess%2A>|<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> Arabirimi kullanarak tanımlanan dinamik bir meta veri sağlayıcısı için meta verilerde bir veri türünün açığa kullanılmasını sağlar.|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeConversion%2A>|Veri hizmeti çalışma zamanının, yükte bulunan türü istekte belirtilen fiili özellik türüne dönüştürüp dönüştürmemesi gerektiğini belirtmenizi sağlar.|  
|<xref:System.Data.Services.DataServiceBehavior.InvokeInterceptorsOnLinkDelete%2A>|İki varlık arasındaki ilişki bağlantısı silindiğinde, kayıtlı değişiklik önleyicilerin ilgili varlıklarüzerinde çağrılup çağrılmadığını belirtmenizi sağlar.|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxBatchCount%2A>|Tek bir toplu iş halinde izin verilen değişiklik kümeleri ve sorgu işlemleri sayısını sınırlamanızı sağlar. Daha fazla bilgi için [Bkz. OData: Toplu İşlemler](https://www.odata.org/documentation/odata-version-2-0/batch-processing/) ve [Toplu İşlemler.](batching-operations-wcf-data-services.md)|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxChangesetCount%2A>|Tek bir değişiklik kümesine dahil edilebilen değişiklik sayısını sınırlamanızı sağlar. Daha fazla bilgi için [bkz: Veri Hizmeti Sonuçlarının Sayfalanmasını Etkinleştirin.](how-to-enable-paging-of-data-service-results-wcf-data-services.md)|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandCount%2A>|`$expand` Sorgu işlecikullanarak tek bir isteğe dahil edilebilen ilgili varlıkların sayısını sınırlayarak yanıtın boyutunu sınırlamanızı sağlar. Daha fazla bilgi için [Bkz. OData: URI Kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) ve [Ertelenmiş İçerik Yükleme.](loading-deferred-content-wcf-data-services.md)|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandDepth%2A>|`$expand` Sorgu işleci kullanarak tek bir isteğe dahil edilebilen ilgili varlıkların grafiğinin derinliğini sınırlayarak yanıtın boyutunu sınırlamanızı sağlar. Daha fazla bilgi için [Bkz. OData: URI Kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) ve [Ertelenmiş İçerik Yükleme.](loading-deferred-content-wcf-data-services.md)|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxObjectCountOnInsert%2A>|Tek bir POSTA isteğinde bulunabilecek eklenecek varlık sayısını sınırlamanızı sağlar.|  
|<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>|Veri hizmeti tarafından kullanılan Atom protokolünün sürümünü tanımlar. Değer, <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> maksimum değerinden daha az bir değere <xref:System.Data.Services.Common.DataServiceProtocolVersion>ayarlandığında, WCF Veri Hizmetleri'nin en son işlevselliği veri hizmetine erişen istemciler tarafından kullanılamaz. Daha fazla bilgi için [Bkz. Veri Hizmeti Sürümü.](data-service-versioning-wcf-data-services.md)|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxResultsPerCollection%2A>|Veri akışı olarak döndürülen her varlık kümesindeki varlık sayısını sınırlayarak yanıt Boyutunu sınırlamanızı sağlar.|  
|<xref:System.Data.Services.DataServiceConfiguration.RegisterKnownType%2A>|Veri hizmeti tarafından tanınan türler listesine bir veri türü ekler.|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetAccessRule%2A>|Veri hizmetinde kullanılabilen varlık kümesi kaynaklarının erişim haklarını ayarlar. Kalan tüm varlık`*`kümeleri için erişimi aynı düzeye ayarlamak için ad parametresi için bir yıldız ( ) değeri sağlanabilir. İstemci uygulamaları tarafından gerekli olan veri hizmeti kaynaklarına en az ayrıcalık erişimini sağlamak için varlık kümelerine erişimi ayarlamanızı öneririz. Daha fazla bilgi için [WCF Veri Hizmetlerinin Güvenliğini Sağlama'ya](securing-wcf-data-services.md)bakın. Belirli bir URI ve HTTP eylemi için gereken minimum erişim hakları örnekleri için, [Minimum Kaynak Erişim Gereksinimleri](configuring-the-data-service-wcf-data-services.md#accessRequirements) bölümündeki tabloya bakın.|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetPageSize%2A>|Varlık kümesi kaynağı için en büyük sayfa boyutunu ayarlar. Daha fazla bilgi için [bkz: Veri Hizmeti Sonuçlarının Sayfalanmasını Etkinleştirin.](how-to-enable-paging-of-data-service-results-wcf-data-services.md)|  
|<xref:System.Data.Services.DataServiceConfiguration.SetServiceOperationAccessRule%2A>|Veri hizmetinde tanımlanan hizmet işlemleri için erişim haklarını ayarlar. Daha fazla bilgi için [Hizmet İşlemleri'ne](service-operations-wcf-data-services.md)bakın. Tüm hizmet işlemlerine erişimi aynı düzeye ayarlamak için ad parametresi için bir yıldız işareti (`*`) değeri sağlanabilir. İstemci uygulamaları tarafından gerekli olan veri hizmeti kaynaklarına en az ayrıcalık erişimini sağlamak için hizmet işlemlerine erişimi ayarlamanızı öneririz. Daha fazla bilgi için [WCF Veri Hizmetlerinin Güvenliğini Sağlama'ya](securing-wcf-data-services.md)bakın.|  
|<xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A>|Bu yapılandırma özelliği, hata yanıt iletisinde daha fazla bilgi döndürerek bir veri hizmetini daha kolay gidermenizi sağlar. Bu seçenek, üretim ortamında kullanılmak üzere tasarlanmamıştır. Daha fazla bilgi için [WCF Veri Hizmetleri Geliştirme ve Dağıtma'ya](developing-and-deploying-wcf-data-services.md)bakın.|  
  
<a name="accessRequirements"></a>
## <a name="minimum-resource-access-requirements"></a>Minimum Kaynak Erişim Gereksinimleri  
 Aşağıdaki tablo, belirli bir işlemi yürütmek için verilmesi gereken minimum varlık kümesi haklarını ayrıntılarıyla açıklar. Yol örnekleri, [hızlı başlatmayı](quickstart-wcf-data-services.md)tamamladığınızda oluşturulan Northwind veri hizmetini temel alıntır. Hem numaralandırma hem <xref:System.Data.Services.EntitySetRights> <xref:System.Data.Services.ServiceOperationRights> de numaralandırma kullanılarak tanımlandığı <xref:System.FlagsAttribute>için, tek bir varlık kümesi veya işlemi için birden çok izin belirtmek için mantıksal bir OR işleci kullanabilirsiniz. Daha fazla bilgi için [bkz: Veri Hizmetine Erişimi Etkinleştirin.](how-to-enable-access-to-the-data-service-wcf-data-services.md)  
  
|Yol/Eylem|`GET`|`DELETE`|`MERGE`|`POST`|`PUT`|  
|------------------|-----------|--------------|-------------|------------|-----------|  
|`/Customers`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmiyor|Desteklenmiyor|<xref:System.Data.Services.EntitySetRights.WriteAppend>|Desteklenmiyor|  
|`/Customers('ALFKI')`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteMerge>|yok|<xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmiyor|Desteklenmiyor|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> <xref:System.Data.Services.EntitySetRights.WriteMerge> ve veya<xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> -ve-<br /><br /> `Orders``:` ve<xref:System.Data.Services.EntitySetRights.WriteAppend>|Desteklenmiyor|  
|`/Customers('ALFKI')/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve<xref:System.Data.Services.EntitySetRights.WriteDelete>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve<xref:System.Data.Services.EntitySetRights.WriteMerge>|Desteklenmiyor|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Orders(10643)/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve<xref:System.Data.Services.EntitySetRights.WriteDelete><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> <xref:System.Data.Services.EntitySetRights.WriteMerge>ve ;<br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.WriteAppend> ve<xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmiyor|  
|`/Customers('ALFKI')/$links/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmiyor|Desteklenmiyor|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> <xref:System.Data.Services.EntitySetRights.WriteMerge> ve veya<xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmiyor|  
|`/Customers('ALFKI')/$links/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> <xref:System.Data.Services.EntitySetRights.WriteMerge> ve veya<xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|  
|`/Orders(10643)/$links/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> <xref:System.Data.Services.EntitySetRights.WriteMerge> ve veya<xref:System.Data.Services.EntitySetRights.WriteReplace>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve<xref:System.Data.Services.EntitySetRights.WriteMerge>|Desteklenmiyor|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle>;<br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> ve<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers/$count`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|  
|`/Customers('ALFKI')/ContactName`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmiyor|<xref:System.Data.Services.EntitySetRights.WriteMerge>|Desteklenmiyor|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Address/StreetAddress/$value`<sup>1.1.2</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.WriteDelete>|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|  
|`/Customers('ALFKI')/ContactName/$value`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> ve <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.WriteMerge>|Desteklenmiyor|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/$value`<sup>2.000</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmiyor|Desteklenmiyor|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend>|Desteklenmiyor|  
|`/Customers('ALFKI')?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -ve-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|Desteklenmiyor|  
  
 <sup>1</sup> Bu örnekte, `Address` adı bir `Customers` `StreetAddress`özelliği olan varlığın karmaşık bir tür özelliğini temsil eder. Northwind veri hizmetleri tarafından kullanılan model açıkça bu karmaşık türü tanımlamaz. Veri modeli Varlık Çerçevesi sağlayıcısı kullanılarak tanımlandığında, böyle karmaşık bir türü tanımlamak için Varlık Veri Modeli araçlarını kullanabilirsiniz. Daha fazla bilgi için [bkz: Karmaşık Türleri Oluştur ve Değiştir.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))  
  
 <sup>2</sup> Bu URI, ikili büyük nesne (BLOB) döndüren bir özellik, medya bağlantı girişi olan bir varlığa ait ortam `Customers`kaynağı olarak tanımlandığında desteklenir. Daha fazla bilgi için [Akış Sağlayıcısı'na](streaming-provider-wcf-data-services.md)bakın.  
  
<a name="versioning"></a>
## <a name="versioning-requirements"></a>Sürüm Gereksinimleri  
 Aşağıdaki veri hizmeti yapılandırma davranışları, OData protokolünün sürüm 2'sini veya daha sonraki sürümleri ni gerektirir:  
  
- Sayım istekleri için destek.  
  
- Projeksiyon için $select sorgu seçeneği için destek.  
  
 Daha fazla bilgi için [Bkz. Veri Hizmeti Sürümü.](data-service-versioning-wcf-data-services.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [Veri Hizmeti Barındırma](hosting-the-data-service-wcf-data-services.md)

---
title: "Yansıma sağlayıcısı (WCF Veri Hizmetleri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52fe7e777cfea04b6da2a04c0badfe92b2a0a756
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="reflection-provider-wcf-data-services"></a>Yansıma sağlayıcısı (WCF Veri Hizmetleri)
Bir veri modeli aracılığıyla Entity Framework verileri gösterme yanı sıra [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kesinlikle bir varlık tabanlı modelde tanımlı değil veri hale getirebilir. Dönüş uygulama türleri sınıflardaki yansıma sağlayıcısı kullanıma sunan <xref:System.Linq.IQueryable%601> arabirimi. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Bu sınıf için bir veri modeli gerçekleştirip yansıma kullanır ve adresi tabanlı sorgular kaynaklara karşı dil ile tümleşik sorgu (LINQ) çevirebilir-gösterilen sorguları temel <xref:System.Linq.IQueryable%601> türleri.  
  
> [!NOTE]
>  Kullanabileceğiniz <xref:System.Linq.Queryable.AsQueryable%2A> döndürülecek yöntemi bir <xref:System.Linq.IQueryable%601> arabirimini uygulayan herhangi bir sınıftan <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Bu veri hizmetiniz için bir veri kaynağı olarak kullanılacak en genel koleksiyon türleri sağlar.  
  
 Yansıma sağlayıcı türü hiyerarşileri destekler. Daha fazla bilgi için bkz: [nasıl yapılır: yansıma sağlayıcı veri kullanarak hizmet oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
## <a name="inferring-the-data-model"></a>Veri modeli çıkarımını yapma  
 Veri Hizmeti oluşturduğunuzda, sağlayıcı yansıma kullanarak veri modeli oluşturur. Aşağıdaki liste, nasıl yansıma sağlayıcısı veri modeli oluşturur gösterir:  
  
-   Varlık kapsayıcı - veri döndüren özellikleri gösteren sınıf bir <xref:System.Linq.IQueryable%601> örneği. Yansıma tabanlı veri modeli yönlendirirken varlık kapsayıcısının hizmetinin kökü temsil eder. Tek bir varlık kapsayıcı sınıfı, belirli bir ad alanı için desteklenir.  
  
-   Varlık ayarlar - döndüren özellikleri <xref:System.Linq.IQueryable%601> örnekleri varlık kümeleri olarak kabul edilir. Varlık kümelerini, doğrudan sorgu içindeki kaynaklar olarak ele alınmıştır. Tek bir özellikte varlık kapsayıcısının dönebilirsiniz bir <xref:System.Linq.IQueryable%601> örneği belirli bir türde.  
  
-   Varlık türleri - türü `T` , <xref:System.Linq.IQueryable%601> varlık döndürür kümesi. Devralma Hiyerarşisi parçası olan sınıfları yansıma sağlayıcısı tarafından bir eşdeğer varlık türü hiyerarşiye çevrilir.  
  
-   Varlık anahtarları - bir varlık türü olduğu her veri sınıfı bir anahtarı özelliği olması gerekir. Bu özellik ile öznitelikli <xref:System.Data.Services.Common.DataServiceKeyAttribute> özniteliği (`[DataServiceKeyAttribute]`).  
  
    > [!NOTE]
    >  Yalnızca uygulamalıdır <xref:System.Data.Services.Common.DataServiceKeyAttribute> öznitelik varlık türünün bir örneğini benzersiz şekilde tanımlamak için kullanılan bir özelliği. Bu öznitelik bir gezinti özelliğine uygulandığında, göz ardı edilir.  
  
-   Varlık türü özellikleri - Varlık anahtarı dışında bir varlık türü gibi bir sınıfı erişilebilir, dizin oluşturucu olmayan özelliklerini yansıma sağlayıcısı değerlendirir:  
  
    -   Özelliği bir ilkel türü döndürürse, özelliği bir özellik bir varlık türü olduğu varsayılır.  
  
    -   Özellik de bir varlık türü olan bir türü döndürürse, özellik, bir çok-bir veya birebir ilişkisi "bir" ucunu temsil eden bir gezinti özelliği olduğu varsayılır.  
  
    -   Özelliği döndürürse bir <xref:System.Collections.Generic.IEnumerable%601> bir varlık türü, ardından özelliği, bir çok veya çok-bir ilişkisi "birçok" sonunu temsil eden bir gezinti özelliği olarak kabul edilir.  
  
    -   Özelliğinin dönüş türü bir değer türü ise, özelliği bir karmaşık tür temsil eder.  
  
> [!NOTE]
>  Varlık ilişkisel modelini temel alan bir veri modeli, yansıma sağlayıcısını temel modelleri ilişkisel veri anlaşılmıyor. İlişkisel veri aracılığıyla kullanıma sunmak için Entity Framework kullanması gereken [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
## <a name="data-type-mapping"></a>Veri türü eşlemesi  
 Bir veri modeli .NET Framework sınıflarını çıkarımı yapılan, veri modeli ilkel türler gibi .NET Framework veri türlerine eşlenir:  
  
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
>  .NET framework boş değer atanabilen değer türleri bir null atanamaz değer türleri ve karşılık gelen aynı veri modeli türlerine eşlenir.  
  
## <a name="enabling-updates-in-the-data-model"></a>Veri modelindeki güncelleştirmeleri etkinleştirme  
 Bu tür bir veri modeli kullanıma sunulan veri güncelleştirmelere izin vermek için yansıma sağlayıcı tanımlar bir <xref:System.Data.Services.IUpdatable> arabirimi. Bu arabirim güncelleştirmeleri gösterilen türlerine kalıcı hale getirmek nasıl veri hizmeti bildirir. Veri modeli tarafından tanımlanmış kaynaklara güncelleştirmeleri etkinleştirmek için varlık kapsayıcı sınıfı uygulamalıdır <xref:System.Data.Services.IUpdatable> arabirimi. Bir örnek uygulaması için <xref:System.Data.Services.IUpdatable> arabirim için bkz: [nasıl yapılır: bir LINQ to SQL veri kaynağı kullanarak bir veri hizmeti oluşturmak](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 <xref:System.Data.Services.IUpdatable> Arabirimi güncelleştirmeleri yansıma sağlayıcıyı kullanarak veri kaynağına yayılamaz böylece aşağıdaki üyeleri uygulanması gerektirir:  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Bir gezinti özelliğinden erişilen ilgili nesneler koleksiyonunu bir nesne eklemek için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Bekleyen verileri değişiklikleri iptal eder işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Belirtilen kapsayıcıda yeni bir kaynak oluşturmak için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Bir kaynak silmek için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Belirli bir sorgu ve tür adıyla belirlenen bir kaynak almak için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Bir kaynak özelliğinin değerini döndürmek için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Bir gezinti özelliğinden erişilen ilgili nesneler koleksiyonunu nesneye kaldırmak için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Belirtilen kaynak güncelleştirmek için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Belirli nesne örneği tarafından temsil edilen kaynak dönmek için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Tüm bekleyen değişiklikleri kaydetmek için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|İlgili nesne başvurusu bir gezinti özelliği kullanarak ayarlamak için işlevsellik sağlar.|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Bir kaynak özelliğinin değeri ayarlamak için işlevsellik sağlar.|  
  
## <a name="handling-concurrency"></a>Eşzamanlılık işleme  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]bir varlık için bir eşzamanlılık belirteci tanımlamanıza olanak sağlayarak bir iyimser eşzamanlılık modelini destekler. Bir veya daha fazla özellik varlık içerir, bu eşzamanlılık belirteci veri hizmeti tarafından bir değişiklik, güncellenen veya silinen istenen verilerde oluşup oluşmadığını belirlemek için kullanılır. Simge değerlerini istekte eTag alınan varlık geçerli değerlerden farklı bir özel durum veri hizmeti tarafından tetiklenir. <xref:System.Data.Services.ETagAttribute> Yansıma sağlayıcısında bir eşzamanlılık belirteci tanımlamak için bir varlık türü için uygulanır. Eşzamanlılık belirteci bir anahtar özellik veya bir gezinti özelliği içeremez. Daha fazla bilgi için bkz: [veri hizmeti güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="using-linq-to-sql-with-the-reflection-provider"></a>LINQ-SQL ile yansıma sağlayıcısını kullanma  
 Entity Framework varsayılan olarak yerel olarak desteklendiğinden ilişkisel veri ile kullanmak için önerilen veri sağlayıcısı olduğu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Ancak, bir veri hizmeti ile SQL sınıfları LINQ kullanmasını yansıma Sağlayıcısı'nı kullanabilirsiniz. <xref:System.Data.Linq.Table%601> Neden üzerinde yöntemleri tarafından döndürülen kümeleri <xref:System.Data.Linq.DataContext> LINQ to SQL Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) uygulama tarafından üretilen <xref:System.Linq.IQueryable%601> arabirimi. Bu, bu yöntemleri erişmek ve varlık verilerini SQL Server'dan SQL sınıfları için oluşturulan LINQ kullanarak dönmek yansıma sağlayıcı sağlar. Ancak, LINQ to SQL uygulamayan çünkü <xref:System.Data.Services.IUpdatable> arabirimi, ihtiyacınız var olan genişleten bir parçalı sınıf eklemek <xref:System.Data.Linq.DataContext> eklemek için kısmi sınıfı <xref:System.Data.Services.IUpdatable> uygulama. Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to SQL veri kaynağı kullanarak bir veri hizmeti oluşturmak](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

---
title: Nesne gerçekleştirme (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: bf75e126c2a44b6b9d151269046d2cb8110815cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774692"
---
# <a name="object-materialization-wcf-data-services"></a>Nesne gerçekleştirme (WCF Data Services)
Kullanırken **hizmet Başvurusu Ekle** iletişim kullanmak için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] bir .NET Framework tabanlı istemci uygulamasında akış, eşdeğeri veri sınıfları için veri modelindeki akış tarafından kullanıma sunulan her varlık türü oluşturulur. Daha fazla bilgi için [veri hizmeti istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Bir sorgu tarafından döndürülen varlık verilerini bu oluşturulan istemci veri hizmeti sınıfları birinin bir örneğine tanımdır. Birleştirme seçeneklerini ve izlenen nesneler için kimlik çözümü hakkında daha fazla bilgi için bkz: [veri hizmeti bağlamını yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Ayrıca, araç tarafından oluşturulan veri sınıflarını kullanmak yerine kendi istemci veri hizmeti sınıfları tanımlamanızı sağlar. Bu, kendi veri sınıfları olarak da bilinen "düz eski CLR nesnesi" kullanmanıza olanak sağlar (POCO) veri sınıfları. Bu tür özel veri sınıfları kullanırken ya da veri sınıfı özniteliği <xref:System.Data.Services.Common.DataServiceKeyAttribute> veya <xref:System.Data.Services.Common.DataServiceEntityAttribute> ve türü üzerinde veri hizmetinin veri modelinde istemci eşleşen tür adları ad emin olun.  
  
 Kitaplık sorgu yanıt iletisini aldıktan sonra döndürülen veriler gerçekleştiren [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sorgu türünü hizmet sınıflarını istemci verilerini örneğine akış. Bu nesneler düzeniyle için genel süreç aşağıdaki gibidir:  
  
1. İstemci Kitaplığı seri hale getirilmiş türünden okur `entry` öğe akışı bir yanıt iletisi ve doğru türde yeni bir örneğini aşağıdaki yollardan biriyle oluşturma denemesi:  
  
    - Ne zaman akışın türü bildirilen türü ile aynı ada sahip <xref:System.Data.Services.Client.DataServiceQuery%601>, bu tür yeni bir örneğini boş oluşturucu kullanılarak oluşturulur.  
  
    - Ne zaman akışın türü bildirilen türünden türetilmiş bir tür aynı ada sahip <xref:System.Data.Services.Client.DataServiceQuery%601>, bu türetilmiş bir türde yeni bir örneği boş oluşturucu kullanılarak oluşturulur.  
  
    - Zaman türü akışta bildirilmiş türüne eşleştirilemiyor <xref:System.Data.Services.Client.DataServiceQuery%601> veya herhangi bir türetilmiş tür, sorgulanan türü yeni bir örneğini boş oluşturucu kullanılarak oluşturulur.  
  
    - Zaman <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> özelliği ayarlanmışsa, varsayılan ad tabanlı tür eşlemesi ve yeni bir örneği tarafından döndürülen tür geçersiz kılmak için sağlanan temsilci çağrılır <xref:System.Func%602> bunun yerine oluşturulur. Bu temsilci, bir null değer döndürürse, sorgulanan türü yeni bir örneğini bunun yerine oluşturulur. Devralma senaryoları desteklemek için varsayılan ad tabanlı tür adı eşlemesine geçersiz kılmak için gerekebilir.  
  
2. İstemci Kitaplığı URI değerini okur `id` öğesinin `entry`, varlık kimlik değeri olduğu. Sürece bir <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> değerini <xref:System.Data.Services.Client.MergeOption.NoTracking> olan kullanıldığında, kimlik değeri nesnesinde izlemek için kullanılan <xref:System.Data.Services.Client.DataServiceContext>. Kimlik değeri bile varlığın birden çok kez sorgu yanıtına döndürdüğünde yalnızca tek bir varlık örneği, oluşturulduğunu garantilemek için de kullanılır.  
  
3. İstemci Kitaplığı, akış girişi özellikleri'ni okur ve yeni oluşturduğunuz nesneye karşılık gelen özellikleri ayarlayın. Aynı kimlik değeri zaten sahip bir nesne oluştuğunda <xref:System.Data.Services.Client.DataServiceContext>, özellikleri temel alınarak ayarlanmış <xref:System.Data.Services.Client.MergeOption> ayarıyla <xref:System.Data.Services.Client.DataServiceContext>. Yanıt, karşılık gelen bir özellik istemci türünde gerçekleşmez özellik değerlerini içerebilir. Bu durumda eylem değerine bağlıdır <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliği <xref:System.Data.Services.Client.DataServiceContext>. Bu özelliği ayarlandığında `true`, eksik özellik yoksayılır. Aksi takdirde bir hata oluşturulur. Özellikleri şu şekilde ayarlayın:  
  
    - Skaler özellikler, yanıt iletisinde giriş karşılık gelen değere ayarlanır.  
  
    - Karmaşık özellikler yanıttan karmaşık tür özelliklerini ile ayarlanan yeni bir karmaşık türü örneğine ayarlanır.  
  
    - İlgili varlık koleksiyonunu döndüren bir gezinti özellikleri, bir yeni veya mevcut örneğine ayarlanır <xref:System.Collections.Generic.ICollection%601>burada `T` ilgili varlık türüdür. İlgili nesneler içine yüklenmiş olan sürece bu koleksiyonu boş olan <xref:System.Data.Services.Client.DataServiceContext>. Daha fazla bilgi için [ertelenmiş içerik yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
        > [!NOTE]
        >  Oluşturulan istemci veri sınıfları veri bağlamayı destekler, gezinti özellikleri örneklerini döndürür <xref:System.Data.Services.Client.DataServiceCollection%601> bunun yerine sınıf. Daha fazla bilgi için [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
4. <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> Olayı oluşturulur.  
  
5. İstemci Kitaplığı nesnesine iliştirir <xref:System.Data.Services.Client.DataServiceContext>. Nesne ne zaman bağlı <xref:System.Data.Services.Client.MergeOption> olduğu <xref:System.Data.Services.Client.MergeOption.NoTracking>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Sorgu Projeksiyonları](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)

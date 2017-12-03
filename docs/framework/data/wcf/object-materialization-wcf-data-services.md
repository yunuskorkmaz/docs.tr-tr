---
title: Nesne Materialization (WCF Veri Hizmetleri)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8f20023e158b388ddd71e518ebcaa48c214252c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="object-materialization-wcf-data-services"></a>Nesne Materialization (WCF Veri Hizmetleri)
Kullandığınızda **hizmet Başvurusu Ekle** iletişim kullanmak için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] bir .NET Framework tabanlı istemci uygulamasında akış, eşdeğer veri sınıfları için akış tarafından kullanıma sunulan veri modelindeki her bir varlık türü oluşturulur. Daha fazla bilgi için bkz: [veri hizmeti istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Bir sorgu tarafından döndürülen varlık verilerini bu oluşturulan istemci veri hizmeti sınıfları birinin bir örneğine gerçekleştirildiği. Birleştirme seçeneklerini ve izlenen nesneler için kimlik çözümleme hakkında daha fazla bilgi için bkz: [veri Hizmet bağlamı yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Ayrıca, aracı tarafından oluşturulan veri sınıflarını kullanmak yerine, kendi istemci veri hizmeti sınıfları tanımlamanıza olanak sağlar. Bu, kendi veri sınıfları olarak da bilinen "düz eski CLR nesnesi" kullanmanızı sağlar (POCO) veri sınıfları. Bu tür özel veri sınıflarını kullanırken ya da veri sınıfı özniteliği <xref:System.Data.Services.Common.DataServiceKeyAttribute> veya <xref:System.Data.Services.Common.DataServiceEntityAttribute> ve türü veri hizmetinin veri modelindeki istemci eşleşme türü adları adları emin olun.  
  
 Kitaplık sorgu yanıt iletisini aldıktan sonra döndürülen veriler gerçeğe [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] istemci verilerini örneğine sorgu türlerinin hizmet sınıfları akış. Bu nesneler gerçekleştirilmesini için genel işlem aşağıdaki gibidir:  
  
1.  İstemci Kitaplığı serileştirilmiş türünden okur `entry` akış yanıt iletisi ve doğru türde yeni bir örneğini aşağıdaki yollardan biriyle oluşturma denemesi öğesinde:  
  
    -   Ne zaman akışın türü bildirilmedi türü aynı ada sahip <xref:System.Data.Services.Client.DataServiceQuery%601>, bu tür yeni bir örneğini boş Oluşturucusu kullanılarak oluşturulur.  
  
    -   Ne zaman akışın türü bildirilmedi türünden türetilmiş bir tür aynı ada sahip <xref:System.Data.Services.Client.DataServiceQuery%601>, bu türetilmiş türü yeni bir örneğini boş Oluşturucusu kullanılarak oluşturulur.  
  
    -   Ne zaman akışın türü bildirilmedi türüne eşleştirilemiyor <xref:System.Data.Services.Client.DataServiceQuery%601> veya herhangi bir türetilmiş türler, sorgulanan türü yeni bir örneğini boş Oluşturucusu kullanılarak oluşturulur.  
  
    -   Zaman <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> özelliği ayarlanmışsa, varsayılan ad tabanlı tür eşlemesi ve tarafından döndürülen türü yeni bir örneğini geçersiz kılmak için sağlanan temsilci çağrılır <xref:System.Func%602> bunun yerine oluşturulur. Bu temsilci boş bir değer döndürürse, sorgulanan türü yeni bir örneğini yerine oluşturulur. Devralma senaryoları desteklemek için varsayılan ad tabanlı türü adı eşlemesi geçersiz kılmak için gerekebilir.  
  
2.  URI değerinin istemci kitaplığı okur `id` öğesinin `entry`, varlık kimlik değeri olduğu. Sürece bir <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> değerini <xref:System.Data.Services.Client.MergeOption.NoTracking> olan kullanıldığında, kimlik değeri nesnesinde izlemek için kullanılan <xref:System.Data.Services.Client.DataServiceContext>. Kimlik değerini de bile bir varlık birden çok kez sorgu yanıtta döndürülen yalnızca tek bir varlık örneği, oluşturulduğunda olduğunu güvence altına almak için kullanılır.  
  
3.  İstemci Kitaplığı akış girdisinden Özellikleri'ni okur ve yeni oluşturulan bir nesne üzerinde karşılık gelen özelliklerini ayarlayın. Zaten aynı kimlik değeri olan bir nesneyi oluştuğunda <xref:System.Data.Services.Client.DataServiceContext>, özellikleri temel alınarak ayarlanır <xref:System.Data.Services.Client.MergeOption> ayarıyla <xref:System.Data.Services.Client.DataServiceContext>. Yanıt karşılık gelen özelliği istemci türünde oluşmaz özellik değerleri içerebilir. Bu durumda, eylem değerine bağlıdır <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliği <xref:System.Data.Services.Client.DataServiceContext>. Bu özellik ayarlandığında `true`, eksik özellik yok sayılır. Aksi takdirde bir hata oluştu. Özellikler aşağıdaki gibi ayarlayın:  
  
    -   Skaler özellikler yanıt iletisi girdisinde karşılık gelen değere ayarlanır.  
  
    -   Karmaşık özellikleri karmaşık tür özellikleri ile yanıttan ayarlanan yeni bir karmaşık tür örneğine ayarlanır.  
  
    -   İlgili varlık koleksiyonu döndüren bir gezinti özellikleri bir yeni veya var olan örneğine ayarlanmış <xref:System.Collections.Generic.ICollection%601>, burada `T` ilgili varlık türü değil. İlişkili nesneleri içine yüklemiş olduğunuz sürece bu koleksiyonu boş olan <xref:System.Data.Services.Client.DataServiceContext>. Daha fazla bilgi için bkz: [ertelenmiş içerik yüklenirken](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
        > [!NOTE]
        >  Oluşturulan istemci veri sınıfları veri bağlamayı destekleyen, gezinti özellikleri örneklerini döndürür <xref:System.Data.Services.Client.DataServiceCollection%601> yerine sınıfı. Daha fazla bilgi için bkz: [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
4.  <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> Olayı oluşturulur.  
  
5.  İstemci Kitaplığı nesneye ekler <xref:System.Data.Services.Client.DataServiceContext>. Nesne değil ne zaman bağlı <xref:System.Data.Services.Client.MergeOption> olan <xref:System.Data.Services.Client.MergeOption.NoTracking>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmeti sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Sorgu projeksiyonu](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)

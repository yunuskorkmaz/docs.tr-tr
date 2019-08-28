---
title: Nesne materialization (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: d45d472a2996c0b501af70a0a2a6d2d669dedb4d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043526"
---
# <a name="object-materialization-wcf-data-services"></a>Nesne materialization (WCF Veri Hizmetleri)

.NET Framework tabanlı bir istemci uygulamasında bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akışı tüketmek için hizmet başvurusu Ekle iletişim kutusunu kullandığınızda, akış tarafından kullanıma sunulan veri modelindeki her bir varlık türü için eşdeğer veri sınıfları oluşturulur. Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Bir sorgu tarafından döndürülen varlık verileri, bu oluşturulan istemci veri hizmeti sınıflarından birinin bir örneğine getirilir. İzlenen nesneler için birleştirme seçenekleri ve kimlik çözümlemesi hakkında daha fazla bilgi için bkz. [veri hizmeti bağlamını yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Ayrıca araç tarafından oluşturulan veri sınıflarını kullanmak yerine kendi istemci veri hizmeti sınıflarınızı tanımlamanızı sağlar. Bu, "düz eski CLR nesnesi" (POCO) veri sınıfları olarak da bilinen kendi veri sınıflarınızı kullanmanıza olanak sağlar. Bu tür özel veri sınıfları kullanılırken, ya da veri sınıfını, ya da <xref:System.Data.Services.Common.DataServiceKeyAttribute> veya <xref:System.Data.Services.Common.DataServiceEntityAttribute> istemci üzerindeki tür adlarının veri hizmetinin veri modelindeki tür adlarıyla eşleştiğinden emin olmalısınız.

Kitaplık sorgu yanıt iletisini aldıktan sonra, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı döndürülen verileri, sorgu türünde olan istemci veri hizmeti sınıflarının örneklerine çıkarır. Bu nesneleri üreten genel süreç aşağıdaki gibidir:

1. İstemci kitaplığı, yanıt iletisi akışındaki `entry` öğeden serileştirilmiş türü okur ve aşağıdaki yollarla doğru türün yeni bir örneğini oluşturmaya çalışır:

    - Akışta belirtilen tür, türüyle <xref:System.Data.Services.Client.DataServiceQuery%601>aynı ada sahip olduğunda, bu türün yeni bir örneği boş Oluşturucu kullanılarak oluşturulur.

    - Akışta belirtilen tür, <xref:System.Data.Services.Client.DataServiceQuery%601>türünden türetilmiş bir türle aynı ada sahip olduğunda, bu türetilmiş türün yeni bir örneği boş Oluşturucu kullanılarak oluşturulur.

    - Akışta belirtilen tür ya da <xref:System.Data.Services.Client.DataServiceQuery%601> türetilmiş türlerin türüyle eşleştirilemezse, sorgulanan türün yeni bir örneği boş Oluşturucu kullanılarak oluşturulur.

    - Özellik ayarlandığında, sağlanan temsilci varsayılan ad tabanlı tür eşlemesini geçersiz kılmak için çağrılır ve bunun yerine <xref:System.Func%602> tarafından döndürülen türün yeni bir örneği oluşturulur. <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> Bu temsilci null değer döndürürse, bunun yerine sorgulanan türün yeni bir örneği oluşturulur. Devralma senaryolarını desteklemek için varsayılan ad tabanlı tür adı eşlemesini geçersiz kılmak gerekebilir.

2. İstemci kitaplığı, varlığının kimlik değeri olan `id` öğesinin öğesinden `entry`URI değerini okur. Bir <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> <xref:System.Data.Services.Client.DataServiceContext>değeri kullanılmadığı takdirde, ' de nesnesini izlemek için kimlik değeri kullanılır. <xref:System.Data.Services.Client.MergeOption.NoTracking> Kimlik değeri, bir varlık sorgu yanıtında birden çok kez döndürüldüğünde bile yalnızca tek bir varlık örneğinin oluşturulmasını sağlamak için de kullanılır.

3. İstemci kitaplığı, akış girdisinden özellikleri okur ve yeni oluşturulan nesnede karşılık gelen özellikleri ayarlar. Aynı kimlik değerine sahip bir nesne öğesinde <xref:System.Data.Services.Client.DataServiceContext>zaten gerçekleşirse, özellikleri <xref:System.Data.Services.Client.MergeOption> ayarına <xref:System.Data.Services.Client.DataServiceContext>göre ayarlanır. Yanıt, karşılık gelen bir özelliğin istemci türünde gerçekleşmeyeceği özellik değerlerini içerebilir. Bu gerçekleştiğinde eylem, <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliğinin <xref:System.Data.Services.Client.DataServiceContext>değerine bağlıdır. Bu özellik olarak `true`ayarlandığında, eksik özellik yok sayılır. Aksi takdirde bir hata oluşur. Özellikler aşağıdaki gibi ayarlanır:

    - Skalar özellikler, yanıt iletisindeki girişte karşılık gelen değere ayarlanır.

    - Karmaşık özellikler, yanıttan karmaşık türün özellikleriyle ayarlanan yeni bir karmaşık tür örneğine ayarlanır.

    - İlgili varlıkların bir koleksiyonunu döndüren gezinti özellikleri yeni veya var olan bir örneğine <xref:System.Collections.Generic.ICollection%601>ayarlanır; burada `T` ilgili varlık türüdür. İlgili nesneler öğesine <xref:System.Data.Services.Client.DataServiceContext>yüklenmediği müddetçe bu koleksiyon boştur. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).

      > [!NOTE]
      > Oluşturulan istemci veri sınıfları veri bağlamayı destekledikleri zaman, gezinti özellikleri bunun yerine <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfının örneklerini döndürür. Daha fazla bilgi için bkz. [verileri denetimlere bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).

4. <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> Olay tetiklenir.

5. İstemci kitaplığı, nesnesini öğesine <xref:System.Data.Services.Client.DataServiceContext>ekler. Nesnesi, olduğunda <xref:System.Data.Services.Client.MergeOption> <xref:System.Data.Services.Client.MergeOption.NoTracking>eklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Sorgu Projeksiyonları](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)

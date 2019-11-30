---
title: Nesne materialization (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: 7a2b201e5690c4304e663e9429c54f377e05f556
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568914"
---
# <a name="object-materialization-wcf-data-services"></a>Nesne materialization (WCF Veri Hizmetleri)

.NET Framework tabanlı bir istemci uygulamasında açık veri Protokolü (OData) akışını tüketmek için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda, akış tarafından kullanıma sunulan veri modelindeki her bir varlık türü için eşdeğer veri sınıfları oluşturulur. Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma](generating-the-data-service-client-library-wcf-data-services.md). Bir sorgu tarafından döndürülen varlık verileri, bu oluşturulan istemci veri hizmeti sınıflarından birinin bir örneğine getirilir. İzlenen nesneler için birleştirme seçenekleri ve kimlik çözümlemesi hakkında daha fazla bilgi için bkz. [veri hizmeti bağlamını yönetme](managing-the-data-service-context-wcf-data-services.md).

WCF Veri Hizmetleri, araç tarafından oluşturulan veri sınıflarını kullanmak yerine kendi istemci veri hizmeti sınıflarınızı tanımlamanızı da sağlar. Bu, "düz eski CLR nesnesi" (POCO) veri sınıfları olarak da bilinen kendi veri sınıflarınızı kullanmanıza olanak sağlar. Bu tür özel veri sınıflarını kullanırken, veri sınıfını <xref:System.Data.Services.Common.DataServiceKeyAttribute> veya <xref:System.Data.Services.Common.DataServiceEntityAttribute> ile özniteleyebilir ve istemcideki tür adlarının veri hizmetinin veri modelindeki tür adlarıyla eşleştiğinden emin olun.

Kitaplık sorgu yanıt iletisini aldıktan sonra, OData akışından döndürülen verileri sorgu türünde olan istemci veri hizmeti sınıflarının örneklerine çıkarır. Bu nesneleri üreten genel süreç aşağıdaki gibidir:

1. İstemci kitaplığı, yanıt iletisi akışındaki `entry` öğeden serileştirilmiş türü okur ve aşağıdaki yollarla doğru türün yeni bir örneğini oluşturmaya çalışır:

    - Akışta bildirildiği tür <xref:System.Data.Services.Client.DataServiceQuery%601>türüyle aynı ada sahip olduğunda, bu türün yeni bir örneği boş Oluşturucu kullanılarak oluşturulur.

    - Akışta bildirildiği tür, <xref:System.Data.Services.Client.DataServiceQuery%601>türünden türetilmiş bir türle aynı ada sahip olduğunda, bu türetilmiş türün yeni bir örneği boş Oluşturucu kullanılarak oluşturulur.

    - Akışta belirtilen tür <xref:System.Data.Services.Client.DataServiceQuery%601> veya herhangi bir türetilmiş tür türüyle eşleştirilemezse, sorgulanan türün yeni bir örneği boş Oluşturucu kullanılarak oluşturulur.

    - <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> özelliği ayarlandığında, sağlanan temsilci varsayılan ad tabanlı tür eşlemesini geçersiz kılmak için çağrılır ve bunun yerine <xref:System.Func%602> tarafından döndürülen türün yeni bir örneği oluşturulur. Bu temsilci null değer döndürürse, bunun yerine sorgulanan türün yeni bir örneği oluşturulur. Devralma senaryolarını desteklemek için varsayılan ad tabanlı tür adı eşlemesini geçersiz kılmak gerekebilir.

2. İstemci kitaplığı, varlığın kimlik değeri olan `entry``id` öğeden URI değerini okur. <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> bir <xref:System.Data.Services.Client.MergeOption.NoTracking> değeri kullanılmamışsa, kimlik değeri <xref:System.Data.Services.Client.DataServiceContext>nesneyi izlemek için kullanılır. Kimlik değeri, bir varlık sorgu yanıtında birden çok kez döndürüldüğünde bile yalnızca tek bir varlık örneğinin oluşturulmasını sağlamak için de kullanılır.

3. İstemci kitaplığı, akış girdisinden özellikleri okur ve yeni oluşturulan nesnede karşılık gelen özellikleri ayarlar. Aynı kimlik değerine sahip bir nesne <xref:System.Data.Services.Client.DataServiceContext>zaten gerçekleşirse özellikler, <xref:System.Data.Services.Client.DataServiceContext><xref:System.Data.Services.Client.MergeOption> ayarına göre ayarlanır. Yanıt, karşılık gelen bir özelliğin istemci türünde gerçekleşmeyeceği özellik değerlerini içerebilir. Bu gerçekleştiğinde, eylem <xref:System.Data.Services.Client.DataServiceContext><xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliğinin değerine bağlıdır. Bu özellik `true`olarak ayarlandığında, eksik özellik yok sayılır. Aksi takdirde bir hata oluşur. Özellikler aşağıdaki gibi ayarlanır:

    - Skalar özellikler, yanıt iletisindeki girişte karşılık gelen değere ayarlanır.

    - Karmaşık özellikler, yanıttan karmaşık türün özellikleriyle ayarlanan yeni bir karmaşık tür örneğine ayarlanır.

    - İlgili varlıkların bir koleksiyonunu döndüren gezinti özellikleri yeni veya mevcut bir <xref:System.Collections.Generic.ICollection%601>örneğine ayarlanır; burada `T` ilgili varlığın türüdür. İlgili nesneler <xref:System.Data.Services.Client.DataServiceContext>yüklenmediği takdirde bu koleksiyon boştur. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).

      > [!NOTE]
      > Oluşturulan istemci veri sınıfları veri bağlamayı destekledikleri zaman, gezinti özellikleri bunun yerine <xref:System.Data.Services.Client.DataServiceCollection%601> sınıfının örneklerini döndürür. Daha fazla bilgi için bkz. [verileri denetimlere bağlama](binding-data-to-controls-wcf-data-services.md).

4. <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> olay tetiklenir.

5. İstemci kitaplığı, nesneyi <xref:System.Data.Services.Client.DataServiceContext>iliştirir. <xref:System.Data.Services.Client.MergeOption> <xref:System.Data.Services.Client.MergeOption.NoTracking>nesne eklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
- [Sorgu Projeksiyonları](query-projections-wcf-data-services.md)

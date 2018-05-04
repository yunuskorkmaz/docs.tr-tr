---
title: Geçiş konuları (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: ab048551f0b6ee9301e93d25257b4dfbff748af0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="migration-considerations-entity-framework"></a>Geçiş konuları (Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework var olan bir uygulamaya birkaç avantaj sağlar. Çoğu biri veri kaynağındaki şemasından uygulama tarafından kullanılan veri yapılarını ayırmak için kavramsal model kullanma yeteneğini bu yararları önemlidir. Bu kolayca gelecekteki depolama modeli için veya uygulamaya karşılayan değişiklikleri yapmadan veri kaynağına kendisini değişiklik yapmanızı sağlar. Kullanmanın yararları hakkında daha fazla bilgi için [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bkz: [Entity Framework genel bakış](../../../../../docs/framework/data/adonet/ef/overview.md) ve [varlık veri modeli](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Avantajlarından yararlanmak için [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], varolan bir uygulamaya geçirebileceğiniz [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Bazı görevleri geçirilen tüm uygulamalar için ortak olan. Bu ortak görevler kullanmak için uygulamayı yükseltme içerir [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 3.5 Service Pack 1 (SP1) sürümünden başlayarak, modelleri tanımlama ve eşleme ve Entity Framework yapılandırma. Bir uygulamaya geçirirken [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], uygulama ek noktalar vardır. Bu noktalar Geçirilmekte olan uygulama türünü ve belirli bir uygulamanın işlevselliğini bağlı. Bu konu, mevcut Uygulamayı yükselttiğinizde kullanmak için en iyi yaklaşımı seçmenize yardımcı olacak bilgiler sağlar.  
  
## <a name="general-migration-considerations"></a>Genel geçiş konuları  
 Herhangi bir uygulama için geçiş yaparken aşağıdaki maddeler geçerlidir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
-   Kullanan herhangi bir uygulama [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürüm 3.5 SP1 ile başlayarak geçiş yapabilir Entity Framework için Entity Framework veri sağlayıcısı uygulama tarafından kullanılan veri kaynağı için desteklediği sürece.  
  
-   Bu sağlayıcı Entity Framework destekliyorsa bile Entity Framework Veri kaynağı sağlayıcı tüm işlevselliğini desteklemiyor olabilir.  
  
-   Büyük veya karmaşık uygulama için aynı anda tüm uygulama Entity Framework geçirmek için gerekli değildir. Ancak, veri kaynağı zaman Entity Framework kullanmaz uygulama herhangi bir kısmını hala değiştirilmelidir.  
  
-   Entity Framework tarafından kullanılan veri sağlayıcı bağlantısı, uygulamanızın diğer bölümleriyle çünkü paylaşılabilir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] kullanan [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] veri kaynağına erişmek için veri sağlayıcıları. Örneğin, SqlClient sağlayıcısı, bir SQL Server veritabanına erişmek için Entity Framework tarafından kullanılır. Daha fazla bilgi için bkz: [EntityClient sağlayıcısı için Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Genel geçiş görevleri  
 Varolan bir uygulamaya geçirilecek yolu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama türü ve var olan veri erişim stratejisi bağlıdır. Varolan bir uygulamaya geçirdiğinizde ancak, her zaman aşağıdaki görevleri gerçekleştirmeniz gerekir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  İle başlayan varlık veri modeli araçları kullandığınızda bu görevlerin tümü otomatik olarak gerçekleştirilir [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)]. Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
1.  Uygulamayı yükseltin.  
  
     Visual Studio'nun önceki bir sürümü kullanılarak oluşturulmuş bir proje ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] kullanılacak yükseltilmelidir [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] SP1 ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürüm 3.5 SP1 ile başlayarak.  
  
2.  Modelleri ve eşleme tanımlayın.  
  
     Model ve eşleme dosyaları varlıklar kavramsal modelde tanımlayın; veri kaynağındaki tablolar gibi yapıları, yordamlar ve görünümlerin depolanan; ve varlıkları ve veri kaynağı Yapılar arasındaki eşleme. Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model el ile tanımlamak](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).  
  
     Depolama modelinde tanımlanan türleri veri kaynağı nesneleri adıyla eşleşmelidir. Var olan uygulama veri nesneleri olarak kullanıma sunar, kavramsal modelde tanımlanan özellikler ve varlıkları adları bu var olan veri sınıfları ve özellikleri ile eşleştiğinden emin olun. Daha fazla bilgi için bkz: [nasıl yapılır: özelleştirme modelleme ve özel nesneleri ile çalışma dosyalarına eşleme](http://msdn.microsoft.com/library/bb40c4db-0121-4e45-a167-8fb06707a708).  
  
    > [!NOTE]
    >  Entity Data Model Designer, varolan nesneleri eşleştirmek için kavramsal model varlıklarda yeniden adlandırmak için kullanılabilir. Daha fazla bilgi için bkz: [Entity Data Model Designer](http://msdn.microsoft.com/library/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf).  
  
3.  Bağlantı dizesini tanımlar.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kavramsal model sorguları yürütülürken özel olarak biçimlendirilmiş bağlantı dizesini kullanır. Bu bağlantı dizesi modeli ve eşleme dosyaları ve veri kaynağı bağlantısı hakkındaki bilgileri yalıtır. Daha fazla bilgi için bkz: [nasıl yapılır: bağlantı dizesini tanımlar](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4.  Visual Studio projesini yapılandırın.  
  
     Başvurular [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] derlemeler, model ve eşleme dosyaları için Visual Studio projesi eklenmesi gerekiyor. Bunlar uygulama bağlantı dizesinde belirtilen konumda ile dağıtılan sağlamak için projeyi Bu eşleme dosyaları ekleyebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: bir Entity Framework projesi el ile yapılandırmanız](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Var olan nesneleri uygulamalarla dikkate alınacak noktalar  
 İle başlayarak [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] "düz eski" destekleyen CLR nesnelerini (POCO) Kalıcılık kullanmayan nesneleri olarak da bilinir. Çoğu durumda, var olan nesneleri ile çalışabilirsiniz [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] küçük değişiklikler yaparak. Daha fazla bilgi için bkz: [POCO varlıklarla çalışmaya](http://msdn.microsoft.com/library/5e0fb82a-b6d1-41a1-b37b-c12db61629d3). Bir uygulamaya da geçirebilirsiniz [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve Entity Framework araçları tarafından oluşturulan veri sınıflarını kullanın. Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>ADO.NET sağlayıcılarını kullanan uygulamalar için ilgili önemli noktalar  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] SqlClient gibi sağlayıcıları tablo veri döndürmek için bir veri kaynağını sorgulamak etkinleştirin. Veri da yüklenebilir içine bir [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] veri kümesi. Aşağıdaki listede varolan kullanan bir uygulamayı yükseltmeyle ilgili konular açıklanmaktadır [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] sağlayıcısı:  
  
 Tablo verisi bir veri okuyucu kullanarak görüntüleme.  
 Yürütme düşünebilirsiniz bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgu EntityClient sağlayıcısı kullanarak ve döndürülen numaralandırma <xref:System.Data.EntityClient.EntityDataReader> nesnesi. Uygulamanız bir veri okuyucu kullanarak tablo verileri görüntüler ve tarafından sağlanan özellikleri gerektirmez bunu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] veri nesnelerini gerçekleştirilmesini için değişiklik izleme ve güncelleştirmeleri yapma. Veri kaynağına güncelleştirmeleri yapar mevcut veri erişim kodu kullanmaya devam edebilirsiniz, ancak erişilen varolan bir bağlantıyı kullanabilirsiniz <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> özelliği <xref:System.Data.EntityClient.EntityConnection>. Daha fazla bilgi için bkz: [EntityClient sağlayıcısı için Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Veri kümeleri ile çalışma.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bellek içi Kalıcılık dahil olmak üzere veri kümesi tarafından sağlanan aynı işlevlerin birçoğunu değişiklik izleme, veri bağlama ve XML verileri olarak nesneleri seri hale getirme sağlar. Daha fazla bilgi için bkz: [nesneleriyle çalışma](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Varsa [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] işlevleri sağlamaz, uygulamanız tarafından gereken veri kaynağının veri kümesi hala avantajlarından biri LINQ sorgularını kullanarak yararlanabilirsiniz [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]. Daha fazla bilgi için bkz: [LINQ-DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Denetimlere veri bağlama uygulamaları için ilgili önemli noktalar  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Veri kümesi veya bir gibi bir veri kaynağındaki kapsülleyen olanak sağlayan [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] veri kaynağı denetimi ve ardından kullanıcı arabirimi öğeleri bu verileri denetimlere bağlama. Aşağıdaki listede Entity Framework verilere denetimler bağlama konuları açıklanmaktadır.  
  
 Denetimlere veri bağlama.  
 Kavramsal modelin sorguladığınızda [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] varlık türleri örnekleri olan nesneler olarak verileri döndürür. Bu nesneler denetimlere doğrudan bağlı olabilir ve bu bağlama güncelleştirmeleri destekler. Bir denetimde bir satırda gibi veri değişikliklerini Bunun anlamı bir <xref:System.Windows.Forms.DataGridView>, otomatik olarak veritabanına kaydedilir, <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> yöntemi çağrılır.  
  
 Uygulamanızı verileri görüntülemek için bir sorgunun sonuçlarını sıralar varsa bir <xref:System.Windows.Forms.DataGridView> veya diğer tür veri bağlamayı destekleyen denetimin sonucuna denetimi bağlamak için uygulamanızın değiştirebilirsiniz bir <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Daha fazla bilgi için bkz: [denetimleri bağlama nesnelere](http://msdn.microsoft.com/library/2fd34855-929b-4303-a91e-4bb69d958f2b).  
  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] veri kaynağı denetimleri.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Veri bağlamanın basitleştirmek üzere tasarlanmış bir veri kaynağı denetimi içeren [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Web uygulamaları. Daha fazla bilgi için bkz: [Entity Framework Veri kaynağı denetimi](http://msdn.microsoft.com/library/1f09af00-9578-4744-a029-765710a3c83f).  
  
## <a name="other-considerations"></a>Diğer Konular  
 Entity Framework uygulamalarını belirli türlerdeki geçirdiğinizde uygulayabilir noktalar şunlardır:  
  
 Veri Hizmetleri kullanıma uygulamalar.  
 Web Hizmetleri ve Windows Communication Foundation (WCF) tabanlı uygulamaları bir XML istek/yanıt ileti biçimi kullanarak bir temel alınan veri kaynağından kullanıma sunar. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] İkili, XML, kullanarak varlık nesnesi seri hale getirme destekler veya WCF veri sözleşmesi seri hale getirme. İkili ve WCF serileştirme nesne grafiklerinin tam serileştirmek destekler. Daha fazla bilgi için bkz: [N katmanlı uygulamalar oluşturma](http://msdn.microsoft.com/library/9439d2ba-6b5f-44e8-be65-8a442d922cbb).  
  
 XML verilerini kullanan uygulamalar.  
 Nesne seri hale getirme oluşturmanıza olanak sağlayan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Veri Hizmetleri. Bu Hizmetleri Internet AJAX tabanlı uygulamalar gibi XML verileri kullanan uygulamalar için veriler sağlar. Bu durumlarda, kullanmayı [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Bu veri hizmetleri varlık veri modelini temel alan ve standart temsili durum aktarımı (REST) HTTP eylemleri kullanarak varlık verilerini dinamik erişim sağlamak gibi Al koy ve gönderin. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri 4.5](../../../../../docs/framework/data/wcf/index.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Yerel XML veri türünü desteklemiyor. Bu bir XML sütunu içeren bir tabloya bir varlık eşlendiğinde XML sütunu için eşdeğer varlık özelliği bir dize anlamına gelir. Nesneleri, bağlantısı kesilen ve XML olarak serileştirilmiş. Daha fazla bilgi için bkz: [seri hale getirme nesnelerini](http://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
 Uygulamanızı sorgulama XML verileri gerektiriyorsa, hala LINQ sorgularını avantajları LINQ-XML kullanarak yararlanabilirsiniz. Daha fazla bilgi için bkz: [LINQ-XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 Durumunu korumak uygulamalar.  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Web uygulamaları bir Web sayfası veya bir kullanıcı oturum durumunu sık bakımını yapmanız gerekir. Nesneler bir <xref:System.Data.Objects.ObjectContext> örneği depolanan istemci görünüm durumu veya sunucu üzerinde oturum durumu ve daha sonra alınabilir ve yeni bir nesne bağlamına yeniden. Daha fazla bilgi için bkz: [Attaching ve ayırma nesneleri](http://msdn.microsoft.com/library/41d5c1ef-1b78-4502-aa10-7e1438d62d23).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dağıtım Konuları](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Entity Framework Terimleri](../../../../../docs/framework/data/adonet/ef/terminology.md)

---
title: Geçiş konuları (varlık çerçevesi)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 359e373476398bb26f06eb86eb13296ab05d2705
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089893"
---
# <a name="migration-considerations-entity-framework"></a>Geçiş konuları (varlık çerçevesi)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework, var olan bir uygulama için çeşitli avantajlar sağlar. Çoğu biri veri kaynağındaki şemasından uygulama tarafından kullanılan veri yapılarını ayırmak için kavramsal bir modeli kullanma olanağı Bu avantajlar önemlidir. Bu depolama modelinin veya uygulamaya telafi değişiklik yapmadan veri kaynağına kendisini gelecekteki değişikliklere kolayca yapmanıza olanak sağlar. Kullanmanın avantajları hakkında daha fazla bilgi için [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bkz: [Entity Framework'e Genel Bakış](../../../../../docs/framework/data/adonet/ef/overview.md) ve [varlık veri modeli](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Avantajlarından yararlanmak için [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], mevcut bir uygulamaya geçirebileceğiniz [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Bazı görevleri, geçirilen tüm uygulamalar için ortaktır. Bu ortak görevlerin kullanmak için uygulamayı yükseltme dahil [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 3.5 Service Pack 1 (SP1) sürümünden itibaren modelleri tanımlama ve eşleme ve Entity Framework yapılandırma. Bir uygulamaya geçirdiğinizde [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], geçerli olan ek hususlar vardır. Bu noktalar, Geçirilmekte olan uygulama türünü ve belirli bir uygulamanın işlevselliğini bağlıdır. Bu konu, mevcut bir uygulamayı yükseltme sırasında kullanılacak en iyi yaklaşım seçmenize yardımcı olacak bilgiler sağlar.  
  
## <a name="general-migration-considerations"></a>Genel geçiş konuları  
 Herhangi bir uygulama için geçiş yaptığınızda, aşağıdaki maddeler geçerlidir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
-   Kullanan tüm uygulamaları [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 3.5 SP1 sürümünden itibaren geçirilebilir Entity Framework için Entity Framework veri sağlayıcısı uygulama tarafından kullanılan veri kaynağı için desteklediği sürece.  
  
-   Entity Framework sağlayıcının destekler olsa bile Entity Framework Veri kaynağı sağlayıcı tüm işlevleri desteklemiyor olabilir.  
  
-   Büyük veya karmaşık uygulama için tek seferde tüm uygulama Entity Framework geçirme gerekmez. Ancak, veri kaynağı, varlık çerçevesi kullanmayan uygulamayı herhangi bir bölümünü hala değiştirilmelidir.  
  
-   Entity Framework tarafından kullanılan veri sağlayıcısına bağlantı uygulamanızın diğer bölümleriyle çünkü paylaşılabilir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] kullanan [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] veri kaynağına erişmek için veri sağlayıcı. Örneğin, SqlClient sağlayıcısı, SQL Server veritabanına erişmek için Entity Framework tarafından kullanılır. Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Sık karşılaşılan geçiş görevleri  
 Mevcut bir uygulamasına geçirmek için yol [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama türü ve mevcut veri erişim stratejisi bağlıdır. Mevcut bir uygulamasına geçirirken ancak, her zaman aşağıdaki görevleri gerçekleştirmeniz [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Visual Studio 2008 ile başlayan varlık veri modeli araçları kullandığınızda bu görevlerin tümü otomatik olarak gerçekleştirilir. Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
1.  Uygulamayı yükseltin.  
  
     Visual Studio'nun önceki bir sürümü kullanılarak oluşturulmuş bir projeyi ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Visual Studio 2008 SP1'i kullanmak için yükseltilmesi gerekir ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 3.5 SP1 sürümünden itibaren.  
  
2.  Eşleme ve modelleri tanımlar.  
  
     Model ve eşleme dosyalarını kavramsal modeldeki varlıklar tanımlayın. yapıları tablolar gibi veri kaynağı, saklı yordamlar ve görünümleri; ve varlıkları ve veri kaynağı Yapılar arasındaki eşleme. Daha fazla bilgi için [nasıl yapılır: El ile bir modeli tanımlamak ve dosyaları eşleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).  
  
     Depolama modelde tanımlı türleri nesne veri kaynağı adı eşleşmelidir. Var olan uygulama veri nesneleri olarak sunarsa, kavramsal modelde tanımlı özellikleri ve varlıkları adlarını bu var olan veri sınıfları ve özellikleri ile eşleştiğinden emin olun. Daha fazla bilgi için [nasıl yapılır: Modelleme ve özel nesneler ile çalışma dosyaları eşleme özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100)).  
  
    > [!NOTE]
    >  Varlık veri modeli Tasarımcısı, varolan nesneleri eşleştirmek için kavramsal modeldeki varlıklar yeniden adlandırmak için kullanılabilir. Daha fazla bilgi için [varlık veri modeli Tasarımcısı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3.  Bağlantı dizesini tanımlar.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Kavramsal modeline karşı sorgular yürütülürken bir özel olarak biçimlendirilmiş bağlantı dizesini kullanır. Bu bağlantı dizesi, model ve eşleme dosyalarını ve veri kaynağı bağlantısı ile ilgili bilgileri yalıtır. Daha fazla bilgi için [nasıl yapılır: Bağlantı dizesi tanımlama](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4.  Visual Studio projesini yapılandırın.  
  
     Başvurular [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] derlemeleri ve model ve eşleme dosyalarını Visual Studio projeye eklenmesi gerekiyor. Bu eşleme dosyaları, bunlar bağlantı dizesinde belirtilen konumda uygulamayla dağıtıldığından emin olmak için projeye ekleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: El ile bir Entity Framework projesinin yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Varolan nesneleri olan uygulamalar için dikkat edilmesi gerekenler  
 İle başlayarak [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] "düz eski" destekleyen CLR nesnelerine (POCO), Kalıcılık ignorant nesneleri olarak da bilinir. Çoğu durumda, var olan nesne ile çalışabilir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] küçük değişiklikler yaparak. Daha fazla bilgi için [Working with Entities POCO](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Ayrıca bir uygulamaya geçirebileceğiniz [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve Entity Framework araçları tarafından oluşturulan veri sınıflarını kullanın. Daha fazla bilgi için [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>ADO.NET sağlayıcıları kullanan uygulamalar için dikkat edilmesi gerekenler  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] SqlClient, örneğin bir sağlayıcı sekmeli veri döndürmek için bir veri kaynağını olanak sağlar. Veri da yüklenebilir içine bir [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] veri kümesi. Aşağıdaki listede açıklanmıştır varolan kullanan bir uygulamayı yükseltme için dikkat edilecekler [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] sağlayıcısı:  
  
- Bir veri okuyucu kullanarak tablo verileri görüntüleme.  

  Yürütme düşünebilirsiniz bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] EntityClient Sağlayıcısı'nı kullanarak ve döndürülen numaralandırma sorgu <xref:System.Data.EntityClient.EntityDataReader> nesne. Uygulamanızı kullanarak bir veri okuyucu sekmeli veri görüntüler ve tarafından sağlanan özellikleri gerektirmez bunu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] değişiklikler veri nesnelerine düzeniyle için izleme ve güncelleştirmeler yapma. Güncelleştirmeleri veri kaynağına hale getirir. mevcut veri erişim kodu kullanmaya devam edebilirsiniz, ancak erişilen varolan bir bağlantıyı kullanabilirsiniz <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> özelliği <xref:System.Data.EntityClient.EntityConnection>. Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
- Veri kümeleri ile çalışma.  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Birçok aynı işlevler bellek içi kalıcılığı dahil olmak üzere veri kümesi tarafından sağlanan değiştirmek izleme, veri bağlama ve XML verileri olarak nesneler serileştiriliyor sağlar. Daha fazla bilgi için [nesneleriyle çalışma](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
  Varsa [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] işlevlerini sağlamadığını uygulamanızın ihtiyaç duyduğu veri kümesi, yine de LINQ sorguları avantajlarını kullanarak yararlanabilirsiniz [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]. Daha fazla bilgi için [LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Verileri denetimlere bağlayabilirsiniz uygulamalar için dikkat edilmesi gerekenler  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Veri kümesi veya bir gibi bir veri kaynağındaki kapsülleyen sayesinde [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] veri kaynak denetimi ve daha sonra kullanıcı arabirimi öğeleri bu verileri denetimlere bağlayabilirsiniz. Aşağıdaki listede, Entity Framework verilere denetimler bağlama konuları açıklanmaktadır.  
  
- Veriyi denetimlere bağlama.  

  Kavramsal model sorguladığınızda [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] verileri varlık türleri örnekleri olan nesneler olarak döndürür. Bu nesneleri denetimlere doğrudan bağlanabilir ve bu bağlama, güncelleştirmeler destekler. Bir satır gibi bir denetimin veri değişikliklerini Bunun anlamı bir <xref:System.Windows.Forms.DataGridView>otomatik olarak veritabanına kaydedilir, <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> yöntemi çağrılır.  
  
  Uygulama verileri görüntülemek için bir sorgunun sonuçlarını sıralar, bir <xref:System.Windows.Forms.DataGridView> veya denetimin sonucuna bağlanması için uygulamanızı değiştirebileceğiniz diğer veri bağlamayı destekleyen bir denetim türü, bir <xref:System.Data.Objects.ObjectQuery%601>.  
  
  Daha fazla bilgi için [denetimlerine nesne bağlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] veri kaynağı denetimleri.  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] İçinde veri bağlamayı kolaylaştırmak amacıyla tasarlanmış bir veri kaynağı denetimi içeren [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Web uygulamaları. Daha fazla bilgi için [EntityDataSource Web sunucusu denetimine genel bakış](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Diğer Konular  
 Entity Framework uygulamalarını belirli türlerdeki geçirdiğinizde, uygulanabilir dikkat edilecek noktalar aşağıda verilmiştir.  
  
- Veri Hizmetleri kullanıma sunan uygulamalar.  

  Web Hizmetleri ve Windows Communication Foundation (WCF) tabanlı uygulamaları istek/yanıt XML ileti biçimi kullanarak bir temel alınan veri kaynağı kullanıma sunar. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] İkili, XML, kullanarak varlık nesneleri serileştirmek destekler veya WCF veri sözleşme seri hale getirme. İkili ve WCF serileştirme tam nesne grafiklerini serileştirme destekler. Daha fazla bilgi için [N katmanlı uygulamalar oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- XML verilerini kullanan uygulamalar.  

  Nesne serileştirme oluşturmanıza olanak sağlar [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Veri Hizmetleri. Bu hizmetler Internet AJAX tabanlı uygulamalar gibi XML verileri kullanan uygulamalar için veri sağlar. Bu gibi durumlarda kullanmayı [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Şu veri hizmetlerini varlık veri modelini temel ve standart temsili durum aktarımı (REST) HTTP eylemleri kullanarak varlık verilerini dinamik erişim sağlamak gibi Al koy ve gönderin. Daha fazla bilgi için [WCF Veri Hizmetleri 4.5](../../../../../docs/framework/data/wcf/index.md).  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Yerel XML veri türünü desteklemiyor. Bu, bir XML sütunu içeren bir tabloya bir varlık eşlendiğinde XML sütunu için eşdeğer varlık özelliği bir dize olduğu anlamına gelir. Nesneler, bağlantısı kesilmiş ve XML olarak serileştirilmiş. Daha fazla bilgi için [nesneleri serileştirmek](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Uygulamanızın gerektirdiği sorgu XML verileri, LINQ to XML kullanarak LINQ sorgularının avantajlarından alabilir. Daha fazla bilgi için [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) veya [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
- Durumunu korumak uygulamalar.  

  [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Web uygulamaları bir Web sayfasının veya bir kullanıcı oturumunun durumunu sık sürdürmeniz gerekir. Nesneler bir <xref:System.Data.Objects.ObjectContext> örneği istemci görünüm durumu veya sunucu üzerinde oturum durumunu depolanan ve daha sonra alınabilir ve yeni bir nesne bağlamına eklenemeyeceği. Daha fazla bilgi için [iliştirme ve nesneleri ayırmaya](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım Hakkında Önemli Noktalar](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Entity Framework Terimleri](../../../../../docs/framework/data/adonet/ef/terminology.md)

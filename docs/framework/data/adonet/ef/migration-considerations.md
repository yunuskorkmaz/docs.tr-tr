---
title: Geçiş konuları (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 168aec6ef369f446cfac22ee5c4361fa06aaf16d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569449"
---
# <a name="migration-considerations-entity-framework"></a>Geçiş konuları (Entity Framework)
ADO.NET Entity Framework, var olan bir uygulamaya çeşitli avantajlar sağlar. Bu avantajlardan en önemli olanlarından biri, uygulama tarafından kullanılan veri yapılarını veri kaynağındaki şemadan ayırmak için kavramsal bir model kullanma yeteneğidir. Bu, uygulamaya telafi değişikliği yapmadan depolama modelinde veya veri kaynağında ileride yapılacak değişiklikler yapmanızı sağlar. Entity Framework kullanmanın avantajları hakkında daha fazla bilgi için bkz. [Entity Framework genel bakış](overview.md) ve [varlık veri modeli](../entity-data-model.md).  
  
 Entity Framework avantajlarından yararlanmak için, mevcut bir uygulamayı Entity Framework geçirebilirsiniz. Bazı görevler, geçirilen tüm uygulamalarda ortaktır. Bu ortak görevler, sürüm 3,5 hizmet paketi 1 ' den (SP1) başlayarak .NET Framework kullanmak, model ve eşlemeyi tanımlamak ve Entity Framework yapılandırmak için uygulamayı yükseltmeyi içerir. Bir uygulamayı Entity Framework geçirdiğinizde, uygulanan ek hususlar vardır. Bu noktalar, geçirilmekte olan uygulamanın türüne ve uygulamanın belirli işlevlerine bağlıdır. Bu konuda, var olan bir uygulamayı yükselttiğinizde kullanılacak en iyi yaklaşımı seçmenize yardımcı olacak bilgiler sağlanmaktadır.  
  
## <a name="general-migration-considerations"></a>Genel geçiş konuları  
 Entity Framework herhangi bir uygulamayı geçirdiğinizde aşağıdaki noktalar geçerlidir:  
  
- Uygulama tarafından kullanılan veri kaynağı için veri sağlayıcısı Entity Framework desteklediği sürece, sürüm 3,5 SP1 ile başlayan .NET Framework kullanan uygulamalar Entity Framework geçirilebilir.  
  
- Entity Framework, bu sağlayıcı Entity Framework desteklese bile, bir veri kaynağı sağlayıcısının tüm işlevlerini desteklemeyebilir.  
  
- Büyük veya karmaşık bir uygulama için tüm uygulamayı tek seferde Entity Framework geçirmeniz gerekmez. Ancak, Entity Framework kullanmayan uygulamanın herhangi bir bölümü, veri kaynağı değiştiğinde yine de değiştirilmelidir.  
  
- Entity Framework veri kaynağına erişmek için ADO.NET veri sağlayıcılarını kullandığından Entity Framework tarafından kullanılan veri sağlayıcısı bağlantısı uygulamanızın diğer bölümleriyle paylaşılabilir. Örneğin, SqlClient sağlayıcısı, bir SQL Server veritabanına erişmek için Entity Framework tarafından kullanılır. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Ortak geçiş görevleri  
 Mevcut bir uygulamayı Entity Framework geçirme yolu, hem uygulama türüne hem de mevcut veri erişim stratejisine bağlıdır. Ancak, mevcut bir uygulamayı Entity Framework geçirirken her zaman aşağıdaki görevleri gerçekleştirmeniz gerekir.  
  
> [!NOTE]
> Bu görevlerin tümü, Visual Studio 2008 ' den başlayarak Varlık Veri Modeli araçları kullandığınızda otomatik olarak gerçekleştirilir. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
1. Uygulamayı yükseltin.  
  
     Visual Studio 'nun önceki bir sürümü kullanılarak oluşturulan bir proje ve .NET Framework Visual Studio 2008 SP1 ve sürüm 3,5 SP1 'den başlayarak .NET Framework kullanacak şekilde yükseltilmelidir.  
  
2. Modelleri ve eşlemeyi tanımlayın.  
  
     Model ve eşleme dosyaları kavramsal modeldeki varlıkları tanımlar; tablolar, saklı yordamlar ve görünümler gibi veri kaynağındaki yapılar; ve varlıklar ile veri kaynağı yapıları arasındaki eşleme. Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını el Ile tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).  
  
     Depolama modelinde tanımlanan türler, veri kaynağındaki nesne adı ile aynı olmalıdır. Mevcut uygulama verileri nesneler olarak kullanıma sunarsa, kavramsal modelde tanımlanan varlıkların ve özelliklerin bu var olan veri sınıflarının ve özelliklerinin adlarıyla eşleştiğinden emin olmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: modelleme ve eşleme dosyalarını özel nesnelerle çalışacak şekilde özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100)).  
  
    > [!NOTE]
    > Varlık Veri Modeli Tasarımcısı, kavramsal modeldeki varlıkları varolan nesnelerle eşleşecek şekilde yeniden adlandırmak için kullanılabilir. Daha fazla bilgi için bkz. [varlık veri modeli Designer](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3. Bağlantı dizesini tanımlayın.  
  
     Entity Framework kavramsal bir modelde sorgu yürütürken özel olarak biçimlendirilmiş bir bağlantı dizesi kullanır. Bu bağlantı dizesi, model ve eşleme dosyalarıyla ilgili bilgileri ve veri kaynağıyla bağlantı bilgilerini kapsüller. Daha fazla bilgi için bkz. [nasıl yapılır: bağlantı dizesini tanımlama](how-to-define-the-connection-string.md).  
  
4. Visual Studio projesini yapılandırın.  
  
     Entity Framework derlemelerine yapılan başvurular ve model ve eşleme dosyaları Visual Studio projesine eklenmelidir. Bu eşleme dosyalarını, bağlantı dizesinde belirtilen konumda uygulamayla dağıtıldığından emin olmak için projeye ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: el ile Entity Framework projesi yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Mevcut nesneleri olan uygulamalara yönelik konular  
 .NET Framework 4 ' te başlayarak, Entity Framework, kalıcılık-Ignorant nesneleri olarak da adlandırılan "düz eski" CLR nesnelerini (POCO) destekler. Çoğu durumda, var olan nesneleriniz küçük değişiklikler yaparak Entity Framework ile çalışabilir. Daha fazla bilgi için bkz. [POCO varlıklarıyla çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Ayrıca, bir uygulamayı Entity Framework geçirebilir ve Entity Framework araçları tarafından oluşturulan veri sınıflarını kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>ADO.NET sağlayıcılarını kullanan uygulamalar için dikkat edilmesi gerekenler  
 SqlClient gibi ADO.NET sağlayıcıları, tablo verilerini döndürmek için bir veri kaynağını sorgulamanızı sağlar. Ayrıca, veriler bir ADO.NET veri kümesine yüklenebilir. Aşağıdaki listede, var olan bir ADO.NET sağlayıcısı kullanan bir uygulamayı yükseltme konuları açıklanmaktadır:  
  
- Veri okuyucu kullanarak tablo verilerini görüntüleme.  

  EntityClient sağlayıcısını kullanarak bir [!INCLUDE[esql](../../../../../includes/esql-md.md)] sorgusu yürütmeyi ve döndürülen <xref:System.Data.EntityClient.EntityDataReader> nesnesinden sıralama yapmayı düşünebilirsiniz. Bunu yalnızca uygulamanız bir veri okuyucusu kullanarak tablo verileri görüntülüyorsa ve verileri nesnelere getirmek, değişiklikleri izlemek ve güncelleştirme yapmak için Entity Framework tarafından sunulan tesislerin gerekli olmaması durumunda bunu yapın. Veri kaynağında güncelleştirme yapan mevcut veri erişim kodunu kullanmaya devam edebilirsiniz, ancak <xref:System.Data.EntityClient.EntityConnection><xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> özelliğinden erişilen mevcut bağlantıyı kullanabilirsiniz. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](entityclient-provider-for-the-entity-framework.md).  
  
- Veri kümeleriyle çalışma.  

  Entity Framework, bellek içi Kalıcılık, değişiklik izleme, veri bağlama ve nesneleri XML verileri olarak serileştirme dahil olmak üzere veri kümesi tarafından sağlanan aynı işlevselliklerin çoğunu sağlar. Daha fazla bilgi için bkz. [nesneleriyle çalışma](working-with-objects.md).  
  
  Entity Framework, uygulamanız için gereken veri kümesi işlevlerini sağlamıyorsa, LINQ to DataSet kullanarak LINQ sorgularının avantajlarından yararlanmaya devam edebilirsiniz. Daha fazla bilgi için bkz. [LINQ to DataSet](../linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Denetimlere veri bağlayan uygulamalar için dikkat edilmesi gerekenler  
 .NET Framework veri kümesi veya ASP.NET veri kaynağı denetimi gibi verileri bir veri kaynağında kapsüllemenizi ve ardından Kullanıcı arabirimi öğelerini bu veri denetimlerine bağlamayı sağlar. Aşağıdaki listede, Entity Framework verilerine yönelik bağlama denetimlerine ilişkin konular açıklanmaktadır.  
  
- Denetimlere veri bağlama.  

  Kavramsal modeli sorguladığınızda Entity Framework, verileri varlık türlerinin örnekleri olan nesneler olarak döndürür. Bu nesneler doğrudan denetimlere bağlanabilir ve bu bağlama güncelleştirmeleri destekler. Bu, bir denetimdeki <xref:System.Windows.Forms.DataGridView>bir satır gibi, <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> yöntemi çağrıldığında otomatik olarak veritabanına kaydedilen değişiklikler anlamına gelir.  
  
  Uygulamanız bir sorgunun sonuçlarını veri bağlamayı destekleyen bir <xref:System.Windows.Forms.DataGridView> veya başka bir denetim türünde göstermek üzere numaralandırdıysanız, uygulamanızı, denetimi bir <xref:System.Data.Objects.ObjectQuery%601>sonucuna bağlamak için değiştirebilirsiniz.  
  
  Daha fazla bilgi için bkz. [nesneleri denetimlere bağlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- ASP.NET veri kaynağı denetimleri.  

  Entity Framework, ASP.NET Web uygulamalarında veri bağlamayı basitleştirmek için tasarlanan bir veri kaynağı denetimini içerir. Daha fazla bilgi için bkz. [EntityDataSource Web sunucusu denetimine genel bakış](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Diğer Konular  
 Aşağıda, belirli uygulama türlerini Entity Framework geçirdiğinizde uygulanabilecek noktalar verilmiştir.  
  
- Veri hizmetlerini kullanıma sunan uygulamalar.  

  Windows Communication Foundation (WCF) tabanlı Web Hizmetleri ve uygulamalar, bir XML istek/yanıt mesajlaşma biçimi kullanarak verileri temel alınan bir veri kaynağından kullanıma sunar. Entity Framework, ikili, XML veya WCF veri sözleşmesi serileştirmesi kullanılarak varlık nesnelerinin serileştirmesini destekler. İkili ve WCF serileştirme her ikisi de nesne grafiklerinin tam serileştirmesini destekler. Daha fazla bilgi için bkz. [N katmanlı uygulamalar oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- XML verileri kullanan uygulamalar.  

  Nesne serileştirme Entity Framework veri Hizmetleri oluşturmanıza olanak sağlar. Bu hizmetler, AJAX tabanlı Internet uygulamaları gibi XML verilerini kullanan uygulamalara veri sağlar. Bu durumlarda WCF Veri Hizmetleri kullanmayı göz önünde bulundurun. Bu veri Hizmetleri Varlık Veri Modeli tabanlıdır ve al, koy ve postala gibi standart temsili durum aktarımı (REST) HTTP eylemleri kullanılarak varlık verilerine dinamik erişim sağlar. Daha fazla bilgi için bkz. [WCF Veri Hizmetleri 4,5](../../wcf/index.md).  
  
  Entity Framework, yerel XML veri türünü desteklemez. Yani bir varlık bir XML sütunu olan bir tabloyla eşlendiğinde, XML sütunu için eşdeğer varlık özelliği bir dizedir. Nesneler, XML olarak kesilebilir ve seri hale getirilebilir. Daha fazla bilgi için bkz. [nesneleri serileştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Uygulamanız XML verilerini sorgulamak için gerekliyse, LINQ to XML kullanarak LINQ sorgularının avantajlarından faydalanabilirsiniz. Daha fazla bilgi için bkz. [LINQ to XMLC#()](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) veya [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
- Durumu devam eden uygulamalar.  

  ASP.NET Web uygulamaları, genellikle bir Web sayfasının veya bir kullanıcı oturumunun durumunu korumalıdır. Bir <xref:System.Data.Objects.ObjectContext> örneğindeki nesneler, istemci görünümü durumunda veya sunucudaki oturum durumunda depolanabilir ve daha sonra yeni bir nesne bağlamına alınıp yeniden eklenebilir. Daha fazla bilgi için bkz. [nesneleri ekleme ve ayırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım Konuları](deployment-considerations.md)
- [Entity Framework Terimleri](terminology.md)

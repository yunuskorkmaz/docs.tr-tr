---
title: 'Nasıl yapılır: bir ADO.NET Entity Framework Veri kaynağı (WCF Veri Hizmetleri) kullanarak bir veri hizmeti oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 95439e2f73350e8f67aff61de7a97d80410109ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365702"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Nasıl yapılır: bir ADO.NET Entity Framework Veri kaynağı (WCF Veri Hizmetleri) kullanarak bir veri hizmeti oluşturma
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] varlık verilerini veri hizmet olarak sunar. Bu varlık verilerini tarafından sağlanan [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] veri kaynağı bir ilişkisel veritabanı olduğunda. Bu konuda nasıl oluşturulacağını gösterir bir [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-tabanlı varolan bir veritabanını temel alan ve yeni bir veri hizmeti oluşturmak için bu veri modelini kullanan bir Visual Studio Web uygulamasında veri modeli.  
  
 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Oluşturabilen bir komut satırı aracı da sağlar bir [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Visual Studio Proje dışındaki model. Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Mevcut bir Web uygulamasını mevcut bir veritabanına dayalı bir Entity Framework modelini eklemek için  
  
1.  Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.  
  
2.  İçinde **şablonları** bölmesinde tıklatın **veri** kategori ve ardından **ADO.NET varlık veri modeli**.  
  
3.  Model adını yazın ve ardından **Ekle**.  
  
     Sihirbazın ilk sayfasında [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Sihirbazı görüntülenir.  
  
4.  İçinde **Model içeriği seçin** iletişim kutusunda **veritabanından Oluştur**. Sonra **İleri**'ye tıklayın.  
  
5.  Tıklatın **yeni bağlantı** düğmesi.  
  
6.  İçinde **bağlantı özelliklerini** iletişim kutusu, sunucunuzun adını yazın, kimlik doğrulama yöntemi seçin, veritabanı adını yazın ve ardından **Tamam**.  
  
     **Veri bağlantınızı**s iletişim kutusunda, veritabanı bağlantı ayarlarınızı ile güncelleştirilir.  
  
7.  Emin **varlık bağlantı ayarlarını App.Config'de şöyle Kaydet:** onay kutusu işaretli. Sonra **İleri**'ye tıklayın.  
  
8.  İçinde **veritabanı nesnelerinizi** veritabanının Tümünü Seç iletişim kutusunda, nesneler veri hizmeti kullanıma sunmak planlama.  
  
    > [!NOTE]
    >  Veri modelinde bulunan nesneleri veri hizmeti tarafından otomatik olarak açık değildir. Hizmet tarafından açıkça sunulmalıdır. Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
9. Tıklatın **son** Sihirbazı tamamlayın.  
  
     Bu, belirli bir veritabanını temel alan bir varsayılan veri modeli oluşturur. [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Veri modelini özelleştirmek için etkinleştirir. Daha fazla bilgi için bkz: [görevleri](http://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Yeni veri modelini kullanarak veri hizmeti oluşturmak için  
  
1.  Visual Studio'da veri modelini gösteren .edmx dosyasının açın.  
  
2.  İçinde **modeli tarayıcısı**, model sağ tıklayın, **özellikleri**, varlık kapsayıcısının adı not edin.  
  
3.  İçinde **Çözüm Gezgini**, adına sağ tıklayın, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proje ve ardından **Yeni Öğe Ekle**.  
  
4.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti**.  
  
5.  Hizmet için bir ad sağlayın ve ardından **Tamam**.  
  
     Visual Studio yeni hizmet için XML biçimlendirme ve kodun dosyaları oluşturur. Varsayılan olarak Kod Düzenleyicisi penceresini açar.  
  
6.  Veri Hizmeti kodunu açıklamayı değiştirin `/* TODO: put your data source class name here */` devraldığı türü ile veri hizmeti tanımlayan sınıf tanımında <xref:System.Data.Objects.ObjectContext> sınıfı ve bu, 2. adımda not veri modelinin varlık kapsayıcısı.  
  
7.  Veri Hizmeti kodunu veri çıkarır hizmeti varlık kümeleri erişmek yetkili istemcilerin etkinleştirin. Daha fazla bilgi için bkz: [veri hizmeti oluşturma](../../../../docs/framework/data/wcf/creating-the-data-service.md).  
  
8.  Northwind.svc veri hizmeti bir Web tarayıcısı kullanarak test etmek için konudaki yönergeleri [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Nasıl yapılır: LINQ to SQL Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)

---
title: 'Nasıl yapılır: ADO.NET varlık çerçevesi veri kaynağı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 4bccd1e4655786ae24166cdc32619b420c4a54d3
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743780"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Nasıl yapılır: ADO.NET varlık çerçevesi veri kaynağı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma

WCF Veri Hizmetleri, varlık verilerini bir veri hizmeti kullanıma sunar. Bu varlık verilerini tarafından sağlanan [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] veri kaynağı, ilişkisel bir veritabanı olduğunda. Bu konu nasıl oluşturulacağını gösterir bir [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-tabanlı veri modeli varolan bir veritabanını temel alan ve yeni bir veri hizmeti oluşturmak için bu veri modeli kullanan bir Visual Studio Web uygulaması.

[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Oluşturabilen bir komut satırı aracı da sağlar bir [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Visual Studio Proje dışındaki model. Daha fazla bilgi için [nasıl yapılır: kullanımı Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Mevcut bir Web uygulaması için varolan bir veritabanını temel alan bir Entity Framework modelini eklemek için

1. Üzerinde **proje** menüsünü tıklatın **Ekle** > **yeni öğe**.

2. İçinde **şablonları** bölmesinde tıklayın **veri** kategori tıklayın ve ardından **ADO.NET varlık veri modeli**.

3. Model adını girin ve ardından **Ekle**.

     ' Nın ilk sayfasında [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Sihirbazı görüntülenir.

4. İçinde **Choose Model Contents** iletişim kutusunda **veritabanından Oluştur**. Sonra **İleri**'ye tıklayın.

5. Tıklayın **yeni bağlantı** düğmesi.

6. İçinde **bağlantı özellikleri** iletişim kutusu, sunucunuzun adını yazın, kimlik doğrulama yöntemini seçin, veritabanı adını yazın ve ardından **Tamam**.

     **Veri bağlantınızı seçin** iletişim kutusunda, veritabanı bağlantı ayarlarınızı ile güncelleştirilir.

7. Emin **varlığı App.Config dosyasındaki bağlantı ayarlarını Kaydet:** onay kutusu işaretli. Sonra **İleri**'ye tıklayın.

8. İçinde **veritabanı nesnelerinizi seçin** veritabanının Tümünü Seç iletişim kutusunda, nesneler veri hizmeti kullanıma sunmak planlama.

    > [!NOTE]
    > Veri modelinde bulunan nesneleri, veri hizmeti tarafından otomatik olarak sunulmaz. Hizmet tarafından açıkça sunulmalıdır. Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

9. Tıklayın **son** Sihirbazı tamamlayın.

     Bu, belirli bir veritabanını temel alan varsayılan bir veri modeli oluşturur. [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Veri modelini özelleştirmek için etkinleştirir. Daha fazla bilgi için [görevleri](https://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Yeni veri modelini kullanarak veri hizmeti oluşturmak için

1. Visual Studio'da veri modelini temsil eden .edmx dosyasını açın.

2. İçinde **Model tarayıcı**, modelin sağ tıklayın, **özellikleri**ve sonra varlık kapsayıcısının adı not edin.

3. İçinde **Çözüm Gezgini**, adına sağ tıklayın, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proje ve ardından **Ekle** > **yeni öğe**.

4. İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti** şablonunda **Web** kategorisi.

   ![Visual Studio 2015'te WCF veri hizmeti öğe şablonu](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF veri hizmeti** şablonu kullanılabilir Visual Studio 2015, ancak Visual Studio 2017 içinde değil.

5. Hizmet için bir ad sağlayın ve ardından **Tamam**.

     Visual Studio, yeni hizmet için XML işaretleme ve kod dosyalarını oluşturur. Varsayılan olarak, kod düzenleyicisi penceresi açılır.

6. Veri Hizmeti için kod içinde açıklamayı değiştirin `/* TODO: put your data source class name here */` devralınan türüyle veri hizmeti tanımlayan sınıf tanımında <xref:System.Data.Objects.ObjectContext> sınıfı ve bu, 2. adımda belirtilen veri modelinin varlık kapsayıcısı.

7. Veri Hizmeti için kodda verileri kullanıma sunan hizmet varlık kümeleri erişmek yetkili istemcilere etkinleştirin. Daha fazla bilgi için [veri hizmeti oluşturma](../../../../docs/framework/data/wcf/creating-the-data-service.md).

8. Bir Web tarayıcısı kullanarak Northwind.svc veri hizmeti test etmek için konusundaki yönergeleri izleyin. [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [Nasıl yapılır: LINQ to SQL Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
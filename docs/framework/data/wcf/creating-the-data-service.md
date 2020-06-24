---
title: Visual Studio 'da WCF veri hizmeti oluşturma
description: Örnek bir veritabanını temel alan OData akışını kullanıma sunmak için WCF Veri Hizmetleri kullanan bir örnek veri hizmeti oluşturmayı öğrenin.
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: 739cb6971209792724a2e939ca4f4821d5879c8c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247797"
---
# <a name="create-the-data-service"></a>Veri hizmetini oluşturma

Bu konu başlığında, Northwind örnek veritabanına dayalı açık veri Protokolü (OData) akışını kullanıma sunmak için WCF Veri Hizmetleri kullanan bir örnek veri hizmeti oluşturacaksınız. Görev aşağıdaki temel adımları içerir:

1. Bir ASP.NET Web uygulaması oluşturun.

2. Varlık Veri Modeli araçlarını kullanarak veri modelini tanımlayın.

3. Veri hizmetini Web uygulamasına ekleyin.

4. Veri hizmetine erişimi etkinleştirin.

## <a name="create-the-aspnet-web-app"></a>ASP.NET Web uygulaması oluşturma

1. Visual Studio 'da, **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.

1. **Yeni proje** iletişim kutusunda, Visual Basic veya Visual C# altında **Web** kategorisini seçin ve ardından **ASP.NET Web uygulaması**' nı seçin.

1. `NorthwindService`Projenin adı olarak girin ve **Tamam**' ı seçin.

1. **Yeni ASP.NET Web uygulaması** Iletişim kutusunda **boş** ' ı seçin ve ardından **Tamam**' ı seçin.

1. Seçim Web uygulamanız için belirli bir bağlantı noktası numarası belirtin. Note: bağlantı noktası numarası, `12345` Bu hızlı başlangıç konuları serisinde kullanılır.

    1. **Çözüm Gezgini**, az önce oluşturduğunuz ASP.NET projesine sağ tıklayın ve ardından **Özellikler**' i seçin.

    2. **Web** sekmesini seçin ve **belirli bir bağlantı noktası** metin kutusunun değerini olarak ayarlayın `12345` .

## <a name="define-the-data-model"></a>Veri modelini tanımlama

1. **Çözüm Gezgini**, ASP.net projesinin adına sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **veri** kategorisini seçin ve ardından **ADO.net varlık veri modeli**öğesini seçin.

3. Veri modeli adı için girin `Northwind.edmx` .

4. **Varlık veri modeli sihirbazında**, **veritabanından EF Designer**' ı seçin ve ardından **İleri**' ye tıklayın.

5. Aşağıdaki adımlardan birini gerçekleştirerek veri modelini veritabanına bağlayın ve ardından **İleri**' ye tıklayın:

    - Zaten yapılandırılmış bir veritabanı bağlantınız yoksa **Yeni bağlantı** ' ya tıklayın ve yeni bir bağlantı oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: SQL Server veritabanlarına bağlantı oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Bu SQL Server örneğine Northwind örnek veritabanının eklenmiş olması gerekir.

         \-veya

    - Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantınız varsa, bağlantı listesinden bu bağlantıyı seçin.

6. Sihirbazın son sayfasında, veritabanındaki tüm tablolar için onay kutularını seçin ve görünümler ve saklı yordamlar onay kutularını temizleyin.

7. Sihirbazı kapatmak için **son** ' a tıklayın.

## <a name="create-the-wcf-data-service"></a>WCF veri hizmetini oluşturma

1. **Çözüm Gezgini**, ASP.NET projesine sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, **Web** kategorisinden **WCF veri hizmeti** öğe şablonunu seçin.

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 veya üzeri sürümlerde kullanılabilir.

3. Hizmetin adı için, yazın `Northwind` .

     Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur. Varsayılan olarak, kod Düzenleyicisi penceresi açılır. **Çözüm Gezgini**, hizmet Northwind adına *. svc.cs* veya *. svc. vb*uzantısına sahiptir.

4. Veri Hizmeti kodunda, veri `/* TODO: put your data source class name here */` hizmetini tanımlayan sınıfın tanımındaki, bu örnekte olduğu gibi veri modelinin varlık kapsayıcısı olan türde olan açıklamayı değiştirin `NorthwindEntities` . Sınıf tanımı aşağıdaki gibi görünmelidir:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>Veri hizmeti kaynaklarına erişimi etkinleştir

1. Veri Hizmeti kodunda, işlevdeki yer tutucu kodunu aşağıdaki gibi değiştirin `InitializeService` :

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     Bu, yetkili istemcilerin belirtilen varlık kümelerine yönelik kaynaklara okuma ve yazma erişimi olmasını sağlar.

    > [!NOTE]
    > ASP.NET uygulamasına erişebilen tüm istemciler de veri hizmeti tarafından sunulan kaynaklara erişebilir. Bir üretim verileri hizmetinde, kaynaklara yetkisiz erişimi engellemek için uygulamanın kendisi de güvence altına alınmalıdır. Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md).

## <a name="next-steps"></a>Sonraki adımlar

Northwind örnek veritabanına dayalı bir OData akışını kullanıma sunan yeni bir veri hizmetini başarıyla oluşturdunuz ve ASP.NET Web uygulamasında izinleri olan istemciler için akışa erişimi etkinleştirdiniz. Ardından, Visual Studio 'dan veri hizmetini başlatacak ve bir Web tarayıcısı aracılığıyla HTTP GET istekleri göndererek OData akışına erişebileceksiniz:

> [!div class="nextstepaction"]
> [Hizmete bir Web tarayıcısından erişin](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))

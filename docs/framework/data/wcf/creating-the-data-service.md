---
title: Visual Studio'da WCF veri hizmeti oluşturma
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: e8d82ff8958af12842366911b6633ea6b2e0efbb
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517232"
---
# <a name="create-the-data-service"></a>Veri hizmetini oluşturma

Bu konu başlığında, WCF Veri Hizmetleri kullanıma sunmak için kullandığı örnek veri hizmeti oluşturma bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Northwind örnek veritabanını temel alan bir akış. Görev aşağıdaki temel adımları içerir:

1. Bir ASP.NET Web uygulaması oluşturun.

2. Veri modeli varlık veri modeli araçları kullanarak tanımlayın.

3. Veri Hizmeti Web uygulamasına ekleyin.

4. Veri hizmetine erişimi etkinleştirin.

## <a name="create-the-aspnet-web-app"></a>ASP.NET web uygulaması oluşturma

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

1. İçinde **yeni proje** altında Visual Basic veya Visual C# Seç iletişim kutusu **Web** kategori tıklayın ve ardından **ASP.NET Web uygulaması**.

1. Girin `NorthwindService` seçin ve proje adı olarak **Tamam**.

1. İçinde **yeni ASP.NET Web uygulaması** iletişim kutusunda **boş** seçip **Tamam**.

1. (İsteğe bağlı) Web uygulamanız için belirli bağlantı noktası numarası belirtin. Not: bağlantı noktası numarası `12345` Bu hızlı başlangıç konuları dizisinde kullanılır.

    1. İçinde **Çözüm Gezgini**, yeni oluşturduğunuz ASP.NET projeye sağ tıklayın ve ardından **özellikleri**.

    2. Seçin **Web** sekmesini ve değerini ayarlama **belirli bağlantı noktası** metin kutusuna `12345`.

## <a name="define-the-data-model"></a>Veri modelini tanımlama

1. İçinde **Çözüm Gezgini**ASP.NET proje adına sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **veri** kategori tıklayın ve ardından **ADO.NET varlık veri modeli**.

3. Veri modeli için adını `Northwind.edmx`.

4. İçinde **varlık veri modeli Sihirbazı**seçin **EF veritabanı Tasarımcısından**ve ardından **sonraki**.

5. Aşağıdakilerden birini yaparak veri modeli veritabanına bağlanmak ve ardından **sonraki**:

    -   Önceden yapılandırılmış bir veritabanı bağlantısı yoksa, tıklayın **yeni bağlantı** ve yeni bir bağlantı oluşturun. Daha fazla bilgi için [nasıl yapılır: SQL Server veritabanlarına bağlantı oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Bu SQL Server örneği, Northwind örnek veritabanına ekli olması gerekir.

         \- veya -

    -   Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantısı varsa, bu bağlantı bağlantılar listesinden seçin.

6. Sihirbazın son sayfasında, veritabanında tüm tabloların onay kutularını işaretleyin ve görünümler ve saklı yordamlar için onay kutularını temizleyin.

7. Tıklayın **son** sihirbazı kapatın.

## <a name="create-the-wcf-data-service"></a>WCF veri hizmeti oluşturma

1. İçinde **Çözüm Gezgini**, ASP.NET proje üzerinde sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti** öğesi şablonundan **Web** kategorisi.

   ![Visual Studio 2015'te WCF veri hizmeti öğe şablonu](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF veri hizmeti** şablonu kullanılabilir Visual Studio 2015, ancak Visual Studio 2017 içinde değil.

3. Hizmet adını yazın `Northwind`.

     Visual Studio, yeni hizmet için XML işaretleme ve kod dosyalarını oluşturur. Varsayılan olarak, kod düzenleyicisi penceresi açılır. İçinde **Çözüm Gezgini**, uzantıyı adıyla Northwind hizmette olduğunu *. svc.cs* veya *. svc.vb*.

4. Veri Hizmeti için kod içinde açıklamayı değiştirin `/* TODO: put your data source class name here */` veri modelinin varlık kapsayıcı türü olan veri hizmeti tanımlayan sınıf tanımında, bu durumda olduğu `NorthwindEntities`. Sınıf tanımını aşağıdaki görünmesi gerekir:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>Veri Hizmeti kaynaklarına erişimi etkinleştirme

1. Veri Hizmeti için kodda yer tutucusunu değiştirin `InitializeService` işlevi aşağıdaki:

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     Bu yetkili istemcilerin okuma ve yazma erişimi için belirtilen varlık kümesi kaynakları sağlar.

    > [!NOTE]
    > ASP.NET uygulamaya erişebilmesi için herhangi bir istemci veri hizmeti tarafından kullanıma sunulan kaynakları da erişebilirsiniz. Bir üretim veri hizmeti kaynaklarına yetkisiz erişimi önlemek için Ayrıca uygulama güvenli hale getirmelisiniz. Daha fazla bilgi için [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).

## <a name="next-steps"></a>Sonraki adımlar

Northwind örnek veritabanını temel alan bir OData akışına sunan yeni bir veri hizmeti başarıyla oluşturdunuz ve ASP.NET Web uygulamasında izinlere sahip istemciler için erişim etkinleştirmesi gerekir. Ardından, Visual Studio'dan veri hizmeti başlatın ve OData akışına bir Web tarayıcısı üzerinden HTTP GET isteği göndererek erişim:

> [!div class="nextstepaction"]
> [Bir web tarayıcısından hizmete erişme](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
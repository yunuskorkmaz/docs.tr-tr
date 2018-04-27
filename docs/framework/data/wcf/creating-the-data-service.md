---
title: Veri hizmeti oluşturma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 781def411214b0804cdc094c00b2f655b6c3823d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="creating-the-data-service"></a>Veri hizmeti oluşturma
Bu görevde kullanan bir örnek veri hizmeti oluşturacak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanıma sunmak için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Northwind örnek veritabanı üzerinde temel akış. Görev aşağıdaki temel adımları içerir:  
  
1.  Oluşturma bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması.  
  
2.  Veri modeli kullanarak tanımlayın [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] araçları.  
  
3.  Veri Hizmeti Web uygulamasına ekleyin.  
  
4.  Veri hizmeti erişimini etkinleştirir.  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Bu görevi tamamladığınızda oluşturduğunuz Web uygulaması üzerinde çalıştığı [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] geliştirme Visual Studio tarafından sağlanan sunucusu. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Geliştirme Sunucusu, yalnızca yerel bilgisayardan erişimi destekler. Ayrıca test ve geliştirme sırasında veri hizmeti sorunlarını kolaylaştırmak için Internet Information Services (IIS) kullanarak veri hizmeti barındıran uygulamayı çalıştırmayı göz önünde bulundurun. Daha fazla bilgi için bkz: [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirmek](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
### <a name="to-create-the-aspnet-web-application"></a>ASP.NET Web uygulaması oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde, select **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda, Visual Basic veya Visual C# seçin altında **Web** şablonu ve ardından **ASP.NET Web uygulaması**.  
  
    > [!NOTE]
    >  Visual Studio Web Developer kullanırsanız, yeni bir Web uygulaması yerine yeni bir Web sitesi oluşturmanız gerekir.  
  
3.  Tür `NorthwindService` projesinin adı olarak.  
  
4.  **Tamam**'ı tıklatın.  
  
5.  (İsteğe bağlı) Web uygulamanız için belirli bir bağlantı noktası numarası belirtin. Not: bağlantı noktası numarası `12345` hızlı geri kalanı kullanılır.  
  
    1.  İçinde **Çözüm Gezgini**, adına sağ tıklayın [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] az önce oluşturduğunuz proje ve ardından **özellikleri**.  
  
    2.  Seçin **Web** sekmesini tıklatın ve değerini ayarlama **belirli bir bağlantı noktası** metin kutusuna `12345`.  
  
### <a name="to-define-the-data-model"></a>Veri modeli tanımlamak için  
  
1.  İçinde **Çözüm Gezgini**, adına sağ tıklayın [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proje ve ardından **Yeni Öğe Ekle.**  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklatın **veri** şablonu ve ardından **ADO.NET varlık veri modeli**.  
  
3.  Veri modeli ad için `Northwind.edmx`.  
  
4.  İçinde [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Sihirbazı'nı seçin **veritabanından Oluştur**ve ardından **sonraki**.  
  
5.  Aşağıdaki adımlardan birini yaparak veri modeli veritabanına bağlanmak ve ardından **sonraki**:  
  
    -   Önceden yapılandırılmış bir veritabanı bağlantısı yoksa tıklatın **yeni bağlantı** ve yeni bir bağlantı oluşturun. Daha fazla bilgi için bkz: [nasıl yapılır: SQL Server veritabanları için bağlantıları oluşturma](http://go.microsoft.com/fwlink/?LinkId=123631). Bu SQL Server örneğine iliştirilmiş Northwind örnek veritabanı olmalıdır.  
  
         \- veya -  
  
    -   Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantısı varsa, bu bağlantıyı bağlantılar listesinden seçin.  
  
6.  Sihirbazın son sayfasında, veritabanındaki tüm tablolar için onay kutularını seçin ve görünümleri ve saklı yordamlar için onay kutularını temizleyin.  
  
7.  Tıklatın **son** sihirbazı kapatın.  
  
    > [!NOTE]
    >  Bu üretilen veri modeli varlık türlerine yabancı anahtar özellikleri sunar. Visual Studio 2008 kullanılarak oluşturulan veri modelleri bu yabancı anahtar özelliklerini içermez. Bu nedenle, Northwind veri hizmetinin bu sürümü erişmeye çalışmadan önce Visual Studio 2008 kullanılarak oluşturulmuş Northwind veri hizmete erişmek için oluşturulmuş tüm istemci uygulamaları istemci veri hizmeti sınıflarını güncelleştirmeniz gerekir.  
  
### <a name="to-create-the-data-service"></a>Veri hizmetini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, adına sağ tıklayın, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proje ve ardından **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti**.  
  
3.  Hizmet ad için `Northwind`.  
  
     Visual StudioVisual Studio yeni hizmet için XML biçimlendirme ve kodun dosyaları oluşturur. Varsayılan olarak Kod Düzenleyicisi penceresini açar. İçinde **Çözüm Gezgini**, hizmet adı, Northwind, uzantıya sahip olacaktır. svc.cs veya. svc.vb.  
  
4.  Veri Hizmeti kodunu açıklamayı değiştirin `/* TODO: put your data source class name here */` , varlık kapsayıcısının veri modelinin türü olan veri hizmeti tanımlayan sınıf tanımında bu durumda olduğu `NorthwindEntities`. Sınıf tanımı bu görünmelidir:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a>Veri Hizmeti kaynaklarına erişimi etkinleştirmek için  
  
1.  Veri Hizmeti için kodda yer tutucu kodu `InitializeService` aşağıdaki işleviyle:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Bu, yetkili istemcilerin okuma ve yazma erişimi kaynaklara belirtilen varlık kümeleri için sağlar.  
  
    > [!NOTE]
    >  Erişebilmeniz için herhangi bir istemci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama aynı zamanda veri hizmeti tarafından sunulan kaynaklara erişebilir. Bir üretim verileri Hizmeti'nde kaynaklara yetkisiz erişimi önlemek için ayrıca uygulamanın kendisinin güvenli. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sunan yeni bir veri hizmeti başarıyla oluşturdunuz bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Northwind örnek veritabanı ve size göre akış akışına izinlere sahip istemciler için erişim etkinleştirdiğinizden [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması. Ardından, Visual Studio'dan veri hizmeti başlatılır ve sunucusuna erişecek [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] HTTP GET isteklerini bir Web tarayıcısı aracılığıyla göndererek akış:  
  
 [Web Tarayıcısından Hizmete Erişme](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET varlık veri modeli araçları](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)

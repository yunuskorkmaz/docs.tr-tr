---
title: 'Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: c9b0128de6459c65e42fc2935222aecc643ec1d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362520"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme
Bu konuda nasıl kullanılacağını gösterir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Internet Information Services (IIS) çalıştıran bir ASP.NET Web uygulaması tarafından barındırılan Northwind örnek veritabanı dayalı bir veri hizmeti oluşturmak için. ASP.NET geliştirme sunucusu üzerinde çalışan bir ASP.NET Web uygulaması olarak aynı Northwind veri hizmeti oluşturma örneği için bkz: [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
> [!NOTE]
>  Northwind veri hizmeti oluşturmak için Northwind örnek veritabanı yerel bilgisayarda yüklü gerekir. Bu örnek veritabanı karşıdan yüklemek için indirme sayfasına bakın [örnek veritabanları için SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).  
  
 Bu konu Entity Framework sağlayıcı kullanarak bir veri hizmeti oluşturulacağını gösterir. Diğer Veri Hizmetleri sağlayıcılar kullanılabilir. Daha fazla bilgi için bkz: [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
 Hizmeti oluşturduktan sonra veri hizmeti kaynaklarına erişimi açıkça sağlamanız gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: veri hizmeti erişimi etkinleştir](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a>IIS üzerinde çalışır ASP.NET Web uygulaması oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde, select **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda, Visual Basic veya Visual C# programlama dili olarak seçin.  
  
3.  İçinde **şablonları** bölmesinde, **ASP.NET Web uygulaması**. Not: Visual Studio Web Developer kullanırsanız, yeni bir Web uygulaması yerine yeni bir Web sitesi oluşturmanız gerekir.  
  
4.  Tür `NorthwindService` projesinin adı olarak.  
  
5.  **Tamam**'ı tıklatın.  
  
6.  Üzerinde **proje** menüsünde, select **NorthwindService özellikleri**.  
  
7.  Seçin **Web** sekmesini tıklatın ve ardından **kullanım yerel IIS Web sunucusunda**.  
  
8.  Tıklatın **sanal dizin oluştur** ve ardından **Tamam**.  
  
9. Yönetici ayrıcalıklarıyla komut isteminden (işletim sistemi için) bağlı olarak aşağıdaki komutlardan birini yürütün:  
  
    -   32 bit sistemler:  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   64 bit sistemler:  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     Bu bilgisayarda Windows Communication Foundation (WCF) kayıtlı olduğundan emin olur.  
  
10. Yönetici ayrıcalıklarıyla komut isteminden (işletim sistemi için) bağlı olarak aşağıdaki komutlardan birini yürütün:  
  
    -   32 bit sistemler:  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   64 bit sistemler:  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     Bu bilgisayarda WCF yüklendikten sonra IIS düzgün çalıştığından emin hale getirir. Ayrıca IIS yeniden başlatmanız gerekebilir.  
  
11. ASP.NET uygulaması IIS7 üzerinde çalıştığında, aşağıdaki adımları gerçekleştirmeniz gerekir:  
  
    1.  IIS Yöneticisi'ni açın ve altındaki PhotoService uygulamaya gidin **varsayılan Web sitesi**.  
  
    2.  İçinde **özellikler görünümü**, çift **kimlik doğrulama**.  
  
    3.  Üzerinde **kimlik doğrulaması** sayfasında, **anonim kimlik doğrulaması**.  
  
    4.  İçinde **Eylemler** bölmesinde tıklatın **Düzenle** altında hangi anonim kullanıcıların siteye bağlanacak güvenlik sorumlusu ayarlamak için.  
  
    5.  İçinde **anonim kimlik doğrulama bilgilerini Düzenle** iletişim kutusunda **uygulama havuzu kimliği**.  
  
    > [!IMPORTANT]
    >  Ağ hizmeti hesabı kullandığınızda, anonim kullanıcılara bu hesaba ilişkin tüm iç ağ erişimini vermiş olursunuz.  
  
12. Visual Studio'da SQL Server Management Studio, sqlcmd.exe yardımcı programını veya Transact-SQL Düzenleyicisi'ni kullanarak, bağlı Northwind veritabanı olan SQL Server örneğini karşı aşağıdaki Transact-SQL komutu yürütün:  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     Bu IIS çalıştırmak için kullanılan Windows hesabının SQL Server örneğinde bir oturum oluşturur. Bu SQL Server örneğine bağlanmak IIS sağlar.  
  
13. Northwind veritabanı bağlı aşağıdaki Transact-SQL komutları yürütün:  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     Bu verileri okumak ve Northwind veritabanına veri yazmak IIS sağlayan yeni oturum açma, hakkı verir.  
  
### <a name="to-define-the-data-model"></a>Veri modeli tanımlamak için  
  
1.  İçinde **Çözüm Gezgini**, ASP.NET proje adına sağ tıklayın ve ardından **Yeni Öğe Ekle.**  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **ADO.NET varlık veri modeli**.  
  
3.  Veri modeli ad için `Northwind.edmx`.  
  
4.  Varlık veri modeli Sihirbazı'nda seçin **veritabanından Oluştur**ve ardından **sonraki**.  
  
5.  Aşağıdaki adımlardan birini yaparak veri modeli veritabanına bağlanmak ve ardından **sonraki**:  
  
    -   Önceden yapılandırılmış bir veritabanı bağlantısı yoksa tıklatın **yeni bağlantı** ve yeni bir bağlantı oluşturun. Daha fazla bilgi için bkz: [nasıl yapılır: SQL Server veritabanları için bağlantıları oluşturma](http://go.microsoft.com/fwlink/?LinkId=123631). Bu SQL Server örneğine iliştirilmiş Northwind örnek veritabanı olmalıdır.  
  
         \- veya -  
  
    -   Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantısı varsa, bu bağlantıyı bağlantılar listesinden seçin.  
  
6.  Sihirbazın son sayfasında, veritabanındaki tüm tablolar için onay kutularını seçin ve görünümleri ve saklı yordamlar için onay kutularını temizleyin.  
  
7.  Tıklatın **son** sihirbazı kapatın.  
  
    > [!NOTE]
    >  Bu üretilen veri modeli varlık türlerine yabancı anahtar özellikleri sunar. Visual Studio 2008 kullanılarak oluşturulan veri modelleri bu yabancı anahtar özelliklerini içermez. Bu nedenle, Northwind veri hizmetinin bu sürümü erişmeye çalışmadan önce Visual Studio 2008 kullanılarak oluşturulmuş Northwind veri hizmete erişmek için oluşturulmuş tüm istemci uygulamaları istemci veri hizmeti sınıflarını güncelleştirmeniz gerekir.  
  
### <a name="to-create-the-data-service"></a>Veri hizmetini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, ASP.NET proje adına sağ tıklayın ve ardından **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **ADO.NET veri hizmeti**.  
  
3.  Hizmet ad için `Northwind`.  
  
     Visual Studio yeni hizmet için XML biçimlendirme ve kodun dosyaları oluşturur. Varsayılan olarak Kod Düzenleyicisi penceresini açar. İçinde **Çözüm Gezgini**, hizmet adı, Northwind, uzantıya sahip olacaktır. svc.cs veya. svc.vb.  
  
4.  Veri Hizmeti kodunu açıklamayı değiştirin `/* TODO: put your data source class name here */` , varlık kapsayıcısının veri modelinin türü olan veri hizmeti tanımlayan sınıf tanımında bu durumda olduğu `NorthwindEntities`. Sınıf tanımı bu görünmelidir:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verilerinizi Hizmet Olarak Kullanıma Sunma](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)

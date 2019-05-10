---
title: 'Nasıl yapılır: IIS üzerinde çalışan bir WCF Veri Hizmeti Geliştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 74c31c748dd3483aa87afb2c9a7d926965c9f1ed
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755613"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme

Bu konuda, WCF Veri Hizmetleri Internet Information Services (IIS) üzerinde çalışan bir ASP.NET Web uygulaması tarafından barındırılıyor Northwind örnek veritabanını temel alan bir veri hizmeti oluşturmak için nasıl kullanılacağını gösterir. ASP.NET geliştirme sunucusu üzerinde çalışan ASP.NET Web uygulaması olarak aynı Northwind verileri hizmeti oluşturmak nasıl bir örnek için bkz [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

> [!NOTE]
> Northwind verileri hizmeti oluşturmak için Northwind örnek veritabanıyla yerel bilgisayarda yüklü gerekir. Bu örnek veritabanı karşıdan yüklemek için indirme sayfasında bakın [örnek veritabanları için SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).

Bu konuda Entity Framework kullanarak bir veri hizmeti oluşturulacağını gösterir. Diğer Veri Hizmetleri sağlayıcıları kullanılabilir. Daha fazla bilgi için [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).

Hizmeti oluşturduktan sonra veri hizmeti kaynaklarına erişimi açıkça sağlamanız gerekir. Daha fazla bilgi için [nasıl yapılır: Veri hizmetine erişmesini](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>IIS üzerinde çalışan ASP.NET web uygulaması oluşturun

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. İçinde **yeni proje** iletişim kutusunda **yüklü** > [**Visual C#**  veya **Visual Basic**] > **Web**  kategorisi.

3. Seçin **ASP.NET Web uygulaması** şablonu.

4. Girin `NorthwindService` olarak projenin adı.

5. **Tamam**'ı tıklatın.

6. Üzerinde **proje** menüsünde **NorthwindService özellikleri**.

7. Seçin **Web** sekmesine tıklayın ve ardından **kullanım yerel IIS Web sunucusunda**.

8. Tıklayın **sanal dizin oluştur** ve ardından **Tamam**.

9. Yönetici ayrıcalıklarıyla komut isteminden (işletim sistemi) bağlı olarak aşağıdaki komutlardan birini yürütün:

    - 32 bit sistemler:

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - 64 bit sistemler:

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Bu bilgisayarda Windows Communication Foundation (WCF) kayıtlı olduğundan emin olur.

10. Yönetici ayrıcalıklarıyla komut isteminden (işletim sistemi) bağlı olarak aşağıdaki komutlardan birini yürütün:

    - 32 bit sistemler:

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - 64 bit sistemler:

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Bu WCF bilgisayara yüklendikten sonra IIS doğru şekilde çalışmasını sağlar. Ayrıca IIS yeniden başlatmanız gerekebilir.

11. IIS7'de ASP.NET uygulama çalıştığında, aşağıdaki adımları da gerçekleştirmeniz gerekir:

    1. IIS Yöneticisi'ni açın ve altındaki PhotoService uygulamaya gidin **varsayılan Web sitesi**.

    2. İçinde **özellikler görünümü**, çift **kimlik doğrulaması**.

    3. Üzerinde **kimlik doğrulaması** sayfasında **anonim kimlik doğrulaması**.

    4. İçinde **eylemleri** bölmesinde tıklayın **Düzenle** altında hangi anonim kullanıcıların siteye bağlanacak güvenlik sorumlusu ayarlamak üzere.

    5. İçinde **anonim kimlik doğrulama bilgilerini Düzenle** iletişim kutusunda **uygulama havuzu kimliği**.

    > [!IMPORTANT]
    > Ağ hizmeti hesabı kullandığınızda, anonim kullanıcılara bu hesaba ilişkin tüm iç ağ erişimini verin.

12. Visual Studio'da SQL Server Management Studio, sqlcmd.exe yardımcı programı veya Transact-SQL Düzenleyicisi'ni kullanarak Northwind veritabanına ekli olan SQL Server örneği üzerinde aşağıdaki Transact-SQL komutu yürütün:

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    Bu, IIS çalıştırmak için kullanılan Windows hesabının SQL Server örneğinde bir oturum oluşturur. Bu SQL Server örneğine bağlanmak IIS sağlar.

13. Northwind veritabanına ekli ile aşağıdaki Transact-SQL komutlarını yürütün:

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

    Bu verileri okumak ve Northwind veritabanına veri yazmak IIS sağlayan yeni oturum açma hakkı verir.

## <a name="define-the-data-model"></a>Veri modelini tanımlama

1. İçinde **Çözüm Gezgini**ASP.NET proje adına sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **ADO.NET varlık veri modeli**.

3. Veri modeli için adını, `Northwind.edmx`.

4. Varlık veri modeli Sihirbazı'nda seçin **veritabanından Oluştur**ve ardından **sonraki**.

5. Aşağıdakilerden birini yaparak veri modeli veritabanına bağlanmak ve ardından **sonraki**:

    - Önceden yapılandırılmış bir veritabanı bağlantısı yoksa tıklayın **yeni bağlantı** ve yeni bir bağlantı oluşturun. Daha fazla bilgi için [nasıl yapılır: SQL Server veritabanlarına bağlantı oluşturma](https://go.microsoft.com/fwlink/?LinkId=123631). Bu SQL Server örneği, Northwind örnek veritabanına ekli olması gerekir.

         \- veya -

    - Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantısı varsa, bu bağlantı bağlantılar listesinden seçin.

6. Sihirbazın son sayfasında, veritabanında tüm tabloların onay kutularını işaretleyin ve görünümler ve saklı yordamlar için onay kutularını temizleyin.

7. Tıklayın **son** sihirbazı kapatın.

## <a name="create-the-data-service"></a>Veri hizmetini oluşturma

1. İçinde **Çözüm Gezgini**ASP.NET projenizin adına sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti**.

   ![Visual Studio 2015'te WCF veri hizmeti öğe şablonu](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF veri hizmeti** şablonu kullanılabilir Visual Studio 2015, ancak Visual Studio 2017 içinde değil.

3. Hizmet adını girin `Northwind`.

     Visual Studio, yeni hizmet için XML işaretleme ve kod dosyalarını oluşturur. Varsayılan olarak, kod düzenleyicisi penceresi açılır. İçinde **Çözüm Gezgini**, hizmet adı, Northwind ve uzantısını içerir. svc.cs veya. svc.vb.

4. Veri Hizmeti için kod içinde açıklamayı değiştirin `/* TODO: put your data source class name here */` veri modelinin varlık kapsayıcı türü olan veri hizmeti tanımlayan sınıf tanımında, bu durumda olduğu `NorthwindEntities`. Sınıf tanımını aşağıdaki görünmesi gerekir:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Ayrıca bkz.

- [Verilerinizi Hizmet Olarak Kullanıma Sunma](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)

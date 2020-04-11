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
ms.openlocfilehash: 8a1a0c2c55267940463e2c9ab82bb52345269260
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121608"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme

Bu makalede, Internet Information Services (IIS) üzerinde çalışan ASP.NET bir Web uygulaması tarafından barındırılan Northwind örnek veritabanını temel alan bir veri hizmeti oluşturmak için WCF Veri Hizmetleri'nin nasıl kullanılacağı gösterilmektedir. ASP.NET Geliştirme Sunucusu'nda çalışan ASP.NET bir Web uygulamasıyla aynı Northwind veri hizmetini nasıl oluşturabileceğinize ilişkin bir örnek için [WCF Veri Hizmetleri'ne hızlı bir şekilde başlayın.](quickstart-wcf-data-services.md)

> [!NOTE]
> Northwind veri hizmetini oluşturmak için önce Northwind örnek veritabanını yerel bilgisayara yükleyin. Veritabanını yüklemek [için, Northwind'den](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)Transact-SQL komut dosyasını çalıştırın ve Microsoft SQL Server için pub örnek veritabanlarını çalıştırın.

Bu makalede, Varlık Çerçevesi sağlayıcısını kullanarak bir veri hizmetinin nasıl oluşturulacak gösterilmektedir. Diğer veri hizmetleri sağlayıcıları kullanılabilir. Daha fazla bilgi için [Bkz. Veri Hizmetleri Sağlayıcıları.](data-services-providers-wcf-data-services.md)

Hizmeti oluşturduktan sonra, veri hizmeti kaynaklarına açıkça erişim sağlamanız gerekir. Daha fazla bilgi için [bkz: Veri Hizmetine Erişimi Etkinleştirin.](how-to-enable-access-to-the-data-service-wcf-data-services.md)

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>IIS'de çalışan ASP.NET web uygulamasını oluşturma

1. Visual Studio'da Dosya **menüsünde** **Yeni** > **Proje'yi**seçin.

2. Yeni **Proje** iletişim kutusunda, Web **>** **Yüklü** > [**Visual C#** veya **Visual Basic**] seçeneğini belirleyin.

3. ASP.NET **Web Uygulaması** şablonunu seçin.

4. Projenin `NorthwindService` adı olarak girin.

5. **Tamam**'a tıklayın.

6. **Project** menüsünde **NorthwindService Özellikleri'ni**seçin.

7. **Web** sekmesini seçin ve ardından **Yerel IIS Web Sunucusu'nu kullan'ı**seçin.

8. **Sanal Dizin Oluştur'u** tıklatın ve ardından **Tamam'ı**tıklatın.

9. Yönetici ayrıcalıkları içeren komut isteminden aşağıdaki komutlardan birini uygulayın (işletim sistemine bağlı olarak):

    - 32 bit sistemler: 

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - 64 bit sistemler: 

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Bu, Windows Communication Foundation'ın (WCF) bilgisayarda kayıtlı olmasını sağlar.

10. Yönetici ayrıcalıkları içeren komut isteminden aşağıdaki komutlardan birini uygulayın (işletim sistemine bağlı olarak):

    - 32 bit sistemler: 

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - 64 bit sistemler: 

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Bu, WCF bilgisayara yüklendikten sonra IIS'nin doğru çalıştığından emin olun. IIS'yi yeniden başlatmanız da gerekebilir.

11. ASP.NET uygulaması IIS7'de çalıştığında, aşağıdaki adımları da gerçekleştirmeniz gerekir:

    1. IIS Manager'ı açın ve **Varsayılan Web Sitesi**altında PhotoService uygulamasına gidin.

    2. **Özellikler Görünümü'nde**, **kimlik doğrulamayı**çift tıklatın.

    3. Kimlik **Doğrulama** sayfasında **Anonim Kimlik Doğrulama'yı**seçin.

    4. **Eylemler** bölmesinde, anonim kullanıcıların siteye bağlanacağı güvenlik ilkesini ayarlamak için **Edet'i** tıklatın.

    5. Anonim **Kimlik Doğrulama Kimlik Bilgilerini Edit** iletişim kutusunda, **Uygulama havuzu kimliği'ni**seçin.

    > [!IMPORTANT]
    > Ağ Hizmeti hesabını kullandığınızda, anonim kullanıcılara bu hesapla ilişkili tüm dahili ağ erişimi verirsiniz.

12. SQL Server Management Studio,sqlcmd.exe yardımcı programını veya Visual Studio'daki Transact-SQL Düzenleyicisi'ni kullanarak, Northwind veritabanını ekleyen SQL Server örneğine karşı aşağıdaki Transact-SQL komutunu uygulayın:

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    Bu, IIS'yi çalıştırmak için kullanılan Windows hesabı için SQL Server örneğinde bir oturum açar. Bu, IIS'nin SQL Server örneğine bağlanmasını sağlar.

13. Northwind veritabanı bağlı ile aşağıdaki Transact-SQL komutlarını çalıştırın:

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

    Bu, IIS'nin Northwind veritabanından gelen verileri okumasına ve verileri yazmasına olanak tanıyan yeni oturum açma hakları verir.

## <a name="define-the-data-model"></a>Veri modelini tanımlama

1. **Çözüm Gezgini'nde,** ASP.NET projesinin adını sağ tıklatın ve sonra**Yeni Öğe** **Ekle'yi** > tıklatın.

2. Yeni **Öğe Ekle** iletişim kutusunda, **Varlık Veri Modeli ADO.NET**seçin.

3. Veri modelinin adı `Northwind.edmx`için.

4. Varlık Veri Modeli Sihirbazı'nda **Veritabanından**Oluştur'u'nu seçin ve sonra **İleri'yi**tıklatın.

5. Aşağıdaki adımlardan birini yaparak veri modelini veritabanına bağlayın ve **sonra İleri'yi**tıklatın:

    - Zaten yapılandırılmış bir veritabanı bağlantınız yoksa, **Yeni Bağlantı'yı** tıklatın ve yeni bir bağlantı oluşturun. Daha fazla bilgi için [bkz: SQL Server Veritabanlarına Bağlantı Oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Bu SQL Server örneğinde Northwind örnek veritabanı eklenmiş olmalıdır.

         \-veya -

    - Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantınız varsa, bu bağlantıyı bağlantı listesinden seçin.

6. Sihirbazın son sayfasında, veritabanındaki tüm tabloların onay kutularını seçin ve görünümler ve depolanan yordamlar için onay kutularını temizleyin.

7. Sihirbazı kapatmak için **Bitir'i** tıklatın.

## <a name="create-the-data-service"></a>Veri hizmetini oluşturma

1. **Çözüm Gezgini'nde,** ASP.NET projenizin adını sağ tıklatın ve sonra**Yeni Öğe** **Ekle'yi** > tıklatın.

2. Yeni **Öğe Ekle** iletişim kutusunda **WCF Veri Hizmeti'ni**seçin.

   ![Visual Studio 2015'te WCF Veri Hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF Veri Hizmeti** şablonu Visual Studio 2015'te kullanılabilir, ancak Visual Studio 2017 veya sonraki ülkelerde kullanılamaz.

3. Hizmetin adı için, `Northwind`girin.

     Visual Studio, yeni hizmet için XML biçimlendirmesi ve kod dosyaları oluşturur. Varsayılan olarak, kod düzenleyicipenceresi açılır. **Solution Explorer'da**hizmetin adı, Northwind ve uzantısı .svc.cs veya .svc.vb vardır.

4. Veri hizmeti kodunda, veri hizmetini `/* TODO: put your data source class name here */` tanımlayan sınıfın tanımındaki yorumu, bu durumda `NorthwindEntities`veri modelinin varlık kapsayıcısı olan türle değiştirin. Sınıf tanımı aşağıdaki lere bakmalıdır:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Ayrıca bkz.

- [Verilerinizi Hizmet Olarak Kullanıma Sunma](exposing-your-data-as-a-service-wcf-data-services.md)

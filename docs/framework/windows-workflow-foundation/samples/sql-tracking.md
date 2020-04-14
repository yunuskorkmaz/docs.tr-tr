---
title: SQL İzleme
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 72bfcaac2903b3e7fa5679422ad4feaa79e93211
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243186"
---
# <a name="sql-tracking"></a>SQL izleme

Bu örnek, izleme kayıtlarını bir SQL veritabanına yazan özel bir SQL izleme katılımcısı nasıl yazılabildiğini gösterir. Windows İş Akışı Temeli (WF), iş akışı örneğinin yürütülmesinde görünürlük elde etmek için iş akışı izleme sağlar. İzleme çalışma zamanı, iş akışının yürütülmesi sırasında iş akışı izleme kayıtlarını yayar. İş akışı izleme hakkında daha fazla bilgi için [bkz.](../workflow-tracking-and-tracing.md)

## <a name="use-the-sample"></a>Örneği kullanma

1. SQL Server 2008, SQL Server 2008 Express veya yeni yüklü olduğunuzu doğrulayın. Örnekle birlikte paketlenmiş komut dosyaları, yerel bilgisayarınızda bir SQL Express örneğinin kullanıldığını varsayar. Farklı bir örneğinvarsa, lütfen örneği çalıştırmadan önce veritabanıyla ilgili komut dosyalarını değiştirin.

2. Komut dosyaları dizininde Trackingsetup.cmd (\WF\Basic\Tracking\SqlTracking\CS\Scripts) çalıştırarak SQL Server izleme veritabanını oluşturun. Bu, TrackingSample adlı bir veritabanı oluşturur.

   > [!NOTE]
   > Komut dosyası, SQL Express'in varsayılan örneğinde veritabanını oluşturur. Farklı bir veritabanı örneğine yüklemek istiyorsanız, Trackingsetup.cmd komut dosyasını düzenleyin.

3. Visual Studio 2010'da SqlTrackingSample.sln'yi açın.

4. Çözümü oluşturmak için **Ctrl**+**Shift**+**B** tuşuna basın.

5. Uygulamayı çalıştırmak için **F5**'e basın.

   Tarayıcı penceresi açılır ve uygulamanın dizin listesini gösterir.

6. Tarayıcıda StockPriceService.xamlx'ı tıklatın.

7. Tarayıcı, yerel hizmet WSDL adresini içeren StockPriceService sayfasını görüntüler. Bu adresi kopyala.

   Yerel hizmet WSDL adresibir `http://localhost:65193/StockPriceService.xamlx?wsdl`örnektir.

8. Dosya Gezgini'ni kullanarak WCF test istemcisini (WcfTestClient.exe) çalıştırın. *Microsoft Visual Studio 10.0\Common7\IDE dizininde*yer alır.

9. WCF test istemcisinde **Dosya** menüsüne tıklayın ve **Hizmet Ekle'yi**seçin. Yerel servis adresini textbox'a yapıştırın. İletişim kutusunu kapatmak için **Tamam'ı** tıklatın.

10. WCF test istemcisinde **GetStockPrice'ı**çift tıklatın. Bu, `GetStockPrice` bir parametre alan işlemi açar, `Contoso` değeri yazın ve **Çağır'ı**tıklatın.

11. Yayılan izleme kayıtları bir SQL veritabanına yazılır. İzleme kayıtlarını görüntülemek için SQL Management Studio'da TrackingSample veritabanını açın ve tablolara gidin. Tablolarda seçili bir sorgunun çalıştırılsa, ilgili tablolarda depolanan izleme kayıtlarıiçindeki verileri görüntüler.

   SQL Server Management Studio hakkında daha fazla bilgi için SQL [Server Management Studio tanıtımına](/sql/ssms/sql-server-management-studio-ssms)bakın. SQL Server Management [Studio'u buradan](https://aka.ms/ssmsfullsetup)indirin.

## <a name="uninstall-the-sample"></a>Örneği kaldırma

1. Örnek dizindeki Trackingcleanup.cmd komut dosyasını çalıştırın (*\WF\Basic\Tracking\SqlTracking*).

    > [!NOTE]
    > Trackingcleanup.cmd, yerel bilgisayarınız SQL Express'teki veritabanını silmeye çalışır. Başka bir SQL sunucu örneği kullanıyorsanız, Trackingcleanup.cmd'yi düzenlemeyi edin.

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

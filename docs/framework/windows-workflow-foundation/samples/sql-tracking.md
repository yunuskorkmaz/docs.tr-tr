---
title: SQL İzleme
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 88f44e5362684f755695aab154842fad2274134d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094598"
---
# <a name="sql-tracking"></a>SQL İzleme
Bu örnek, izleme kayıtlarını bir SQL veritabanına yazan özel bir SQL izleme katılımcısının nasıl yazılacağını gösterir. Windows Workflow Foundation (WF), bir iş akışı örneğinin yürütülmesi için görünürlük elde etmek üzere iş akışı izleme sağlar. İzleme çalışma zamanı, iş akışının yürütülmesi sırasında iş akışı izleme kayıtlarını yayar. İş akışı izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../workflow-tracking-and-tracing.md).

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. SQL Server 2008, SQL Server 2008 Express veya daha yeni bir sürümün yüklü olduğunu doğrulayın. Örnekle paketlenmiş betikler, yerel bilgisayarınızda bir SQL Express örneği kullanımını varsayar. Farklı bir örneğiniz varsa, örneği çalıştırmadan önce lütfen veritabanıyla ilgili betikleri değiştirin.

2. Betikler dizinindeki Trackingsetup. cmd ' i çalıştırarak SQL Server izleme veritabanını oluşturun (\Wf\basic\izlemedosyası \ KomutDosyaları). Bu, TrackingSample adlı bir veritabanı oluşturur.

    > [!NOTE]
    > Betik, SQL Express 'in varsayılan örneğinde veritabanını oluşturur. Farklı bir veritabanı örneğine yüklemek isterseniz, Trackingsetup. cmd betiğini düzenleyin.

3. Visual Studio 2010 ' de SqlTrackingSample. sln dosyasını açın.

4. Çözümü derlemek için CTRL+SHIFT+B'ye basın.

5. Uygulamayı çalıştırmak için F5'e basın.

     Tarayıcı penceresi açılır ve uygulamanın dizin listesini gösterir.

6. Tarayıcıda, StockPriceService. xamlx ' ye tıklayın.

7. Tarayıcı, yerel hizmet WSDL adresini içeren StockPriceService sayfasını görüntüler. Bu adresi kopyalayın.

     Yerel hizmet WSDL adresine bir örnek `http://localhost:65193/StockPriceService.xamlx?wsdl`.

8. Dosya Gezgini 'ni kullanarak WCF test istemcisini (WcfTestClient. exe) çalıştırın. Microsoft Visual Studio 10.0 \ Common7\ıde dizininde bulunur.

9. WCF test istemcisinde **Dosya** menüsüne tıklayın ve **Hizmet Ekle**' yi seçin. Yerel hizmet adresini metin kutusuna yapıştırın. İletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

10. WCF test istemcisinde **GetStockPrice**' ye çift tıklayın. Bu, tek bir parametre alan `GetStockPrice` işlemini açar, `Contoso` değeri yazın ve **çağır**' a tıklayın.

11. Yayınlanan izleme kayıtları bir SQL veritabanına yazılır. İzleme kayıtlarını görüntülemek için, SQL Management Studio 'de TrackingSample veritabanını açın ve tablolara gidin. SQL Server Management Studio hakkında daha fazla bilgi için bkz. [SQL Server Management Studio tanıtımı](/sql/ssms/sql-server-management-studio-ssms). SQL Server 2008 Management Studio Express [buradan](https://www.microsoft.com/download/details.aspx?id=7593)indirilebilir. Tablolarda bir SELECT sorgusu çalıştırmak, ilgili tablolarda depolanan izleme kayıtları içindeki verileri görüntüler.

#### <a name="to-uninstall-the-sample"></a>Örneği kaldırmak için

1. Örnek dizininde theTrackingcleanup. cmd betiğini çalıştırın (\Wf\basic\izlemesqltracking).

    > [!NOTE]
    > Trackingcleanup. cmd yerel bilgisayarınızdaki SQL Express veritabanını silmeye çalışır. Başka bir SQL Server örneği kullanıyorsanız, Trackingcleanup. cmd ' yi düzenleyin.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

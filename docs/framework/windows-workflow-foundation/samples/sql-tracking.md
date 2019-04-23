---
title: SQL İzleme
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: f3c48b40e2d3d7dec2b9008b3de738f9b2983610
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308932"
---
# <a name="sql-tracking"></a>SQL İzleme
Bu örnek nasıl yazılacağını özel SQL izleme katılımcı gösterir, bu bir SQL veritabanı'na izleme kayıtları yazar. Windows Workflow Foundation (WF) iş akışı yürütme iş akışı örneğinin görünürlük elde etmek için izleme sağlar. İzleme çalışma zamanı iş akışı iş akışı yürütülürken kayıtları izleme yayar. İş akışı izleme hakkında daha fazla bilgi için bkz: [takip ve izleme iş akışı](../workflow-tracking-and-tracing.md).

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Bilgisayarınızda SQL Server 2008, SQL Server 2008 Express veya üzerinin yüklü doğrulayın. Örnek ile paketlenmiş betikleri yerel bilgisayarınızda bir SQL Express örneği kullanımını varsayılır. Lütfen veritabanı ile ilgili betikleri örneği çalıştırmadan önce değiştirin. farklı bir örneğine sahipseniz.

2. SQL Server veritabanı izleme betikleri dizininde (\WF\Basic\Tracking\SqlTracking\CS\Scripts) Trackingsetup.cmd çalıştırarak oluşturun. Bu TrackingSample adlı bir veritabanı oluşturur.

    > [!NOTE]
    >  Betik, SQL Express varsayılan örnekte veritabanı oluşturur. Farklı bir veritabanı örneği üzerinde yüklemek istiyorsanız, Trackingsetup.cmd betiği düzenleyin.  
  
3. Open SqlTrackingSample.sln in Visual Studio 2010.  
  
4. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
5. Uygulamayı çalıştırmak için F5'e basın.  
  
     Tarayıcı penceresi açılır ve dizin için uygulama listesi gösterilir.  
  
6. Tarayıcıda StockPriceService.xamlx tıklayın.  
  
7. Tarayıcı, yerel hizmet WSDL adresini içeren StockPriceService sayfası görüntüler. Bu adresini kopyalayın.  
  
     Yerel Hizmet WSDL adresi örneğidir `http://localhost:65193/StockPriceService.xamlx?wsdl`.  
  
8. Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test istemcisi (WcfTestClient.exe) çalıştırın. Bunu yapmak için Microsoft Visual Studio 10.0\Common7\IDE dizininde bulunur.  
  
9. WCF test İstemcisi'nde tıklayın **dosya** menü ve select **Hizmet Ekle**. Yerel hizmet adresi metin kutusuna yapıştırın. Tıklayın **Tamam** iletişim kutusunu kapatmak için.  
  
10. WCF test İstemcisi'nde çift tıklayarak **GetStockPrice**. Bu açılır `GetStockPrice` bir parametre, değer alan işlemi `Contoso` tıklatıp **Invoke**.  
  
11. Bir SQL veritabanına yayılan izleme kayıtları yazılır. İzleme kayıtları görüntülemek için SQL Management Studio'da TrackingSample veritabanını açın ve tablolara gidin. SQL Server Management Studio hakkında daha fazla bilgi için bkz: [Karşınızda SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645). SQL Server 2008 Management Studio Express'i indirilebilir [burada](https://go.microsoft.com/fwlink/?LinkId=180520). Tabloları seçme sorgusu çalıştıran izleme kayıtları ilgili tablolarında depolanan verileri görüntüler.  
  
#### <a name="to-uninstall-the-sample"></a>Örnek kaldırmak için  
  
1. Örnek dizini (\WF\Basic\Tracking\SqlTracking) theTrackingcleanup.cmd betiği çalıştırın.  
  
    > [!NOTE]
    >  Trackingcleanup.cmd, yerel bilgisayarınıza SQL Express veritabanında silmeyi dener. Başka bir SQL server örneği kullanıyorsanız, Trackingcleanup.cmd düzenleyin.

> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)

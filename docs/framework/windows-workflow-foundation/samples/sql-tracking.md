---
title: SQL izleme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6bd8fbe1a29793778d93eeca64b185079d706f3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-tracking"></a>SQL izleme
Bu örnek, bir özel SQL izleme katılımcı yazma gösterilmiştir, bir SQL veritabanına izleme kayıtları yazar. [!INCLUDE[wf](../../../../includes/wf-md.md)]İş akışı iş akışı örneğini yürütmeyi görünürlük elde etmek için izleme sağlar. İzleme çalışma zamanı iş akışı iş akışı yürütme sırasında kayıtları izleme yayar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]İzleme, iş akışı bkz [izleme ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  SQL Server 2008, SQL Server 2008 Express veya daha yeni yüklü doğrulayın. SQL Express örneği, yerel bilgisayarınızda kullanımını örnekle paketlenmiş betikleri varsayalım. Veritabanı ile ilgili betikleri örneği çalıştırmadan önce lütfen değiştirin farklı bir örnek varsa.  
  
2.  SQL Server veritabanı izleme betikleri dizininde (\WF\Basic\Tracking\SqlTracking\CS\Scripts) Trackingsetup.cmd çalıştırarak oluşturun. Bu TrackingSample adlı bir veritabanı oluşturur.  
  
    > [!NOTE]
    >  Komut dosyası, SQL Express varsayılan örneğinde veritabanı oluşturur. Farklı bir veritabanı örneği üzerinde yüklemek istiyorsanız, Trackingsetup.cmd betiğini düzenleyin.  
  
3.  İçinde SqlTrackingSample.sln açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
5.  Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     Bir tarayıcı penceresi açar ve dizin için uygulama listesi gösterilir.  
  
6.  Tarayıcıda StockPriceService.xamlx'ı tıklatın.  
  
7.  Tarayıcı yerel hizmet WSDL adresi içeren StockPriceService sayfa görüntüler. Bu adresini kopyalayın.  
  
     Yerel Hizmet WSDL adresi http://localhost:65193/StockPriceService.xamlx?wsdl örneğidir.  
  
8.  Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test istemcisi (WcfTestClient.exe) çalıştırın. Microsoft Visual Studio 10.0\Common7\IDE dizininde bulunur.  
  
9. WCF test İstemcisi'ni tıklatın **dosya** menü ve select **Hizmet Ekle**. Yerel hizmet adresi metin kutusuna yapıştırın. Tıklatın **Tamam** iletişim kutusunu kapatmak için.  
  
10. WCF test istemcisi çift tıklayarak **GetStockPrice**. Bu açılır `GetStockPrice` bir parametre değeri türü alan işlemi `Contoso` tıklatıp **Invoke**.  
  
11. Verilmiş izleme kayıtları bir SQL veritabanına yazılır. İzleme kayıtları görüntülemek için SQL Management Studio'da TrackingSample veritabanı açın ve tablolara gidin. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SQL Server Management Studio bkz [SQL Server Management Studio Tanıtımı](http://go.microsoft.com/fwlink/?LinkId=165645). SQL Server 2008 Management Studio Express indirilebilir [burada](http://go.microsoft.com/fwlink/?LinkId=180520). Tabloları seçme sorgusu çalıştıran ilgili tablolarda depolanan izleme kayıtları içinde verileri görüntüler.  
  
#### <a name="to-uninstall-the-sample"></a>Örnek kaldırmak için  
  
1.  TheTrackingcleanup.cmd betik örnek dizininde (\WF\Basic\Tracking\SqlTracking) çalıştırın.  
  
    > [!NOTE]
    >  Yerel bilgisayarınızda SQL Express veritabanını silmek Trackingcleanup.cmd çalışır. Başka bir SQL server örneği kullanıyorsanız, Trackingcleanup.cmd düzenleyin.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)

---
title: SQLStoreExtensibility
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 111e7aa4164d9fc811ebe3f5efb196df77d1ded0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sqlstoreextensibility"></a>SQLStoreExtensibility
Bu örnek kullanım ve SQL iş akışı örneği deposundaki yükseltilen özellikleri yapılandırmasını gösterir. SQL iş akışı örneği deposuna bir SQL tabanlı bir örnek deposuna uygulamasıdır. Durumu kaydedin ve durumunu bir SQL Server veya SQL Server Express veritabanı gelen ve giden yüklemek bir örnek sağlar. Depolama genişletilebilirlik özelliği örneği deposunda saklanır özelliklerini tanımlamak kullanıcı sağlar. Bu özellikler için sorgu kullanıcıya veren bir yükseltilen özellikleri görünümü görüntülenir.  
  
 Bu örnek bir sayım hizmeti uygulayan bir iş akışı oluşur. Hizmetin başlangıç yöntemi çağrıldıktan sonra hizmet 29 için 0'dan sayar. 2 saniyede sayaç artırılır. Her sayısı sonra iş akışı devam ettirir. Geçerli sayaç değeri örnek deposunda yükseltilen bir özellik olarak depolanır.  
  
 Sayım iş akışını bir iş akışı hizmeti ana bilgisayar tarafından kendiliğinden barındırılır. Programın `Main` yöntemi aşağıdaki eylemleri gerçekleştirir:  
  
-   Sayım iş akışı barındıran ve altında sayım iş akışı ulaşılabilen uç noktalarını tanımlayan iş akışı hizmeti konak örneği oluşturur.  
  
-   SQL iş akışı örneği deposunu yapılandırmak için kullanılan bir SQL iş akışı örneği deposu davranışı tanımlar. Mağaza işlemek için talimat `CountStatus` yükseltilen bir özellik olarak.  
  
-   Sayım bir iş akışı başlatma yöntemini çağıran bir istemci oluşturur.  
  
 Program başladıktan sonra sayaç sayım otomatik olarak başlar. Örneği yüklemek ve SQL iş akışı örneği deposunu yapılandırmak için birkaç saniye sürebilir unutmayın.  
  
 Sayaç değeri özel bir özellik olarak yükseltmek için aşağıdaki adımlar izlenmelidir:  
  
1.  Sınıf `CounterStatus` türünün bir örneği uzantısını tanımlayan <xref:System.Activities.Persistence.PersistenceParticipant>, etkinlikler tarafından durumu değişkenleri sağlamak için kullanılan. `Count`bir salt değer olarak tanımlanır. Bir iş akışı örneği Kalıcılık noktasına geldiğinde, örnek uzantısı kaydeder `Count` özelliği Kalıcılık veri koleksiyonu.  
  
2.  Örnek deposu, yeni bir özellik oluştururken `CountStatus`, aracılığıyla tanımlanan `store.Promote()` yöntemi.  
  
3.  İş akışı `SaveCounter` Etkinlik geçerli sayaç değeri atar `Count` durum alanı.  
  
### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Örnek deposu veritabanı oluşturun.  
  
    1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
    2.  Örnek dizine (\WF\Basic\Persistence\SqlStoreExtensibility\CS) gidin ve CreateInstanceStore.cmd çalıştırmadan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
        > [!WARNING]
        >  CreateInstanceStore.cmd komut dosyası, SQL Server 2008 Express varsayılan örneğinde veritabanı oluşturma dener. Veritabanını farklı bir örneğinde yüklemek istiyorsanız, bunu yapmak için komut dosyasını değiştirin.  
  
2.  Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] SqlStoreExtensibility.sln çözüm yük ve CTRL + SHIFT + B tuşuna basarak oluşturun.  
  
    > [!WARNING]
    >  Varsayılan olmayan SQL Server örneğinde veritabanı yüklü değilse, bağlantı dizesi çözümü oluşturma önce kodda güncelleştirin.  
  
3.  Örnek, projenin bin dizinine (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) giderek yönetici ayrıcalıklarıyla çalıştırın [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], SqlStoreExtensibility.exe sağ tıklayıp seçerek **farklı çalıştır Yönetici**.  
  
### <a name="to-verify-the-sample-is-working-correctly"></a>Örnek doğru şekilde çalıştığını doğrulama  
  
1.  Seçerek örneği tablosunun içeriğini görüntülemek için SQL Server Management Studio kullanın **veritabanları**, **InstanceStore**ve ardından  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** nesne Gezgini'nde sağ **System.ServiceModel.Activities.DurableInstancing.InstanceTable** ve seçin **İlk 1000 satırı Seç**. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SQL Server Management Studio bkz [SQL Server Management Studio Tanıtımı](http://go.microsoft.com/fwlink/?LinkId=165645)  
  
2.  Listelenen iş akışı örnekleri inceleyin.  
  
3.  İçinde bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi, (\WF\Basic\Persistence\SqlStoreExtensibility) örnek dizininde bulunan QueryInstanceStore.cmd komut dosyasını çalıştırın.  
  
4.  Sayaç değeri görüntülenen altındaki gözlemlemek **CountStatus**.  
  
5.  Birkaç kez komut dosyasını çalıştırmak görmek için **CountStats** değeri değiştirin.  
  
6.  İş akışı sonlandırmak için ENTER tuşuna basın.  
  
### <a name="to-uninstall-the-sample"></a>Örnek kaldırmak için  
  
1.  Örnek deposu veritabanı (\WF\Basic\Persistence\SqlStoreExtensibility) örnek dizininde bulunan RemoveInstanceStore.cmd komut dosyası çalıştırarak kaldırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş akışı kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [İş akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)

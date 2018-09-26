---
title: SQLStoreExtensibility
ms.date: 03/30/2017
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
ms.openlocfilehash: f49d05244cf9f65a8e06f39c7e40391aaebd9f77
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231531"
---
# <a name="sqlstoreextensibility"></a>SQLStoreExtensibility
Bu örnek, kullanılması ve yapılandırılması SQL iş akışı örnek deposu yükseltilen özellikleri gösterir. SQL iş akışı örnek deposu örnek deposunun SQL tabanlı bir uygulamasıdır. İmkanı tanıyacaktır ve durumuna için ve SQL Server veya SQL Server Express veritabanı yüklemek bir örnek sağlar. Örnek deposunda saklanır özelliklerini tanımlamak kullanıcı deposu genişletilebilirlik özelliği sağlar. Bu özellikler için sorgu kullanıcıya veren bir yükseltilen özellikleri görünümü görüntülenir.  
  
 Bu örnek, bir sayım hizmeti uygulayan bir iş akışı oluşur. Hizmetin başlangıç yöntemi çağrıldıktan sonra hizmet için 29 0'dan sayar. Her 2 saniyede sayaç artırılır. Her sayısı sonra iş akışı devam ettirir. Geçerli sayaç değeri, yükseltilen bir özellik örnek deposunda depolanır.  
  
 Sayım iş akışını bir iş akışı hizmeti ana bilgisayar tarafından kendi kendini barındırır. Programın `Main` yöntemi aşağıdaki eylemleri gerçekleştirir:  
  
-   Sayım iş akışı barındıran ve sayım iş akışı altında ulaşılabilir uç noktalarını tanımlar iş akışı hizmeti konak örneği oluşturur.  
  
-   SQL iş akışı örnek deposu yapılandırmak için kullanılan bir SQL iş akışı örnek deposu davranışı tanımlar. Değerlendirilecek deponun belirtildiği `CountStatus` yükseltilen bir özellik olarak.  
  
-   Sayım iş akışının başlangıç yöntemi çağıran bir istemci oluşturur.  
  
 Program başlatıldıktan sonra sayım sayacı otomatik olarak başlar. Örneği yükleme ve SQL iş akışı örnek deposu yapılandırmak için birkaç saniye sürebilir unutmayın.  
  
 Sayaç değeri özel bir özellik olarak yükseltmek için aşağıdaki adım atılmalıdır:  
  
1.  Sınıf `CounterStatus` türünün bir örneği uzantısını tanımlar <xref:System.Activities.Persistence.PersistenceParticipant>, durumu değişkenleri sağlamak için etkinlikleri tarafından kullanılır. `Count` bir salt değer olarak tanımlanır. Bir iş akışı örneği kalıcı noktasına geldiğinde, örnek uzantısı kaydeder `Count` Kalıcılık veri koleksiyonuna özelliği.  
  
2.  Örnek depo, yeni bir özellik oluştururken `CountStatus`, aracılığıyla tanımlanır `store.Promote()` yöntemi.  
  
3.  İş akışının `SaveCounter` etkinlik için geçerli sayaç değeri atar `Count` durumu alanı.  
  
### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Örnek depo veritabanı oluşturun.  
  
    1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
    2.  Örnek dizine (\WF\Basic\Persistence\SqlStoreExtensibility\CS) gidin ve CreateInstanceStore.cmd çalıştırılan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
        > [!WARNING]
        >  SQL Server 2008 Express varsayılan örneğinde veritabanı oluşturma CreateInstanceStore.cmd betik çalışır. Veritabanını farklı bir örneğinde yüklemek istiyorsanız, bunu yapmak için komut dosyasını değiştirin.  
  
2.  Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] SqlStoreExtensibility.sln çözümü yüklemek ve CTRL + SHIFT + B tuşlarına basarak oluşturun.  
  
    > [!WARNING]
    >  Veritabanı bir SQL Server varsayılan olmayan örneğini yüklediyseniz, çözümü ile önce kod bağlantı dizesini güncelleştirin.  
  
3.  Örnek olarak projenin bin dizinine (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) giderek yönetici ayrıcalıklarıyla çalıştırın [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], SqlStoreExtensibility.exe sağ tıklayıp **Çalıştır Yönetici**.  
  
### <a name="to-verify-the-sample-is-working-correctly"></a>Örnek doğrulamak için doğru şekilde çalışıyor  
  
1.  Örnek tablo içeriğini görüntülemek için SQL Server Management Studio kullanın **veritabanları**, **InstanceStore**, ardından  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** nesne Gezgini'nde sağ **System.ServiceModel.Activities.DurableInstancing.InstanceTable** seçin **İlk 1000 satırı Seç**. SQL Server Management Studio hakkında daha fazla bilgi için bkz: [SQL Server Management Studio ile tanışın](https://go.microsoft.com/fwlink/?LinkId=165645)  
  
2.  Listelenen iş akışı örnekleri gözlemleyin.  
  
3.  İçinde bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi (\WF\Basic\Persistence\SqlStoreExtensibility) örnek dizininde bulunan QueryInstanceStore.cmd betiği çalıştırın.  
  
4.  Sayaç değeri altında görüntülenen gözlemleyin **CountStatus**.  
  
5.  Betiği birkaç kez çalıştırın görmek için **CountStats** değerini değiştirin.  
  
6.  İş akışı uygulamayı sonlandırmak için ENTER tuşuna basın.  
  
### <a name="to-uninstall-the-sample"></a>Örnek kaldırmak için  
  
1.  Örnek deposu veritabanı (\WF\Basic\Persistence\SqlStoreExtensibility) örnek dizininde bulunan RemoveInstanceStore.cmd betiği çalıştırarak kaldırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)

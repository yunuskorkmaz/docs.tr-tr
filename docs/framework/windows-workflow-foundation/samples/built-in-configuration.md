---
title: Yerleşik yapılandırma
ms.date: 03/30/2017
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
ms.openlocfilehash: e76c019d9fc1b416e6fa8175a70b5fd01d9ff53e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43476124"
---
# <a name="built-in-configuration"></a>Yerleşik yapılandırma
Bu örnek, kullanılması ve yapılandırılması SQL iş akışı örnek deposunun gösterir. SQL iş akışı örnek deposu örnek deposunun SQL tabanlı bir uygulamasıdır. Durum kaydetme ve yükleme durumu için ve SQL Server veya SQL Server Express veritabanı örneği sağlar.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse (indirme sayfası) Git tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnek, bir sayım hizmeti uygulayan bir iş akışı oluşur. Hizmetin başlangıç yöntemi çağrıldıktan sonra hizmet 0 ile 59 arasında sayar. Her 2 saniyede sayaç artırılır. Her sayısı sonra iş akışı devam ettirir.  
  
 Sayım iş akışını bir iş akışı hizmeti ana bilgisayar tarafından kendi kendini barındırır. Programın `Main` yöntemi sayım iş akışı barındıran iş akışı hizmeti konağı bir örneğini oluşturur. Bu, altında sayım iş akışı erişilebilir uç noktalarını tanımlar. Bundan sonra SQL iş akışı örnek deposu yapılandırmak için kullanılan bir SQL iş akışı örnek deposu davranışı tanımlar. Ardından, sayım iş akışının başlangıç yöntemi çağıran bir istemci bir program oluşturur.  
  
 Program başlatıldıktan sonra sayım sayacı otomatik olarak başlar. Örneği yükleme ve SQL iş akışı örnek deposu yapılandırmak için birkaç saniye sürebilir unutmayın. İş akışı örnek deposu hakkında daha fazla bilgi için bkz: [SQL iş akışı örneği Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
 Örnek, iki bölümden oluşur:  
  
1.  InstanceStore1 gösterir nasıl <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> C# kodunu kullanarak yapılandırılır (Program.cs bakın).  
  
2.  InstanceStore2 gösterir nasıl <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> XML kullanılarak yapılandırılır (App.config bakın).  
  
 SQL iş akışı örneği Store davranışı yapılandırmak aşağıdaki ayarlar kullanılabilir:  
  
-   Ayarlama `HostLockRenewalPeriod`. Bu zaman aralığı ile sahipliği kilit örneklerin çalıştığı konak yeniler tanımlar. Kilit bilgiler örneği Store içinde depolanır. Sahipliği iki tanımlanan aralıklarla yenilenen değil, `HostLockRenewalPeriod`, örnek terk edilmiş kabul edilir. Başka bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> aynı iş akışını çalıştıran ve aynı örnek depolama (ya da aynı bilgisayarda veya farklı bir bilgisayarda) bağlı, söz konusu örneğine kurtarır. (Örnek kurtarma, bu örnek kapsamı dışındadır.)  
  
-   Ayarlama `RunnableInstancesDetectionPeriod`. Bu süre için konak yoklama aralığı tanımlar çalıştırılabilir duruma örnekleri. Örnekleri aşağıdaki olaylardan herhangi biri meydana gelirse çalıştırılabilir duruma gelebilir:  
  
    -   Dayanıklı bir zamanlayıcı (<xref:System.Activities.Statements.Delay>) süresi dolar.  
  
    -   Başka bir konak isabetsiz kendi `HostLockRenewal` sinyali (örneğin, nedeniyle bir bilgisayarı kilitlenme) ve örnek kurtarıldı.  
  
-   Ayarlama `InstanceCompletionAction`. Bu özellik, kümesine `DeleteNothing`, örneği Store durumlarda tamamlandı tutar; Eğer kümesine `DeleteAll`, örnekleri tamamlandıktan sonra mağaza'dan silindi. Aşağıdakilere dikkat edin:  
  
    > [!NOTE]
    >  Ana bilgisayar sayım tamamlanmadan önce ENTER tuşuna basarak sonlandırılıyor. iş akışı örneği işlemi.  
  
-   Ayarlama `InstanceLockedExceptionAction`. Bu ayar, başka bir ana bilgisayar tarafından kilitlenmiş bir örnek yüklemek istiyorsa, bir ana ne yapmalı tanımlar. Aşağıdaki seçenekler mevcuttur:  
  
    -   Varsa kümesine `NoRetry`: değil yüklemeyi yeniden deneyin ve dönüş bir `InstanceLockedException` konağa.  
  
    -   Varsa kümesine `BasicRetry`: örneği yüklemek için yeniden denemeye devam. Basit bir doğrusal algoritması göre yeniden deneme işlemleri zamanlanır (örneğin, yeniden deneme her 5 saniyede bir).  
  
    -   Varsa kümesine `AggressiveRetry`: örneği yüklemek için yeniden denemeye devam. Yeniden deneme işlemleri bir agresif üstel geri alma algoritmaya göre zamanlanır.  
  
-   Kodlama seçeneğini ayarlayın. Bu ayar, örnek durumu SQL iş akışı örneği Store içinde depolanan nasıl tanımlar. Aşağıdaki seçenekler mevcuttur:  
  
    -   Örnek durum GZip sıkıştırma algoritması kullanılarak sıkıştırılmış.  
  
    -   Örnek durum sıkıştırılmış değil.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] izinleri varsa bir yönetici olarak komut istemi.  
  
2.  Örnek dizine (\WF\Basic\Persistence\BuiltInConfiguration\CS) gidin ve CreateInstanceStore.cmd çalıştırın.  
  
3.  Yönetici ayrıcalıkları yoksa, oluşturma, SQL Server oturum açma. Git `Security`, **oturumları**. Sağ **oturumları** ve yeni bir oturum oluşturun.  
  
4.  ACL kullanıcınızın SQL rolüne ekleyin. Açık **veritabanları**, **InstanceStore**, **güvenlik**. Sağ **kullanıcılar** seçip **yeni kullanıcılar**. Ayarlama **oturum açma adı** önceki adımda oluşturduğunuz kullanıcı. Kullanıcı eklemek için veritabanı rolü üyeliği **System.Activities.DurableInstancing.InstanceStoreUsers** (ve diğer kişiler). Kullanıcı zaten (örneğin, dbo kullanıcısı) bulunmayabilir unutmayın.  
  
5.  InstanceStore.sln açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
6.  İçinde [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)](\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug) örnek'ın uygun bin\debug dizinine gidin, InstanceStore.exe sağ tıklayın ve seçin **yöneticiolarakçalıştır**. Kanal dinleyicisi açtığı için bu örnek yönetici ayrıcalıklarıyla çalıştırılmalıdır.  
  
7.  Yerel SQL Server Express yüklemesi dışında bir veritabanında örnek deposu oluşturduysanız, veritabanı bağlantı dizesini güncelleştirmeniz gerekir (`const string ConnectionString` program.CS'de Webhostbuilder'a InstanceStore1 projenin ve `connectionString` App.config özniteliği InstanceStore2 Proje) örnek ve örnek yeniden derleyin.  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a>Örnek doğrulamak için doğru şekilde çalışıyor  
  
1.  Örnek çalışırken, SQL Server Management Studio'yu başlatın.  
  
2.  İçinde **Nesne Gezgini**seçin **veritabanları**, **InstanceStore**, **tabloları**, ardından  **System.Activities.DurableInstancing.InstanceTable**.  
  
3.  Sağ tıklayın **InstanceTable** seçip **ilk 1000 satırı Seç**.  
  
4.  Yeni bir giriş ve bu olup olmadığına bakın **kilit zaman aşımı** 5 saniyede değiştirir (görev çubuğu tıklayın **yürütme** sorguyu yenilemek için düğme). Bu ayar bir sonucu, **konak kilidi yenileme dönemi** 5.  
  
5.  Sayım tamamlandıktan sonra giriş örneği tabloda kaldırılır gözlemleyin. Bu ayar bir sonucu, **örnek tamamlama eylemi** için **DeleteAll**.  
  
6.  Mesajının görüntülendiğini görün ve iş akışı konak uygulamayı sonlandırmak için ENTER tuşuna basın **LockOwnersTable** silinir.  
  
#### <a name="to-uninstall-the-sample"></a>Örnek kaldırmak için  
  
1.  RemoveInstanceStore.cmd örnek dizinde (\WF\Basic\Persistence\BuiltInConfiguration) çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)

---
title: "Yerleşik yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ddf9b316074a69a88f08a0d7f519533f2db0002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="built-in-configuration"></a>Yerleşik yapılandırma
Bu örnek, kullanım ve SQL iş akışı örneği depolama yapılandırmasını gösterir. SQL iş akışı örneği deposuna bir SQL tabanlı bir örnek deposuna uygulamasıdır. Kaydetme ve yükleme durumu için ve SQL Server veya SQL Server Express veritabanından bir örnek sağlar.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse (indirme) gidin tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnek bir sayım hizmeti uygulayan bir iş akışı oluşur. Hizmetin başlangıç yöntemi çağrıldıktan sonra hizmet 0 ile 59 arasında sayar. 2 saniyede sayaç artırılır. Her sayısı sonra iş akışı devam ettirir.  
  
 Sayım iş akışını bir iş akışı hizmeti ana bilgisayar tarafından kendiliğinden barındırılır. Programın `Main` yöntemi sayım iş akışı barındıran iş akışı hizmeti ana bilgisayarı örneği oluşturur. Sayım iş akışı altında ulaşılabilen uç noktaları tanımlar. Bundan sonra SQL iş akışı örneği deposunu yapılandırmak için kullanılan bir SQL iş akışı örneği deposu davranışı tanımlar. Ardından, program sayım iş akışının başlangıç yöntemini çağıran bir istemci oluşturur.  
  
 Program başladıktan sonra sayaç sayım otomatik olarak başlar. Örneği yüklemek ve SQL iş akışı örneği deposunu yapılandırmak için birkaç saniye sürebilir unutmayın. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]İş akışı örneği deposu bkz [SQL iş akışı örneği deposuna](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
 Örnek iki bölümden oluşur:  
  
1.  InstanceStore1 gösterir nasıl <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> C# kodu kullanarak yapılandırılır (Program.cs bakın).  
  
2.  InstanceStore2 gösterir nasıl <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> XML kullanarak yapılandırılır (App.config bakın).  
  
 SQL iş akışı örneği deposuna davranışı yapılandırmak aşağıdaki ayarlar kullanılabilir:  
  
-   Ayarlama `HostLockRenewalPeriod`. Bu süre ile ana bilgisayar çalıştırılan örneklerinin sahipliği kilit yeniler aralığı tanımlar. Kilit bilgileri örnek deposunda saklanır. Sahipliği iki tanımlı aralıklar için yenilendi değil, `HostLockRenewalPeriod`, örnek terk değerlendirilir. Başka bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> aynı iş akışını çalıştıran ve aynı örnek depolama (ya da aynı bilgisayarda veya farklı bir bilgisayara) bağlı, bu örnek kurtarır. (Bu örnek için kapsam dışına örneği kurtarma olur.)  
  
-   Ayarlama `RunnableInstancesDetectionPeriod`. Bu süre içinde ana bilgisayar yoklama için aralığı tanımlar runnable duruma gelmiş örnekleri. Örnekleri aşağıdaki olaylardan herhangi biri oluştuğunda runnable hale gelebilir:  
  
    -   Dayanıklı bir süreölçer (<xref:System.Activities.Statements.Delay>) süresi dolar.  
  
    -   Başka bir ana bilgisayar isabetsiz kendi `HostLockRenewal` sinyal (örneğin, bir bilgisayar çökmesinden dolayı) ve örnek kurtarıldı.  
  
-   Ayarlama `InstanceCompletionAction`. Bu özellik, kümesine `DeleteNothing`, örnek deposuna tamamlandı tutar durumlarda; kümesine IF `DeleteAll`, örnekleri tamamlanmasından sonra mağaza'dan silinir. Aşağıdakilere dikkat edin:  
  
    > [!NOTE]
    >  Ana bilgisayar sayım tamamlanmadan önce ENTER tuşuna basarak sonlandırma iş akışı örneği tamamlanmaz.  
  
-   Ayarlama `InstanceLockedExceptionAction`. Bu ayar, başka bir ana bilgisayar tarafından kilitlenmiş bir örneğini yükleme istiyorsa, bir ana ne tanımlar. Aşağıdaki seçenekler mevcuttur:  
  
    -   Varsa kümesine `NoRetry`: değil yükleme işlemini yeniden deneyin ve dönüş bir `InstanceLockedException` ana bilgisayara.  
  
    -   Varsa kümesine `BasicRetry`: örneğini yükleme yeniden denemeye devam. Yeniden deneme işlemleri bir Basit doğrusal algoritması göre zamanlanmış (örneğin, 5 saniyede yeniden).  
  
    -   Varsa kümesine `AggressiveRetry`: örneğini yükleme yeniden denemeye devam. Yeniden deneme işlemleri bir agresif üstel geri alma algoritma göre zamanlanır.  
  
-   Kodlama seçeneğini ayarlayın. Bu ayar, örneğin durumu SQL iş akışı örneği deposunda nasıl depolandığını tanımlar. Aşağıdaki seçenekler mevcuttur:  
  
    -   Örnek durum GZip sıkıştırma algoritması kullanılarak sıkıştırılmış.  
  
    -   Örnek durum sıkıştırılmış değil.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] izinleri varsa bir yönetici olarak komut istemi.  
  
2.  Örnek dizine (\WF\Basic\Persistence\BuiltInConfiguration\CS) gidin ve CreateInstanceStore.cmd çalıştırın.  
  
3.  Yönetici ayrıcalıkları yoksa, Create SQL Server oturum açma. Git `Security`, **oturumları**. Sağ **oturumları** ve yeni bir oturum oluşturun.  
  
4.  ACL kullanıcınız SQL rolüne ekleyin. Açık **veritabanları**, **InstanceStore**, **güvenlik**. Sağ **kullanıcılar** seçip **yeni kullanıcılar**. Ayarlama **oturum açma adı** önceki adımda oluşturduğunuz kullanıcı. Kullanıcı eklemek için veritabanı rolü üyeliği **System.Activities.DurableInstancing.InstanceStoreUsers** (ve diğerleri). Kullanıcı zaten (örneğin, dbo kullanıcısı) bulunmayabilir unutmayın.  
  
5.  InstanceStore.sln dosyasında açma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
6.  İçinde [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], örnek 's uygun bin\debug dizinine (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug) gidin, InstanceStore.exe sağ tıklatın ve seçin **yöneticiolarakçalıştır**. Bir kanal dinleyicisi açtığından Bu örnek yönetici ayrıcalıklarıyla çalıştırılmalıdır.  
  
7.  Yerel SQL Server Express yüklemesi dışında bir veritabanında örnek deposuna oluşturduysanız, veritabanı bağlantı dizesi güncelleştirmeniz gerekir (`const string ConnectionString` InstanceStore1 projenin Program.cs içinde ve `connectionString` App.config özniteliği InstanceStore2 Proje) örnek ve örnek yeniden derleyebilirsiniz.  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a>Örnek doğrulamak için düzgün çalışıyor  
  
1.  Örnek çalışırken, SQL Server Management Studio'yu başlatın.  
  
2.  İçinde **Object Explorer**seçin **veritabanları**, **InstanceStore**, **tabloları**ve ardından  **System.Activities.DurableInstancing.InstanceTable**.  
  
3.  Sağ tıklayın **InstanceTable** seçip **ilk 1000 satırı Seç**.  
  
4.  Yeni bir giriş ve, olup olmadığına bakın **kilitleme sona erme** 5 saniyede değiştirir (görev çubuğunu tıklatın **yürütme** sorgu yenilemek için düğmesini). Bu ayar bir sonucu olduğundan **konak kilit yenileme süresini** 5.  
  
5.  Sayım tamamlandıktan sonra örnek tablosunda girişi kaldırılır inceleyin. Bu ayar bir sonucu olduğundan **örneği tamamlama eylem** için **DeleteAll**.  
  
6.  İş akışı ana sonlandırmak ve görüntülendiğini için ENTER tuşuna basın **LockOwnersTable** silinir.  
  
#### <a name="to-uninstall-the-sample"></a>Örnek kaldırmak için  
  
1.  RemoveInstanceStore.cmd örnek dizininde (\WF\Basic\Persistence\BuiltInConfiguration) çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)

---
title: Windows Communication Foundation Örnekleri için Bir Kerelik Kurulum Prosedürü
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 3c3c5934cbbc7dd68f03d888aa0594f9ff61c225
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216613"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örnekleri için Bir Kerelik Kurulum Prosedürü
Windows Communication Foundation (WCF) örnekleri çoğu Internet Information Services (IIS) barındırılan ve genel sanal dizinden çalıştırın. Bu tek seferlik Kurulum yordamı diskte bir klasörü oluşturur; Ayrıca IIS adlı bir sanal dizin ekler **ServiceModelSamples**.  
  
 **ServiceModelSamples** sanal dizin oluşturma ve bir IIS tarafından barındırılan hizmeti kullanan tüm örnekleri çalıştırmak için kullanılır. Bu örnekleri çalıştırmak için gereken yalnızca sanal dizindir. Bir örnek oluşturmak, daha önceden dağıtılan tüm sanal dizin hizmeti yerini alır; yalnızca en son oluşturulan örnek dağıtılan ve bu sanal dizin kullanılabilir olacaktır.  
  
> [!NOTE]
>  Bir yerel yönetici hesabı altındaki tüm komutları çalıştırmanız gerekir. Windows 7 kullanıyorsanız [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], veya Windows Server 2008 R2, ayrıca çalıştırmalısınız komut isteminde yükseltilmiş ayrıcalıklara sahip. Bunu yapmak için komut istemi simgesini sağ tıklatın ve ardından **yönetici olarak çalıştır**. Bu konu başlığı altındaki tüm komutları uygun yolu ayarlara sahip bir komut isteminde çalıştırılması gerekir.  Bunu sağlamanın en kolay yolu, Visual Studio komut istemini kullanmaktır. Bu İstemi'ni açmak için **Başlat**seçin **tüm programlar**, ekranı aşağı kaydırarak **Visual Studio 2010**seçin **Visual Studio Araçları**, sağ **Visual Studio komut istemi (2010)** ve ardından **yönetici olarak çalıştır**. Visual Studio Express sürümleri yüklü birine sahipseniz, bu komut istemi kullanılabilir değil ve "C:\Windows\Microsoft.Net\Framework\v4.0" Sistem yoluna eklemeniz gerekecektir.  
  
### <a name="one-time-setup-procedure-for-wcf-samples"></a>WCF örnekleri için bir kerelik Kurulum yordamı  
  
1.  Emin [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ayarlanır. Nasıl ayarlandığı hakkında daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], bkz: [Internet Information Service barındırma yönergeleri](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).  
  
2.  Emin [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] yüklenir. Arama aşağıdaki v4.0 dizinini (veya üzeri): **\Windows\Microsoft.NET\Framework**  
  
3.  Varsa [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yüklü değil ve işletim sisteminizi Windows Server 2008 SP2 değil ya da daha sonra yükleme [düzeltme 251798](https://go.microsoft.com/fwlink/?LinkId=184693).  
  
4.  Aşağıdaki komutları çalıştırın. Bu komutlar neden çalıştırılmalıdır hakkında daha fazla bilgi için bkz. [IIS barındırılan hizmet başarısız](https://msdn.microsoft.com/library/ee5499fc-1b10-4cda-a9b1-13dba70f05f8).  
  
    > [!WARNING]
    >  IIS yeniden yüklenirse, aşağıdaki komutları yeniden çalıştırılması gerekir.  
  
    ```  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r  
    ```  
  
    > [!WARNING]
    >  Komutu çalıştırmadan `aspnet_regiis –i –enable` varsayılan uygulama havuzunu kullanarak çalışma hale getirecek [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], aynı bilgisayarda diğer uygulamalar için uyumsuzluk sorunlarını oluşturabilir.  
  
5.  İzleyin [güvenlik duvarı yönergeleri](../../../../docs/framework/wcf/samples/firewall-instructions.md) örnekleri tarafından kullanılan bağlantı noktaları etkinleştirmek için.  
  
6.  Denetlemek için aşağıdaki varsayılan dizin: \<Installdrive >:**\WF_WCF_Samples**. Bu, örneklerin daha önce yüklenmişse, varsayılan dizindir.  
  
7.  Örnekleri indirme konumundan için bunları yüklemeniz örnekleri yüklü değilse [Visual C#](https://go.microsoft.com/fwlink/?LinkId=190939) veya [Visual Basic](https://go.microsoft.com/fwlink/?LinkID=193373).  
  
8.  Örnekleri yükledikten sonra gidin: \<Installdrive >:**\WF_WCF_Samples\WCF\Setup\\**  
  
9. Çalıştırma **Setupvroot.bat** toplu iş dosyası. Aşağıdaki adımları gerçekleştirilir:  
  
    -   Bir sanal dizin ServiceModelSamples adlı IIS içinde oluşturulur.  
  
    -   Yeni disk dizinler, adlandırılmış %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples ve % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin oluşturulur.  
  
     Bu dizinler el ile ayarlamak isterseniz bkz [sanal dizin ayarlama yönergeleri](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Bu adımda yapılan tüm değişiklikleri geri almak, örneklerini kullanma işlemini tamamladıktan sonra cleanupvroot.bat çalıştırın.  
  
    > [!NOTE]
    >  Cleanupvroot.bat çalıştırmadığınız sürece bir bilgisayarda bu yordamı yalnızca bir kez gerçekleştirilmesi gerekir.  
  
10. %SystemDrive%\inetpub\wwwroot altında örnekleri ve Network SERVICE kullanıcısı oluşturmakta olduğunuz hesabına değiştirme izni gerekir. Yapı, yaparken bazı Web barındırılan örnekleri, derlenmiş ikili dosyaları yukarıda belirtilen konuma kopyalanacak deneyebilir ve uygun izinleri ayarlamadıysanız, derleme kesilir. Alternatif olarak, bunlar ve SDK komut istemi veya Visual Studio komut istemi (2012) yönetici olarak çalıştırmak gibi izinleri bırakın veya kullanabilirsiniz örnekleri yapı içinde [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]de yönetici olarak çalıştırın.  
  
    > [!NOTE]
    >  Bu adım tamamlanmazsa, IIS tarafından barındırılan tüm örnekleri derleme sırasında başarısız olur. Doğru izinleri ayarlamak veya SDK komut istemi hem Visual Studio komut istemi (2012) yönetici olarak çalıştır emin olun.  
  
11. Bilgisayarda bir C:\logs dizin oluşturun; Bazı örnekler, bekliyor olabilir. Uygun hesabı bu klasöre verilen yazma erişimi olduğundan emin olun. Windows 7'de, [!INCLUDE[wv](../../../../includes/wv-md.md)], ve Windows Server 2008 R2'de, bu hesap, **ağ hizmeti**. İçin [!INCLUDE[lserver](../../../../includes/lserver-md.md)], NT AUTHORITY\NETWORK SERVICE hesaptır. İçin [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ASP.NET hesaptır.  
  
12. Setupcerttool.bat dosyasını çalıştırın. Bu dosya bulunan \<InstallPath > \WF_WCF_Samples\WCF\Setup\ klasör.  Bu betik aşağıdaki görevleri gerçekleştireceksiniz:  
  
    -   Derleme FindPrivateKey aracı.  
  
    -   % ProgramFiles%\ServiceModelSampleTools adlı bir dizin oluşturun.  
  
    -   Yeni FindPrivateKey aracı bu dizine kopyalayın.  
  
     Bu araç, sertifikalar kullanmak ve IIS'de barındırılan örnekleri gereklidir.  
  
    > [!NOTE]
    >  Güvenlik nedenleriyle, sanal dizin tanımını ve örneklerle tamamladıktan sonra Cleanupvroot.bat adlı toplu iş dosyası çalıştırılarak kurulum adımları, verilen izinleri kaldırmayı unutmayın.  
  
13. (IIS'de barındırılan değil) şirket içinde barındırılan örnekleri dinleme bu bilgisayarda HTTP adresleri kaydetme izni gerektirir. Bir HTTP ad alanı ayırmasını iznini örneği çalıştırmak için kullanılan kullanıcı hesabını gelir. Varsayılan olarak, yönetici hesapları, tüm HTTP adresini kaydetmek için izne sahip. Yönetici olmayan hesaplar örnekleri tarafından kullanılan HTTP ad alanları için izin verilmelidir. Ad alanı ayırmaları yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma HTTP ve HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).  
  
14. Bazı örnekler, Message Queuing gerektirir. Bkz: [yükleme Message Queuing (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) yükleme yönergeleri için.  
  
    > [!NOTE]
    >  Message Queuing gerektiren örnek çalıştırmadan önce MSMQ hizmeti başlatmak emin olun.  
  
15. Bazı örnekler sertifikaları gerektirir. Bkz: [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

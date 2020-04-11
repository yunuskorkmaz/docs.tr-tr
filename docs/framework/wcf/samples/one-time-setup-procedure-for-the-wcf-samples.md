---
title: Windows Communication Foundation Örnekleri için Bir Kerelik Kurulum Prosedürü
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 954ec04d2ef1ca7667b4f75a8a6652010b5dbd33
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121623"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örnekleri için Bir Kerelik Kurulum Prosedürü

Windows Communication Foundation (WCF) örneklerinin çoğu Internet Information Services (IIS) adresinde barındırılır ve ortak bir sanal dizinden çalıştırılır. Bu tek seferlik kurulum yordamı diskte bir klasör oluşturur; ayrıca **ServiceModelSamples**adlı IIS için sanal bir dizin ekler.

**ServiceModelSamples** sanal dizini, IIS tarafından barındırılan bir hizmeti kullanan tüm örnekleri oluşturmak ve çalıştırmak için kullanılır. Bu, örnekleri çalıştırmak için gereken tek sanal dizindir. Bir örnek oluşturma, bu sanal dizinde daha önce dağıtılan herhangi bir hizmetin yerini alacaktır; yalnızca en son oluşturulmuş örnek dağıtılır ve bu sanal dizinde kullanılabilir.

> [!NOTE]
> Tüm komutları yerel bir yönetici hesabı altında çalıştırmanız gerekir. Windows 7, Windows Vista veya Windows Server 2008 R2 kullanıyorsanız, komut istemini yüksek ayrıcalıklarla da çalıştırmanız gerekir. Bunu yapmak için komut istemi simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır'ı**tıklatın. Bu konudaki tüm komutlar, uygun yol ayarlarına sahip bir komut isteminde çalıştırılmalıdır.  Bunu sağlamanın en kolay yolu Visual Studio Komut Komut Komut Ustem'ini kullanmaktır. Bu istemi açmak için, **Başlat'ı**tıklatın , **Tüm Programlar**seçin , **Visual Studio 2010**aşağı kaydırın , Visual Studio Tools seçin , Visual **Studio** **Komut Istemi (2010)** sağ tıklayın , ve sonra **yönetici olarak çalıştır'ı**tıklatın . Visual Studio Express sürümlerinden biri yüklüyse, bu komut istemi kullanılamaz ve sistem yoluna "C:\Windows\Microsoft.Net\Framework\v4.0" eklemeniz gerekir.

### <a name="one-time-setup-procedure-for-wcf-samples"></a>WCF örnekleri için tek seferlik kurulum yordamı

1. ASP.NET ayarlandığından emin olun. ASP.NET nasıl ayarlanın açılacağına ilişkin daha fazla bilgi için [Internet Information Service Hosting Instructions](internet-information-service-hosting-instructions.md)'a bakın.

2. .NET Framework 4'ün yüklü olduğundan emin olun. v4.0 (veya sonraki) için aşağıdaki dizini arayın: **\Windows\Microsoft.NET\Framework**

3. Visual Studio 2012 veya daha sonra yüklü olduğundan veya işletim sisteminizin Windows Server 2008 SP2 veya sonraki olduğundan emin olun.

4. Aşağıdaki komutları çalıştırın. Bu komutların neden çalıştırılması gerektiği hakkında daha fazla bilgi için Bkz. [IIS Hosted Service Fails](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > IIS yeniden yüklenirse, aşağıdaki komutların yeniden çalıştırılması gerekir.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > Komutu `aspnet_regiis –i –enable` çalıştırmak, aynı bilgisayardaki diğer uygulamalar için uyumsuzluk sorunlarına neden olabilecek .NET Framework 4 kullanarak Varsayılan Uygulama Havuzu'nu çalıştırır.

5. Örnekler tarafından kullanılan bağlantı noktalarını etkinleştirmek için [Güvenlik Duvarı Yönergeleri'ni](firewall-instructions.md) izleyin.

6. Aşağıdaki varsayılan dizin için \<denetleyin: InstallDrive>:**\WF_WCF_Samples**. Örnekler daha önce yüklenmişse, bu varsayılan dizindir.

7. Örnekler yüklenmezse, [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) Örneklerinden](https://www.microsoft.com/download/details.aspx?id=21459)yükleyin.

8. Örnekleri yükledikten sonra: \<InstallDrive>:**\WF_WCF_Samples\WCF\Setup\\ **

9. **Setupvroot.bat** toplu iş dosyasını çalıştırın. Aşağıdaki adımlar gerçekleştirilir:

    - ServiceModelSamples adlı IIS'de sanal bir dizin oluşturulur.

    - Yeni disk dizinleri %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples ve %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin olarak oluşturulur.

    Bu dizinleri el ile ayarlamayı tercih ederseniz, [Sanal Dizin Kurulum Yönergeleri'ne](virtual-directory-setup-instructions.md)bakın. Bu adımda yapılan tüm değişiklikleri geri almak için, örnekleri kullanarak bitirdikten sonra cleanupvroot.bat çalıştırın.

    > [!NOTE]
    > Bu yordam, cleanupvroot.bat çalıştırılmadığı sürece, bir bilgisayarda yalnızca bir kez yapılmalıdır.

10. Örnekleri ve Ağ Hizmeti kullanıcısını oluşturmakta olduğunuz hesaba %SystemDrive%\inetpub\wwwroot için değişiklik izni vermelisiniz. Bina oluştururken, bazı Web tarafından barındırılan örnekler derlenmiş ikilileri önceden belirtilen konuma kopyalamayı deneyebilir ve uygun izinleri ayarlamadıysanız, yapı bozulur. Alternatif olarak, izinleri olduğu gibi bırakabilir ve SDK komut istemini veya Visual Studio Komut Komut Istemi'ni (2012) Yönetici olarak çalıştırabilir veya Visual Studio 2012'de de Yönetici olarak çalışan örnekleri oluşturabilirsiniz.

    > [!NOTE]
    > Bu adım tamamlanmazsa, IIS tarafından barındırılan tüm örnekler bina sırasında başarısız olur. İzinleri doğru ayarladığınızdan veya hem SDK komut istemini hem de Visual Studio Komut Komut Istemi'ni (2012) Yönetici olarak çalıştırdığınızdan emin olun.

11. Bilgisayarda C:\günlük dizini oluşturun; bazı örnekler bunu bekliyor olabilir. Uygun hesabın bu klasöre verilen yazma erişimine sahip olduğundan emin olun. Windows 7, Windows Vista ve Windows Server 2008 R2 için bu hesap **Ağ Hizmeti'dir.** Windows Server 2008 için hesap NT Authority\Network Service'dir. Windows XP ve Windows Server 2003 için hesap ASPNET'tir.

12. Setupcerttool.bat dosyasını çalıştırın. Bu dosya \<InstallPath>\WF_WCF_Samples\WCF\Setup\ klasöründe bulunur.  Bu komut dosyası aşağıdaki görevleri gerçekleştirir:

    - FindPrivateKey aracını oluşturun.

    - %ProgramFiles%\ServiceModelSampleTools adlı bir dizin oluşturun.

    - Yeni FindPrivateKey aracını bu dizine kopyalayın.

    Bu araç, sertifika kullanan ve IIS'de barındırılan örnekler tarafından gereklidir.

    > [!NOTE]
    > Güvenlik amacıyla, örnekleri bitirdikten sonra Cleanupvroot.bat adlı toplu iş dosyasını çalıştırarak yukarıdaki kurulum adımlarında verilen sanal dizin tanımını ve izinleri kaldırmayı unutmayın.

13. Kendi kendine barındırılan (IIS'de barındırılan değil) örnekler, dinleme için http adreslerini bilgisayara kaydetmek için izin gerektirir. HTTP ad alanı rezervasyonu izni, örneği çalıştırmak için kullanılan kullanıcı hesabından gelir. Varsayılan olarak, yönetici hesapları herhangi bir HTTP adresini kaydetme iznine sahiptir. Yönetici olmayan hesaplara örnekler tarafından kullanılan HTTP ad alanları için izin verilmelidir. Ad alanı rezervasyonlarını yapılandırma hakkında daha fazla bilgi için [http ve HTTPS yapılandırma](../feature-details/configuring-http-and-https.md)bölümüne bakın.

14. Bazı örnekler ileti sıralaması gerektirir. Yükleme yönergeleri için [İleti Sıralamasını (MSMQ) yükleme](installing-message-queuing-msmq.md) ye bakın.

    > [!NOTE]
    > İleti Sıralaması gerektiren örnekleri çalıştırmadan önce MSMQ hizmetini başlattığınıza emin olun.

15. Bazı örnekler sertifika gerektirir. Bkz. [Internet Bilgi Hizmetleri (IIS) Sunucu Sertifikası Yükleme Talimatları.](iis-server-certificate-installation-instructions.md)

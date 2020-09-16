---
title: Windows Communication Foundation Örnekleri için Bir Kerelik Kurulum Prosedürü
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: bf25ea4734bad007fa3ac19df0664932d981519c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548123"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Windows Communication Foundation Örnekleri için Bir Kerelik Kurulum Prosedürü

Windows Communication Foundation (WCF) örneklerinin çoğu Internet Information Services (IIS) içinde barındırılır ve ortak bir sanal dizinden çalıştırılır. Bu tek seferlik kurulum yordamı, disk üzerinde bir klasör oluşturur; Ayrıca, **servicemodelsamples**adlı IIS 'ye bir sanal dizin ekler.

**Servicemodelsamples** sanal DIZINI, IIS tarafından barındırılan bir hizmeti kullanan tüm örnekleri oluşturmak ve çalıştırmak için kullanılır. Bu, örnekleri çalıştırmak için gereken tek sanal dizindir. Örnek oluşturmak, bu sanal dizinde önceden dağıtılan tüm hizmetleri değiştirecek; Bu sanal dizinde yalnızca en son oluşturulan örnek dağıtılır ve kullanılabilir.

> [!NOTE]
> Tüm komutları bir yerel yönetici hesabı altında çalıştırmalısınız. Windows 7, Windows Vista veya Windows Server 2008 R2 kullanıyorsanız, komut istemi ' ni yükseltilmiş ayrıcalıklarla da çalıştırmanız gerekir. Bunu yapmak için, komut istemi simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın. Bu konudaki tüm komutların, uygun yol ayarlarına sahip bir komut isteminde çalıştırılması gerekir.  Bunu sağlamanın en kolay yolu Visual Studio komut Istemi ' ni kullanmaktır. Bu istemi açmak için **Başlat**' a tıklayın, **tüm programlar**' ı seçin, **Visual Studio 2010**' ye kaydırın, **Visual Studio Araçları**' yi seçin, **Visual Studio komut istemi (2010)** öğesini sağ tıklatın ve ardından **yönetici olarak çalıştır**' ı tıklatın. Visual Studio Express sürümlerinden biri yüklüyse, bu komut istemi kullanılamaz ve sistem yoluna "C:\Windows\Microsoft.Net\Framework\v4.0" eklemeniz gerekir.

### <a name="one-time-setup-procedure-for-wcf-samples"></a>WCF örnekleri için bir kerelik Kurulum yordamı

1. ASP.NET ayarlandığından emin olun. ASP.NET ayarlama hakkında daha fazla bilgi için bkz. [Internet Information Service barındırma yönergeleri](internet-information-service-hosting-instructions.md).

2. .NET Framework 4 ' ün yüklü olduğundan emin olun. V 4.0 (veya üzeri) için şu dizinde arama yapın: **\Windows\microsoft.NET\Framework**

3. Visual Studio 2012 veya sonraki bir sürümünün yüklü olduğundan veya işletim sisteminizin Windows Server 2008 SP2 veya sonraki bir sürümü olduğundan emin olun.

4. Aşağıdaki komutları çalıştırın. Bu komutların neden çalıştırılması gereken hakkında daha fazla bilgi için bkz. [IIS barındırılan hizmeti başarısız oluyor](/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > IIS yeniden yüklenirse, aşağıdaki komutların yeniden çalıştırılması gerekir.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > Komutu çalıştırmak, `aspnet_regiis –i –enable` Varsayılan uygulama havuzunu aynı bilgisayardaki diğer uygulamalar için uyumsuzluk sorunları oluşturabilecek .NET Framework 4 kullanarak çalışır hale getirir.

5. Örnekler tarafından kullanılan bağlantı noktalarını etkinleştirmeye yönelik [güvenlik duvarı yönergelerini](firewall-instructions.md) izleyin.

6. Şu varsayılan dizini denetle: \<InstallDrive> :**\ WF_WCF_Samples**. Örnekler daha önce yüklenmişse, bu varsayılan dizindir.

7. Örnekler yüklü değilse, [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerinden](https://www.microsoft.com/download/details.aspx?id=21459)onları yükleme.

8. Örnekleri yükledikten sonra şuraya gidin: \<InstallDrive> :**\ WF_WCF_Samples \WCF\Setup \\ **

9. **Setupvroot.bat** Batch dosyasını çalıştırın. Aşağıdaki adımlar gerçekleştirilir:

    - ServiceModelSamples adlı IIS 'de bir sanal dizin oluşturulur.

    - %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples ve%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin. adlı yeni disk dizinleri oluşturulur

    Bu dizinleri el ile ayarlamayı tercih ediyorsanız, [sanal dizin kurulum yönergelerine](virtual-directory-setup-instructions.md)bakın. Bu adımda yapılan tüm değişiklikleri dönmek için, örnekleri kullanmayı bitirdikten sonra cleanupvroot.bat çalıştırın.

    > [!NOTE]
    > cleanupvroot.bat çalıştırılmamışsa, bu yordamın bir bilgisayarda yalnızca bir kez gerçekleştirilmesi gerekir.

10. %Systemdrive%\ınetpub\wwwroot için, örnekleri ve ağ hizmeti kullanıcısını oluşturduğunuz hesaba yönelik değiştirme izni vermelisiniz. Derlenirken, Web 'de barındırılan bazı örnekler derlenmiş ikilileri önceden belirtilen konuma kopyalamaya çalışabilir ve uygun izinleri ayarlanmamışsa, derleme kesilir. Alternatif olarak, izinleri oldukları gibi bırakabilir ve SDK komut istemi veya Visual Studio komut Istemi 'ni (2012) yönetici olarak çalıştırabilir ya da Visual Studio 2012 ' de aynı zamanda yönetici olarak da çalıştırabilirsiniz.

    > [!NOTE]
    > Bu adım tamamlanmazsa, derleme sırasında IIS 'de barındırılan tüm örnekler başarısız olur. İzinleri doğru şekilde ayarlamış olduğunuzdan emin olun veya hem SDK komut istemi 'ni hem de Visual Studio komut Istemi 'ni (2012) yönetici olarak çalıştırın.

11. Bilgisayarda C:\logs dizini oluşturun; bazı örnekler bekleniyor olabilir. Uygun hesabın bu klasöre verilen yazma erişimi olduğundan emin olun. Windows 7, Windows Vista ve Windows Server 2008 R2 için bu hesap, **ağ hizmetidir**. Windows Server 2008 için, hesap NT Authority\Network Service ' dir. Windows XP ve Windows Server 2003 için, bu hesap ASPNET ' dir.

12. Setupcerttool.bat dosyasını çalıştırın. Bu dosya  \<InstallPath> \ WF_WCF_Samples \WCF\Setup\ klasöründe bulunur.  Bu betik aşağıdaki görevleri gerçekleştirir:

    - FindPrivateKey aracını oluşturun.

    - %ProgramFiles%\ServiceModelSampleTools. adlı bir dizin oluşturun

    - Yeni FindPrivateKey aracını bu dizine kopyalayın.

    Bu araç, sertifikaları kullanan ve IIS 'de barındırılan örnekler için gereklidir.

    > [!NOTE]
    > Güvenlik nedeniyle, örnekleri ile işiniz bittiğinde Cleanupvroot.bat adlı toplu iş dosyasını çalıştırarak yukarıdaki Kurulum adımlarında verilen sanal dizin tanımını ve izinleri kaldırmayı unutmayın.

13. Şirket içinde barındırılan (IIS 'de barındırılmayan) örnekler, dinlemek üzere bilgisayarda HTTP adreslerini kaydetmek için izin gerektirir. Bir HTTP ad alanı ayırması için izin, örneği çalıştırmak için kullanılan kullanıcı hesabından gelir. Varsayılan olarak, yönetici hesaplarının herhangi bir HTTP adresini kaydetme izni vardır. Yönetici olmayan hesaplara, örnekler tarafından kullanılan HTTP ad alanları için izin verilmesi gerekir. Ad alanı ayırmalarını yapılandırma hakkında daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md).

14. Bazı örnekler Message Queuing gerektirir. Yükleme yönergeleri için bkz. [Message Queuing (MSMQ) yükleme](installing-message-queuing-msmq.md) .

    > [!NOTE]
    > Message Queuing gerektiren örnekleri çalıştırmadan önce MSMQ hizmetini başlattığınızdan emin olun.

15. Bazı örnekler için sertifikalar gerekir. Bkz. [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](iis-server-certificate-installation-instructions.md).

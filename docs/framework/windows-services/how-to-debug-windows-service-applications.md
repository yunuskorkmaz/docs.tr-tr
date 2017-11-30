---
title: "Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: c49d05a9ca09a12044c0846db381368166e105bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-debug-windows-service-applications"></a>Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama
Bir hizmet, hizmet denetimi Yöneticisi'ni yerine içinden bağlamında çalıştırılmak gerekir Visual Studio. Bir hizmet hata ayıklama özelliği bu nedenle, diğer Visual Studio uygulama türleri hata ayıklama olarak kadar basit değildir. Bir hizmette hata ayıklamak için hizmeti başlatın ve sonra onu çalıştığı işlem bir hata ayıklayıcısı eklemeniz gerekir. Sonra tüm standart hata ayıklama işlevselliğini Visual Studio kullanarak uygulamanızı ayıklayabilirsiniz.  
  
> [!CAUTION]
>  Hangi işlemin ve ekleme ve büyük olasılıkla bu işlemin sonlandırılması sonuçlarını anlama bilmiyorsanız, bir işleme ek yapmamanız gerekir. Örneğin, WinLogon işleme ekleyin ve ardından hata ayıklamayı durdurun, WinLogon işleyemeyeceği sistem durdurulur.  
  
 Hata ayıklayıcı yalnızca çalışan bir hizmete ekleyebilirsiniz. Ek işlemi geçerli işleyişini keser; gerçekte durdurmak veya hizmetin işleme duraklatmak değil. Hata ayıklama başladığınızda, hizmet çalışıyorsa, diğer bir deyişle, bu teknik olarak hala başlatıldı ayıklama, ancak işleme askıya alındı olarak durumda.  
  
 İşleme ekledikten sonra kesme noktalarını ayarlayabilir ve bunlar kodunuzun hatalarını ayıklamak için kullanabilirsiniz. İşleme iliştirilemiyor için kullandığınız iletişim kutusundan çıktıktan sonra etkin hata ayıklama modunda demektir. Başlatma, durdurma, duraklatma ve böylece ayarladığınız kesme noktaları basarsa hizmetiniz, devam etmek için Hizmet Denetimi Yöneticisi'ni kullanabilirsiniz. Hata ayıklama başarılı olduktan sonra daha sonra bu kukla hizmetini kaldırabilirsiniz.  
  
 Bu makalede, yerel bilgisayarda çalışan bir hizmet hata ayıklama yer almaktadır, ancak uzak bir bilgisayarda çalışan Windows Hizmetleri de ayıklayabilirsiniz. Bkz: [uzaktan hata ayıklama](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
>  Hata ayıklama <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Hizmet Denetim Yöneticisi bir hizmeti başlatmak için tüm girişimleri üzerinde 30 saniyelik bir sınır getirir çünkü yöntemi zor olabilir. Daha fazla bilgi için bkz: [sorun giderme: hata ayıklama Windows Hizmetleri](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
> [!WARNING]
>  Hata ayıklama için anlamlı bilgiler almak için Visual Studio hata ayıklayıcısında simge dosyaları ayıklanacak ikili dosyaları bulması gerekir. Visual Studio'da yerleşik bir hizmet hata ayıklama, simge (.pdb dosyaları) yürütülebilir dosya veya kitaplığı olarak aynı klasörde dosyalardır ve hata ayıklayıcı bunları otomatik olarak yükler. Yapı gelmedi bir hizmet hata ayıklama, ilk sembolleri için hizmeti bulun ve gerekir hata ayıklayıcı tarafından bulunabilir olduğundan emin olun. Bkz: [simge (.pdb) belirtin ve kaynak dosyaları](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b). Bir sistem işlemi hatalarını ayıkladığınız veya sistem çağrıları simgelerini hizmetlerinizi içinde olmasını istiyorsanız, Microsoft simge sunucuları eklemeniz gerekir. Bkz: [hata ayıklama simgeleri](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).  
  
### <a name="to-debug-a-service"></a>Bir hizmette hata ayıklamak için  
  
1.  Hata ayıklama yapılandırmasını hizmetinizi oluşturun.  
  
2.  Hizmetinizi yükleyin. Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
3.  Hizmetinizi herhangi birinden Başlat **Hizmet Denetim Yöneticisi**, **Sunucu Gezgini**, veya koddan. Daha fazla bilgi için bkz: [nasıl yapılır: Hizmetleri başlatma](../../../docs/framework/windows-services/how-to-start-services.md).  
  
4.  Sistem işlemleri ekleyebilirsiniz. böylece yönetici kimlik bilgileriyle Visual Studio'yu başlatın.  
  
5.  (İsteğe bağlı) Visual Studio menü çubuğunda seçin **Araçları**, **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda, seçin **hata ayıklama**, **simgeleri**seçin **Microsoft simge sunucuları** onay kutusunu işaretleyin ve ardından seçin **Tamam** düğmesi.  
  
6.  Menü çubuğunda seçin **ekleme işlemi için** gelen **hata ayıklama** veya **Araçları** menüsü. (Klavye: Ctrl + Alt + P)  
  
     **İşlemleri** iletişim kutusu görüntülenir.  
  
7.  Seçin **işlemleri tüm kullanıcıları göster** onay kutusu.  
  
8.  İçinde **kullanılabilir işlemler** bölümünde, hizmetiniz için işlem seçin ve ardından **Attach**.  
  
    > [!TIP]
    >  İşlem yürütülebilir dosyası hizmetiniz için aynı ada sahip olacaktır.  
  
     **Ekleme işlemi için** iletişim kutusu görüntülenir.  
  
9. Uygun seçenekleri seçin ve ardından **Tamam** iletişim kutusunu kapatın.  
  
    > [!NOTE]
    >  Hata ayıklama modunda sunulmuştur.  
  
10. Kodunuzda kullanmak istediğiniz tüm kesme noktalarını ayarlayın.  
  
11. Hizmet Denetim Yöneticisi erişim ve yönlendirme hizmeti, gönderen durdurma, duraklatma ve devam et noktalarınıza isabet komutlarını. Hizmet Denetimi Yöneticisi'ni çalıştırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Hizmetleri başlatma](../../../docs/framework/windows-services/how-to-start-services.md). Ayrıca bkz [sorun giderme: hata ayıklama Windows Hizmetleri](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
## <a name="debugging-tips-for-windows-services"></a>Windows Hizmetleri için hata ayıklama ipuçları  
 Hizmetin işlemine iliştirme tümünün değil ancak bu hizmet için kod ayıklamanızı sağlar. Örneğin, hizmetin zaten başlatılmış olduğundan, hizmetin kodda hata ayıklama olamaz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi veya kodda `Main` hizmeti bu şekilde yüklemek için kullanılan yöntem. Bu sınırlamaya geçici bir çözüm yollarından biri yalnızca hata ayıklamaya yardımcı olmak için mevcut hizmet uygulamanızın geçici olarak ikinci hizmet oluşturmaktır. Her iki hizmet yükleyin ve ardından hizmet işlemini yüklemek için bu kukla hizmetini başlatın. Geçici olarak hizmet işlemi başladıktan sonra kullanabileceğiniz **hata ayıklama** hizmet işlemini iliştirmek için Visual Studio menüsünde.  
  
 Çağrı eklemeyi deneyin <xref:System.Threading.Thread.Sleep%2A> işleme iliştirilemiyor mümkün kadar gecikme eylem yöntemi.  
  
 Program bir normal konsol uygulaması değiştirmeyi deneyin. Bunu yapmak için yeniden yazma `Main` şu şekilde bir Windows hizmeti hem nasıl başlatılacağını bağlı olarak bir konsol uygulaması olarak çalıştırabilmeniz yöntemi.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Nasıl yapılır: bir Windows hizmeti bir konsol uygulaması olarak çalıştırmak  
  
1.  Hizmetinize çalıştıran bir yöntem ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemleri:  
  
    ```  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  Yeniden yazma `Main` yöntemini aşağıdaki şekilde:  
  
    ```  
    static void Main(string[] args)  
            {  
                if (Environment.UserInteractive)  
                {  
                    MyNewService service1 = new MyNewService(args);  
                    service1.TestStartupAndStop(args);  
                }  
                else  
                {  
                    // Put the body of your old Main method here.  
                }  
    ```  
  
3.  İçinde **uygulama** projenin özelliklerinin sekmesinde ayarlamak **çıktı türü** için **konsol uygulaması**.  
  
4.  Seçin **hata ayıklamayı Başlat** (F5).  
  
5.  Programı bir Windows hizmeti olarak yeniden çalıştırmak için yüklemek ve bir Windows hizmeti için her zamanki gibi başlatın. Bu değişiklikleri geri almak gerekli değildir.  
  
 Yalnızca sistem başlangıçta oluşan bir sorun hata ayıklamak istediğiniz zaman gibi bazı durumlarda, Windows hata ayıklayıcı kullanmak zorunda. Yükleme [Windows için hata ayıklama araçları](http://msdn.microsoft.com/windows/hardware/hh852365) ve [Windows Hizmetleri hata ayıklamak nasıl](http://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows hizmet uygulamalarına giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl yapılır: Hizmetleri Yükleme ve kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Nasıl yapılır: Hizmetleri başlatma](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Bir hizmet hata ayıklama](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)

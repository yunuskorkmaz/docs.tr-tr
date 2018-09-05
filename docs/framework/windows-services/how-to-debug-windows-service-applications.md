---
title: 'Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
manager: douge
ms.openlocfilehash: a0c57ab049fff699d5bb12004fd48d90a226e514
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525028"
---
# <a name="how-to-debug-windows-service-applications"></a>Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama
Bir hizmet alanından, Hizmet Denetim Yöneticisi yerine içinden bağlam içinde çalıştırılmalıdır Visual Studio. Bu nedenle, bir hizmette hata ayıklamak diğer Visual Studio uygulama türlerinde hata ayıklamak kadar basit değil Bir hizmette hata ayıklamak için hizmeti başlatın ve sonra içinde çalıştığı işleme bir hata ayıklayıcı eklemeniz gerekir. Ardından tüm Visual Studio standart hata ayıklama işlevselliğini kullanarak uygulamanızın hatalarını ayıklayabilirsiniz.  
  
> [!CAUTION]
>  Hangi işlemin ve büyük olasılıkla, işlemi öldürmenin ve işleme ekleme sonuçları anladığınızdan bilmediği sürece bir işleme eklememelisiniz. Örneğin, WinLogon işlemine eklerseniz ardından hata ayıklamayı durdurmak, WinLogon işleyemeyeceği sistem durdurulur.  
  
 Hata ayıklayıcıyı yalnızca çalışan bir hizmete ekleyebilirsiniz. Ek işlemi, hizmetinizin geçerli işleyişini keser; Bu değil gerçekten durdurmaz veya duraklatmaz. Hata ayıklamayı başladığınızda, hizmet çalışıyorsa, diğer bir deyişle, bu teknik olarak hala başlatılmış durumdadır ayıklama, ancak işlemesi askıya aynıdır.  
  
 İşleme iliştirdikten sonra kesme noktaları ayarlayabilir ve bunları kodunuzdaki hataları ayıklamak için kullanın. İşleme için kullandığınız iletişim kutusundan çıktıktan sonra etkili bir şekilde hata ayıklama modunda olursunuz. Başlatma, durdurma, duraklatma ve böylece ayarladığınız kesme noktalarının isabet hizmetiniz, devam etmek için Hizmet Denetim Yöneticisi'ni kullanabilirsiniz. Hata ayıklama başarılı olduktan sonra bu kukla hizmetini daha sonra kaldırabilirsiniz.  
  
 Bu makalede yerel bilgisayar üzerinde çalışan bir hizmette hata ayıklamak yer almaktadır, ancak uzak bir bilgisayarda çalışan Windows Hizmetleri de ayıklayabilirsiniz. Bkz: [uzaktan hata ayıklama](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
>  Hata ayıklama <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 30 saniyelik bir sınır üzerinde bir hizmet başlatmaya yönelik tüm girişimleri Hizmet Denetim Yöneticisi'ni getirir çünkü yöntemi zor olabilir. Daha fazla bilgi için [sorunlarını giderme: Windows Hizmetleri hata ayıklama](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
> [!WARNING]
>  Hata ayıklama için anlamlı bilgiler almak için Visual Studio hata ayıklayıcının, hatası ayıklanan ikililer için Sembol dosyalarını bulmak gerekir. Visual Studio'da oluşturulan bir hizmet ayıklıyorsanız, sembol dosyalarını (.pdb) yürütülebilir veya kitaplık aynı klasörde olan ve hata ayıklayıcının bunları otomatik olarak yükler. Yapı gelmedi bir hizmeti hata ayıklaması yapıyorsanız, ilk hizmet için simgeleri Bul ve hata ayıklayıcı tarafından bulunabilir emin olmak gerekir. Bkz: [sembol (.pdb) belirtin ve kaynak dosyaları](https://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b). Bir sistem işlemi hata ayıklama veya sistem çağrıları için semboller hizmetlerinizde sahip olmasını isterseniz Microsoft sembol sunucuları eklemeniz gerekir. Bkz: [hata ayıklama simgeleri](/windows/desktop/DxTechArts/debugging-with-symbols).  
  
### <a name="to-debug-a-service"></a>Bir hizmette hata ayıklamak için  
  
1.  Hizmetinizde hata ayıklama yapılandırmasını oluşturun.  
  
2.  Hizmetinizi yükleyin. Daha fazla bilgi için [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
3.  Başlat'nden ya da hizmetiniz **Hizmet Denetim Yöneticisi**, **Sunucu Gezgini**, veya koddan. Daha fazla bilgi için [nasıl yapılır: hizmetlerini başlatma](../../../docs/framework/windows-services/how-to-start-services.md).  
  
4.  Sistem işleme iliştirebilirsiniz için yönetici kimlik bilgileriyle Visual Studio'yu başlatın.  
  
5.  (İsteğe bağlı) Visual Studio menü çubuğunda **Araçları**, **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **hata ayıklama**, **sembolleri**seçin **Microsoft sembol sunucuları** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
6.  Menü çubuğunda, **iliştirme** gelen **hata ayıklama** veya **Araçları** menüsü. (Klavye: Ctrl + Alt + P)  
  
     **İşlemleri** iletişim kutusu görüntülenir.  
  
7.  Seçin **tüm kullanıcıların işlemlerini göster** onay kutusu.  
  
8.  İçinde **kullanılabilir işlemler** bölümünde hizmetinizin işlemini seçin ve ardından **iliştirme**.  
  
    > [!TIP]
    >  İşlem hizmetiniz için yürütülebilir dosyasıyla aynı ada sahip olacaktır.  
  
     **İliştirme** iletişim kutusu görüntülenir.  
  
9. Uygun seçenekleri seçin ve ardından **Tamam** iletişim kutusunu kapatın.  
  
    > [!NOTE]
    >  Hata ayıklama modunda sunulmuştur.  
  
10. Kodunuzda kullanmak istediğiniz herhangi bir kesme noktası ayarlayın.  
  
11. Hizmet Denetim Yöneticisi erişim işleme hizmeti, gönderen durdurma, duraklatma ve devam et komutlarını kesme noktalarınıza isabet ettirmek için. Hizmet Denetimi Yöneticisi'ni çalıştırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmetlerini başlatma](../../../docs/framework/windows-services/how-to-start-services.md). Ayrıca bkz [sorunlarını giderme: Windows Hizmetleri hata ayıklama](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
## <a name="debugging-tips-for-windows-services"></a>Windows Hizmetleri için hata ayıklama ipuçları  
 Hizmet işlemine iliştirme tümünü değil ancak bu hizmet için kod hatalarını ayıklamak sağlar. Örneğin, hizmet zaten başlatılmış olduğundan, hizmetin kodunda hata ayıklaması yapılamıyor <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi veya kodda `Main` bu şekilde hizmeti yüklemek için kullanılan yöntem. Bu sınırlamaya geçici bir çözüm yollarından biri yalnızca hata ayıklamaya yardımcı olmak için mevcut hizmet uygulamanızda ikinci bir geçici hizmet oluşturmaktır. İki hizmeti de yükleyebilir ve sonra hizmet işlemini yüklemek üzere bu kukla hizmetini başlatın. Geçici hizmet işlemi başlattıktan sonra kullanabileceğiniz **hata ayıklama** hizmet işlemini iliştirmek için Visual Studio'da menü.  
  
 Çağrıları eklemeyi deneyin <xref:System.Threading.Thread.Sleep%2A> işleme olanağına kadar gecikme eylemi için yöntemi.  
  
 Normal bir konsol programı değiştirmeyi deneyin. Bunu yapmak için yeniden `Main` şu şekilde bir Windows hizmeti olarak ve kullanmaya nasıl bağlı olarak bir konsol uygulaması olarak çalıştırabilmeniz yöntemi.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Nasıl yapılır: bir Windows hizmeti bir konsol uygulaması olarak çalıştır  
  
1.  Çalışan hizmetinize bir yöntem ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemleri:  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  Yeniden `Main` yöntemini aşağıdaki şekilde:  
  
    ```csharp  
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
    }
    ```  
  
3.  İçinde **uygulama** sekmesinde projenin özelliklerini ayarlamak **çıkış türü** için **konsol uygulaması**.  
  
4.  Seçin **hata ayıklamayı Başlat** (F5).  
  
5.  Program bir Windows hizmeti olarak yeniden çalıştırmak için yükleyin ve bir Windows hizmeti için her zamanki şekilde başlatın. Bu değişiklikleri geri almak gerekli değildir.  
  
 Yalnızca sistem başlatma sırasında oluşan bir sorunu hata ayıklamak istediğiniz zaman gibi bazı durumlarda, Windows hata ayıklayıcı kullanmak zorunda. Yükleme [Windows için hata ayıklama araçları](https://msdn.microsoft.com/windows/hardware/hh852365) görüp [nasıl Windows hizmetlerinde hata ayıklama](https://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Nasıl Yapılır: Hizmetleri Başlatma](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Hizmet hata ayıklama](/windows/desktop/Services/debugging-a-service)

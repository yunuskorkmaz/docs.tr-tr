---
title: 'Nasıl Yapılır: Hizmetleri Başlatma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
manager: douge
ms.openlocfilehash: 3c8382d2e425d11dc8aa8b22e361b3cc5637744f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-start-services"></a>Nasıl Yapılır: Hizmetleri Başlatma
Bir hizmeti yüklendikten sonra başlatılmalıdır. Çağrıları başlangıç <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmet sınıfı üzerinde. Genellikle, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmetin gerçekleştirecek yararlı çalışmaları tanımlar. Bir hizmeti başlatıldıktan sonra el ile duraklatıldı veya durduruluncaya kadar etkin kalır.  
  
 Hizmetleri otomatik olarak veya el ile başlatmak için ayarlanabilir. Yüklü olduğu bilgisayarın yeniden başlatılmasıyla ya da ilk açık olduğunda otomatik olarak başlayan bir hizmeti başlatılır. Bir kullanıcı el ile başlayan bir hizmetin başlatılması gerekir.  
  
> [!NOTE]
>  Varsayılan olarak, Visual Studio ile oluşturulan hizmetleri el ile başlatmak için ayarlanır.  
  
 Bir hizmeti el ile başlatabilirsiniz birkaç yolu vardır: gelen **Sunucu Gezgini**, gelen **Hizmet Denetim Yöneticisi**, veya bir bileşen kullanarak koddan çağrılan <xref:System.ServiceProcess.ServiceController>.  
  
 Ayarladığınız <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özellikte <xref:System.ServiceProcess.ServiceInstaller> bir hizmeti el ile veya otomatik olarak başlatılıp başlatılmayacağını belirlemek için sınıf.  
  
### <a name="to-specify-how-a-service-should-start"></a>Bir hizmetin nasıl başlaması gerektiğini belirtmek için  
  
1.  Hizmetinizi oluşturduktan sonra onun için gerekli yükleyicileri ekleyin. Daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  Tasarımcısı'nda çalıştığınız hizmeti için hizmet Yükleyici'yi tıklatın.  
  
3.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini şunlardan biri:  
  
    |Hizmetinizin yüklemesini sağlamak için|Bu değeri ayarlayın|  
    |----------------------------------|--------------------|  
    |Bilgisayar ne zaman yeniden|**Otomatik**|  
    |Açık bir kullanıcı eylem hizmeti başladığında|**El ile**|  
  
    > [!TIP]
    >  Hiç başlatılan hizmetinizi önlemek için ayarlayabileceğiniz <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğine **devre dışı**. Bir sunucunun yeniden başlatılması birkaç kez geçiyor ve normal şekilde başlamasını başlarsınız Hizmetleri engelleyerek zamandan tasarruf etmek istiyorsanız bunu yapabilirsiniz.  
  
    > [!NOTE]
    >  Hizmetinizi yüklendikten sonra bu ve diğer özellikleri değiştirilebilir.  
  
     Sahip bir hizmeti başlatmak çeşitli yolları vardır, <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> işlem kümesine **el ile** — gelen **Sunucu Gezgini**, gelen **Windows Hizmet Denetimi Yöneticisi**, veya koddan. Gerçekte bağlamında hizmeti bu yöntemler tüm başlatmak dikkate almak önemlidir **Hizmet Denetim Yöneticisi**; **Sunucu Gezgini** ve hizmet başlatma programlama yöntemleri gerçekte denetleyici.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>Server Explorer'dan el ile bir hizmeti başlatmak için  
  
1.  İçinde **Sunucu Gezgini**, zaten listede yoksa istediğiniz sunucuyu ekleyin. Daha fazla bilgi için bkz: nasıl yapılır: erişim ve Sunucu Gezgini veritabanı Gezgini başlatılamıyor.  
  
2.  Genişletme **Hizmetleri** düğümünü ve ardından başlatmak istiyor hizmetini bulun.  
  
3.  Hizmet adını sağ tıklatın ve **Başlat**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>El ile bir hizmeti Hizmet Denetim Yöneticisi'nden başlatmak için  
  
1.  Açık **Hizmet Denetim Yöneticisi** aşağıdakilerden birini yaparak:  
  
    -   Windows XP ve 2000 Professional, sağ **Bilgisayarım** Masaüstü ve ardından **Yönet**. Görüntülenen iletişim kutusunda genişletin **hizmetler ve uygulamalar** düğümü.  
  
         \- veya -  
  
    -   Windows Server 2003 ve Windows 2000 Server'ı tıklatın **Başlat**, işaret **programları**, tıklatın **Yönetimsel Araçlar**ve ardından **Hizmetleri**.  
  
        > [!NOTE]
        >  Windows NT sürüm 4. 0'da, bu iletişim kutusundan açabilirsiniz **Denetim Masası**.  
  
     Listelenen hizmetinizi görmelisiniz **Hizmetleri** penceresinin bölümü.  
  
2.  Listeden hizmetinizi seçin, sağ tıklatın ve ardından **Başlat**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Bir hizmet kodundan el ile başlatmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceProcess.ServiceController> sınıfı ve yönetmek istediğiniz hizmet ile etkileşimde bulunacak şekilde yapılandırın.  
  
2.  Çağrı <xref:System.ServiceProcess.ServiceController.Start%2A> hizmetini başlatmak için yöntem.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Windows Hizmetleri Oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)

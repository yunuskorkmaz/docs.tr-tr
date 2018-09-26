---
title: 'Nasıl Yapılır: Hizmetleri Başlatma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: b3f04deb11a23957198864c444b4872aef45b2e4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176753"
---
# <a name="how-to-start-services"></a>Nasıl Yapılır: Hizmetleri Başlatma
Bir hizmeti yüklendikten sonra başlatılmalıdır. Çağrı <xref:System.ServiceProcess.ServiceBase.OnStart%2A> hizmet sınıfı yöntemi. Genellikle, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> hizmetin gerçekleştirecek faydalı bir iş yöntemi tanımlar. Bir hizmeti başlatıldıktan sonra el ile duraklatıldı veya durduruluncaya kadar etkin kalır.  
  
 Hizmetleri otomatik olarak veya el ile başlatmak için ayarlanabilir. Yüklü olduğu bilgisayarın yeniden başlatılmasıyla ya da önce açık olduğunda otomatik olarak başlatan bir hizmet başlatılır. Bir kullanıcı el ile başlayan bir hizmetin başlatılması gerekir.  
  
> [!NOTE]
>  Varsayılan olarak, Visual Studio ile oluşturulan hizmetleri el ile başlatmak için ayarlanır.  
  
 Bir hizmeti el ile başlatabilir birkaç yolu vardır — dan **Sunucu Gezgini**, gelen **Hizmet Denetim Yöneticisi**, veya koddan bir bileşen kullanma adlı <xref:System.ServiceProcess.ServiceController>.  
  
 Ayarladığınız <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği <xref:System.ServiceProcess.ServiceInstaller> bir hizmeti elle veya otomatik olarak başlatılıp başlatılmayacağını belirlemek için sınıf.  
  
### <a name="to-specify-how-a-service-should-start"></a>Bir hizmetin nasıl başlaması gerektiğini belirtmek için  
  
1.  Hizmetinizi oluşturduktan sonra bunun için gerekli yükleyicileri ekleyin. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanız için yükleyicileri ekleyin](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  Tasarımcısı'nda çalıştığınız hizmeti için hizmet Yükleyici'yi tıklatın.  
  
3.  İçinde **özellikleri** penceresinde <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini aşağıdakilerden biri:  
  
    |Hizmetinizi yüklemek için|Bu değeri ayarlayın|  
    |----------------------------------|--------------------|  
    |Bilgisayarın ne zaman yeniden başlatılır|**Otomatik**|  
    |Bir açık kullanıcı eylemi hizmeti başladığında|**El ile**|  
  
    > [!TIP]
    >  Hizmetinizi hiç çalışmaya önlemek için ayarlayabileceğiniz <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini **devre dışı bırakılmış**. Bir sunucuyu birkaç kez yeniden olacak ve normalde başlatılması başlar Hizmetleri engelleyerek zamandan tasarruf yapmak istiyorsanız bunu yapabilirsiniz.  
  
    > [!NOTE]
    >  Hizmet yüklendikten sonra bu ve diğer özellikleri değiştirilebilir.  
  
     Bir hizmet başlangıç birkaç yolu vardır, <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> işlem kümesine **el ile** — gelen **Sunucu Gezgini**, gelen **Windows Hizmet Denetim Yöneticisi**, veya koddan. Aslında bağlamında hizmeti tüm bu yöntemleri başlatmak dikkat edin önemlidir **Hizmet Denetim Yöneticisi**; **Sunucu Gezgini** ve hizmet başlatma programlı yöntemlerle gerçekten işlemek denetleyici.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>El ile bir hizmeti sunucu Gezgini'nden başlatmak için  
  
1.  İçinde **Sunucu Gezgini**, zaten listede yoksa istediğiniz sunucuya ekleyin. Daha fazla bilgi için bkz: nasıl yapılır: erişim ve Sunucu Gezgini veritabanı Gezgini başlatılamıyor.  
  
2.  Genişletin **Hizmetleri** düğümünü ve ardından başlamak istediğiniz hizmeti bulun.  
  
3.  Hizmet adını sağ tıklayın ve **Başlat**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>El ile bir hizmeti Hizmet Denetim Yöneticisi'nden başlatmak için  
  
1.  Açık **Hizmet Denetim Yöneticisi** aşağıdakilerden birini yaparak:  
  
    -   Windows XP ve 2000 Professional, sağ **Bilgisayarım** Masaüstü ve ardından **Yönet**. Görüntülenen iletişim kutusunda Genişlet **hizmetler ve uygulamalar** düğümü.  
  
         \- veya -  
  
    -   Windows Server 2003 ve Windows 2000 Server **Başlat**, işaret **programlar**, tıklayın **Yönetimsel Araçlar**ve ardından **Hizmetleri**.  
  
        > [!NOTE]
        >  Windows NT sürüm 4. 0'da, bu iletişim kutusundan açabilirsiniz **Denetim Masası**.  
  
     Hizmetiniz listede görmelisiniz **Hizmetleri** pencerenin.  
  
2.  Listeden hizmetinizi seçin, sağ tıklayın ve ardından **Başlat**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Bir hizmeti koddan el ile başlatmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceProcess.ServiceController> sınıfı ve yönetmek istediğiniz hizmetiyle etkileşim kurmak üzere yapılandırın.  
  
2.  Çağrı <xref:System.ServiceProcess.ServiceController.Start%2A> hizmeti başlatmak için yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Windows Hizmetleri Oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)

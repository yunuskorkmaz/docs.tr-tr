---
title: 'Nasıl yapılır: Hizmetleri Başlatma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 5be803e2f4face60318a4c9ed12f1b58edaeace6
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044434"
---
# <a name="how-to-start-services"></a>Nasıl yapılır: Hizmetleri Başlatma

Bir hizmet yüklendikten sonra, başlatılmış olması gerekir. Başlatılıyor <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmet sınıfında çağırır. Genellikle, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmetin gerçekleştireceği faydalı işleri tanımlar. Bir hizmet başladıktan sonra, el ile duraklatıldığı veya durduruluncaya kadar etkin kalır.

Hizmetler, otomatik olarak veya el ile başlayacak şekilde ayarlanabilir. Otomatik olarak başlatılan bir hizmet, yüklendiği bilgisayar yeniden başlatıldığında veya ilk açıldığında başlatılır. Bir kullanıcının el ile başlatılan bir hizmeti başlatması gerekir.

> [!NOTE]
> Varsayılan olarak, Visual Studio ile oluşturulan hizmetler el ile başlayacak şekilde ayarlanmıştır.

**Sunucu Gezgini**, **Hizmetler denetim yöneticisinden**veya ' de adlı bir <xref:System.ServiceProcess.ServiceController>bileşeni kullanarak koddan el ile bir hizmeti başlatabilmeniz için kullanabileceğiniz çeşitli yollar vardır.

Bir hizmetin el <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> ile mi yoksa <xref:System.ServiceProcess.ServiceInstaller> otomatik olarak mı başlatılacağını öğrenmek için sınıfında özelliğini ayarlarsınız.

### <a name="to-specify-how-a-service-should-start"></a>Bir hizmetin nasıl başlaması gerektiğini belirtmek için

1. Hizmetinizi oluşturduktan sonra, için gerekli yükleyicileri ekleyin. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanıza](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)yükleyicileri ekleyin.

2. Tasarımcıda çalıştığınız hizmetin hizmet yükleyicisine tıklayın.

3. **Özellikler** penceresinde, <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği aşağıdakilerden biri olarak ayarlayın:

    |Hizmetinizin yüklenmesini sağlamak için|Bu değeri ayarla|
    |----------------------------------|--------------------|
    |Bilgisayar yeniden başlatıldığında|**Otomatik**|
    |Açık Kullanıcı eylemi hizmeti başlattığında|**El ile**|

    > [!TIP]
    > Hizmetinizin hiç başlatılmasını engellemek için <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği **devre dışı**olarak ayarlayabilirsiniz. Bir sunucuyu birkaç kez yeniden başlatacaksanız ve normalde başlamadan başlayan Hizmetleri kaldırarak zamandan tasarruf etmek istiyorsanız bunu yapabilirsiniz.

    > [!NOTE]
    > Bu ve diğer özellikler, hizmetiniz yüklendikten sonra değiştirilebilir.

    **Sunucu Gezgini**, **Windows Hizmetleri denetim yöneticisinden**veya koddan **el ile** olarak ayarlanmış <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> bir hizmeti başlamanın birkaç yolu vardır. Bu yöntemlerin tümünün hizmeti hizmet **Denetimi Yöneticisi**bağlamında başlatmadığını unutmayın; **Sunucu Gezgini** ve hizmetin başlatılmasına yönelik programlama yöntemleri, denetleyiciyi gerçekten işleyebilir.

### <a name="to-manually-start-a-service-from-server-explorer"></a>Sunucu Gezgini bir hizmeti el ile başlatmak için

1. **Sunucu Gezgini**, zaten listede yoksa istediğiniz sunucuyu ekleyin. Daha fazla bilgi için bkz. nasıl yapılır: Sunucu Gezgini Veritabanı Gezgini erişin ve başlatın.

2. **Hizmetler** düğümünü genişletin ve ardından başlatmak istediğiniz hizmeti bulun.

3. Hizmetin adına sağ tıklayın ve **Başlat**' a tıklayın.

### <a name="to-manually-start-a-service-from-services-control-manager"></a>Hizmet Denetim yöneticisinden bir hizmeti el ile başlatmak için

1. Aşağıdakilerden birini yaparak **Hizmetler denetim yöneticisini** açın:

    - Windows XP ve 2000 Professional 'da, masaüstünde Bilgisayarım ' a sağ tıklayın ve ardından **Yönet**' e tıklayın. Görüntülenen iletişim kutusunda, **Hizmetler ve uygulamalar** düğümünü genişletin.

      \- veya -

    - Windows Server 2003 ve Windows 2000 sunucusunda **Başlat**' a tıklayın, **Programlar**' ın üzerine gelin, **Yönetimsel Araçlar**' a ve ardından **Hizmetler**' e tıklayın.

      > [!NOTE]
      > Windows NT sürüm 4,0 ' de bu iletişim kutusunu **Denetim Masası**'ndan açabilirsiniz.

    Şimdi, pencerenin **Hizmetler** bölümünde hizmetinizi görmeniz gerekir.

2. Listeden hizmetinizi seçin, sağ tıklayın ve ardından **Başlat**' a tıklayın.

### <a name="to-manually-start-a-service-from-code"></a>Koddan bir hizmeti el ile başlatmak için

1. <xref:System.ServiceProcess.ServiceController> Sınıfının bir örneğini oluşturun ve yönetmek istediğiniz hizmetle etkileşimde bulunmak üzere yapılandırın.

2. Hizmeti başlatmak için yöntemini çağırın. <xref:System.ServiceProcess.ServiceController.Start%2A>

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Nasıl yapılır: Hizmet uygulamanıza yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)

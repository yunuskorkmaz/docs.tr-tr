---
title: 'Nasıl yapılır: Hizmetleri Başlatma'
description: Hizmetleri başlatmak için çeşitli yollar edinin. Bir hizmet yüklendikten sonra, başlatılmış olması gerekir. Başlatılıyor, hizmet sınıfında OnStart yöntemini çağırır.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 4a2f9b291e60b12b1465fbb6bbbd1604572359a7
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925728"
---
# <a name="how-to-start-services"></a>Nasıl yapılır: Hizmetleri Başlatma

Bir hizmet yüklendikten sonra, başlatılmış olması gerekir. Başlatılıyor <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmet sınıfında çağırır. Genellikle, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmetin gerçekleştireceği faydalı işleri tanımlar. Bir hizmet başladıktan sonra, el ile duraklatıldığı veya durduruluncaya kadar etkin kalır.

Hizmetler, otomatik olarak veya el ile başlayacak şekilde ayarlanabilir. Otomatik olarak başlatılan bir hizmet, yüklendiği bilgisayar yeniden başlatıldığında veya ilk açıldığında başlatılır. Bir kullanıcının el ile başlatılan bir hizmeti başlatması gerekir.

> [!NOTE]
> Varsayılan olarak, Visual Studio ile oluşturulan hizmetler el ile başlayacak şekilde ayarlanmıştır.

**Sunucu Gezgini**, **Hizmetler denetim yöneticisinden**veya ' de adlı bir bileşeni kullanarak koddan el ile bir hizmeti başlatabilmeniz için kullanabileceğiniz çeşitli yollar vardır <xref:System.ServiceProcess.ServiceController> .

<xref:System.ServiceProcess.ServiceInstaller.StartType%2A> <xref:System.ServiceProcess.ServiceInstaller> Bir hizmetin el ile mi yoksa otomatik olarak mı başlatılacağını öğrenmek için sınıfında özelliğini ayarlarsınız.

### <a name="to-specify-how-a-service-should-start"></a>Bir hizmetin nasıl başlaması gerektiğini belirtmek için

1. Hizmetinizi oluşturduktan sonra, için gerekli yükleyicileri ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).

2. Tasarımcıda çalıştığınız hizmetin hizmet yükleyicisine tıklayın.

3. **Özellikler** penceresinde, <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği aşağıdakilerden biri olarak ayarlayın:

    |Hizmetinizin yüklenmesini sağlamak için|Bu değeri ayarla|
    |----------------------------------|--------------------|
    |Bilgisayar yeniden başlatıldığında|**Automatic**|
    |Açık Kullanıcı eylemi hizmeti başlattığında|**El ile**|

    > [!TIP]
    > Hizmetinizin hiç başlatılmasını engellemek için <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği **devre dışı**olarak ayarlayabilirsiniz. Bir sunucuyu birkaç kez yeniden başlatacaksanız ve normalde başlamadan başlayan Hizmetleri kaldırarak zamandan tasarruf etmek istiyorsanız bunu yapabilirsiniz.

    > [!NOTE]
    > Bu ve diğer özellikler, hizmetiniz yüklendikten sonra değiştirilebilir.

    <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> **Sunucu Gezgini**, **Windows Hizmetleri denetim yöneticisinden**veya koddan **el ile** olarak ayarlanmış bir hizmeti başlamanın birkaç yolu vardır. Bu yöntemlerin tümünün hizmeti hizmet **Denetimi Yöneticisi**bağlamında başlatmadığını unutmayın; **Sunucu Gezgini** ve hizmetin başlatılmasına yönelik programlama yöntemleri, denetleyiciyi gerçekten işleyebilir.

### <a name="to-manually-start-a-service-from-server-explorer"></a>Sunucu Gezgini bir hizmeti el ile başlatmak için

1. **Sunucu Gezgini**, zaten listede yoksa istediğiniz sunucuyu ekleyin. Daha fazla bilgi için bkz. nasıl yapılır: erişim ve başlatma Sunucu Gezgini-Veritabanı Gezgini.

2. **Hizmetler** düğümünü genişletin ve ardından başlatmak istediğiniz hizmeti bulun.

3. Hizmetin adına sağ tıklayın ve **Başlat**' a tıklayın.

### <a name="to-manually-start-a-service-from-services-control-manager"></a>Hizmet Denetim yöneticisinden bir hizmeti el ile başlatmak için

1. Aşağıdakilerden birini yaparak **Hizmetler denetim yöneticisini** açın:

    - Windows XP ve 2000 Professional 'da, **masaüstünde Bilgisayarım ' a sağ tıklayın ve** ardından **Yönet**' e tıklayın. Görüntülenen iletişim kutusunda, **Hizmetler ve uygulamalar** düğümünü genişletin.

      \-veya

    - Windows Server 2003 ve Windows 2000 sunucusunda **Başlat**' a tıklayın, **Programlar**' ın üzerine gelin, **Yönetimsel Araçlar**' a ve ardından **Hizmetler**' e tıklayın.

      > [!NOTE]
      > Windows NT sürüm 4,0 ' de bu iletişim kutusunu **Denetim Masası**'ndan açabilirsiniz.

    Şimdi, pencerenin **Hizmetler** bölümünde hizmetinizi görmeniz gerekir.

2. Listeden hizmetinizi seçin, sağ tıklayın ve ardından **Başlat**' a tıklayın.

### <a name="to-manually-start-a-service-from-code"></a>Koddan bir hizmeti el ile başlatmak için

1. Sınıfının bir örneğini oluşturun <xref:System.ServiceProcess.ServiceController> ve yönetmek istediğiniz hizmetle etkileşimde bulunmak üzere yapılandırın.

2. <xref:System.ServiceProcess.ServiceController.Start%2A>Hizmeti başlatmak için yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmet Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri Oluşturma](how-to-create-windows-services.md)
- [Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](how-to-add-installers-to-your-service-application.md)

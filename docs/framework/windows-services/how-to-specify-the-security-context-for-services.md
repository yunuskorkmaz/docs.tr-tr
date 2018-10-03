---
title: 'Nasıl Yapılır: Hizmetler için Güvenlik İçeriği Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
ms.openlocfilehash: a5a437af90f29bc601215176ad5c4fec702ddbc0
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036084"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Nasıl Yapılır: Hizmetler için Güvenlik İçeriği Belirtme
Varsayılan olarak, hizmetler, oturum açan kullanıcının farklı güvenlik bağlamında çalışır. Varsayılan sistem hesabına ait içerikte çalıştırmasına Hizmetleri olarak adlandırılır `LocalSystem`, sağlayan farklı erişim ayrıcalığı kullanıcı dışındaki sistem kaynaklarına. Hizmetinizin altında çalıştırılması farklı bir kullanıcı hesabı belirtmek için bu davranışı değiştirebilirsiniz.  
  
 İşleyerek güvenlik bağlamını ayarlayın <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> hizmet içinde çalıştığı işlemin özelliği. Bu özellik hizmet dört hesap türünden biri olarak ayarlamanıza olanak sağlar:  
  
-   `User`, hizmet yüklendiğinde ve ağdaki; tek bir kullanıcı tarafından belirtilen bir hesabı bağlamında çalışır bir geçerli kullanıcı adı ve parolanın sorulduğu sisteme neden olur  
  
-   `LocalService`, yerel bilgisayarda ayrıcalıklı olmayan kullanıcı olarak görev yapar ve bir uzak sunucuya anonim kimlik bilgileri sunan bir hesabı bağlamında çalışır  
  
-   `LocalSystem`, kapsamlı Yerel ayrıcalıklar sağlar ve herhangi bir uzak sunucuya; bilgisayarın kimlik bilgileri sunan bir hesabı bağlamında çalışır  
  
-   `NetworkService`, yerel bilgisayarda ayrıcalıklı olmayan kullanıcı olarak davranan ve herhangi bir uzak sunucuya bilgisayarın kimlik bilgileri sunan bir hesabı bağlamında çalışır.  
  
 Daha fazla bilgi için <xref:System.ServiceProcess.ServiceAccount> sabit listesi.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Bir hizmet için güvenlik bağlamı belirtmek için  
  
1.  Hizmetinizi oluşturduktan sonra bunun için gerekli yükleyicileri ekleyin. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanız için yükleyicileri ekleyin](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  Tasarımcıda erişim `ProjectInstaller` sınıfı ve birlikte çalıştığınız hizmeti için hizmet işlemi Yükleyici'yi tıklatın.  
  
    > [!NOTE]
    >  Her hizmet uygulaması için en az iki yükleme bileşenleri vardır `ProjectInstaller` sınıfı — bir proje ve uygulamayı içeren her bir hizmet için bir yükleyici tüm hizmetler için işlemleri yükler. Bu örnekte, seçmek istediğiniz <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3.  İçinde **özellikleri** penceresinde <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> uygun değere.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Nasıl Yapılır: Windows Hizmetleri Oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)

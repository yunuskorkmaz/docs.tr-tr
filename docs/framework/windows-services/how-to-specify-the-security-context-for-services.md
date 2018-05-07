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
manager: douge
ms.openlocfilehash: e3e5ad7dd44dcaf1593ac80bbe6d0a367964e4e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-security-context-for-services"></a>Nasıl Yapılır: Hizmetler için Güvenlik İçeriği Belirtme
Varsayılan olarak, hizmetler, oturum açan kullanıcının daha farklı güvenlik bağlamında çalışır. Varsayılan sistem hesabı bağlamında çalıştırmanız Hizmetleri olarak adlandırılır `LocalSystem`, sağlayan farklı erişim ayrıcalıkları kullanıcı dışındaki sistem kaynaklarına. Hizmetinizin altında çalışması gerektiğini farklı bir kullanıcı hesabı belirtmek için bu davranışı değiştirebilirsiniz.  
  
 İşleyerek güvenlik bağlamını ayarlayın <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> hizmet içinde çalıştığı işlem özelliği. Bu özellik hizmeti dört hesap türünden birine ayarlamanıza olanak sağlar:  
  
-   `User`, hizmet yüklendiğinde ve ağdaki; tek bir kullanıcı tarafından belirtilen bir hesabı bağlamında çalışır bir geçerli bir kullanıcı adı ve parola istemek sistem neden olur  
  
-   `LocalService`, yerel bilgisayarda ayrıcalıklı olmayan kullanıcı görevi görür ve herhangi bir uzak sunucuya; anonim kimlik bilgileri sunan bir hesabı bağlamında çalışır  
  
-   `LocalSystem`, kapsamlı Yerel ayrıcalıklar sağlar ve herhangi bir uzak sunucuya; bilgisayarın kimlik bilgilerini sunan bir hesabı bağlamında çalışır  
  
-   `NetworkService`, yerel bilgisayarda ayrıcalıklı olmayan kullanıcı görevi görür ve herhangi bir uzak sunucuya bilgisayarın kimlik bilgilerini sunan bir hesabı bağlamında çalışır.  
  
 Daha fazla bilgi için bkz: <xref:System.ServiceProcess.ServiceAccount> numaralandırması.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Bir hizmet için güvenlik bağlamı belirtmek için  
  
1.  Hizmetinizi oluşturduktan sonra onun için gerekli yükleyicileri ekleyin. Daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  Tasarımcıda erişim `ProjectInstaller` sınıfı ve çalıştığınız hizmetin hizmet işlemi yükleyicisini tıklatın.  
  
    > [!NOTE]
    >  Her hizmet uygulaması için en az iki yükleme bileşenlerinde vardır `ProjectInstaller` sınıfı — bir projeyi ve uygulamayı içeren her bir hizmet için bir yükleyici tüm hizmetler için işlemleri yükler. Bu örnekte, seçmek istediğiniz <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> uygun değere.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Nasıl Yapılır: Windows Hizmetleri Oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)

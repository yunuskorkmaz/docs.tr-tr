---
title: 'Nasıl yapılır: Hizmetler için Güvenlik İçeriği Belirtme'
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
ms.openlocfilehash: 88dc9c40a2b8ff0ac9bba26c991ba2a4ac2dcb43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952431"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Nasıl yapılır: Hizmetler için Güvenlik İçeriği Belirtme
Varsayılan olarak, hizmetler, oturum açmış kullanıcının farklı bir güvenlik bağlamında çalışır. Hizmetler, olarak adlandırılan `LocalSystem`varsayılan sistem hesabı bağlamında çalışır ve bu da kullanıcılara göre sistem kaynaklarına farklı erişim ayrıcalıkları verir. Bu davranışı, hizmetinizin çalışması gereken farklı bir kullanıcı hesabı belirtmek için değiştirebilirsiniz.  
  
 Hizmetin çalıştırıldığı işlemin <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> özelliğini düzenleyerek güvenlik bağlamını ayarlarsınız. Bu özellik, hizmeti dört hesap türünden birine ayarlamanıza olanak tanır:  
  
- `User`Bu, sistemin hizmet yüklendiği ve ağdaki tek bir kullanıcı tarafından belirtilen bir hesap bağlamında çalıştırıldığı sırada geçerli bir Kullanıcı adı ve parola sormasını sağlar;  
  
- `LocalService`, yerel bilgisayarda ayrıcalıklı olmayan bir kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgileri sunan bir hesap bağlamında çalışır;  
  
- `LocalSystem`, kapsamlı yerel ayrıcalıklar sağlayan bir hesap bağlamında çalışır ve bilgisayarın kimlik bilgilerini herhangi bir uzak sunucuya sunar;  
  
- `NetworkService`, yerel bilgisayarda ayrıcalıklı olmayan bir kullanıcı olarak davranan bir hesap bağlamında çalışır ve bilgisayarın kimlik bilgilerini herhangi bir uzak sunucuya gösterir.  
  
 Daha fazla bilgi için bkz <xref:System.ServiceProcess.ServiceAccount> . sabit listesi.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Bir hizmetin güvenlik bağlamını belirtmek için  
  
1. Hizmetinizi oluşturduktan sonra, için gerekli yükleyicileri ekleyin. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanıza](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)yükleyicileri ekleyin.  
  
2. Tasarımcıda `ProjectInstaller` sınıfına erişin ve çalıştığınız hizmet için hizmet işlem yükleyicisinden tıklayın.  
  
    > [!NOTE]
    > Her hizmet uygulaması için, `ProjectInstaller` sınıfında en az iki yükleme bileşeni vardır: Bu, projedeki tüm hizmetler için işlem yükleyen ve uygulamanın içerdiği her hizmet için bir yükleyiciden biridir. Bu örnekte, öğesini seçmek <xref:System.ServiceProcess.ServiceProcessInstaller>istiyorsunuz.  
  
3. **Özellikler** penceresinde, <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> öğesini uygun değere ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Hizmet uygulamanıza yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)

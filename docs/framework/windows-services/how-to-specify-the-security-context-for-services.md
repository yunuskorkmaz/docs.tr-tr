---
title: 'Nasıl yapılır: Hizmetler için Güvenlik İçeriği Belirtme'
description: Hizmetler için güvenlik bağlamını belirtin. Varsayılan sistem hesabı bağlamında çalıştırılan hizmetler, oturum açan kullanıcıdan farklı sistem kaynağı erişim haklarına sahiptir.
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
ms.openlocfilehash: 06053ee069777f69eea15a7ec3125b510bb34602
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608432"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Nasıl yapılır: Hizmetler için Güvenlik İçeriği Belirtme
Varsayılan olarak, hizmetler, oturum açmış kullanıcının farklı bir güvenlik bağlamında çalışır. Hizmetler, olarak adlandırılan varsayılan sistem hesabı bağlamında çalışır ve bu da `LocalSystem` kullanıcılara göre sistem kaynaklarına farklı erişim ayrıcalıkları verir. Bu davranışı, hizmetinizin çalışması gereken farklı bir kullanıcı hesabı belirtmek için değiştirebilirsiniz.  
  
 Hizmetin çalıştırıldığı işlemin özelliğini düzenleyerek güvenlik bağlamını ayarlarsınız <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> . Bu özellik, hizmeti dört hesap türünden birine ayarlamanıza olanak tanır:  
  
- `User`Bu, sistemin hizmet yüklendiği ve ağdaki tek bir kullanıcı tarafından belirtilen bir hesap bağlamında çalıştırıldığı sırada geçerli bir Kullanıcı adı ve parola sormasını sağlar;  
  
- `LocalService`, yerel bilgisayarda ayrıcalıklı olmayan bir kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgileri sunan bir hesap bağlamında çalışır;  
  
- `LocalSystem`, kapsamlı yerel ayrıcalıklar sağlayan bir hesap bağlamında çalışır ve bilgisayarın kimlik bilgilerini herhangi bir uzak sunucuya sunar;  
  
- `NetworkService`, yerel bilgisayarda ayrıcalıklı olmayan bir kullanıcı olarak davranan bir hesap bağlamında çalışır ve bilgisayarın kimlik bilgilerini herhangi bir uzak sunucuya gösterir.  
  
 Daha fazla bilgi için bkz <xref:System.ServiceProcess.ServiceAccount> . sabit listesi.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Bir hizmetin güvenlik bağlamını belirtmek için  
  
1. Hizmetinizi oluşturduktan sonra, için gerekli yükleyicileri ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).  
  
2. Tasarımcıda `ProjectInstaller` sınıfına erişin ve çalıştığınız hizmet için hizmet işlem yükleyicisinden tıklayın.  
  
    > [!NOTE]
    > Her hizmet uygulaması için, sınıfında en az iki yükleme bileşeni vardır: `ProjectInstaller` Bu, projedeki tüm hizmetler için işlem yükleyen ve uygulamanın içerdiği her hizmet için bir yükleyiciden biridir. Bu örnekte, öğesini seçmek istiyorsunuz <xref:System.ServiceProcess.ServiceProcessInstaller> .  
  
3. **Özellikler** penceresinde, öğesini <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> uygun değere ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmet Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](how-to-add-installers-to-your-service-application.md)
- [Nasıl yapılır: Windows Hizmetleri Oluşturma](how-to-create-windows-services.md)

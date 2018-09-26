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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073729"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="dbb44-102">Nasıl Yapılır: Hizmetler için Güvenlik İçeriği Belirtme</span><span class="sxs-lookup"><span data-stu-id="dbb44-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="dbb44-103">Varsayılan olarak, hizmetler, oturum açan kullanıcının farklı güvenlik bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="dbb44-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="dbb44-104">Varsayılan sistem hesabına ait içerikte çalıştırmasına Hizmetleri olarak adlandırılır `LocalSystem`, sağlayan farklı erişim ayrıcalığı kullanıcı dışındaki sistem kaynaklarına.</span><span class="sxs-lookup"><span data-stu-id="dbb44-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="dbb44-105">Hizmetinizin altında çalıştırılması farklı bir kullanıcı hesabı belirtmek için bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbb44-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="dbb44-106">İşleyerek güvenlik bağlamını ayarlayın <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> hizmet içinde çalıştığı işlemin özelliği.</span><span class="sxs-lookup"><span data-stu-id="dbb44-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="dbb44-107">Bu özellik hizmet dört hesap türünden biri olarak ayarlamanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="dbb44-107">This property allows you to set the service to one of four account types:</span></span>  
  
-   <span data-ttu-id="dbb44-108">`User`, hizmet yüklendiğinde ve ağdaki; tek bir kullanıcı tarafından belirtilen bir hesabı bağlamında çalışır bir geçerli kullanıcı adı ve parolanın sorulduğu sisteme neden olur</span><span class="sxs-lookup"><span data-stu-id="dbb44-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
-   <span data-ttu-id="dbb44-109">`LocalService`, yerel bilgisayarda ayrıcalıklı olmayan kullanıcı olarak görev yapar ve bir uzak sunucuya anonim kimlik bilgileri sunan bir hesabı bağlamında çalışır</span><span class="sxs-lookup"><span data-stu-id="dbb44-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="dbb44-110">`LocalSystem`, kapsamlı Yerel ayrıcalıklar sağlar ve herhangi bir uzak sunucuya; bilgisayarın kimlik bilgileri sunan bir hesabı bağlamında çalışır</span><span class="sxs-lookup"><span data-stu-id="dbb44-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="dbb44-111">`NetworkService`, yerel bilgisayarda ayrıcalıklı olmayan kullanıcı olarak davranan ve herhangi bir uzak sunucuya bilgisayarın kimlik bilgileri sunan bir hesabı bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="dbb44-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="dbb44-112">Daha fazla bilgi için <xref:System.ServiceProcess.ServiceAccount> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="dbb44-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="dbb44-113">Bir hizmet için güvenlik bağlamı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="dbb44-113">To specify the security context for a service</span></span>  
  
1.  <span data-ttu-id="dbb44-114">Hizmetinizi oluşturduktan sonra bunun için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dbb44-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="dbb44-115">Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanız için yükleyicileri ekleyin](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="dbb44-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="dbb44-116">Tasarımcıda erişim `ProjectInstaller` sınıfı ve birlikte çalıştığınız hizmeti için hizmet işlemi Yükleyici'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="dbb44-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dbb44-117">Her hizmet uygulaması için en az iki yükleme bileşenleri vardır `ProjectInstaller` sınıfı — bir proje ve uygulamayı içeren her bir hizmet için bir yükleyici tüm hizmetler için işlemleri yükler.</span><span class="sxs-lookup"><span data-stu-id="dbb44-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="dbb44-118">Bu örnekte, seçmek istediğiniz <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="dbb44-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3.  <span data-ttu-id="dbb44-119">İçinde **özellikleri** penceresinde <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> uygun değere.</span><span class="sxs-lookup"><span data-stu-id="dbb44-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb44-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbb44-120">See Also</span></span>  
 [<span data-ttu-id="dbb44-121">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="dbb44-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="dbb44-122">Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="dbb44-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="dbb44-123">Nasıl Yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dbb44-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

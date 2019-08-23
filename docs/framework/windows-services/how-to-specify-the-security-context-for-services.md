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
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="24290-102">Nasıl yapılır: Hizmetler için Güvenlik İçeriği Belirtme</span><span class="sxs-lookup"><span data-stu-id="24290-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="24290-103">Varsayılan olarak, hizmetler, oturum açmış kullanıcının farklı bir güvenlik bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="24290-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="24290-104">Hizmetler, olarak adlandırılan `LocalSystem`varsayılan sistem hesabı bağlamında çalışır ve bu da kullanıcılara göre sistem kaynaklarına farklı erişim ayrıcalıkları verir.</span><span class="sxs-lookup"><span data-stu-id="24290-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="24290-105">Bu davranışı, hizmetinizin çalışması gereken farklı bir kullanıcı hesabı belirtmek için değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24290-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="24290-106">Hizmetin çalıştırıldığı işlemin <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> özelliğini düzenleyerek güvenlik bağlamını ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="24290-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="24290-107">Bu özellik, hizmeti dört hesap türünden birine ayarlamanıza olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="24290-107">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="24290-108">`User`Bu, sistemin hizmet yüklendiği ve ağdaki tek bir kullanıcı tarafından belirtilen bir hesap bağlamında çalıştırıldığı sırada geçerli bir Kullanıcı adı ve parola sormasını sağlar;</span><span class="sxs-lookup"><span data-stu-id="24290-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="24290-109">`LocalService`, yerel bilgisayarda ayrıcalıklı olmayan bir kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgileri sunan bir hesap bağlamında çalışır;</span><span class="sxs-lookup"><span data-stu-id="24290-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="24290-110">`LocalSystem`, kapsamlı yerel ayrıcalıklar sağlayan bir hesap bağlamında çalışır ve bilgisayarın kimlik bilgilerini herhangi bir uzak sunucuya sunar;</span><span class="sxs-lookup"><span data-stu-id="24290-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="24290-111">`NetworkService`, yerel bilgisayarda ayrıcalıklı olmayan bir kullanıcı olarak davranan bir hesap bağlamında çalışır ve bilgisayarın kimlik bilgilerini herhangi bir uzak sunucuya gösterir.</span><span class="sxs-lookup"><span data-stu-id="24290-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="24290-112">Daha fazla bilgi için bkz <xref:System.ServiceProcess.ServiceAccount> . sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="24290-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="24290-113">Bir hizmetin güvenlik bağlamını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="24290-113">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="24290-114">Hizmetinizi oluşturduktan sonra, için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24290-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="24290-115">Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanıza](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24290-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="24290-116">Tasarımcıda `ProjectInstaller` sınıfına erişin ve çalıştığınız hizmet için hizmet işlem yükleyicisinden tıklayın.</span><span class="sxs-lookup"><span data-stu-id="24290-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="24290-117">Her hizmet uygulaması için, `ProjectInstaller` sınıfında en az iki yükleme bileşeni vardır: Bu, projedeki tüm hizmetler için işlem yükleyen ve uygulamanın içerdiği her hizmet için bir yükleyiciden biridir.</span><span class="sxs-lookup"><span data-stu-id="24290-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="24290-118">Bu örnekte, öğesini seçmek <xref:System.ServiceProcess.ServiceProcessInstaller>istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="24290-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="24290-119">**Özellikler** penceresinde, <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> öğesini uygun değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="24290-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24290-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24290-120">See also</span></span>

- [<span data-ttu-id="24290-121">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="24290-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="24290-122">Nasıl yapılır: Hizmet uygulamanıza yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="24290-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="24290-123">Nasıl yapılır: Windows Hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="24290-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

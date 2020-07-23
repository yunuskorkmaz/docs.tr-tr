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
author: ghogen
ms.openlocfilehash: 4ed531cb520a781fd38f8bf5491da6948901a1d5
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925741"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="83a6d-104">Nasıl yapılır: Hizmetler için Güvenlik İçeriği Belirtme</span><span class="sxs-lookup"><span data-stu-id="83a6d-104">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="83a6d-105">Varsayılan olarak, hizmetler, oturum açmış kullanıcının farklı bir güvenlik bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="83a6d-105">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="83a6d-106">Hizmetler, olarak adlandırılan varsayılan sistem hesabı bağlamında çalışır ve bu da `LocalSystem` kullanıcılara göre sistem kaynaklarına farklı erişim ayrıcalıkları verir.</span><span class="sxs-lookup"><span data-stu-id="83a6d-106">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="83a6d-107">Bu davranışı, hizmetinizin çalışması gereken farklı bir kullanıcı hesabı belirtmek için değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83a6d-107">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="83a6d-108">Hizmetin çalıştırıldığı işlemin özelliğini düzenleyerek güvenlik bağlamını ayarlarsınız <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> .</span><span class="sxs-lookup"><span data-stu-id="83a6d-108">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="83a6d-109">Bu özellik, hizmeti dört hesap türünden birine ayarlamanıza olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="83a6d-109">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="83a6d-110">`User`Bu, sistemin hizmet yüklendiği ve ağdaki tek bir kullanıcı tarafından belirtilen bir hesap bağlamında çalıştırıldığı sırada geçerli bir Kullanıcı adı ve parola sormasını sağlar;</span><span class="sxs-lookup"><span data-stu-id="83a6d-110">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="83a6d-111">`LocalService`, yerel bilgisayarda ayrıcalıklı olmayan bir kullanıcı olarak davranan ve herhangi bir uzak sunucuya anonim kimlik bilgileri sunan bir hesap bağlamında çalışır;</span><span class="sxs-lookup"><span data-stu-id="83a6d-111">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="83a6d-112">`LocalSystem`, kapsamlı yerel ayrıcalıklar sağlayan bir hesap bağlamında çalışır ve bilgisayarın kimlik bilgilerini herhangi bir uzak sunucuya sunar;</span><span class="sxs-lookup"><span data-stu-id="83a6d-112">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="83a6d-113">`NetworkService`, yerel bilgisayarda ayrıcalıklı olmayan bir kullanıcı olarak davranan bir hesap bağlamında çalışır ve bilgisayarın kimlik bilgilerini herhangi bir uzak sunucuya gösterir.</span><span class="sxs-lookup"><span data-stu-id="83a6d-113">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="83a6d-114">Daha fazla bilgi için bkz <xref:System.ServiceProcess.ServiceAccount> . sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="83a6d-114">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="83a6d-115">Bir hizmetin güvenlik bağlamını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="83a6d-115">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="83a6d-116">Hizmetinizi oluşturduktan sonra, için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="83a6d-116">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="83a6d-117">Daha fazla bilgi için bkz. [nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="83a6d-117">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="83a6d-118">Tasarımcıda `ProjectInstaller` sınıfına erişin ve çalıştığınız hizmet için hizmet işlem yükleyicisinden tıklayın.</span><span class="sxs-lookup"><span data-stu-id="83a6d-118">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="83a6d-119">Her hizmet uygulaması için, sınıfında en az iki yükleme bileşeni vardır: `ProjectInstaller` Bu, projedeki tüm hizmetler için işlem yükleyen ve uygulamanın içerdiği her hizmet için bir yükleyiciden biridir.</span><span class="sxs-lookup"><span data-stu-id="83a6d-119">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="83a6d-120">Bu örnekte, öğesini seçmek istiyorsunuz <xref:System.ServiceProcess.ServiceProcessInstaller> .</span><span class="sxs-lookup"><span data-stu-id="83a6d-120">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="83a6d-121">**Özellikler** penceresinde, öğesini <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> uygun değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="83a6d-121">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a6d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83a6d-122">See also</span></span>

- [<span data-ttu-id="83a6d-123">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="83a6d-123">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="83a6d-124">Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="83a6d-124">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="83a6d-125">Nasıl yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="83a6d-125">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

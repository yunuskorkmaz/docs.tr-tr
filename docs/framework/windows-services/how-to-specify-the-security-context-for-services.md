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
ms.locfileid: "33512482"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="725a3-102">Nasıl Yapılır: Hizmetler için Güvenlik İçeriği Belirtme</span><span class="sxs-lookup"><span data-stu-id="725a3-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="725a3-103">Varsayılan olarak, hizmetler, oturum açan kullanıcının daha farklı güvenlik bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="725a3-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="725a3-104">Varsayılan sistem hesabı bağlamında çalıştırmanız Hizmetleri olarak adlandırılır `LocalSystem`, sağlayan farklı erişim ayrıcalıkları kullanıcı dışındaki sistem kaynaklarına.</span><span class="sxs-lookup"><span data-stu-id="725a3-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="725a3-105">Hizmetinizin altında çalışması gerektiğini farklı bir kullanıcı hesabı belirtmek için bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="725a3-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="725a3-106">İşleyerek güvenlik bağlamını ayarlayın <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> hizmet içinde çalıştığı işlem özelliği.</span><span class="sxs-lookup"><span data-stu-id="725a3-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="725a3-107">Bu özellik hizmeti dört hesap türünden birine ayarlamanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="725a3-107">This property allows you to set the service to one of four account types:</span></span>  
  
-   <span data-ttu-id="725a3-108">`User`, hizmet yüklendiğinde ve ağdaki; tek bir kullanıcı tarafından belirtilen bir hesabı bağlamında çalışır bir geçerli bir kullanıcı adı ve parola istemek sistem neden olur</span><span class="sxs-lookup"><span data-stu-id="725a3-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
-   <span data-ttu-id="725a3-109">`LocalService`, yerel bilgisayarda ayrıcalıklı olmayan kullanıcı görevi görür ve herhangi bir uzak sunucuya; anonim kimlik bilgileri sunan bir hesabı bağlamında çalışır</span><span class="sxs-lookup"><span data-stu-id="725a3-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="725a3-110">`LocalSystem`, kapsamlı Yerel ayrıcalıklar sağlar ve herhangi bir uzak sunucuya; bilgisayarın kimlik bilgilerini sunan bir hesabı bağlamında çalışır</span><span class="sxs-lookup"><span data-stu-id="725a3-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="725a3-111">`NetworkService`, yerel bilgisayarda ayrıcalıklı olmayan kullanıcı görevi görür ve herhangi bir uzak sunucuya bilgisayarın kimlik bilgilerini sunan bir hesabı bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="725a3-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="725a3-112">Daha fazla bilgi için bkz: <xref:System.ServiceProcess.ServiceAccount> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="725a3-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="725a3-113">Bir hizmet için güvenlik bağlamı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="725a3-113">To specify the security context for a service</span></span>  
  
1.  <span data-ttu-id="725a3-114">Hizmetinizi oluşturduktan sonra onun için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="725a3-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="725a3-115">Daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="725a3-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="725a3-116">Tasarımcıda erişim `ProjectInstaller` sınıfı ve çalıştığınız hizmetin hizmet işlemi yükleyicisini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="725a3-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="725a3-117">Her hizmet uygulaması için en az iki yükleme bileşenlerinde vardır `ProjectInstaller` sınıfı — bir projeyi ve uygulamayı içeren her bir hizmet için bir yükleyici tüm hizmetler için işlemleri yükler.</span><span class="sxs-lookup"><span data-stu-id="725a3-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="725a3-118">Bu örnekte, seçmek istediğiniz <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="725a3-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3.  <span data-ttu-id="725a3-119">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> uygun değere.</span><span class="sxs-lookup"><span data-stu-id="725a3-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725a3-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="725a3-120">See Also</span></span>  
 [<span data-ttu-id="725a3-121">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="725a3-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="725a3-122">Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="725a3-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="725a3-123">Nasıl Yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="725a3-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

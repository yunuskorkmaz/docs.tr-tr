---
title: 'Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 096a3dd1ae5035f6b015ec88ccd8f1ada1dc55ea
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-impersonate-a-client-on-a-service"></a><span data-ttu-id="8432c-102">Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme</span><span class="sxs-lookup"><span data-stu-id="8432c-102">How to: Impersonate a Client on a Service</span></span>
<span data-ttu-id="8432c-103">Üzerinde bir istemci kimliğine bürünme bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmeti, istemci adına eylemleri gerçekleştirmek hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="8432c-103">Impersonating a client on a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service enables the service to perform actions on behalf of the client.</span></span> <span data-ttu-id="8432c-104">Eylemler tabi erişim denetim listesi (ACL), dizinleri ve dosyaları bir makinede erişim veya bir SQL Server veritabanına erişimi gibi ACL onay istemci kullanıcı hesabıdır karşı denetler.</span><span class="sxs-lookup"><span data-stu-id="8432c-104">For actions subject to access control list (ACL) checks, such as access to directories and files on a machine or access to a SQL Server database, the ACL check is against the client user account.</span></span> <span data-ttu-id="8432c-105">Bu konu, bir istemcinin kimliğe bürünme düzeyi ayarlamak bir istemci bir Windows etki alanında etkinleştirmek için gereken temel adımlarda gösterir.</span><span class="sxs-lookup"><span data-stu-id="8432c-105">This topic shows the basic steps required to enable a client in a Windows domain to set a client impersonation level.</span></span> <span data-ttu-id="8432c-106">Bu çalışma örnek için bkz: [istemci kimliğine bürünme](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span><span class="sxs-lookup"><span data-stu-id="8432c-106">For a working example of this, see [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span></span> <span data-ttu-id="8432c-107">İstemcinin kimliğe bürünme hakkında daha fazla bilgi için bkz: [temsilcilik ve kimliğe bürünme](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="8432c-107">For more information about client impersonation, see [Delegation and Impersonation](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8432c-108">Ne zaman istemci hem de hizmet aynı bilgisayarda çalışan ve istemci bir sistem hesabı altında çalışan (diğer bir deyişle, `Local System` veya `Network Service`), güvenli oturum durum bilgisi olan güvenlik bağlamı belirteçleriyle kurulduğunda istemci bürünülemez.</span><span class="sxs-lookup"><span data-stu-id="8432c-108">When the client and service are running on the same computer and the client is running under a system account (that is, `Local System` or `Network Service`), the client cannot be impersonated when a secure session is established with stateful Security Context tokens.</span></span> <span data-ttu-id="8432c-109">Böylece hesap varsayılan olarak taklit edilebileceğini bir WinForms ya da konsol uygulaması genellikle şu anda oturum açmış hesabı altında çalışır.</span><span class="sxs-lookup"><span data-stu-id="8432c-109">A WinForms or console application typically is run under the currently logged in account, so that account can be impersonated by default.</span></span> <span data-ttu-id="8432c-110">Ancak, istemci olduğunda bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfa ve bu sayfa barındırılan [!INCLUDE[iis601](../../../includes/iis601-md.md)] veya IIS 7.0 sonra istemci altında Çalıştır `Network Service` varsayılan hesabı.</span><span class="sxs-lookup"><span data-stu-id="8432c-110">However, when the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and that page is hosted in [!INCLUDE[iis601](../../../includes/iis601-md.md)] or IIS 7.0, then the client does run under the `Network Service` account by default.</span></span> <span data-ttu-id="8432c-111">Güvenli oturumlar destek sistem tarafından sağlanan bağlamalar tümünün durumsuz bir güvenlik bağlamı belirteci varsayılan olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="8432c-111">All of the system-provided bindings that support secure sessions use a stateless Security Context token by default.</span></span> <span data-ttu-id="8432c-112">Ancak, istemci ise bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfası ve durum bilgisi olan güvenlik bağlamı belirteçleri ile güvenli oturumlar kullanılıyorsa, istemci bürünülemez.</span><span class="sxs-lookup"><span data-stu-id="8432c-112">However, if the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and secure sessions with stateful Security Context tokens are used, the client cannot be impersonated.</span></span> <span data-ttu-id="8432c-113">Durum bilgisi olan güvenlik bağlamı belirteçleri güvenli bir oturumda kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="8432c-113">For more information about using stateful Security Context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a><span data-ttu-id="8432c-114">Bir hizmet önbelleğe alınmış Windows belirteç istemciden kimliğine bürünme etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="8432c-114">To enable impersonation of a client from a cached Windows token on a service</span></span>  
  
1.  <span data-ttu-id="8432c-115">Hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8432c-115">Create the service.</span></span> <span data-ttu-id="8432c-116">Bu temel yordamı öğretici için bkz [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="8432c-116">For a tutorial of this basic procedure, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
2.  <span data-ttu-id="8432c-117">Windows kimlik doğrulamasını kullanır ve bir oturum gibi oluşturan bir bağlama kullanmak <xref:System.ServiceModel.NetTcpBinding> veya <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="8432c-117">Use a binding that uses Windows authentication and creates a session, such as <xref:System.ServiceModel.NetTcpBinding> or <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3.  <span data-ttu-id="8432c-118">Hizmetin arabirimini uygulaması oluştururken, uygulama <xref:System.ServiceModel.OperationBehaviorAttribute> istemci kimliğe bürünme gerektiren yöntemi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8432c-118">When creating the implementation of the service's interface, apply the <xref:System.ServiceModel.OperationBehaviorAttribute> class to the method that requires client impersonation.</span></span> <span data-ttu-id="8432c-119">Ayarlama <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliğine <xref:System.ServiceModel.ImpersonationOption.Required>.</span><span class="sxs-lookup"><span data-stu-id="8432c-119">Set the <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> property to <xref:System.ServiceModel.ImpersonationOption.Required>.</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a><span data-ttu-id="8432c-120">İstemci üzerinde izin verilen kimliğe bürünme düzeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8432c-120">To set the allowed impersonation level on the client</span></span>  
  
1.  <span data-ttu-id="8432c-121">Kullanarak hizmeti istemci kodunu oluşturmak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8432c-121">Create service client code by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="8432c-122">Daha fazla bilgi için bkz: [bir WCF istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="8432c-122">For more information, see [Accessing Services Using a WCF Client](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="8432c-123">Oluşturduktan sonra [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci, kümesi <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.ServiceModel.Security.WindowsClientCredential> birine sınıfı <xref:System.Security.Principal.TokenImpersonationLevel> numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="8432c-123">After creating the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client, set the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property of the <xref:System.ServiceModel.Security.WindowsClientCredential> class to one of the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration values.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8432c-124">Kullanmak için <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, üzerinde anlaşılan Kerberos kimlik doğrulaması (bazen adlı *çok leg* veya *çok adımlı* Kerberos) kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8432c-124">To use <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negotiated Kerberos authentication (sometimes called *multi-leg* or *multi-step* Kerberos) must be used.</span></span> <span data-ttu-id="8432c-125">Bu uygulama açıklaması için bkz: [en iyi güvenlik uygulamaları](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="8432c-125">For a description of how to implement this, see [Best Practices for Security](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8432c-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8432c-126">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [<span data-ttu-id="8432c-127">İstemci Kimliğine Bürünme</span><span class="sxs-lookup"><span data-stu-id="8432c-127">Impersonating the Client</span></span>](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [<span data-ttu-id="8432c-128">Temsilcilik ve Kimliğe Bürünme</span><span class="sxs-lookup"><span data-stu-id="8432c-128">Delegation and Impersonation</span></span>](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)

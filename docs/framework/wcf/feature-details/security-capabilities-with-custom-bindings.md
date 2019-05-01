---
title: Özel Bağlamalarla Güvenlik Özellikleri
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 25d203fa706eeb0d0ccf1eaf4367ffa5bd7b83aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990931"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="cd14a-102">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="cd14a-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="cd14a-103">Sistem tarafından sağlanan bağlamalar birini kullanarak en yaygın güvenlik görevlerini gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd14a-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="cd14a-104">Daha fazla denetime ihtiyacınız varsa, ancak ile özel bir bağlama oluşturabilirsiniz bir <xref:System.ServiceModel.Channels.SecurityBindingElement>, bu konu başlıklarında açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="cd14a-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="cd14a-105">Özel bağlamalar hakkında daha fazla bilgi için bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="cd14a-105">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cd14a-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cd14a-106">In This Section</span></span>  
 [<span data-ttu-id="cd14a-107">SecurityBindingElement Kimlik Doğrulama Modları</span><span class="sxs-lookup"><span data-stu-id="cd14a-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="cd14a-108">Özel bağlama ile olası kimlik doğrulama modları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="cd14a-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="cd14a-109">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd14a-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="cd14a-110">Özel bağlama güvenliği öğeyle oluşturmaya yönelik temel adımlar açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cd14a-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="cd14a-111">Nasıl yapılır: Belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd14a-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="cd14a-112">Belirtilen kimlik doğrulama modu için bir güvenlik öğesi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd14a-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="cd14a-113">Nasıl yapılır: WSFederationHttpBinding güvenli oturumlarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="cd14a-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="cd14a-114">Güvenli oturumlarını devre dışı bırakma açıklayan bir Federasyon Hizmeti oluşturma.</span><span class="sxs-lookup"><span data-stu-id="cd14a-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="cd14a-115">Nasıl yapılır: İleti yeniden yürütme algılamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="cd14a-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="cd14a-116">Yeniden yürütme saldırı gerçekleştiğinde belirlemeye açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd14a-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="cd14a-117">Nasıl yapılır: Destekleyici bir kimlik bilgisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd14a-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="cd14a-118">Hizmet gerektiriyorsa bir hizmete destekleyen bir kimlik bilgisi sağlamak üzere nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd14a-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="cd14a-119">Nasıl yapılır: Bir imza onayı ayarlama</span><span class="sxs-lookup"><span data-stu-id="cd14a-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="cd14a-120">İletileri imzalanırken dijital imzaları doğrulamak için gereken adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd14a-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="cd14a-121">Nasıl yapılır: Maksimum saat eğriltme ayarlama</span><span class="sxs-lookup"><span data-stu-id="cd14a-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="cd14a-122">Bir hizmet ve istemci arasındaki izin verilen en uzun süreyi fark ayarlama işlemi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd14a-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="cd14a-123">Nasıl yapılır: Dijital imzaların şifrelenmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="cd14a-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="cd14a-124">Dijital imzaların şifrelenmesini devre dışı bırakılması performans avantajı nasıl olabilir açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd14a-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cd14a-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="cd14a-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="cd14a-126">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="cd14a-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="cd14a-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="cd14a-127">Related Sections</span></span>  
 [<span data-ttu-id="cd14a-128">Koruma Düzeylerini Anlama</span><span class="sxs-lookup"><span data-stu-id="cd14a-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="cd14a-129">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="cd14a-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd14a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd14a-130">See also</span></span>

- [<span data-ttu-id="cd14a-131">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="cd14a-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [<span data-ttu-id="cd14a-132">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd14a-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="cd14a-133">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cd14a-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)

---
title: Özel Bağlamalarla Güvenlik Özellikleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: 11
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 31da996feae4e6509bea637bd17b4f538a75c5af
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="1832c-102">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="1832c-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="1832c-103">Sistem tarafından sağlanan bağlamalar birini kullanarak en yaygın güvenlik görevlerini gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1832c-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="1832c-104">Daha fazla denetim ihtiyacınız varsa, ancak, özel bağlama ile oluşturabileceğiniz bir <xref:System.ServiceModel.Channels.SecurityBindingElement>, bu konu başlıklarında açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="1832c-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="1832c-105">Özel bağlama hakkında daha fazla bilgi için bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="1832c-105">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1832c-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1832c-106">In This Section</span></span>  
 [<span data-ttu-id="1832c-107">SecurityBindingElement Kimlik Doğrulama Modları</span><span class="sxs-lookup"><span data-stu-id="1832c-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="1832c-108">Özel bağlama ile olası kimlik doğrulama modları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1832c-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="1832c-109">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1832c-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="1832c-110">Özel bağlama olan bir güvenlik öğesi oluşturmak için temel adımlar açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1832c-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="1832c-111">Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1832c-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="1832c-112">Belirtilen kimlik doğrulama modu için bir güvenlik öğesi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="1832c-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="1832c-113">Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="1832c-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="1832c-114">Güvenli oturumlar devre dışı bırakma açıklayan bir Federasyon Hizmeti oluştururken.</span><span class="sxs-lookup"><span data-stu-id="1832c-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="1832c-115">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1832c-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="1832c-116">Yeniden yürütme saldırısını oluştuğunda belirlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="1832c-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="1832c-117">Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1832c-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="1832c-118">Hizmet gerektiriyorsa bir hizmete destekleyen bir kimlik bilgisi sağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="1832c-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="1832c-119">Nasıl yapılır: İmza Onayı Ayarlama</span><span class="sxs-lookup"><span data-stu-id="1832c-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="1832c-120">Dijital olarak iletileri imzalarken imzaları doğrulamak için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="1832c-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="1832c-121">Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama</span><span class="sxs-lookup"><span data-stu-id="1832c-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="1832c-122">Bir hizmet ve istemci arasındaki en fazla izin verilen zaman farkı ayarlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1832c-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="1832c-123">Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="1832c-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="1832c-124">Dijital imzaların şifrelenmesi devre dışı bırakma performans avantajı nasıl sağlayabilirsiniz açıklar.</span><span class="sxs-lookup"><span data-stu-id="1832c-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1832c-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1832c-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="1832c-126">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="1832c-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="1832c-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1832c-127">Related Sections</span></span>  
 [<span data-ttu-id="1832c-128">Koruma Düzeylerini Anlama</span><span class="sxs-lookup"><span data-stu-id="1832c-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="1832c-129">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1832c-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="1832c-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1832c-130">See Also</span></span>  
 [<span data-ttu-id="1832c-131">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="1832c-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="1832c-132">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1832c-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="1832c-133">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1832c-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)

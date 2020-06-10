---
title: Özel Bağlamalarla Güvenlik Özellikleri
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 48d17543f2b133c74bcfa82cfe1a2a0de28b1d01
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595199"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="a3577-102">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a3577-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="a3577-103">Sistem tarafından belirtilen bağlamalardan birini kullanarak en yaygın güvenlik görevlerini gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3577-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="a3577-104">Ancak, daha fazla denetime ihtiyacınız varsa, <xref:System.ServiceModel.Channels.SecurityBindingElement> Bu konularda açıklandığı gibi, ile özel bir bağlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3577-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="a3577-105">Özel Bağlamalar hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a3577-105">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3577-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a3577-106">In This Section</span></span>  
 [<span data-ttu-id="a3577-107">SecurityBindingElement Kimlik Doğrulama Modları</span><span class="sxs-lookup"><span data-stu-id="a3577-107">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="a3577-108">Özel bir bağlama ile mümkün olan kimlik doğrulama modlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3577-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="a3577-109">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3577-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="a3577-110">Bir güvenlik öğesiyle özel bağlama oluşturmaya yönelik temel adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3577-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="a3577-111">Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3577-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="a3577-112">Belirtilen bir kimlik doğrulama modu için bir güvenlik öğesinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3577-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="a3577-113">Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="a3577-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="a3577-114">Federasyon Hizmeti oluştururken güvenli oturumların nasıl devre dışı bırakılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3577-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="a3577-115">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a3577-115">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="a3577-116">Bir yeniden yürütme saldırısının ne zaman gerçekleşeceğini nasıl belirleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3577-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="a3577-117">Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3577-117">How to: Create a Supporting Credential</span></span>](how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="a3577-118">Hizmeti gerektiriyorsa, bir hizmete destekleyici kimlik bilgisi sağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3577-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="a3577-119">Nasıl yapılır: İmza Onayı Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a3577-119">How to: Set Up a Signature Confirmation</span></span>](how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="a3577-120">İletileri dijital olarak imzalarken imzaları onaylama adımlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3577-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="a3577-121">Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a3577-121">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="a3577-122">Bir hizmet ve istemci arasında izin verilen en uzun zaman farkının nasıl ayarlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3577-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="a3577-123">Nasıl yapılır: Dijital İmzaların Şifrelenmesini Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="a3577-123">How to: Disable Encryption of Digital Signatures</span></span>](how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="a3577-124">Dijital imzaların şifrelenmesini devre dışı bırakmanın performans avantajına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3577-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a3577-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a3577-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="a3577-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a3577-126">Related Sections</span></span>  
 [<span data-ttu-id="a3577-127">Koruma Düzeylerini Anlama</span><span class="sxs-lookup"><span data-stu-id="a3577-127">Understanding Protection Level</span></span>](../understanding-protection-level.md)  
  
 [<span data-ttu-id="a3577-128">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a3577-128">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="a3577-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3577-129">See also</span></span>

- [<span data-ttu-id="a3577-130">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="a3577-130">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="a3577-131">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="a3577-131">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="a3577-132">Sistem tarafından sağlanmış bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a3577-132">System-Provided Bindings</span></span>](../system-provided-bindings.md)

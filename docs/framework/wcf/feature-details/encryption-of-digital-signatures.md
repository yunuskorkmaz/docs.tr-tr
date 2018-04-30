---
title: Dijital İmzaların Şifrelenmesi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 630465367eb4cee164a222bb5449070ac0726d5e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="encryption-of-digital-signatures"></a><span data-ttu-id="63273-102">Dijital İmzaların Şifrelenmesi</span><span class="sxs-lookup"><span data-stu-id="63273-102">Encryption of Digital Signatures</span></span>
<span data-ttu-id="63273-103">Varsayılan olarak, bir ileti imzalanır ve şifrelenir ve imza dijital olarak şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="63273-103">By default, a message is signed and encrypted, and the signature is digitally encrypted.</span></span> <span data-ttu-id="63273-104">Bu örneği ile özel bağlama oluşturarak kontrol <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ardından ayarlar `MessageProtectionOrder` özelliği için her iki sınıfın bir <xref:System.ServiceModel.Security.MessageProtectionOrder> numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="63273-104">You can control this by creating a custom binding with an instance of the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and then setting the `MessageProtectionOrder` property of either class to a <xref:System.ServiceModel.Security.MessageProtectionOrder> enumeration value.</span></span> <span data-ttu-id="63273-105">Varsayılan, <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> değeridir.</span><span class="sxs-lookup"><span data-stu-id="63273-105">The default is <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span></span> <span data-ttu-id="63273-106">Bu işlem 10-40 yüzde sadece imzalama ve şifreleme daha uzun sürer.</span><span class="sxs-lookup"><span data-stu-id="63273-106">This process takes 10 to 40 percent longer than simply signing and encrypting.</span></span> <span data-ttu-id="63273-107">İmza şifrelemeyi devre dışı bırakmak ancak, bir saldırganın iletinin içeriğini tahmin sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="63273-107">Disabling encryption of the signature, however, might allow an attacker to guess the contents of the message.</span></span> <span data-ttu-id="63273-108">Düz metin iletisi imzalı her bölümünün karma kodunu imza öğesi içerdiği için bu mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="63273-108">This is possible because the signature element contains the hash code of the plain text of every signed part in the message.</span></span> <span data-ttu-id="63273-109">Örneğin, varsayılan ileti gövdesi şifrelenmesine rağmen şifrelenmemiş imza ileti gövdesinin karma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="63273-109">For example, although the message body is encrypted by default, the unencrypted signature contains the hash code of the message body.</span></span> <span data-ttu-id="63273-110">İleti küçükse, bir saldırganın içeriği türetme olabilir.</span><span class="sxs-lookup"><span data-stu-id="63273-110">If the message is small, an attacker might be able to deduce the contents.</span></span> <span data-ttu-id="63273-111">İmza şifreleme küçültür veya bu olasılığını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="63273-111">Encrypting the signature reduces or eliminates this possibility.</span></span>  
  
 <span data-ttu-id="63273-112">Bu nedenle, şifreleme imza yalnızca içeriğin değerinin düşük olduğunda ve performans kazancı Örneğin, hiçbir güvenlik uygulamalarını sahip büyük ikili dosyaları gönderirken önemli olacaktır devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="63273-112">Therefore, disable encryption of the signature only when the value of the content is low, and the performance gain will be significant, for example, when sending large binary files that have no security implications.</span></span>  
  
### <a name="to-disable-digital-signing"></a><span data-ttu-id="63273-113">Dijital imzasını devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="63273-113">To disable digital signing</span></span>  
  
1.  <span data-ttu-id="63273-114">Oluşturma bir <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="63273-114">Create a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="63273-115">Daha fazla bilgi için bkz: [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="63273-115">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
2.  <span data-ttu-id="63273-116">Ekleyip ya da bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> bağlama koleksiyonuna.</span><span class="sxs-lookup"><span data-stu-id="63273-116">Add either an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> to the binding collection.</span></span>  
  
3.  <span data-ttu-id="63273-117">Ayarlama <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, veya <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span><span class="sxs-lookup"><span data-stu-id="63273-117">Set the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, or set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span></span>  
  
 <span data-ttu-id="63273-118">Özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="63273-118">For more information about creating custom bindings, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).</span></span> <span data-ttu-id="63273-119">Özel kimlik doğrulama modu için özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).</span><span class="sxs-lookup"><span data-stu-id="63273-119">For more information about creating a custom binding for a specific authentication mode, see [How to: Create a SecurityBindingElement for a Specified Authentication Mode](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63273-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63273-120">See Also</span></span>  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 [<span data-ttu-id="63273-121">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="63273-121">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="63273-122">Kullanıcı Tanımlı Bağlamalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="63273-122">Creating User-Defined Bindings</span></span>](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [<span data-ttu-id="63273-123">Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma</span><span class="sxs-lookup"><span data-stu-id="63273-123">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)

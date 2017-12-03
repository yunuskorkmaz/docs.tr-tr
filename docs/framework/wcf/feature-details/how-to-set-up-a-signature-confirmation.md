---
title: "Nasıl yapılır: İmza Onayı Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fced2ddd16ae244e2ea3d945082f48ffd23302e6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="fcc6d-102">Nasıl yapılır: İmza Onayı Ayarlama</span><span class="sxs-lookup"><span data-stu-id="fcc6d-102">How to: Set Up a Signature Confirmation</span></span>
<span data-ttu-id="fcc6d-103">*İmza onayı* alınan yanıt gönderenin özgün iletisine yanıt olarak oluşturulan emin olmak bir ileti başlatıcı için bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="fcc6d-104">İmza onayı WS güvenliği 1.1 belirtimini tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="fcc6d-105">Bir uç nokta WS güvenliği 1.0 destekliyorsa, imza onayı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>  
  
 <span data-ttu-id="fcc6d-106">Aşağıdaki yordamlar imza onayı kullanarak etkinleştirmek nasıl belirtin bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="fcc6d-107">Yordamın aynısını ile kullanabileceğiniz bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="fcc6d-108">Bulunan temel adımlar üzerine yordamı derlemeler [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="fcc6d-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="fcc6d-109">İmza onayı kodda etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="fcc6d-109">To enable signature confirmation in code</span></span>  
  
1.  <span data-ttu-id="fcc6d-110">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>  
  
2.  <span data-ttu-id="fcc6d-111">Bir örneğini oluşturmak <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>  
  
3.  <span data-ttu-id="fcc6d-112">Ayarlama <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="fcc6d-113">Güvenlik öğesinin bağlama koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-113">Add the security element to the binding collection.</span></span>  
  
5.  <span data-ttu-id="fcc6d-114">Belirtildiği gibi özel bağlama oluşturma [nasıl yapılır: SecurityBindingElement kullanarak özel bir bağlama oluşturun](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="fcc6d-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="fcc6d-115">İmza onayı yapılandırmasında etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="fcc6d-115">To enable signature confirmation in configuration</span></span>  
  
1.  <span data-ttu-id="fcc6d-116">Ekleme bir `<customBinding>` öğesine `<bindings>` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="fcc6d-117">Ekleme bir `<binding>` öğesi ve kümesi adı özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="fcc6d-118">Uygun kodlama öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="fcc6d-119">Aşağıdaki örnek, bir `<TextMessageEncoding>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-119">The following example adds a `<TextMessageEncoding>` element.</span></span>  
  
4.  <span data-ttu-id="fcc6d-120">Ekleme bir `<security>` alt öğesi ve kümesi `requireSignatureConfirmation` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>  
  
5.  <span data-ttu-id="fcc6d-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-121">Optional.</span></span> <span data-ttu-id="fcc6d-122">İmza onayı önyükleme sırasında etkinleştirmek için add bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğesi ve kümesi `equireSignatureConfirmation` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `equireSignatureConfirmation` attribute to `true`.</span></span>  
  
6.  <span data-ttu-id="fcc6d-123">Uygun bir taşıma öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-123">Add an appropriate transport element.</span></span> <span data-ttu-id="fcc6d-124">Aşağıdaki örnek, bir [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="fcc6d-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SignatureConfirmationBinding">  
          <security requireSignatureConfirmation="true">  
            <secureConversationBootstrap requireSignatureConfirmation="true" />  
              </security>  
           <textMessageEncoding />  
             <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="example"></a><span data-ttu-id="fcc6d-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcc6d-125">Example</span></span>  
 <span data-ttu-id="fcc6d-126">Aşağıdaki kod örneği oluşturur <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ayarlar <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="fcc6d-127">Bu örnek kullanmayan Not `<secureConversationBootstrap>` önceki örnekte gösterilen öğesi.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="fcc6d-128">Bu örnek, bir Windows (Kerberos protokolü) belirteci kullanırken imza onayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="fcc6d-129">Bu durumda, istemcinin imza hizmetinden tüm yanıtları döndürülür ve istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fcc6d-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
 [<span data-ttu-id="fcc6d-131">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="fcc6d-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="fcc6d-132">Nasıl yapılır: belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="fcc6d-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)

---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Imza onayı ayarlama'
title: 'Nasıl yapılır: İmza Onayı Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 158ec2a5f74038f5c1ca1af847f57457a8881974
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643195"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="54760-103">Nasıl yapılır: İmza Onayı Ayarlama</span><span class="sxs-lookup"><span data-stu-id="54760-103">How to: Set Up a Signature Confirmation</span></span>

<span data-ttu-id="54760-104">*İmza onaylama* bir ileti başlatıcısının, gönderenin özgün iletisine yanıt olarak alınan bir yanıtın oluşturulduğundan emin olmak için bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="54760-104">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="54760-105">İmza onayı WS-Security 1,1 belirtiminde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="54760-105">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="54760-106">Bir uç nokta WS-Security 1,0 destekliyorsa, imza onayını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="54760-106">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>

<span data-ttu-id="54760-107">Aşağıdaki yordamlar, kullanarak imza onayını etkinleştirmeyi belirtir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="54760-107">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="54760-108">İle aynı yordamı kullanabilirsiniz <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="54760-108">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="54760-109">Yordamı, [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)bölümünde bulunan temel adımların üzerine oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54760-109">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="54760-110">Kodda imza onayını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="54760-110">To enable signature confirmation in code</span></span>

1. <span data-ttu-id="54760-111">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="54760-111">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>

2. <span data-ttu-id="54760-112">Sınıfının bir örneğini oluşturun  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="54760-112">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>

3. <span data-ttu-id="54760-113">Öğesini <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="54760-113">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>

4. <span data-ttu-id="54760-114">Bağlama koleksiyonuna güvenlik öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54760-114">Add the security element to the binding collection.</span></span>

5. <span data-ttu-id="54760-115">[Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)bölümünde belirtildiği gibi özel bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54760-115">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="54760-116">Yapılandırmada imza onayını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="54760-116">To enable signature confirmation in configuration</span></span>

1. <span data-ttu-id="54760-117">`<customBinding>` `<bindings>` Yapılandırma dosyasının bölümüne bir öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54760-117">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>

2. <span data-ttu-id="54760-118">Bir `<binding>` öğesi ekleyin ve Name özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54760-118">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>

3. <span data-ttu-id="54760-119">Uygun bir kodlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54760-119">Add an appropriate encoding element.</span></span> <span data-ttu-id="54760-120">Aşağıdaki örnek bir öğesi ekler `<TextMessageEncoding>` .</span><span class="sxs-lookup"><span data-stu-id="54760-120">The following example adds a `<TextMessageEncoding>` element.</span></span>

4. <span data-ttu-id="54760-121">Bir `<security>` alt öğesi ekleyin ve `requireSignatureConfirmation` özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="54760-121">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

5. <span data-ttu-id="54760-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="54760-122">Optional.</span></span> <span data-ttu-id="54760-123">Önyükleme sırasında imza onayını etkinleştirmek için bir [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğe ekleyin ve `requireSignatureConfirmation` özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="54760-123">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

6. <span data-ttu-id="54760-124">Uygun bir taşıma öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54760-124">Add an appropriate transport element.</span></span> <span data-ttu-id="54760-125">Aşağıdaki örnek şunu ekler [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) :</span><span class="sxs-lookup"><span data-stu-id="54760-125">The following example adds an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md):</span></span>

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

## <a name="example"></a><span data-ttu-id="54760-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="54760-126">Example</span></span>

<span data-ttu-id="54760-127">Aşağıdaki kod öğesinin bir örneğini oluşturur <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> özelliğini olarak ayarlar `true` .</span><span class="sxs-lookup"><span data-stu-id="54760-127">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="54760-128">Bu örneğin, `<secureConversationBootstrap>` Önceki örnekte gösterilen öğesini kullanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="54760-128">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="54760-129">Bu örnekte, bir Windows (Kerberos protokolü) belirteci kullanılırken imza onayı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="54760-129">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="54760-130">Bu durumda, istemcinin imzası hizmetten gelen tüm yanıtlardan döndürülür ve istemci tarafından onaylanır.</span><span class="sxs-lookup"><span data-stu-id="54760-130">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="54760-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54760-131">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [<span data-ttu-id="54760-132">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54760-132">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="54760-133">Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma</span><span class="sxs-lookup"><span data-stu-id="54760-133">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)

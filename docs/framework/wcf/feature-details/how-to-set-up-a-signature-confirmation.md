---
title: 'Nasıl yapılır: İmza Onayı Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 56e8720a6130d2908fbfb83bd243a54fae9a2406
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315822"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="f5081-102">Nasıl yapılır: İmza Onayı Ayarlama</span><span class="sxs-lookup"><span data-stu-id="f5081-102">How to: Set Up a Signature Confirmation</span></span>
<span data-ttu-id="f5081-103">*İmza onayı* alınan yanıtı gönderen kişinin orijinal iletiye yanıt olarak oluşturulan emin olmak bir ileti Başlatıcı bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="f5081-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="f5081-104">İmza onayı WS-güvenlik 1.1 belirtiminde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f5081-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="f5081-105">Bir uç nokta WS-güvenlik 1.0 destekliyorsa, imza onayını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f5081-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>  
  
 <span data-ttu-id="f5081-106">Nasıl imza onayı kullanarak etkinleştirmek aşağıdaki yordamları belirtin bir <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f5081-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="f5081-107">Yordamın aynısını ile kullanabileceğiniz bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f5081-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="f5081-108">Bulunan temel adımları sırasında yordamı yapılar [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="f5081-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="f5081-109">İmza onayı kodda etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="f5081-109">To enable signature confirmation in code</span></span>  
  
1. <span data-ttu-id="f5081-110">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5081-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>  
  
2. <span data-ttu-id="f5081-111">Bir örneğini oluşturmak <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5081-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>  
  
3. <span data-ttu-id="f5081-112">Ayarlama <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="f5081-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>  
  
4. <span data-ttu-id="f5081-113">Güvenlik öğesinin bağlama koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f5081-113">Add the security element to the binding collection.</span></span>  
  
5. <span data-ttu-id="f5081-114">Belirtilen özel bir bağlama oluşturma [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="f5081-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="f5081-115">İmza onayı yapılandırması etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="f5081-115">To enable signature confirmation in configuration</span></span>  
  
1. <span data-ttu-id="f5081-116">Ekleme bir `<customBinding>` öğesine `<bindings>` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="f5081-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>  
  
2. <span data-ttu-id="f5081-117">Ekleme bir `<binding>` öğesi ve küme adı özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="f5081-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="f5081-118">Uygun bir kodlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f5081-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="f5081-119">Aşağıdaki örnek ekler bir `<TextMessageEncoding>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f5081-119">The following example adds a `<TextMessageEncoding>` element.</span></span>  
  
4. <span data-ttu-id="f5081-120">Ekleme bir `<security>` alt öğesi ve kümesi `requireSignatureConfirmation` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="f5081-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>  
  
5. <span data-ttu-id="f5081-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f5081-121">Optional.</span></span> <span data-ttu-id="f5081-122">Önyükleme sırasında imza Onayı etkinleştirmek için eklemeniz bir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) alt öğesi ve kümesi `equireSignatureConfirmation` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="f5081-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `equireSignatureConfirmation` attribute to `true`.</span></span>  
  
6. <span data-ttu-id="f5081-123">Uygun aktarma öğesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f5081-123">Add an appropriate transport element.</span></span> <span data-ttu-id="f5081-124">Aşağıdaki örnek ekler bir [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="f5081-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f5081-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5081-125">Example</span></span>  
 <span data-ttu-id="f5081-126">Aşağıdaki kod örneği oluşturur <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve ayarlar <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="f5081-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="f5081-127">Bu örnekte kullanmaz Not `<secureConversationBootstrap>` yukarıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f5081-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="f5081-128">Bu örnek, bir Windows (Kerberos protokolü) belirteci kullanıldığında imza onayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5081-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="f5081-129">Bu durumda, imza istemcinin hizmetinden alınan tüm yanıtları döndürülür ve istemci tarafından onaylanır.</span><span class="sxs-lookup"><span data-stu-id="f5081-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f5081-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5081-130">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [<span data-ttu-id="f5081-131">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5081-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="f5081-132">Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5081-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)

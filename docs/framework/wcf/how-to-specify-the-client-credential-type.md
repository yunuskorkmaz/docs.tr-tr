---
title: 'Nasıl yapılır: İstemci kimlik bilgileri türünü belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 9fe999c4ee27d4a78bfad185fa3bcc065d74708a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643387"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="2e877-102">Nasıl yapılır: İstemci kimlik bilgileri türünü belirtme</span><span class="sxs-lookup"><span data-stu-id="2e877-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="2e877-103">(Aktarım veya iletisi) bir güvenlik modu ayarlandıktan sonra istemci kimlik bilgisi türünü ayarlama seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="2e877-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="2e877-104">Bu özellik, istemci hizmete kimlik doğrulaması için kimlik bilgisi türü sağlamanız gerekir belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e877-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="2e877-105">(İstemci kimlik bilgisi türü ayarlamadan önce gerekli bir adım) güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Güvenlik modunu ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="2e877-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="2e877-106">İstemci kimlik bilgisi türü kodunda ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2e877-106">To set the client credential type in code</span></span>  
  
1.  <span data-ttu-id="2e877-107">Hizmetini kullanacak olan bağlama örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2e877-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="2e877-108">Bu örnekte <xref:System.ServiceModel.WSHttpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="2e877-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2.  <span data-ttu-id="2e877-109">Ayarlama <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="2e877-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="2e877-110">Bu örnek, mesajı modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e877-110">This example uses the Message mode.</span></span>  
  
3.  <span data-ttu-id="2e877-111">Ayarlama <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="2e877-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="2e877-112">Bu örnekte Windows kimlik doğrulaması kullanacak şekilde ayarlar (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="2e877-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="2e877-113">İstemci kimlik bilgisi türü yapılandırmada ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2e877-113">To set the client credential type in configuration</span></span>  
  
1.  <span data-ttu-id="2e877-114">Ekleme bir [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma dosyasına öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e877-114">Add a [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2.  <span data-ttu-id="2e877-115">Bir alt öğesi ekleyin bir [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e877-115">As a child element, add a [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3.  <span data-ttu-id="2e877-116">Uygun bir bağlaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e877-116">Add an appropriate binding.</span></span> <span data-ttu-id="2e877-117">Bu örnekte [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e877-117">This example uses the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4.  <span data-ttu-id="2e877-118">Ekleme bir [ \<bağlama >](../../../docs/framework/misc/binding.md) öğesi ve kümesi `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="2e877-118">Add a [\<binding>](../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="2e877-119">Bu örnek, "SecureBinding" adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e877-119">This example uses the name "SecureBinding".</span></span>  
  
5.  <span data-ttu-id="2e877-120">Ekleme bir `<security>` bağlama.</span><span class="sxs-lookup"><span data-stu-id="2e877-120">Add a `<security>` binding.</span></span> <span data-ttu-id="2e877-121">Ayarlama `mode` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="2e877-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="2e877-122">Bu örnek ayarlar `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="2e877-122">This example sets it to `"Message"`.</span></span>  
  
6.  <span data-ttu-id="2e877-123">Ekleyin ya da bir `<message>` veya `<transport>` güvenlik modu tarafından belirlenen şekilde öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e877-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="2e877-124">Ayarlama `clientCredentialType` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="2e877-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="2e877-125">Bu örnekte `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="2e877-125">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2e877-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e877-126">See also</span></span>
- [<span data-ttu-id="2e877-127">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2e877-127">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="2e877-128">Nasıl yapılır: Güvenlik modunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="2e877-128">How to: Set the Security Mode</span></span>](../../../docs/framework/wcf/how-to-set-the-security-mode.md)

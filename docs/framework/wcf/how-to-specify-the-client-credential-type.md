---
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: d62011728b6b03023ef4039480cea8dfa0ec8f02
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321294"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="bd0cb-102">Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme</span><span class="sxs-lookup"><span data-stu-id="bd0cb-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="bd0cb-103">Bir güvenlik modu (aktarım veya ileti) ayarladıktan sonra istemci kimlik bilgisi türünü ayarlama seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="bd0cb-104">Bu özellik, istemcinin kimlik doğrulaması için hizmete sağlaması gereken kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="bd0cb-105">Güvenlik modunu ayarlama hakkında daha fazla bilgi için (istemci kimlik bilgisi türünü ayarlamadan önce gerekli bir adım), bkz. [nasıl yapılır: güvenlik modunu ayarlama](how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="bd0cb-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="bd0cb-106">Kodda istemci kimlik bilgisi türünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="bd0cb-106">To set the client credential type in code</span></span>  
  
1. <span data-ttu-id="bd0cb-107">Hizmetin kullanacağı bağlamanın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="bd0cb-108">Bu örnek <xref:System.ServiceModel.WSHttpBinding> bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2. <span data-ttu-id="bd0cb-109">@No__t-0 özelliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="bd0cb-110">Bu örnek Ileti modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-110">This example uses the Message mode.</span></span>  
  
3. <span data-ttu-id="bd0cb-111">@No__t-0 özelliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="bd0cb-112">Bu örnek, Windows kimlik doğrulaması (<xref:System.ServiceModel.MessageCredentialType.Windows>) kullanacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="bd0cb-113">Yapılandırmada istemci kimlik bilgisi türünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="bd0cb-113">To set the client credential type in configuration</span></span>  
  
1. <span data-ttu-id="bd0cb-114">Yapılandırma dosyasına bir [\<System. serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-114">Add a [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2. <span data-ttu-id="bd0cb-115">Bir alt öğe olarak [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-115">As a child element, add a [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3. <span data-ttu-id="bd0cb-116">Uygun bir bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-116">Add an appropriate binding.</span></span> <span data-ttu-id="bd0cb-117">Bu örnek [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-117">This example uses the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4. <span data-ttu-id="bd0cb-118">[@No__t-1binding >](../misc/binding.md) öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-118">Add a [\<binding>](../misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="bd0cb-119">Bu örnekte "SecureBinding" adı kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-119">This example uses the name "SecureBinding".</span></span>  
  
5. <span data-ttu-id="bd0cb-120">@No__t-0 bağlaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-120">Add a `<security>` binding.</span></span> <span data-ttu-id="bd0cb-121">@No__t-0 özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="bd0cb-122">Bu örnek, `"Message"` olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-122">This example sets it to `"Message"`.</span></span>  
  
6. <span data-ttu-id="bd0cb-123">Güvenlik modu tarafından belirlendiği gibi `<message>` veya `<transport>` öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="bd0cb-124">@No__t-0 özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="bd0cb-125">Bu örnek `"Windows"` kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-125">This example uses `"Windows"`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bd0cb-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-126">See also</span></span>

- [<span data-ttu-id="bd0cb-127">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="bd0cb-127">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="bd0cb-128">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="bd0cb-128">How to: Set the Security Mode</span></span>](how-to-set-the-security-mode.md)

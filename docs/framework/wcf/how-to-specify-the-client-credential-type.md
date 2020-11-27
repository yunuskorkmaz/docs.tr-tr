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
ms.openlocfilehash: b45d7b58d8a1fe79f9d7a8cff6e328b46633985c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293682"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="eb1b2-102">Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme</span><span class="sxs-lookup"><span data-stu-id="eb1b2-102">How to: Specify the Client Credential Type</span></span>

<span data-ttu-id="eb1b2-103">Bir güvenlik modu (aktarım veya ileti) ayarladıktan sonra istemci kimlik bilgisi türünü ayarlama seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="eb1b2-104">Bu özellik, istemcinin kimlik doğrulaması için hizmete sağlaması gereken kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="eb1b2-105">Güvenlik modunu ayarlama hakkında daha fazla bilgi için (istemci kimlik bilgisi türünü ayarlamadan önce gerekli bir adım), bkz. [nasıl yapılır: güvenlik modunu ayarlama](how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="eb1b2-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="eb1b2-106">Kodda istemci kimlik bilgisi türünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="eb1b2-106">To set the client credential type in code</span></span>  
  
1. <span data-ttu-id="eb1b2-107">Hizmetin kullanacağı bağlamanın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="eb1b2-108">Bu örnek, <xref:System.ServiceModel.WSHttpBinding> bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2. <span data-ttu-id="eb1b2-109"><xref:System.ServiceModel.WSHttpSecurity.Mode%2A>Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="eb1b2-110">Bu örnek Ileti modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-110">This example uses the Message mode.</span></span>  
  
3. <span data-ttu-id="eb1b2-111"><xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A>Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="eb1b2-112">Bu örnek, Windows kimlik doğrulaması () kullanmak üzere ayarlar <xref:System.ServiceModel.MessageCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="eb1b2-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="eb1b2-113">Yapılandırmada istemci kimlik bilgisi türünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="eb1b2-113">To set the client credential type in configuration</span></span>  
  
1. <span data-ttu-id="eb1b2-114">[\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md)Yapılandırma dosyasına bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-114">Add a [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2. <span data-ttu-id="eb1b2-115">Alt öğe olarak bir [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-115">As a child element, add a [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3. <span data-ttu-id="eb1b2-116">Uygun bir bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-116">Add an appropriate binding.</span></span> <span data-ttu-id="eb1b2-117">Bu örnek öğesini kullanır [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="eb1b2-117">This example uses the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4. <span data-ttu-id="eb1b2-118">Bir [\<binding>](../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-118">Add a [\<binding>](../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="eb1b2-119">Bu örnekte "SecureBinding" adı kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-119">This example uses the name "SecureBinding".</span></span>  
  
5. <span data-ttu-id="eb1b2-120">Bağlama ekleyin `<security>` .</span><span class="sxs-lookup"><span data-stu-id="eb1b2-120">Add a `<security>` binding.</span></span> <span data-ttu-id="eb1b2-121">`mode`Özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="eb1b2-122">Bu örnek olarak ayarlanır `"Message"` .</span><span class="sxs-lookup"><span data-stu-id="eb1b2-122">This example sets it to `"Message"`.</span></span>  
  
6. <span data-ttu-id="eb1b2-123">`<message>` `<transport>` Güvenlik modu tarafından belirlendiği şekilde ya da öğesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="eb1b2-124">`clientCredentialType`Özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="eb1b2-125">Bu örnekte, kullanılır `"Windows"` .</span><span class="sxs-lookup"><span data-stu-id="eb1b2-125">This example uses `"Windows"`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb1b2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb1b2-126">See also</span></span>

- [<span data-ttu-id="eb1b2-127">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="eb1b2-127">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="eb1b2-128">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="eb1b2-128">How to: Set the Security Mode</span></span>](how-to-set-the-security-mode.md)

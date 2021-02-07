---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Istemci kimlik bilgileri türünü belirtme'
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: f6536778e8814a1b5a4c03e22c0fe4108f89b6eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752541"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="eecac-103">Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme</span><span class="sxs-lookup"><span data-stu-id="eecac-103">How to: Specify the Client Credential Type</span></span>

<span data-ttu-id="eecac-104">Bir güvenlik modu (aktarım veya ileti) ayarladıktan sonra istemci kimlik bilgisi türünü ayarlama seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="eecac-104">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="eecac-105">Bu özellik, istemcinin kimlik doğrulaması için hizmete sağlaması gereken kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="eecac-105">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="eecac-106">Güvenlik modunu ayarlama hakkında daha fazla bilgi için (istemci kimlik bilgisi türünü ayarlamadan önce gerekli bir adım), bkz. [nasıl yapılır: güvenlik modunu ayarlama](how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="eecac-106">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="eecac-107">Kodda istemci kimlik bilgisi türünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="eecac-107">To set the client credential type in code</span></span>  
  
1. <span data-ttu-id="eecac-108">Hizmetin kullanacağı bağlamanın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eecac-108">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="eecac-109">Bu örnek, <xref:System.ServiceModel.WSHttpBinding> bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="eecac-109">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2. <span data-ttu-id="eecac-110"><xref:System.ServiceModel.WSHttpSecurity.Mode%2A>Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eecac-110">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="eecac-111">Bu örnek Ileti modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="eecac-111">This example uses the Message mode.</span></span>  
  
3. <span data-ttu-id="eecac-112"><xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A>Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eecac-112">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="eecac-113">Bu örnek, Windows kimlik doğrulaması () kullanmak üzere ayarlar <xref:System.ServiceModel.MessageCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="eecac-113">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="eecac-114">Yapılandırmada istemci kimlik bilgisi türünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="eecac-114">To set the client credential type in configuration</span></span>  
  
1. <span data-ttu-id="eecac-115">[\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md)Yapılandırma dosyasına bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eecac-115">Add a [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2. <span data-ttu-id="eecac-116">Alt öğe olarak bir [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eecac-116">As a child element, add a [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3. <span data-ttu-id="eecac-117">Uygun bir bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eecac-117">Add an appropriate binding.</span></span> <span data-ttu-id="eecac-118">Bu örnek öğesini kullanır [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="eecac-118">This example uses the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4. <span data-ttu-id="eecac-119">Bir [\<binding>](../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eecac-119">Add a [\<binding>](../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="eecac-120">Bu örnekte "SecureBinding" adı kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eecac-120">This example uses the name "SecureBinding".</span></span>  
  
5. <span data-ttu-id="eecac-121">Bağlama ekleyin `<security>` .</span><span class="sxs-lookup"><span data-stu-id="eecac-121">Add a `<security>` binding.</span></span> <span data-ttu-id="eecac-122">`mode`Özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eecac-122">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="eecac-123">Bu örnek olarak ayarlanır `"Message"` .</span><span class="sxs-lookup"><span data-stu-id="eecac-123">This example sets it to `"Message"`.</span></span>  
  
6. <span data-ttu-id="eecac-124">`<message>` `<transport>` Güvenlik modu tarafından belirlendiği şekilde ya da öğesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eecac-124">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="eecac-125">`clientCredentialType`Özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eecac-125">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="eecac-126">Bu örnekte `"Windows"` kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="eecac-126">This example uses `"Windows"`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eecac-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eecac-127">See also</span></span>

- [<span data-ttu-id="eecac-128">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="eecac-128">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="eecac-129">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="eecac-129">How to: Set the Security Mode</span></span>](how-to-set-the-security-mode.md)

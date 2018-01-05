---
title: "Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme"
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
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24336c180ad8d10a60567ebfeb0f0899f972e2c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="d8fb7-102">Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme</span><span class="sxs-lookup"><span data-stu-id="d8fb7-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="d8fb7-103">Bir güvenlik modunu (taşıma veya ileti) ayarladıktan sonra istemci ayar kimlik bilgisi türü seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="d8fb7-104">Bu özellik ne tür bir kimlik bilgisi istemci kimlik doğrulaması için hizmet sağlamalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="d8fb7-105">bkz: (istemci kimlik bilgisi türü ayarlamadan önce gerekli bir adım), güvenlik modu ayarı [nasıl yapılır: güvenlik modunu ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="d8fb7-105"> setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="d8fb7-106">İstemci kimlik bilgisi türü kodda ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d8fb7-106">To set the client credential type in code</span></span>  
  
1.  <span data-ttu-id="d8fb7-107">Hizmet kullanacak bağlama örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="d8fb7-108">Bu örnekte <xref:System.ServiceModel.WSHttpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2.  <span data-ttu-id="d8fb7-109">Ayarlama <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> uygun bir değere özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="d8fb7-110">Bu örnek ileti modu kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-110">This example uses the Message mode.</span></span>  
  
3.  <span data-ttu-id="d8fb7-111">Ayarlama <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> uygun bir değere özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="d8fb7-112">Bu örnekte Windows kimlik doğrulaması kullanacak şekilde ayarlar (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="d8fb7-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="d8fb7-113">İstemci kimlik bilgisi türü yapılandırmasında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d8fb7-113">To set the client credential type in configuration</span></span>  
  
1.  <span data-ttu-id="d8fb7-114">Ekleme bir [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-114">Add a [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2.  <span data-ttu-id="d8fb7-115">Bir alt öğesi Ekle bir [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-115">As a child element, add a [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3.  <span data-ttu-id="d8fb7-116">Uygun bir bağlaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-116">Add an appropriate binding.</span></span> <span data-ttu-id="d8fb7-117">Bu örnekte [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-117">This example uses the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4.  <span data-ttu-id="d8fb7-118">Ekleme bir [ \<bağlama >](../../../docs/framework/misc/binding.md) öğesi ve kümesi `name` öznitelik için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-118">Add a [\<binding>](../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="d8fb7-119">Bu örnekte "SecureBinding" adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-119">This example uses the name "SecureBinding".</span></span>  
  
5.  <span data-ttu-id="d8fb7-120">Ekleme bir `<security>` bağlama.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-120">Add a `<security>` binding.</span></span> <span data-ttu-id="d8fb7-121">Ayarlama `mode` öznitelik için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="d8fb7-122">Bu örnek ayarlar `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-122">This example sets it to `"Message"`.</span></span>  
  
6.  <span data-ttu-id="d8fb7-123">Ekleyip ya da bir `<message>` veya `<transport>` güvenlik modu tarafından belirlenen öğesi.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="d8fb7-124">Ayarlama `clientCredentialType` öznitelik için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="d8fb7-125">Bu örnekte `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-125">This example uses `"Windows"`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8fb7-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8fb7-126">See Also</span></span>  
 [<span data-ttu-id="d8fb7-127">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d8fb7-127">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="d8fb7-128">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="d8fb7-128">How to: Set the Security Mode</span></span>](../../../docs/framework/wcf/how-to-set-the-security-mode.md)

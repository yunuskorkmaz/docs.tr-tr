---
description: 'Hakkında daha fazla bilgi <transport> edinin: <netNamedPipeBinding>'
title: <transport> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: a54c429bcac192ddc46df7232c33ab98bd1a4c58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773491"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="1b0d9-103">\<transport> / \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="1b0d9-103">\<transport> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="1b0d9-104">Adlandırılmış bir kanal için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-104">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="1b0d9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b0d9-105">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b0d9-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b0d9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1b0d9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b0d9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b0d9-108">Attributes</span></span>  
  
|<span data-ttu-id="1b0d9-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1b0d9-109">Attribute</span></span>|<span data-ttu-id="1b0d9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b0d9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b0d9-111">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1b0d9-111">protectionLevel</span></span>|<span data-ttu-id="1b0d9-112">Adlandırılmış kanalın koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-112">Defines protection level of the named pipe.</span></span> <span data-ttu-id="1b0d9-113">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-113">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="1b0d9-114">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-114">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="1b0d9-115">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1b0d9-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1b0d9-116">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-116">-   None: No protection.</span></span><br /><span data-ttu-id="1b0d9-117">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-117">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1b0d9-118">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-118">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="1b0d9-119">Varsayılan değer EncryptAndSign ' dır.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-119">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b0d9-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b0d9-120">Child Elements</span></span>  

 <span data-ttu-id="1b0d9-121">Yok</span><span class="sxs-lookup"><span data-stu-id="1b0d9-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b0d9-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b0d9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1b0d9-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b0d9-123">Element</span></span>|<span data-ttu-id="1b0d9-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b0d9-124">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="1b0d9-125">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-125">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b0d9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b0d9-126">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="1b0d9-127">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1b0d9-127">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1b0d9-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1b0d9-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1b0d9-129">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1b0d9-129">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1b0d9-130">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1b0d9-130">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

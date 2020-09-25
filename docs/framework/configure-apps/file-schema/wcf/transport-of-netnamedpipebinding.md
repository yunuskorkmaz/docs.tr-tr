---
title: <transport> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 81c52405478d4c1ab5c65aab73f7feff61b879d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178027"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="e3875-102">\<transport> / \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="e3875-102">\<transport> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="e3875-103">Adlandırılmış bir kanal için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3875-103">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="e3875-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3875-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3875-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3875-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e3875-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3875-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3875-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3875-107">Attributes</span></span>  
  
|<span data-ttu-id="e3875-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e3875-108">Attribute</span></span>|<span data-ttu-id="e3875-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3875-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3875-110">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="e3875-110">protectionLevel</span></span>|<span data-ttu-id="e3875-111">Adlandırılmış kanalın koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3875-111">Defines protection level of the named pipe.</span></span> <span data-ttu-id="e3875-112">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="e3875-112">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="e3875-113">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3875-113">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="e3875-114">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e3875-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e3875-115">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="e3875-115">-   None: No protection.</span></span><br /><span data-ttu-id="e3875-116">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="e3875-116">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="e3875-117">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="e3875-117">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="e3875-118">Varsayılan değer EncryptAndSign ' dır.</span><span class="sxs-lookup"><span data-stu-id="e3875-118">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3875-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3875-119">Child Elements</span></span>  

 <span data-ttu-id="e3875-120">Yok</span><span class="sxs-lookup"><span data-stu-id="e3875-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3875-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3875-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e3875-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3875-122">Element</span></span>|<span data-ttu-id="e3875-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3875-123">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="e3875-124">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3875-124">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3875-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3875-125">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="e3875-126">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e3875-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e3875-127">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e3875-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e3875-128">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e3875-128">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e3875-129">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e3875-129">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

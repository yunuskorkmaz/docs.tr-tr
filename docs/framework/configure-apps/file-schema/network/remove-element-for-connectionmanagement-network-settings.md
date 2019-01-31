---
title: connectionManagement için <remove> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 62f7793c8f25f4803e881e2f183c99c62000ca23
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270536"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="269df-102">\<kaldırma > connectionManagement (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="269df-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="269df-103">Bir IP adresi veya DNS adı bağlantı yönetimi listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="269df-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="269df-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="269df-104">\<configuration></span></span>  
<span data-ttu-id="269df-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="269df-105">\<system.net></span></span>  
<span data-ttu-id="269df-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="269df-106">\<connectionManagement></span></span>  
<span data-ttu-id="269df-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="269df-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="269df-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="269df-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="269df-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="269df-109">Attributes and Elements</span></span>  
 <span data-ttu-id="269df-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="269df-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="269df-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="269df-111">Attributes</span></span>  
  
|<span data-ttu-id="269df-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="269df-112">**Attribute**</span></span>|<span data-ttu-id="269df-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="269df-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="269df-114">Bir IP adresi veya DNS adı.</span><span class="sxs-lookup"><span data-stu-id="269df-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="269df-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="269df-115">Child Elements</span></span>  
 <span data-ttu-id="269df-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="269df-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="269df-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="269df-117">Parent Elements</span></span>  
  
|<span data-ttu-id="269df-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="269df-118">**Element**</span></span>|<span data-ttu-id="269df-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="269df-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="269df-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="269df-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="269df-121">Bir ağ konak bağlantı maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="269df-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="269df-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="269df-122">Remarks</span></span>  
 <span data-ttu-id="269df-123">`remove` Bağlantı yönetim listesi girişi için belirtilen server öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="269df-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="269df-124">Değerini `address` özniteliği geçerli bir IP adresi veya ana bilgisayar adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="269df-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="269df-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="269df-125">Configuration Files</span></span>  
 <span data-ttu-id="269df-126">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="269df-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="269df-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="269df-127">Example</span></span>  
 <span data-ttu-id="269df-128">Aşağıdaki örnek, tüm sunucu için bağlantı yönetim Liste girişlerini kaldırır `www.adventure-works.com` ve ardından sunucu için dört bağlantıları kullanmak için bir uygulamayı yapılandırır `www.contoso.com` ve diğer tüm sunucular iki bağlantı.</span><span class="sxs-lookup"><span data-stu-id="269df-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="269df-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="269df-129">See also</span></span>
- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="269df-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="269df-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

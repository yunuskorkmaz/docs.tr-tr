---
description: 'Daha fazla bilgi edinin: <clear> connectionManagement için öğesi (ağ ayarları)'
title: connectionManagement için <clear> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
ms.openlocfilehash: e6e756e1065e48e79d59e02858963ded70d30f7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698595"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="95944-103">connectionManagement için \<clear> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="95944-103">\<clear> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="95944-104">Bağlantı yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="95944-104">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="95944-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="95944-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95944-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="95944-106">Attributes and Elements</span></span>  

 <span data-ttu-id="95944-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="95944-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95944-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="95944-108">Attributes</span></span>  

 <span data-ttu-id="95944-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="95944-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="95944-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="95944-110">Child Elements</span></span>  

 <span data-ttu-id="95944-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="95944-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95944-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="95944-112">Parent Elements</span></span>  
  
|<span data-ttu-id="95944-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="95944-113">**Element**</span></span>|<span data-ttu-id="95944-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="95944-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="95944-115">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="95944-115">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="95944-116">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="95944-116">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95944-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95944-117">Remarks</span></span>  

 <span data-ttu-id="95944-118">`clear`Öğesi bağlantı yönetimi listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="95944-118">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="95944-119">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="95944-119">Configuration Files</span></span>  

 <span data-ttu-id="95944-120">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95944-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95944-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="95944-121">Example</span></span>  

 <span data-ttu-id="95944-122">Aşağıdaki örnek bağlantı yönetimi listesini temizler ve ardından sunucu `www.contoso.com` ve diğer tüm ağ konakları için yeni bağlantı yönetimi girişleri ekler.</span><span class="sxs-lookup"><span data-stu-id="95944-122">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95944-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95944-123">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="95944-124">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="95944-124">Network Settings Schema</span></span>](index.md)

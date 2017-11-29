---
title: "&lt;oidMap&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: eab9be57b6f8fac5f208e39a6aaa8eb7be92558d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltoidmapgt-element"></a><span data-ttu-id="0dc25-102">&lt;oidMap&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="0dc25-102">&lt;oidMap&gt; Element</span></span>
<span data-ttu-id="0dc25-103">ASN.1 nesne tanımlayıcısı (OID) eşlemeleri sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="0dc25-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="0dc25-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0dc25-104">\<configuration></span></span>  
<span data-ttu-id="0dc25-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="0dc25-105">\<mscorlib></span></span>  
<span data-ttu-id="0dc25-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="0dc25-106">\<cryptographySettings></span></span>  
<span data-ttu-id="0dc25-107">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="0dc25-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc25-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dc25-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dc25-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0dc25-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0dc25-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0dc25-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dc25-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0dc25-111">Attributes</span></span>  
 <span data-ttu-id="0dc25-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="0dc25-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0dc25-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0dc25-113">Child Elements</span></span>  
  
|<span data-ttu-id="0dc25-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="0dc25-114">Element</span></span>|<span data-ttu-id="0dc25-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dc25-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0dc25-116">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="0dc25-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="0dc25-117">ASN.1 OID için kolay bir ad eşler.</span><span class="sxs-lookup"><span data-stu-id="0dc25-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0dc25-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0dc25-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0dc25-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="0dc25-119">Element</span></span>|<span data-ttu-id="0dc25-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dc25-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0dc25-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0dc25-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="0dc25-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="0dc25-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="0dc25-123">İçeren `cryptographySettings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0dc25-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0dc25-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dc25-124">Example</span></span>  
 <span data-ttu-id="0dc25-125">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<oidMap >** öğesi RIPEMD 160 karma algoritmasını Bu karma algoritmayı uygulaması için bir OID eşlemesi içerir.</span><span class="sxs-lookup"><span data-stu-id="0dc25-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dc25-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0dc25-126">See Also</span></span>  
 [<span data-ttu-id="0dc25-127">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="0dc25-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0dc25-128">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0dc25-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="0dc25-129">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="0dc25-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="0dc25-130">Şifreleme sınıflarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0dc25-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="0dc25-131">Nesne tanımlayıcılarını şifreleme algoritmalarıyla eşleştirme</span><span class="sxs-lookup"><span data-stu-id="0dc25-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)

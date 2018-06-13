---
title: '&lt;oidMap&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: db39d7de3566647b5171b71940c78a9a0ab6f5f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350228"
---
# <a name="ltoidmapgt-element"></a><span data-ttu-id="667f8-102">&lt;oidMap&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="667f8-102">&lt;oidMap&gt; Element</span></span>
<span data-ttu-id="667f8-103">ASN.1 nesne tanımlayıcısı (OID) eşlemeleri sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="667f8-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="667f8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="667f8-104">\<configuration></span></span>  
<span data-ttu-id="667f8-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="667f8-105">\<mscorlib></span></span>  
<span data-ttu-id="667f8-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="667f8-106">\<cryptographySettings></span></span>  
<span data-ttu-id="667f8-107">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="667f8-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="667f8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="667f8-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="667f8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="667f8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="667f8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="667f8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="667f8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="667f8-111">Attributes</span></span>  
 <span data-ttu-id="667f8-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="667f8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="667f8-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="667f8-113">Child Elements</span></span>  
  
|<span data-ttu-id="667f8-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="667f8-114">Element</span></span>|<span data-ttu-id="667f8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="667f8-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="667f8-116">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="667f8-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="667f8-117">ASN.1 OID için kolay bir ad eşler.</span><span class="sxs-lookup"><span data-stu-id="667f8-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="667f8-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="667f8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="667f8-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="667f8-119">Element</span></span>|<span data-ttu-id="667f8-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="667f8-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="667f8-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="667f8-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="667f8-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="667f8-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="667f8-123">İçeren `cryptographySettings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="667f8-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="667f8-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="667f8-124">Example</span></span>  
 <span data-ttu-id="667f8-125">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<oidMap >** öğesi RIPEMD 160 karma algoritmasını Bu karma algoritmayı uygulaması için bir OID eşlemesi içerir.</span><span class="sxs-lookup"><span data-stu-id="667f8-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="667f8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="667f8-126">See Also</span></span>  
 [<span data-ttu-id="667f8-127">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="667f8-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="667f8-128">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="667f8-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="667f8-129">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="667f8-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="667f8-130">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="667f8-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="667f8-131">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="667f8-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)

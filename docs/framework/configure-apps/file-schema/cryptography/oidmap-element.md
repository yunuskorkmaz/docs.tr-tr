---
title: <oidMap> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: e01cdd942237141b8ef35495d3b74d6b2282a865
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664251"
---
# <a name="oidmap-element"></a><span data-ttu-id="e5a3a-102">\<Oıdmap > öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a3a-102">\<oidMap> Element</span></span>
<span data-ttu-id="e5a3a-103">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e5a3a-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="e5a3a-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e5a3a-104">\<configuration></span></span>  
<span data-ttu-id="e5a3a-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="e5a3a-105">\<mscorlib></span></span>  
<span data-ttu-id="e5a3a-106">\<Cryptographyısettings ></span><span class="sxs-lookup"><span data-stu-id="e5a3a-106">\<cryptographySettings></span></span>  
<span data-ttu-id="e5a3a-107">\<Oıdmap ></span><span class="sxs-lookup"><span data-stu-id="e5a3a-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a3a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5a3a-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5a3a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5a3a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e5a3a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5a3a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5a3a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5a3a-111">Attributes</span></span>  
 <span data-ttu-id="e5a3a-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5a3a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5a3a-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5a3a-113">Child Elements</span></span>  
  
|<span data-ttu-id="e5a3a-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5a3a-114">Element</span></span>|<span data-ttu-id="e5a3a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5a3a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5a3a-116">\<Oıdentry ></span><span class="sxs-lookup"><span data-stu-id="e5a3a-116">\<oidEntry></span></span>](oidentry-element.md)|<span data-ttu-id="e5a3a-117">Bir ASN. 1 OID 'yi kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="e5a3a-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5a3a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5a3a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e5a3a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5a3a-119">Element</span></span>|<span data-ttu-id="e5a3a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5a3a-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e5a3a-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e5a3a-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="e5a3a-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e5a3a-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="e5a3a-123">`cryptographySettings` Öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="e5a3a-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5a3a-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5a3a-124">Example</span></span>  
 <span data-ttu-id="e5a3a-125">Aşağıdaki örnek, RIPEMD-160 karma algoritması için bir OID 'nin bu karma algoritmanın bir uygulamasına eşlemesini içeren  **\<oıdmap >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5a3a-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5a3a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a3a-126">See also</span></span>

- [<span data-ttu-id="e5a3a-127">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e5a3a-127">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e5a3a-128">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e5a3a-128">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e5a3a-129">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e5a3a-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="e5a3a-130">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e5a3a-130">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="e5a3a-131">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="e5a3a-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)

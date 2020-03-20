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
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155173"
---
# <a name="oidmap-element"></a><span data-ttu-id="ed48b-102">\<oidMap> Elemanı</span><span class="sxs-lookup"><span data-stu-id="ed48b-102">\<oidMap> Element</span></span>
<span data-ttu-id="ed48b-103">Sınıflara ASN.1 nesne tanımlayıcısı (OID) eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ed48b-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

<span data-ttu-id="ed48b-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed48b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed48b-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ed48b-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="ed48b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<şifrelemeAyarlar>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed48b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="ed48b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="ed48b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ed48b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed48b-108">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed48b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed48b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ed48b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed48b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed48b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ed48b-111">Attributes</span></span>  
 <span data-ttu-id="ed48b-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="ed48b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ed48b-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed48b-113">Child Elements</span></span>  
  
|<span data-ttu-id="ed48b-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed48b-114">Element</span></span>|<span data-ttu-id="ed48b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed48b-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed48b-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="ed48b-116">\<oidEntry></span></span>](oidentry-element.md)|<span data-ttu-id="ed48b-117">Bir ASN.1 OID'yi dost bir isme eşler.</span><span class="sxs-lookup"><span data-stu-id="ed48b-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed48b-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed48b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ed48b-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed48b-119">Element</span></span>|<span data-ttu-id="ed48b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed48b-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ed48b-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ed48b-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ed48b-122">Şifreleme ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ed48b-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="ed48b-123">Öğeyi `cryptographySettings` içerir.</span><span class="sxs-lookup"><span data-stu-id="ed48b-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ed48b-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed48b-124">Example</span></span>  
 <span data-ttu-id="ed48b-125">Aşağıdaki örnek, \*\* \<OIDMap>\*\* elemanının RIPEMD-160 karma algoritması için bir OID eşlemesini içeren bu karma algoritmanın uygulanmasına nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed48b-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed48b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed48b-126">See also</span></span>

- [<span data-ttu-id="ed48b-127">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ed48b-127">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ed48b-128">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ed48b-128">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ed48b-129">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ed48b-129">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ed48b-130">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed48b-130">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="ed48b-131">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="ed48b-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)

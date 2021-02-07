---
description: 'Daha fazla bilgi edinin: <oidMap> öğesi'
title: <oidMap> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: 9a71cc54546f49fcada90a0f9915d44d1fc65e89
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729998"
---
# <a name="oidmap-element"></a><span data-ttu-id="0687f-103">\<oidMap> Öğesi</span><span class="sxs-lookup"><span data-stu-id="0687f-103">\<oidMap> Element</span></span>

<span data-ttu-id="0687f-104">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0687f-104">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="0687f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0687f-105">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0687f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0687f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0687f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0687f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0687f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0687f-108">Attributes</span></span>  

 <span data-ttu-id="0687f-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="0687f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0687f-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0687f-110">Child Elements</span></span>  
  
|<span data-ttu-id="0687f-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="0687f-111">Element</span></span>|<span data-ttu-id="0687f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0687f-112">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="0687f-113">Bir ASN. 1 OID 'yi kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="0687f-113">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0687f-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0687f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0687f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="0687f-115">Element</span></span>|<span data-ttu-id="0687f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0687f-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0687f-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0687f-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="0687f-118">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="0687f-118">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="0687f-119">Öğesini içerir `cryptographySettings` .</span><span class="sxs-lookup"><span data-stu-id="0687f-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0687f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="0687f-120">Example</span></span>  

 <span data-ttu-id="0687f-121">Aşağıdaki örnek, **\<oidMap>** RIPEMD-160 karma algoritması için BIR OID 'nin bu karma algoritmanın bir uygulamasına eşlemesini içeren öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0687f-121">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0687f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0687f-122">See also</span></span>

- [<span data-ttu-id="0687f-123">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="0687f-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0687f-124">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="0687f-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0687f-125">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="0687f-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="0687f-126">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0687f-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="0687f-127">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="0687f-127">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)

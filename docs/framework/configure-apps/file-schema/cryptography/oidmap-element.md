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
ms.openlocfilehash: 6c57810389acbd58e6d2e05277a6f26fa0aac8c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149523"
---
# <a name="oidmap-element"></a><span data-ttu-id="e25ce-102">\<oidMap> Öğesi</span><span class="sxs-lookup"><span data-stu-id="e25ce-102">\<oidMap> Element</span></span>

<span data-ttu-id="e25ce-103">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e25ce-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="e25ce-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e25ce-104">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e25ce-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e25ce-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e25ce-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e25ce-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e25ce-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e25ce-107">Attributes</span></span>  

 <span data-ttu-id="e25ce-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="e25ce-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e25ce-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e25ce-109">Child Elements</span></span>  
  
|<span data-ttu-id="e25ce-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="e25ce-110">Element</span></span>|<span data-ttu-id="e25ce-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e25ce-111">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="e25ce-112">Bir ASN. 1 OID 'yi kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="e25ce-112">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e25ce-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e25ce-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e25ce-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e25ce-114">Element</span></span>|<span data-ttu-id="e25ce-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e25ce-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e25ce-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e25ce-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="e25ce-117">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e25ce-117">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="e25ce-118">Öğesini içerir `cryptographySettings` .</span><span class="sxs-lookup"><span data-stu-id="e25ce-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e25ce-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="e25ce-119">Example</span></span>  

 <span data-ttu-id="e25ce-120">Aşağıdaki örnek, **\<oidMap>** RIPEMD-160 karma algoritması için BIR OID 'nin bu karma algoritmanın bir uygulamasına eşlemesini içeren öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e25ce-120">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e25ce-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e25ce-121">See also</span></span>

- [<span data-ttu-id="e25ce-122">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e25ce-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e25ce-123">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e25ce-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e25ce-124">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e25ce-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="e25ce-125">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e25ce-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="e25ce-126">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="e25ce-126">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)

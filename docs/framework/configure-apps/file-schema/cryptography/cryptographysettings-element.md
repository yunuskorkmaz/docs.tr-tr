---
title: <cryptographySettings> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: fe6de09213c6f980e8eb205a318aae50033b2a84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155238"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="cd21c-102">\<cryptographySettings> Öğesi</span><span class="sxs-lookup"><span data-stu-id="cd21c-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="cd21c-103">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd21c-103">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="cd21c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd21c-104">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd21c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd21c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cd21c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd21c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd21c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cd21c-107">Attributes</span></span>  
 <span data-ttu-id="cd21c-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="cd21c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cd21c-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd21c-109">Child Elements</span></span>  
  
|<span data-ttu-id="cd21c-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd21c-110">Element</span></span>|<span data-ttu-id="cd21c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd21c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="cd21c-112">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cd21c-112">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="cd21c-113">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cd21c-113">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd21c-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd21c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cd21c-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd21c-115">Element</span></span>|<span data-ttu-id="cd21c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd21c-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cd21c-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cd21c-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="cd21c-118">Öğesini içerir `cryptographySettings` .</span><span class="sxs-lookup"><span data-stu-id="cd21c-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cd21c-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd21c-119">Example</span></span>  
 <span data-ttu-id="cd21c-120">Aşağıdaki örnek, **\<cryptographySettings>** öğesinin şifreleme adı eşlemelerini ve OID eşlemelerini içermesi için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd21c-120">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="cd21c-121">Bu örnek, çalışma zamanını <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> bir `MyHashClass` nesne döndüren ve `MyCryptoClass` sınıfı 1.3.36.2.1 nesne tanımlayıcısına eşlenecek şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="cd21c-121">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd21c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd21c-122">See also</span></span>

- [<span data-ttu-id="cd21c-123">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="cd21c-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cd21c-124">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cd21c-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cd21c-125">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="cd21c-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

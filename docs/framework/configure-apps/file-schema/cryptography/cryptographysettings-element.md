---
description: 'Daha fazla bilgi edinin: <cryptographySettings> öğesi'
title: <cryptographySettings> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: afd4fdbc24dfaac60ce24b7a439a8d4d8a9427ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730102"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="0f2f2-103">\<cryptographySettings> Öğesi</span><span class="sxs-lookup"><span data-stu-id="0f2f2-103">\<cryptographySettings> Element</span></span>

<span data-ttu-id="0f2f2-104">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="0f2f2-104">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="0f2f2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0f2f2-105">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f2f2-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f2f2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0f2f2-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f2f2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f2f2-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0f2f2-108">Attributes</span></span>  

 <span data-ttu-id="0f2f2-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="0f2f2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0f2f2-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f2f2-110">Child Elements</span></span>  
  
|<span data-ttu-id="0f2f2-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f2f2-111">Element</span></span>|<span data-ttu-id="0f2f2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f2f2-112">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="0f2f2-113">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0f2f2-113">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="0f2f2-114">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0f2f2-114">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f2f2-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f2f2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0f2f2-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f2f2-116">Element</span></span>|<span data-ttu-id="0f2f2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f2f2-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0f2f2-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0f2f2-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="0f2f2-119">Öğesini içerir `cryptographySettings` .</span><span class="sxs-lookup"><span data-stu-id="0f2f2-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0f2f2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f2f2-120">Example</span></span>  

 <span data-ttu-id="0f2f2-121">Aşağıdaki örnek, **\<cryptographySettings>** öğesinin şifreleme adı eşlemelerini ve OID eşlemelerini içermesi için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f2f2-121">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="0f2f2-122">Bu örnek, çalışma zamanını <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> bir `MyHashClass` nesne döndüren ve `MyCryptoClass` sınıfı 1.3.36.2.1 nesne tanımlayıcısına eşlenecek şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0f2f2-122">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f2f2-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f2f2-123">See also</span></span>

- [<span data-ttu-id="0f2f2-124">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="0f2f2-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0f2f2-125">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="0f2f2-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0f2f2-126">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="0f2f2-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

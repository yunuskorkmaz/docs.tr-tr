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
ms.openlocfilehash: ca0a9a4b37f28eb03f58de4fd9b120cb7e654e0c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088651"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="442d6-102">\<Cryptographyısettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="442d6-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="442d6-103">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="442d6-103">Contains cryptography settings.</span></span>  

<span data-ttu-id="442d6-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="442d6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="442d6-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="442d6-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="442d6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Cryptographyısettings >**</span><span class="sxs-lookup"><span data-stu-id="442d6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="442d6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="442d6-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="442d6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="442d6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="442d6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="442d6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="442d6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="442d6-110">Attributes</span></span>  
 <span data-ttu-id="442d6-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="442d6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="442d6-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="442d6-112">Child Elements</span></span>  
  
|<span data-ttu-id="442d6-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="442d6-113">Element</span></span>|<span data-ttu-id="442d6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="442d6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="442d6-115">cryptoNameMapping > \<</span><span class="sxs-lookup"><span data-stu-id="442d6-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="442d6-116">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="442d6-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="442d6-117">\<Oıdmap ></span><span class="sxs-lookup"><span data-stu-id="442d6-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="442d6-118">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="442d6-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="442d6-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="442d6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="442d6-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="442d6-120">Element</span></span>|<span data-ttu-id="442d6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="442d6-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="442d6-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="442d6-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="442d6-123">`cryptographySettings` öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="442d6-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="442d6-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="442d6-124">Example</span></span>  
 <span data-ttu-id="442d6-125">Aşağıdaki örnek, şifreleme adı eşlemelerini ve OID eşlemelerini içeren **\<Cryptographısettings >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="442d6-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="442d6-126">Bu örnek, <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> bir `MyHashClass` nesnesi döndürmesi ve `MyCryptoClass` sınıfı 1.3.36.2.1 nesne tanımlayıcısına eşlenecek şekilde çalışma zamanını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="442d6-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="442d6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="442d6-127">See also</span></span>

- [<span data-ttu-id="442d6-128">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="442d6-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="442d6-129">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="442d6-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="442d6-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="442d6-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

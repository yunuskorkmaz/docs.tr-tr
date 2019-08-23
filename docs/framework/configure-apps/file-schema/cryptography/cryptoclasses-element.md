---
title: <cryptoClasses> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 87e64ecd79ebc54a669d33550790781c87b5917c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921124"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="7d1a9-102">\<cryptoClasses > öğesi</span><span class="sxs-lookup"><span data-stu-id="7d1a9-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="7d1a9-103">NameEntry > öğesinde kolay bir ada [ \<](nameentry-element.md) eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="7d1a9-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="7d1a9-104">\<configuration></span></span>  
<span data-ttu-id="7d1a9-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="7d1a9-105">\<mscorlib></span></span>  
<span data-ttu-id="7d1a9-106">\<Cryptographyısettings ></span><span class="sxs-lookup"><span data-stu-id="7d1a9-106">\<cryptographySettings></span></span>  
<span data-ttu-id="7d1a9-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="7d1a9-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="7d1a9-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="7d1a9-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d1a9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d1a9-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d1a9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d1a9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7d1a9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d1a9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d1a9-112">Attributes</span></span>  
 <span data-ttu-id="7d1a9-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d1a9-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d1a9-114">Child Elements</span></span>  
  
|<span data-ttu-id="7d1a9-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d1a9-115">Element</span></span>|<span data-ttu-id="7d1a9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d1a9-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d1a9-117">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="7d1a9-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="7d1a9-118">NameEntry > öğesinde kolay bir ad  **\<** ile eşleşen bir şifreleme sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d1a9-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d1a9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7d1a9-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d1a9-120">Element</span></span>|<span data-ttu-id="7d1a9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d1a9-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7d1a9-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="7d1a9-123">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="7d1a9-124">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="7d1a9-125">`cryptographySettings` Öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d1a9-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d1a9-126">Example</span></span>  
 <span data-ttu-id="7d1a9-127">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için  **\<CryptoClass >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="7d1a9-128">Daha sonra "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> dizesini yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d1a9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d1a9-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="7d1a9-130">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="7d1a9-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7d1a9-131">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7d1a9-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7d1a9-132">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="7d1a9-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="7d1a9-133">System. Security. Cryptography. CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="7d1a9-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="7d1a9-134">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7d1a9-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

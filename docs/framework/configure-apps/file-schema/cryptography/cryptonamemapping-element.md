---
description: 'Daha fazla bilgi edinin: <cryptoNameMapping> öğesi'
title: <cryptoNameMapping> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: b7dac458fdda0aabf36df96b43dca1529ffe4743
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698914"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="efcea-103">\<cryptoNameMapping> Öğesi</span><span class="sxs-lookup"><span data-stu-id="efcea-103">\<cryptoNameMapping> Element</span></span>

<span data-ttu-id="efcea-104">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="efcea-104">Contains mappings of classes to friendly names.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**

## <a name="syntax"></a><span data-ttu-id="efcea-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="efcea-105">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efcea-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="efcea-106">Attributes and Elements</span></span>  

 <span data-ttu-id="efcea-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="efcea-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efcea-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="efcea-108">Attributes</span></span>  

 <span data-ttu-id="efcea-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="efcea-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="efcea-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="efcea-110">Child Elements</span></span>  
  
|<span data-ttu-id="efcea-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="efcea-111">Element</span></span>|<span data-ttu-id="efcea-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efcea-112">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="efcea-113">Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="efcea-113">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="efcea-114">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="efcea-114">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efcea-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="efcea-115">Parent Elements</span></span>  
  
|<span data-ttu-id="efcea-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="efcea-116">Element</span></span>|<span data-ttu-id="efcea-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efcea-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="efcea-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="efcea-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="efcea-119">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="efcea-119">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="efcea-120">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="efcea-120">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="efcea-121">Öğesini içerir \<cryptographySettings> .</span><span class="sxs-lookup"><span data-stu-id="efcea-121">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="efcea-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="efcea-122">Example</span></span>  

 <span data-ttu-id="efcea-123">Aşağıdaki örnek, **\<cryptoNameMapping>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="efcea-123">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="efcea-124">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efcea-124">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="efcea-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efcea-125">See also</span></span>

- [<span data-ttu-id="efcea-126">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="efcea-126">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="efcea-127">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="efcea-127">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="efcea-128">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="efcea-128">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="efcea-129">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="efcea-129">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

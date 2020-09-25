---
title: <cryptoNameMapping> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: 9ffae33a3c8a06d6cfcabf5a58b7d72baeda79c5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201804"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="1d526-102">\<cryptoNameMapping> Öğesi</span><span class="sxs-lookup"><span data-stu-id="1d526-102">\<cryptoNameMapping> Element</span></span>

<span data-ttu-id="1d526-103">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1d526-103">Contains mappings of classes to friendly names.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**

## <a name="syntax"></a><span data-ttu-id="1d526-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1d526-104">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d526-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d526-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1d526-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d526-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d526-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d526-107">Attributes</span></span>  

 <span data-ttu-id="1d526-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d526-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d526-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d526-109">Child Elements</span></span>  
  
|<span data-ttu-id="1d526-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d526-110">Element</span></span>|<span data-ttu-id="1d526-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d526-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="1d526-112">Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="1d526-112">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="1d526-113">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1d526-113">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d526-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d526-114">Parent Elements</span></span>  
  
|<span data-ttu-id="1d526-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d526-115">Element</span></span>|<span data-ttu-id="1d526-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d526-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1d526-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1d526-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="1d526-118">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1d526-118">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="1d526-119">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1d526-119">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="1d526-120">Öğesini içerir \<cryptographySettings> .</span><span class="sxs-lookup"><span data-stu-id="1d526-120">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d526-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d526-121">Example</span></span>  

 <span data-ttu-id="1d526-122">Aşağıdaki örnek, **\<cryptoNameMapping>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d526-122">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="1d526-123">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d526-123">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d526-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d526-124">See also</span></span>

- [<span data-ttu-id="1d526-125">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="1d526-125">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1d526-126">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="1d526-126">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1d526-127">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1d526-127">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="1d526-128">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1d526-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

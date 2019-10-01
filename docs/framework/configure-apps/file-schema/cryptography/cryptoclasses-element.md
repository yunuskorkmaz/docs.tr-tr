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
ms.openlocfilehash: 89f1d89ea397794e366b53205ac23b94d7892869
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699748"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="01813-102">\<cryptoClasses > öğesi</span><span class="sxs-lookup"><span data-stu-id="01813-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="01813-103">[@No__t-1nameEntry >](nameentry-element.md) öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="01813-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="01813-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="01813-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="01813-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="01813-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="01813-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<Cryptographrivsettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="01813-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="01813-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="01813-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="01813-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="01813-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01813-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01813-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01813-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="01813-110">Attributes and Elements</span></span>  
 <span data-ttu-id="01813-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="01813-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01813-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="01813-112">Attributes</span></span>  
 <span data-ttu-id="01813-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="01813-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01813-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="01813-114">Child Elements</span></span>  
  
|<span data-ttu-id="01813-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="01813-115">Element</span></span>|<span data-ttu-id="01813-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01813-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01813-117">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="01813-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="01813-118">**@No__t-1nameEntry >** öğesinde kolay bir adla eşleşen bir şifreleme sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="01813-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01813-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="01813-119">Parent Elements</span></span>  
  
|<span data-ttu-id="01813-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="01813-120">Element</span></span>|<span data-ttu-id="01813-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01813-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="01813-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="01813-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="01813-123">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="01813-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="01813-124">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="01813-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="01813-125">@No__t-0 öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="01813-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="01813-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="01813-126">Example</span></span>  
 <span data-ttu-id="01813-127">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için **\<cryptoClass >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="01813-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="01813-128">Daha sonra, "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak `MyCryptoRSAClass` nesnesini döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01813-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01813-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01813-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="01813-130">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="01813-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="01813-131">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="01813-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="01813-132">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="01813-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="01813-133">System. Security. Cryptography. CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="01813-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="01813-134">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="01813-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

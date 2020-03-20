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
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155252"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="2ff7f-102">\<cryptoClasses> Öğesi</span><span class="sxs-lookup"><span data-stu-id="2ff7f-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="2ff7f-103">[ \<NameEntry>](nameentry-element.md) öğesinde dost bir ada eşleme olan şifreleme sınıflarının listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="2ff7f-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="2ff7f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2ff7f-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2ff7f-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="2ff7f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<şifrelemeAyarlar>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="2ff7f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="2ff7f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="2ff7f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="2ff7f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="2ff7f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff7f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ff7f-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ff7f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ff7f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2ff7f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ff7f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2ff7f-112">Attributes</span></span>  
 <span data-ttu-id="2ff7f-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2ff7f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ff7f-114">Child Elements</span></span>  
  
|<span data-ttu-id="2ff7f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="2ff7f-115">Element</span></span>|<span data-ttu-id="2ff7f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ff7f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ff7f-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="2ff7f-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="2ff7f-118">\*\* \<Entry>\*\* öğesinde dost bir ada eşleme olan bir şifreleme sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ff7f-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ff7f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2ff7f-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="2ff7f-120">Element</span></span>|<span data-ttu-id="2ff7f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ff7f-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2ff7f-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="2ff7f-123">Şifreleme ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="2ff7f-124">Sınıfların dost adlara eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="2ff7f-125">Öğeyi `cryptographySettings` içerir.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2ff7f-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ff7f-126">Example</span></span>  
 <span data-ttu-id="2ff7f-127">Aşağıdaki örnek, \*\* \<şifreleme\*\* sınıfına başvurmak ve çalışma süresini yapılandırmak için cryptoClass>öğesini nasıl kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="2ff7f-128">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yönteme <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> geçirebilir ve `MyCryptoRSAClass` bir nesneyi döndürmek için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ff7f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ff7f-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="2ff7f-130">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="2ff7f-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2ff7f-131">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2ff7f-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2ff7f-132">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="2ff7f-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="2ff7f-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="2ff7f-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="2ff7f-134">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2ff7f-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

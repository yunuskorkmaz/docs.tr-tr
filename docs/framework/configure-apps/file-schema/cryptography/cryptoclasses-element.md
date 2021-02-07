---
description: 'Daha fazla bilgi edinin: <cryptoClasses> öğesi'
title: <cryptoClasses> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 5ae9b85d477a71eedc3c8b32bba2b4639414163c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698927"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="f72ab-103">\<cryptoClasses> Öğesi</span><span class="sxs-lookup"><span data-stu-id="f72ab-103">\<cryptoClasses> Element</span></span>

<span data-ttu-id="f72ab-104">Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir [\<nameEntry>](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="f72ab-104">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="f72ab-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f72ab-105">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f72ab-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f72ab-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f72ab-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f72ab-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f72ab-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f72ab-108">Attributes</span></span>  

 <span data-ttu-id="f72ab-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="f72ab-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f72ab-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f72ab-110">Child Elements</span></span>  
  
|<span data-ttu-id="f72ab-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="f72ab-111">Element</span></span>|<span data-ttu-id="f72ab-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f72ab-112">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="f72ab-113">Öğesinde bir kolay ad ile eşleşen bir şifreleme sınıfı içerir **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="f72ab-113">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f72ab-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f72ab-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f72ab-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="f72ab-115">Element</span></span>|<span data-ttu-id="f72ab-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f72ab-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f72ab-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f72ab-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="f72ab-118">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-118">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="f72ab-119">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-119">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="f72ab-120">Öğesini içerir `cryptographySettings` .</span><span class="sxs-lookup"><span data-stu-id="f72ab-120">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f72ab-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="f72ab-121">Example</span></span>  

 <span data-ttu-id="f72ab-122">Aşağıdaki örnek, **\<cryptoClass>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-122">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="f72ab-123">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f72ab-123">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f72ab-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f72ab-124">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="f72ab-125">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="f72ab-125">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f72ab-126">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="f72ab-126">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f72ab-127">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="f72ab-127">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="f72ab-128">System. Security. Cryptography. CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="f72ab-128">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="f72ab-129">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f72ab-129">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

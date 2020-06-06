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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155252"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="ee3e0-102">\<cryptoClasses> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ee3e0-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="ee3e0-103">Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir [\<nameEntry>](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ee3e0-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="ee3e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee3e0-104">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee3e0-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee3e0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ee3e0-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee3e0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee3e0-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee3e0-107">Attributes</span></span>  
 <span data-ttu-id="ee3e0-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee3e0-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee3e0-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee3e0-109">Child Elements</span></span>  
  
|<span data-ttu-id="ee3e0-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee3e0-110">Element</span></span>|<span data-ttu-id="ee3e0-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee3e0-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="ee3e0-112">Öğesinde bir kolay ad ile eşleşen bir şifreleme sınıfı içerir **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="ee3e0-112">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee3e0-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee3e0-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ee3e0-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee3e0-114">Element</span></span>|<span data-ttu-id="ee3e0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee3e0-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ee3e0-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ee3e0-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ee3e0-117">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ee3e0-117">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ee3e0-118">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ee3e0-118">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ee3e0-119">Öğesini içerir `cryptographySettings` .</span><span class="sxs-lookup"><span data-stu-id="ee3e0-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee3e0-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee3e0-120">Example</span></span>  
 <span data-ttu-id="ee3e0-121">Aşağıdaki örnek, **\<cryptoClass>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee3e0-121">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ee3e0-122">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee3e0-122">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee3e0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee3e0-123">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="ee3e0-124">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ee3e0-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ee3e0-125">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ee3e0-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ee3e0-126">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ee3e0-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ee3e0-127">System. Security. Cryptography. CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="ee3e0-127">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="ee3e0-128">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ee3e0-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

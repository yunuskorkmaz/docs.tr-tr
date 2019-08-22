---
title: Şifreleme Ayarları için <mscorlib> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 312db8ea5ae4b66fd00faad1b788eac0356aeaa7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659596"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="c1cbc-102">\<Şifreleme ayarları için mscorlib > öğesi</span><span class="sxs-lookup"><span data-stu-id="c1cbc-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="c1cbc-103">Cryptographrivsettings > öğesini içerir. [ \<](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1cbc-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="c1cbc-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c1cbc-104">\<configuration></span></span>  
<span data-ttu-id="c1cbc-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="c1cbc-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1cbc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1cbc-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1cbc-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1cbc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c1cbc-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1cbc-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1cbc-109">Attributes</span></span>  
 <span data-ttu-id="c1cbc-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c1cbc-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1cbc-111">Child Elements</span></span>  
  
|<span data-ttu-id="c1cbc-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1cbc-112">Element</span></span>|<span data-ttu-id="c1cbc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1cbc-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="c1cbc-114">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1cbc-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1cbc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c1cbc-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1cbc-116">Element</span></span>|<span data-ttu-id="c1cbc-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1cbc-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c1cbc-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c1cbc-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1cbc-119">Example</span></span>  
 <span data-ttu-id="c1cbc-120">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için  **\<mscorlib >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="c1cbc-121">Daha sonra "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> dizesini yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1cbc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="c1cbc-123">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="c1cbc-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c1cbc-124">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c1cbc-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c1cbc-125">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="c1cbc-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="c1cbc-126">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c1cbc-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

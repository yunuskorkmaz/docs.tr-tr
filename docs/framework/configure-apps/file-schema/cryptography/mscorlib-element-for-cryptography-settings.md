---
title: '&lt;mscorlib&gt; öğesi için şifreleme ayarları'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: a067f1f2793d98c51304269c7a37754031940824
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084165"
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="d6d62-102">&lt;mscorlib&gt; öğesi için şifreleme ayarları</span><span class="sxs-lookup"><span data-stu-id="d6d62-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="d6d62-103">İçeren [ \<cryptographySettings > öğesi](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="d6d62-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="d6d62-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d6d62-104">\<configuration></span></span>  
<span data-ttu-id="d6d62-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="d6d62-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6d62-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6d62-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6d62-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6d62-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d6d62-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d6d62-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6d62-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d6d62-109">Attributes</span></span>  
 <span data-ttu-id="d6d62-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="d6d62-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6d62-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6d62-111">Child Elements</span></span>  
  
|<span data-ttu-id="d6d62-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="d6d62-112">Element</span></span>|<span data-ttu-id="d6d62-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6d62-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="d6d62-114">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d6d62-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6d62-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6d62-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d6d62-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d6d62-116">Element</span></span>|<span data-ttu-id="d6d62-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6d62-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d6d62-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d6d62-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d6d62-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6d62-119">Example</span></span>  
 <span data-ttu-id="d6d62-120">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<mscorlib >** bir şifreleme sınıfına başvurmak için ve çalışma zamanı yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="d6d62-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="d6d62-121">Ardından "RSA" dize iletebileceğiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemini <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesne.</span><span class="sxs-lookup"><span data-stu-id="d6d62-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6d62-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6d62-122">See also</span></span>
- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="d6d62-123">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d6d62-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="d6d62-124">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d6d62-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="d6d62-125">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d6d62-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="d6d62-126">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d6d62-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

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
ms.openlocfilehash: 1788205997d0dc49df172c9dfe48faceb8fc3290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201791"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="5b4ca-102">Şifreleme Ayarları için \<mscorlib> Öğesi</span><span class="sxs-lookup"><span data-stu-id="5b4ca-102">\<mscorlib> Element for Cryptography Settings</span></span>

<span data-ttu-id="5b4ca-103">[ \<cryptographySettings> Öğesini](cryptographysettings-element.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="5b4ca-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="5b4ca-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b4ca-104">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b4ca-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b4ca-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5b4ca-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b4ca-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b4ca-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b4ca-107">Attributes</span></span>  

 <span data-ttu-id="5b4ca-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="5b4ca-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b4ca-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b4ca-109">Child Elements</span></span>  
  
|<span data-ttu-id="5b4ca-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b4ca-110">Element</span></span>|<span data-ttu-id="5b4ca-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b4ca-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="5b4ca-112">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5b4ca-112">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b4ca-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b4ca-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5b4ca-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b4ca-114">Element</span></span>|<span data-ttu-id="5b4ca-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b4ca-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5b4ca-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5b4ca-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b4ca-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b4ca-117">Example</span></span>  

 <span data-ttu-id="5b4ca-118">Aşağıdaki örnek, **\<mscorlib>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b4ca-118">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="5b4ca-119">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b4ca-119">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b4ca-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b4ca-120">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="5b4ca-121">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="5b4ca-121">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5b4ca-122">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="5b4ca-122">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5b4ca-123">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5b4ca-123">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="5b4ca-124">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5b4ca-124">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

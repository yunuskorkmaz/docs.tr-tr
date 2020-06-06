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
ms.openlocfilehash: d1d805f7154c18dba2dcd4eb7228cc200d8da811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155187"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="7e36f-102">Şifreleme Ayarları için \<mscorlib> Öğesi</span><span class="sxs-lookup"><span data-stu-id="7e36f-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="7e36f-103">[ \<cryptographySettings> Öğesini](cryptographysettings-element.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="7e36f-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="7e36f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e36f-104">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e36f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e36f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7e36f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e36f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e36f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7e36f-107">Attributes</span></span>  
 <span data-ttu-id="7e36f-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="7e36f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7e36f-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e36f-109">Child Elements</span></span>  
  
|<span data-ttu-id="7e36f-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e36f-110">Element</span></span>|<span data-ttu-id="7e36f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e36f-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="7e36f-112">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7e36f-112">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e36f-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e36f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="7e36f-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e36f-114">Element</span></span>|<span data-ttu-id="7e36f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e36f-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7e36f-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7e36f-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7e36f-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e36f-117">Example</span></span>  
 <span data-ttu-id="7e36f-118">Aşağıdaki örnek, **\<mscorlib>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e36f-118">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="7e36f-119">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e36f-119">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e36f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e36f-120">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="7e36f-121">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="7e36f-121">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7e36f-122">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7e36f-122">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7e36f-123">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="7e36f-123">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="7e36f-124">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7e36f-124">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

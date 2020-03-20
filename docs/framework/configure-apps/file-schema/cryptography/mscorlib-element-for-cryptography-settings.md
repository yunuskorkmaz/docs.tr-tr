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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155187"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="ff5ae-102">\<şifreleme ayarları için mscorlib> Elemanı</span><span class="sxs-lookup"><span data-stu-id="ff5ae-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="ff5ae-103">Şifreleme [ \<Ayarlar> öğesini](cryptographysettings-element.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[<span data-ttu-id="ff5ae-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="ff5ae-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ff5ae-105">&nbsp;&nbsp;**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="ff5ae-105">&nbsp;&nbsp;**\<mscorlib>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff5ae-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff5ae-106">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff5ae-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff5ae-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ff5ae-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff5ae-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ff5ae-109">Attributes</span></span>  
 <span data-ttu-id="ff5ae-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ff5ae-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff5ae-111">Child Elements</span></span>  
  
|<span data-ttu-id="ff5ae-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff5ae-112">Element</span></span>|<span data-ttu-id="ff5ae-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff5ae-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="ff5ae-114">Şifreleme ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff5ae-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff5ae-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ff5ae-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff5ae-116">Element</span></span>|<span data-ttu-id="ff5ae-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff5ae-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ff5ae-118">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff5ae-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff5ae-119">Example</span></span>  
 <span data-ttu-id="ff5ae-120">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma süresini yapılandırmak için \*\* \<mscorlib>\*\* öğesini nasıl kullanacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ff5ae-121">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yönteme <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> geçirebilir ve `MyCryptoRSAClass` bir nesneyi döndürmek için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff5ae-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="ff5ae-123">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ff5ae-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ff5ae-124">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ff5ae-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ff5ae-125">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ff5ae-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ff5ae-126">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ff5ae-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

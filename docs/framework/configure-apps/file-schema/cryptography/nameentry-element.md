---
title: <nameEntry> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: a339638587f8b544bbc1b0073553f6232ce09694
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71699774"
---
# <a name="nameentry-element"></a><span data-ttu-id="7bd38-102">\<nameEntry> Öğesi</span><span class="sxs-lookup"><span data-stu-id="7bd38-102">\<nameEntry> Element</span></span>
<span data-ttu-id="7bd38-103">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7bd38-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="7bd38-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bd38-104">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bd38-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bd38-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7bd38-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bd38-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bd38-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7bd38-107">Attributes</span></span>  
  
|<span data-ttu-id="7bd38-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7bd38-108">Attribute</span></span>|<span data-ttu-id="7bd38-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bd38-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bd38-110">**ada**</span><span class="sxs-lookup"><span data-stu-id="7bd38-110">**name**</span></span>|<span data-ttu-id="7bd38-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7bd38-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="7bd38-112">Şifreleme sınıfının uyguladığı algoritmanın kolay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bd38-112">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="7bd38-113">**sınıfı**</span><span class="sxs-lookup"><span data-stu-id="7bd38-113">**class**</span></span>|<span data-ttu-id="7bd38-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7bd38-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="7bd38-115">Öğesindeki **Name** özniteliği için değeri belirtir [\<cryptoClass>](cryptoclass-element.md) .</span><span class="sxs-lookup"><span data-stu-id="7bd38-115">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bd38-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bd38-116">Child Elements</span></span>  
 <span data-ttu-id="7bd38-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7bd38-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bd38-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bd38-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7bd38-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7bd38-119">Element</span></span>|<span data-ttu-id="7bd38-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bd38-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7bd38-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7bd38-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="7bd38-122">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bd38-122">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bd38-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bd38-123">Remarks</span></span>  
 <span data-ttu-id="7bd38-124">**Ad** özniteliği ad alanında bulunan soyut sınıflardan birinin adı olabilir <xref:System.Security.Cryptography> .</span><span class="sxs-lookup"><span data-stu-id="7bd38-124">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="7bd38-125">Bir soyut şifreleme sınıfında **Create** yöntemini çağırdığınızda, soyut sınıf adı <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7bd38-125">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="7bd38-126">**CreateFromName** , **sınıf** özniteliği tarafından belirtilen türün bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bd38-126">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="7bd38-127">**Ad** özniteliği RSA gibi kısa bir addır, **CreateFromName** metodunu çağırırken bu adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bd38-127">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bd38-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bd38-128">Example</span></span>  
 <span data-ttu-id="7bd38-129">Aşağıdaki örnek, **\<nameEntry>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bd38-129">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="7bd38-130">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bd38-130">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7bd38-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bd38-131">See also</span></span>

- [<span data-ttu-id="7bd38-132">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="7bd38-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7bd38-133">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7bd38-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7bd38-134">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="7bd38-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="7bd38-135">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7bd38-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

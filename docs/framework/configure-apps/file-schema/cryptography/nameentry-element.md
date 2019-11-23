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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699774"
---
# <a name="nameentry-element"></a><span data-ttu-id="ac997-102">\<nameEntry > öğesi</span><span class="sxs-lookup"><span data-stu-id="ac997-102">\<nameEntry> Element</span></span>
<span data-ttu-id="ac997-103">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ac997-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[<span data-ttu-id="ac997-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="ac997-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ac997-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ac997-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="ac997-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Cryptographyısettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="ac997-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="ac997-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="ac997-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="ac997-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="ac997-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac997-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac997-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac997-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac997-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ac997-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac997-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac997-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ac997-112">Attributes</span></span>  
  
|<span data-ttu-id="ac997-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ac997-113">Attribute</span></span>|<span data-ttu-id="ac997-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac997-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac997-115">**name**</span><span class="sxs-lookup"><span data-stu-id="ac997-115">**name**</span></span>|<span data-ttu-id="ac997-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ac997-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac997-117">Şifreleme sınıfının uyguladığı algoritmanın kolay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac997-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="ac997-118">**class**</span><span class="sxs-lookup"><span data-stu-id="ac997-118">**class**</span></span>|<span data-ttu-id="ac997-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ac997-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac997-120">[\<cryptoClass >](cryptoclass-element.md) öğesindeki **Name** özniteliğinin değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac997-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac997-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac997-121">Child Elements</span></span>  
 <span data-ttu-id="ac997-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="ac997-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac997-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac997-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ac997-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac997-124">Element</span></span>|<span data-ttu-id="ac997-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac997-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ac997-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ac997-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="ac997-127">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac997-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac997-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac997-128">Remarks</span></span>  
 <span data-ttu-id="ac997-129">**Name** özniteliği, <xref:System.Security.Cryptography> ad alanında bulunan soyut sınıflardan birinin adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac997-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="ac997-130">Bir soyut şifreleme sınıfında **Create** yöntemini çağırdığınızda, soyut sınıf adı <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ac997-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="ac997-131">**CreateFromName** , **sınıf** özniteliği tarafından belirtilen türün bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac997-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="ac997-132">**Ad** özniteliği RSA gibi kısa bir addır, **CreateFromName** metodunu çağırırken bu adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac997-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac997-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac997-133">Example</span></span>  
 <span data-ttu-id="ac997-134">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için **\<nameEntry >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac997-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ac997-135">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve bir `MyCryptoRSAClass` nesnesi döndürmek için <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac997-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac997-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac997-136">See also</span></span>

- [<span data-ttu-id="ac997-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ac997-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ac997-138">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ac997-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ac997-139">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ac997-139">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ac997-140">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ac997-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

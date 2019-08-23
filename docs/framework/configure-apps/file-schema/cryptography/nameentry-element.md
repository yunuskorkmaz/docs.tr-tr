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
ms.openlocfilehash: d8f4d4aa9c80990cdf858da9fcdf6465438866cf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927570"
---
# <a name="nameentry-element"></a><span data-ttu-id="cf720-102">\<nameEntry > öğesi</span><span class="sxs-lookup"><span data-stu-id="cf720-102">\<nameEntry> Element</span></span>
<span data-ttu-id="cf720-103">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cf720-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="cf720-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="cf720-104">\<configuration></span></span>  
<span data-ttu-id="cf720-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="cf720-105">\<mscorlib></span></span>  
<span data-ttu-id="cf720-106">\<Cryptographyısettings ></span><span class="sxs-lookup"><span data-stu-id="cf720-106">\<cryptographySettings></span></span>  
<span data-ttu-id="cf720-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="cf720-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="cf720-108">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="cf720-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf720-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf720-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf720-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf720-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cf720-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf720-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf720-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cf720-112">Attributes</span></span>  
  
|<span data-ttu-id="cf720-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cf720-113">Attribute</span></span>|<span data-ttu-id="cf720-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf720-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf720-115">**name**</span><span class="sxs-lookup"><span data-stu-id="cf720-115">**name**</span></span>|<span data-ttu-id="cf720-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cf720-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="cf720-117">Şifreleme sınıfının uyguladığı algoritmanın kolay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf720-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="cf720-118">**class**</span><span class="sxs-lookup"><span data-stu-id="cf720-118">**class**</span></span>|<span data-ttu-id="cf720-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cf720-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="cf720-120">CryptoClass > öğesindeki **Name** özniteliğinin [değerini belirtir. \<](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf720-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf720-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf720-121">Child Elements</span></span>  
 <span data-ttu-id="cf720-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="cf720-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf720-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf720-123">Parent Elements</span></span>  
  
|<span data-ttu-id="cf720-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="cf720-124">Element</span></span>|<span data-ttu-id="cf720-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf720-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cf720-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cf720-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="cf720-127">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf720-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf720-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf720-128">Remarks</span></span>  
 <span data-ttu-id="cf720-129">**Ad** özniteliği ad <xref:System.Security.Cryptography> alanında bulunan soyut sınıflardan birinin adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf720-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="cf720-130">Bir soyut şifreleme sınıfında **Create** yöntemini çağırdığınızda, soyut sınıf adı <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cf720-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="cf720-131">**CreateFromName** , **sınıf** özniteliği tarafından belirtilen türün bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf720-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="cf720-132">**Ad** özniteliği RSA gibi kısa bir addır, **CreateFromName** metodunu çağırırken bu adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf720-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf720-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf720-133">Example</span></span>  
 <span data-ttu-id="cf720-134">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için  **\<nameEntry >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf720-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="cf720-135">Daha sonra "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> dizesini yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf720-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf720-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf720-136">See also</span></span>

- [<span data-ttu-id="cf720-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="cf720-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cf720-138">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cf720-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cf720-139">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="cf720-139">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="cf720-140">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cf720-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

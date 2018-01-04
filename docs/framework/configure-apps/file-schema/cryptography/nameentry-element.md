---
title: "&lt;nameEntry&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7c9a4b4532d98b7dfc2484dab1bb57e5a26fa392
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnameentrygt-element"></a><span data-ttu-id="39853-102">&lt;nameEntry&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="39853-102">&lt;nameEntry&gt; Element</span></span>
<span data-ttu-id="39853-103">Çok sayıda kolay adlar sağlamak bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="39853-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="39853-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="39853-104">\<configuration></span></span>  
<span data-ttu-id="39853-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="39853-105">\<mscorlib></span></span>  
<span data-ttu-id="39853-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="39853-106">\<cryptographySettings></span></span>  
<span data-ttu-id="39853-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="39853-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="39853-108">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="39853-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39853-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39853-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39853-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39853-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39853-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39853-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39853-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39853-112">Attributes</span></span>  
  
|<span data-ttu-id="39853-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39853-113">Attribute</span></span>|<span data-ttu-id="39853-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39853-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39853-115">**adı**</span><span class="sxs-lookup"><span data-stu-id="39853-115">**name**</span></span>|<span data-ttu-id="39853-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="39853-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="39853-117">Şifreleme sınıfı uygulayan algoritması kolay adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="39853-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="39853-118">**class**</span><span class="sxs-lookup"><span data-stu-id="39853-118">**class**</span></span>|<span data-ttu-id="39853-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="39853-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="39853-120">Değerini belirtir **adı** özniteliğini [ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="39853-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39853-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39853-121">Child Elements</span></span>  
 <span data-ttu-id="39853-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="39853-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39853-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39853-123">Parent Elements</span></span>  
  
|<span data-ttu-id="39853-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="39853-124">Element</span></span>|<span data-ttu-id="39853-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39853-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="39853-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="39853-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="39853-127">ASP.NET yapılandırma bölümü için kök öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="39853-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39853-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39853-128">Remarks</span></span>  
 <span data-ttu-id="39853-129">**Adı** özniteliği bulunan soyut sınıflar birinin adını olabilir <xref:System.Security.Cryptography> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="39853-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="39853-130">Çağırdığınızda **oluşturma** yöntemi bir soyut şifreleme sınıf üzerinde soyut sınıf adı için geçirilir <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="39853-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="39853-131">**CreateFromName** tarafından gösterilen türünün bir örneği döndürür **sınıfı** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="39853-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="39853-132">Varsa **adı** özniteliktir kısa bir ad RSA gibi bu adı çağrılırken kullanabilirsiniz **CreateFromName** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="39853-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39853-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="39853-133">Example</span></span>  
 <span data-ttu-id="39853-134">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<nameEntry >** öğesi bir şifreleme sınıf başvurusu ve çalışma zamanı yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="39853-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="39853-135">Ardından "RSA" dizesi geçirebilirsiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemi ve kullanım <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="39853-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39853-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39853-136">See Also</span></span>  
 [<span data-ttu-id="39853-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="39853-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="39853-138">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="39853-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="39853-139">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="39853-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="39853-140">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="39853-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

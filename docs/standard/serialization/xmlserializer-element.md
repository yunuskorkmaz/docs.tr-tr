---
title: "&lt;xmlSerializer&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17e4fcd1b471a5197f2e6a30bad10cbdbe22f216
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltxmlserializergt-element"></a><span data-ttu-id="c9536-102">&lt;xmlSerializer&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="c9536-102">&lt;xmlSerializer&gt; Element</span></span>
<span data-ttu-id="c9536-103">Belirtir ilerleme durumunu ek bir denetim olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> yapılır.</span><span class="sxs-lookup"><span data-stu-id="c9536-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="c9536-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c9536-104">\<configuration></span></span>  
<span data-ttu-id="c9536-105">\<dizileştirme mekanizmasını System.xml.Serialization ></span><span class="sxs-lookup"><span data-stu-id="c9536-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9536-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9536-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9536-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9536-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c9536-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9536-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9536-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9536-109">Attributes</span></span>  
  
|<span data-ttu-id="c9536-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9536-110">Attribute</span></span>|<span data-ttu-id="c9536-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9536-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9536-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="c9536-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="c9536-113">Belirtir olup olmadığını ilerleme durumunu <xref:System.Xml.Serialization.XmlSerializer> denetlenir.</span><span class="sxs-lookup"><span data-stu-id="c9536-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="c9536-114">Özniteliği "true" veya "false" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9536-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="c9536-115">Varsayılan değer "true" ise.</span><span class="sxs-lookup"><span data-stu-id="c9536-115">The default is "true".</span></span>|  
|<span data-ttu-id="c9536-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="c9536-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="c9536-117">Belirtir olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> C# kod bir dosyaya yazmak ve sonra da bir derlemeye derlemek tarafından derlemeleri oluşturan eski serileştirme oluşturma kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9536-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="c9536-118">Varsayılan değer **false**.</span><span class="sxs-lookup"><span data-stu-id="c9536-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9536-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9536-119">Child Elements</span></span>  
 <span data-ttu-id="c9536-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9536-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9536-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9536-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c9536-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9536-122">Element</span></span>|<span data-ttu-id="c9536-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9536-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9536-124">\<dizileştirme mekanizmasını System.xml.Serialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="c9536-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="c9536-125">İçin yapılandırma ayarlarını içeren <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c9536-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9536-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9536-126">Remarks</span></span>  
 <span data-ttu-id="c9536-127">Varsayılan olarak, <xref:System.Xml.Serialization.XmlSerializer> güvenilmeyen verileri işlenirken ek bir olası hizmet reddi saldırılarına karşı güvenliği katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9536-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="c9536-128">Bunu seri durumundan çıkarma sırasında sonsuz döngü algılamak deneyerek yapar.</span><span class="sxs-lookup"><span data-stu-id="c9536-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="c9536-129">Bir koşul algılanırsa, aşağıdaki iletisiyle bir özel durum: "İç hata: temel alınan akışta seri durumdan çıkarma başarısız oldu."</span><span class="sxs-lookup"><span data-stu-id="c9536-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="c9536-130">Bu iletiyi alan değil gerekmeyen gösteren bir saldırı hizmet reddi devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="c9536-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="c9536-131">Bazı ender durumlarda, yanlış Pozitif sonsuz döngü algılama mekanizması oluşturur ve yasal gelen ileti için özel durum.</span><span class="sxs-lookup"><span data-stu-id="c9536-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="c9536-132">Belirli uygulamanızda bu ek koruma katmanı tarafından yasal iletileri reddediliyor bulursanız, ayarlamak **checkDeserializeAdvances** özniteliği "false".</span><span class="sxs-lookup"><span data-stu-id="c9536-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9536-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9536-133">Example</span></span>  
 <span data-ttu-id="c9536-134">Aşağıdaki örnek kod **checkDeserializeAdvances** özniteliği "false".</span><span class="sxs-lookup"><span data-stu-id="c9536-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9536-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9536-135">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="c9536-136">\<dizileştirme mekanizmasını System.xml.Serialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="c9536-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="c9536-137">XML ve SOAP seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="c9536-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)

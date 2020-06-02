---
title: <xmlSerializer> Öğesi
description: <xmlSerializer>Öğesi XmlSerializer 'ın ilerleme durumunun gerçekleştirilip yapılmadığını belirtir.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 667d59f7eb0d1c7682afcdda584cc5b0ca2da802
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288933"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="65b6e-103">\<xmlSerializer> Öğesi</span><span class="sxs-lookup"><span data-stu-id="65b6e-103">\<xmlSerializer> Element</span></span>
<span data-ttu-id="65b6e-104">Belirtir ilerleme durumunu ek bir denetim olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> yapılır.</span><span class="sxs-lookup"><span data-stu-id="65b6e-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a><span data-ttu-id="65b6e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65b6e-105">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65b6e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="65b6e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="65b6e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="65b6e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65b6e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="65b6e-108">Attributes</span></span>  
  
|<span data-ttu-id="65b6e-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="65b6e-109">Attribute</span></span>|<span data-ttu-id="65b6e-110">Description</span><span class="sxs-lookup"><span data-stu-id="65b6e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65b6e-111">**Checkdeserializeavanslar**</span><span class="sxs-lookup"><span data-stu-id="65b6e-111">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="65b6e-112">Belirtir olup olmadığını ilerleme durumunu <xref:System.Xml.Serialization.XmlSerializer> denetlenir.</span><span class="sxs-lookup"><span data-stu-id="65b6e-112">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="65b6e-113">Özniteliği "true" veya "false" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65b6e-113">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="65b6e-114">Varsayılan değer "true" dır.</span><span class="sxs-lookup"><span data-stu-id="65b6e-114">The default is "true".</span></span>|  
|<span data-ttu-id="65b6e-115">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="65b6e-115">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="65b6e-116">Belirtir olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> C# kod bir dosyaya yazmak ve sonra da bir derlemeye derlemek tarafından derlemeleri oluşturan eski serileştirme oluşturma kullanır.</span><span class="sxs-lookup"><span data-stu-id="65b6e-116">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="65b6e-117">Varsayılan değer **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="65b6e-117">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65b6e-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="65b6e-118">Child Elements</span></span>  
 <span data-ttu-id="65b6e-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="65b6e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65b6e-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="65b6e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="65b6e-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="65b6e-121">Element</span></span>|<span data-ttu-id="65b6e-122">Description</span><span class="sxs-lookup"><span data-stu-id="65b6e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65b6e-123">\<system.xml.serialization>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="65b6e-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="65b6e-124">İçin yapılandırma ayarlarını içeren <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="65b6e-124">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65b6e-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65b6e-125">Remarks</span></span>  
 <span data-ttu-id="65b6e-126">Varsayılan olarak, <xref:System.Xml.Serialization.XmlSerializer> Güvenilmeyen verilerin serisi kaldırılırken olası hizmet reddi saldırılarına karşı ek bir güvenlik katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="65b6e-126">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="65b6e-127">Bunu seri durumundan çıkarma sırasında sonsuz döngü algılamak deneyerek yapar.</span><span class="sxs-lookup"><span data-stu-id="65b6e-127">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="65b6e-128">Böyle bir koşul algılanırsa, şu iletiyle bir özel durum oluşturulur: "Iç hata: seri kaldırma, temel alınan akışın üzerinde ilerleyemedi."</span><span class="sxs-lookup"><span data-stu-id="65b6e-128">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="65b6e-129">Bu iletiyi alan değil gerekmeyen gösteren bir saldırı hizmet reddi devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="65b6e-129">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="65b6e-130">Bazı ender durumlarda, yanlış Pozitif sonsuz döngü algılama mekanizması oluşturur ve yasal gelen ileti için özel durum.</span><span class="sxs-lookup"><span data-stu-id="65b6e-130">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="65b6e-131">Özel uygulamanızda bu ek koruma katmanı tarafından meşru iletiler reddedilmekte olduğunu fark ederseniz **Checkdeserializeavanslar** özniteliğini "false" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65b6e-131">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="65b6e-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="65b6e-132">Example</span></span>  
 <span data-ttu-id="65b6e-133">Aşağıdaki kod örneği **Checkdeserializeavanslar** özniteliğini "false" olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="65b6e-133">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="65b6e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65b6e-134">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="65b6e-135">\<system.xml.serialization>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="65b6e-135">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="65b6e-136">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="65b6e-136">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)

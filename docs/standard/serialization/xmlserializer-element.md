---
title: <xmlSerializer> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: b83ecda30bba8af1f3175eb6ad08593b07a80e6c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249545"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="22286-102">\<xmlSerializer> öğesi</span><span class="sxs-lookup"><span data-stu-id="22286-102">\<xmlSerializer> Element</span></span>
<span data-ttu-id="22286-103">Belirtir ilerleme durumunu ek bir denetim olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> yapılır.</span><span class="sxs-lookup"><span data-stu-id="22286-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="22286-104">\<yapılandırma></span><span class="sxs-lookup"><span data-stu-id="22286-104">\<configuration></span></span>  
<span data-ttu-id="22286-105">\<System. xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="22286-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22286-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22286-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22286-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="22286-107">Attributes and Elements</span></span>  
 <span data-ttu-id="22286-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22286-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22286-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="22286-109">Attributes</span></span>  
  
|<span data-ttu-id="22286-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="22286-110">Attribute</span></span>|<span data-ttu-id="22286-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22286-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22286-112">**Checkdeserializeavanslar**</span><span class="sxs-lookup"><span data-stu-id="22286-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="22286-113">Belirtir olup olmadığını ilerleme durumunu <xref:System.Xml.Serialization.XmlSerializer> denetlenir.</span><span class="sxs-lookup"><span data-stu-id="22286-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="22286-114">Özniteliği "true" veya "false" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="22286-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="22286-115">Varsayılan değer "true" dır.</span><span class="sxs-lookup"><span data-stu-id="22286-115">The default is "true".</span></span>|  
|<span data-ttu-id="22286-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="22286-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="22286-117">Belirtir olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> C# kod bir dosyaya yazmak ve sonra da bir derlemeye derlemek tarafından derlemeleri oluşturan eski serileştirme oluşturma kullanır.</span><span class="sxs-lookup"><span data-stu-id="22286-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="22286-118">Varsayılan değer **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="22286-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22286-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="22286-119">Child Elements</span></span>  
 <span data-ttu-id="22286-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="22286-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22286-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="22286-121">Parent Elements</span></span>  
  
|<span data-ttu-id="22286-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="22286-122">Element</span></span>|<span data-ttu-id="22286-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22286-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22286-124">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="22286-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="22286-125">İçin yapılandırma ayarlarını içeren <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="22286-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22286-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22286-126">Remarks</span></span>  
 <span data-ttu-id="22286-127">Varsayılan olarak, <xref:System.Xml.Serialization.XmlSerializer> güvenilmeyen verilerin serisi kaldırılırken olası hizmet reddi saldırılarına karşı ek bir güvenlik katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="22286-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="22286-128">Bunu seri durumundan çıkarma sırasında sonsuz döngü algılamak deneyerek yapar.</span><span class="sxs-lookup"><span data-stu-id="22286-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="22286-129">Böyle bir koşul algılanırsa, şu iletiyle bir özel durum oluşturulur: "Iç hata: seri kaldırma, temel alınan akışın üzerinde ilerleyemedi."</span><span class="sxs-lookup"><span data-stu-id="22286-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="22286-130">Bu iletiyi alan değil gerekmeyen gösteren bir saldırı hizmet reddi devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="22286-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="22286-131">Bazı ender durumlarda, yanlış Pozitif sonsuz döngü algılama mekanizması oluşturur ve yasal gelen ileti için özel durum.</span><span class="sxs-lookup"><span data-stu-id="22286-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="22286-132">Özel uygulamanızda bu ek koruma katmanı tarafından meşru iletiler reddedilmekte olduğunu fark ederseniz **Checkdeserializeavanslar** özniteliğini "false" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="22286-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="22286-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="22286-133">Example</span></span>  
 <span data-ttu-id="22286-134">Aşağıdaki kod örneği **Checkdeserializeavanslar** özniteliğini "false" olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="22286-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22286-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22286-135">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="22286-136">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="22286-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="22286-137">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="22286-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)

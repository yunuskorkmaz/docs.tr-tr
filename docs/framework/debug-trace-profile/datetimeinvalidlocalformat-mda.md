---
title: dateTimeInvalidLocalFormat MDA
ms.date: 03/30/2017
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32217b9e681179c246560ff5b51b65b4f4e044d5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052880"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="12634-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="12634-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="12634-103">Evrensel Eşgüdümlü saat (UTC) <xref:System.DateTime> olarak depolanan bir örnek, yalnızca yerel <xref:System.DateTime> örnekler için kullanılmak üzere tasarlanan bir biçim kullanılarak biçimlendirilirken MDAetkinleştirilir.`dateTimeInvalidLocalFormat`</span><span class="sxs-lookup"><span data-stu-id="12634-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="12634-104">Bu mda belirtilmemiş veya varsayılan <xref:System.DateTime> örnekler için etkinleştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="12634-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="12634-105">Belirti</span><span class="sxs-lookup"><span data-stu-id="12634-105">Symptom</span></span>  
 <span data-ttu-id="12634-106">Bir uygulama, bir UTC <xref:System.DateTime> örneğini yerel biçim kullanarak el ile serileştiriliyor:</span><span class="sxs-lookup"><span data-stu-id="12634-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="12634-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="12634-107">Cause</span></span>  
 <span data-ttu-id="12634-108"><xref:System.DateTime.ToString%2A?displayProperty=nameWithType> Yöntemin ' z ' biçimi yerel saat dilimi sapmasını içerir, örneğin, Sidney saati için "+ 10:00".</span><span class="sxs-lookup"><span data-stu-id="12634-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="12634-109">Bu nedenle, yalnızca değerinin <xref:System.DateTime> yerel olması durumunda anlamlı bir sonuç üretir.</span><span class="sxs-lookup"><span data-stu-id="12634-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="12634-110">Değer UTC zamanı <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> ise, yerel saat dilimi sapmasını içerir, ancak saat dilimi tanımlayıcısını görüntülemez veya ayarlamalamaz.</span><span class="sxs-lookup"><span data-stu-id="12634-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="12634-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="12634-111">Resolution</span></span>  
 <span data-ttu-id="12634-112">UTC <xref:System.DateTime> örneklerinin UTC olduğunu belirten bir şekilde biçimlendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="12634-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="12634-113">UTC zamanının UTC zamanını belirtmek için ' Z ' kullanması için önerilen biçim:</span><span class="sxs-lookup"><span data-stu-id="12634-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="12634-114">Örneğin yerel, UTC veya belirtilmemiş olsa da doğru şekilde seri hale <xref:System.DateTime> getirilen <xref:System.DateTime.Kind%2A> özelliği kullanan bir "o" biçimi de vardır:</span><span class="sxs-lookup"><span data-stu-id="12634-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="12634-115">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="12634-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="12634-116">Bu MDA, çalışma zamanını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="12634-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="12634-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="12634-117">Output</span></span>  
 <span data-ttu-id="12634-118">Bu mda ' ın etkinleştirilmesiyle ilgili özel bir çıktı yoktur. ancak, çağrı yığını, MDA ' ı etkinleştiren <xref:System.DateTime.ToString%2A> çağrının konumunu belirlemede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12634-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="12634-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="12634-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="12634-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="12634-120">Example</span></span>  
 <span data-ttu-id="12634-121">Aşağıdaki şekilde, <xref:System.DateTime> <xref:System.Xml.XmlConvert> veya <xref:System.Data.DataSet> sınıfını kullanarak UTC değerini dolaylı olarak serileştirtiren bir uygulamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="12634-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="12634-122"><xref:System.Xml.XmlConvert> Ve<xref:System.Data.DataSet> serileştirmeler varsayılan olarak serileştirme için yerel biçimler kullanır.</span><span class="sxs-lookup"><span data-stu-id="12634-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="12634-123">UTC gibi diğer <xref:System.DateTime> değer türlerini seri hale getirmek için ek seçenekler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="12634-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="12634-124">Bu belirli örnek için, `XmlDateTimeSerializationMode.RoundtripKind` `ToString` çağrısına `XmlConvert`geçin.</span><span class="sxs-lookup"><span data-stu-id="12634-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="12634-125">Bu, verileri UTC saati olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="12634-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="12634-126">Kullanıyorsanız <xref:System.Data.DataSet> <xref:System.Data.DataColumn.DateTimeMode%2A> , nesnesi<xref:System.Data.DataColumn> üzerinde özelliğini olarak<xref:System.Data.DataSetDateTime.Utc>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="12634-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="12634-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12634-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="12634-128">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="12634-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)

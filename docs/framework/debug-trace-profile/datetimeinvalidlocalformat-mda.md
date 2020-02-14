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
ms.openlocfilehash: 2fdace8a9c7bcc090fd801be3bd717e4a2b34a87
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217544"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="01f7a-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="01f7a-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="01f7a-103">Evrensel Eşgüdümlü saat (UTC) olarak depolanan bir <xref:System.DateTime> örneği, yalnızca yerel <xref:System.DateTime> örnekleri için kullanılmak üzere tasarlanan bir biçim kullanılarak biçimlendirildiğinde `dateTimeInvalidLocalFormat` MDA etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="01f7a-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="01f7a-104">Bu MDA, belirtilmeyen veya varsayılan <xref:System.DateTime> örnekleri için etkinleştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="01f7a-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="01f7a-105">Belirti</span><span class="sxs-lookup"><span data-stu-id="01f7a-105">Symptom</span></span>  
 <span data-ttu-id="01f7a-106">Bir uygulama, bir UTC <xref:System.DateTime> örneğini yerel bir biçim kullanarak el ile serileştiriliyor:</span><span class="sxs-lookup"><span data-stu-id="01f7a-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="01f7a-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="01f7a-107">Cause</span></span>  
 <span data-ttu-id="01f7a-108"><xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yöntemi için ' z ' biçimi, örneğin "+ 10:00", Sidney saati için yerel saat dilimi sapmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="01f7a-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="01f7a-109">Bu nedenle, <xref:System.DateTime> değeri yerel ise yalnızca anlamlı bir sonuç üretir.</span><span class="sxs-lookup"><span data-stu-id="01f7a-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="01f7a-110">Değer UTC zamanı ise, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yerel saat dilimi sapmasını içerir, ancak saat dilimi tanımlayıcısını görüntülemez veya ayarlamalamaz.</span><span class="sxs-lookup"><span data-stu-id="01f7a-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="01f7a-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="01f7a-111">Resolution</span></span>  
 <span data-ttu-id="01f7a-112">UTC <xref:System.DateTime> örnekleri UTC olduğunu belirten bir şekilde biçimlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="01f7a-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="01f7a-113">UTC zamanının UTC zamanını belirtmek için ' Z ' kullanması için önerilen biçim:</span><span class="sxs-lookup"><span data-stu-id="01f7a-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="01f7a-114">Örneğin yerel, UTC veya belirtilmemiş olsa da doğru şekilde seri hale getirilen <xref:System.DateTime.Kind%2A> özelliğini kullanan bir <xref:System.DateTime> seri hale getiren bir "o" biçimi de vardır:</span><span class="sxs-lookup"><span data-stu-id="01f7a-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="01f7a-115">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="01f7a-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="01f7a-116">Bu MDA, çalışma zamanını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="01f7a-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="01f7a-117">Çıktı</span><span class="sxs-lookup"><span data-stu-id="01f7a-117">Output</span></span>  
 <span data-ttu-id="01f7a-118">Bu MDA ' ın etkinleştirilmesiyle ilgili özel bir çıktı yoktur. ancak, çağrı yığını, MDA ' ı etkinleştiren <xref:System.DateTime.ToString%2A> çağrısının konumunu belirlemede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01f7a-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="01f7a-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="01f7a-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="01f7a-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="01f7a-120">Example</span></span>  
 <span data-ttu-id="01f7a-121">Bir UTC <xref:System.DateTime> değerini, aşağıdaki şekilde <xref:System.Xml.XmlConvert> veya <xref:System.Data.DataSet> sınıfını kullanarak dolaylı olarak serileştirerek bir uygulamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="01f7a-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="01f7a-122"><xref:System.Xml.XmlConvert> ve <xref:System.Data.DataSet> serileştirmeler, varsayılan olarak serileştirme için yerel biçimler kullanır.</span><span class="sxs-lookup"><span data-stu-id="01f7a-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="01f7a-123">UTC gibi diğer <xref:System.DateTime> değer türlerini seri hale getirmek için ek seçenekler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="01f7a-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="01f7a-124">Bu belirli örnekte, `XmlConvert``ToString` çağrısına `XmlDateTimeSerializationMode.RoundtripKind` geçirin.</span><span class="sxs-lookup"><span data-stu-id="01f7a-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="01f7a-125">Bu, verileri UTC saati olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="01f7a-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="01f7a-126"><xref:System.Data.DataSet>kullanıyorsanız, <xref:System.Data.DataColumn> nesnesindeki <xref:System.Data.DataColumn.DateTimeMode%2A> özelliğini <xref:System.Data.DataSetDateTime.Utc>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="01f7a-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="01f7a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01f7a-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="01f7a-128">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="01f7a-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)

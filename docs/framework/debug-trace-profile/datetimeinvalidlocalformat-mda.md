---
title: dateTimeInvalidLocalFormat MDA
description: UTC saklı bir tarih saat değeri yalnızca yerel bir tarih saat biçimi aldığında etkinleştirilen Datetimeınvalidlocalformat yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: ed2cf0b960c0a8f51dc327a5c58770fcf5e2fa17
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286064"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="d4df2-103">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="d4df2-103">dateTimeInvalidLocalFormat MDA</span></span>

<span data-ttu-id="d4df2-104">`dateTimeInvalidLocalFormat` <xref:System.DateTime> Evrensel Eşgüdümlü saat (UTC) olarak depolanan bir örnek, yalnızca yerel örnekler için kullanılmak üzere tasarlanan bir biçim kullanılarak biçimlendirilirken MDA etkinleştirilir <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="d4df2-104">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="d4df2-105">Bu MDA belirtilmemiş veya varsayılan örnekler için etkinleştirilmemiş <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="d4df2-105">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="d4df2-106">Belirti</span><span class="sxs-lookup"><span data-stu-id="d4df2-106">Symptom</span></span>  

 <span data-ttu-id="d4df2-107">Bir uygulama, bir UTC <xref:System.DateTime> örneğini yerel biçim kullanarak el ile serileştiriliyor:</span><span class="sxs-lookup"><span data-stu-id="d4df2-107">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="d4df2-108">Nedeni</span><span class="sxs-lookup"><span data-stu-id="d4df2-108">Cause</span></span>  

 <span data-ttu-id="d4df2-109">Yöntemin ' z ' biçimi <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> Yerel Saat dilimi sapmasını içerir, örneğin, Sidney saati için "+ 10:00".</span><span class="sxs-lookup"><span data-stu-id="d4df2-109">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="d4df2-110">Bu nedenle, yalnızca değerinin yerel olması durumunda anlamlı bir sonuç üretir <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="d4df2-110">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="d4df2-111">Değer UTC zamanı ise, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> Yerel Saat dilimi sapmasını içerir, ancak saat dilimi tanımlayıcısını görüntülemez veya ayarlamalamaz.</span><span class="sxs-lookup"><span data-stu-id="d4df2-111">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="d4df2-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="d4df2-112">Resolution</span></span>  

 <span data-ttu-id="d4df2-113">UTC <xref:System.DateTime> ÖRNEKLERININ UTC olduğunu belirten bir şekilde biçimlendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4df2-113">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="d4df2-114">UTC zamanının UTC zamanını belirtmek için ' Z ' kullanması için önerilen biçim:</span><span class="sxs-lookup"><span data-stu-id="d4df2-114">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="d4df2-115"><xref:System.DateTime> <xref:System.DateTime.Kind%2A> Örneğin yerel, UTC veya belirtilmemiş olsa da doğru şekilde seri hale getirilen özelliği kullanan bir "o" biçimi de vardır:</span><span class="sxs-lookup"><span data-stu-id="d4df2-115">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d4df2-116">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="d4df2-116">Effect on the Runtime</span></span>  

 <span data-ttu-id="d4df2-117">Bu MDA, çalışma zamanını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="d4df2-117">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d4df2-118">Çıkış</span><span class="sxs-lookup"><span data-stu-id="d4df2-118">Output</span></span>  

 <span data-ttu-id="d4df2-119">Bu MDA ' ın etkinleştirilmesiyle ilgili özel bir çıktı yoktur. ancak, çağrı yığını, MDA ' ı etkinleştiren çağrının konumunu belirlemede kullanılabilir <xref:System.DateTime.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="d4df2-119">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d4df2-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d4df2-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="d4df2-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4df2-121">Example</span></span>  

 <span data-ttu-id="d4df2-122"><xref:System.DateTime> <xref:System.Xml.XmlConvert> Aşağıdaki şekilde, veya SıNıFıNı kullanarak UTC değerini dolaylı olarak serileştirtiren bir uygulamayı düşünün <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d4df2-122">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="d4df2-123"><xref:System.Xml.XmlConvert>Ve <xref:System.Data.DataSet> serileştirmeler varsayılan olarak serileştirme için yerel biçimler kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4df2-123">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="d4df2-124">UTC gibi diğer değer türlerini seri hale getirmek için ek seçenekler gereklidir <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="d4df2-124">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="d4df2-125">Bu belirli örnek için, çağrısına geçin `XmlDateTimeSerializationMode.RoundtripKind` `ToString` `XmlConvert` .</span><span class="sxs-lookup"><span data-stu-id="d4df2-125">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="d4df2-126">Bu, verileri UTC saati olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="d4df2-126">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="d4df2-127">Kullanıyorsanız <xref:System.Data.DataSet> , <xref:System.Data.DataColumn.DateTimeMode%2A> nesnesi üzerinde özelliğini <xref:System.Data.DataColumn> olarak ayarlayın <xref:System.Data.DataSetDateTime.Utc> .</span><span class="sxs-lookup"><span data-stu-id="d4df2-127">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4df2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4df2-128">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="d4df2-129">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="d4df2-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)

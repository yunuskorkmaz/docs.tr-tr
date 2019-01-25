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
ms.openlocfilehash: 78d9d769deefedef0c72b847c86e7b9fc175288c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732680"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="57612-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="57612-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="57612-103">`dateTimeInvalidLocalFormat` MDA etkinleştirilmiş olduğunda bir <xref:System.DateTime> yalnızca yerel için kullanılmak üzere tasarlanan bir biçimi kullanılarak biçimlendirilmiş bir Eşgüdümlü Evrensel Saat (UTC) olarak depolanan örneği <xref:System.DateTime> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="57612-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="57612-104">Bu mda'nın belirtilmemiş veya varsayılan etkinleştirilmedi <xref:System.DateTime> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="57612-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="57612-105">Belirti</span><span class="sxs-lookup"><span data-stu-id="57612-105">Symptom</span></span>  
 <span data-ttu-id="57612-106">Bir uygulamayı el ile bir UTC serileştiren <xref:System.DateTime> yerel biçimini kullanarak örneği:</span><span class="sxs-lookup"><span data-stu-id="57612-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="57612-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="57612-107">Cause</span></span>  
 <span data-ttu-id="57612-108">'z' biçimlendirmek için <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yöntemi içeren yerel saat dilimi uzaklığı, örneğin, "+ 10:00" Sidney kez.</span><span class="sxs-lookup"><span data-stu-id="57612-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="57612-109">Bu nedenle, bunu yalnızca anlamlı bir sonuç ise üretecektir değerini <xref:System.DateTime> yereldir.</span><span class="sxs-lookup"><span data-stu-id="57612-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="57612-110">UTC saat değeriyse <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yerel saatini içeren dilimi uzaklığı, ancak bunu dotnetclıtools'u görüntülemiyor ve saat dilimi belirteci ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="57612-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="57612-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="57612-111">Resolution</span></span>  
 <span data-ttu-id="57612-112">UTC <xref:System.DateTime> örnekleri UTC olduklarını bildiren bir şekilde biçimlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="57612-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="57612-113">UTC saatleri UTC saati belirtmek için 'Z' kullanmak için önerilen biçim:</span><span class="sxs-lookup"><span data-stu-id="57612-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="57612-114">Ayrıca serileştiren bir "o" biçim vardır bir <xref:System.DateTime> ipconfigurations <xref:System.DateTime.Kind%2A> örneği yerel olup olmadığına bakılmaksızın doğru olarak serileştiren özelliğini, UTC veya belirtilmeyen:</span><span class="sxs-lookup"><span data-stu-id="57612-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="57612-115">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="57612-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="57612-116">Bu MDA, çalışma zamanı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="57612-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="57612-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="57612-117">Output</span></span>  
 <span data-ttu-id="57612-118">Bu MDA etkinleştirme sonucu olarak özel çıkış yok., Bununla birlikte, çağrı yığını konumunu belirlemek için kullanılabilir <xref:System.DateTime.ToString%2A> MDA etkinleştirilmiş çağrısı.</span><span class="sxs-lookup"><span data-stu-id="57612-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="57612-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="57612-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="57612-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="57612-120">Example</span></span>  
 <span data-ttu-id="57612-121">UTC biçiminde dolaylı olarak serileştiren bir uygulama düşünün <xref:System.DateTime> kullanarak değer <xref:System.Xml.XmlConvert> veya <xref:System.Data.DataSet> sınıfında aşağıdaki şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="57612-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="57612-122"><xref:System.Xml.XmlConvert> Ve <xref:System.Data.DataSet> serializations varsayılan olarak seri hale getirme için yerel biçimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="57612-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="57612-123">Ek seçenekler, diğer türleri serileştirmek için gereklidir, <xref:System.DateTime> UTC gibi değerler.</span><span class="sxs-lookup"><span data-stu-id="57612-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="57612-124">Bu örnek için geçirin `XmlDateTimeSerializationMode.RoundtripKind` için `ToString` çağırmak `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="57612-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="57612-125">Bu veriler UTC saati olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="57612-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="57612-126">Kullanılıyorsa bir <xref:System.Data.DataSet>ayarlayın <xref:System.Data.DataColumn.DateTimeMode%2A> özelliği <xref:System.Data.DataColumn> nesnesini <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="57612-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="57612-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57612-127">See also</span></span>
- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="57612-128">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="57612-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

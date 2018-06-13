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
ms.openlocfilehash: bb5777e275fd7c48f7125b9e0315b08d3095c373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357812"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="9fbea-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="9fbea-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="9fbea-103">`dateTimeInvalidLocalFormat` MDA etkinleştirilirse, bir <xref:System.DateTime> yalnızca yerel için kullanılması hedeflenen bir biçimi kullanarak bir Evrensel Eşgüdümlü saate (UTC) biçimli olarak depolanan örneği <xref:System.DateTime> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9fbea-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="9fbea-104">Bu MDA belirtilmemiş veya varsayılan etkinleştirilmedi <xref:System.DateTime> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9fbea-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="9fbea-105">Belirti</span><span class="sxs-lookup"><span data-stu-id="9fbea-105">Symptom</span></span>  
 <span data-ttu-id="9fbea-106">Bir uygulamayı el ile bir UTC serileştirme <xref:System.DateTime> yerel biçimini kullanarak örneği:</span><span class="sxs-lookup"><span data-stu-id="9fbea-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="9fbea-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="9fbea-107">Cause</span></span>  
 <span data-ttu-id="9fbea-108">'z' biçimlendirmek için <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yöntemi içeren yerel saat dilimi konumu, örneğin, "+ 10:00" Sidney süre.</span><span class="sxs-lookup"><span data-stu-id="9fbea-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="9fbea-109">Bu nedenle, onu yalnızca anlamlı bir sonuç varsa üretecektir değerini <xref:System.DateTime> yereldir.</span><span class="sxs-lookup"><span data-stu-id="9fbea-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="9fbea-110">UTC saat değeri geçerliyse <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yerel saati içeren bölge uzaklığı, ancak bırakmaz görüntülemek veya saat dilimi belirleyici ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9fbea-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="9fbea-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="9fbea-111">Resolution</span></span>  
 <span data-ttu-id="9fbea-112">UTC <xref:System.DateTime> örnekleri UTC olduğunu gösterir şekilde biçimlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9fbea-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="9fbea-113">UTC saatleri UTC saati belirtmek için 'Z' kullanmak Önerilen biçimi:</span><span class="sxs-lookup"><span data-stu-id="9fbea-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="9fbea-114">Ayrıca serileştiren bir "o" biçiminde olan bir <xref:System.DateTime> yapmayı kullanımını <xref:System.DateTime.Kind%2A> örneği yerel olup olmadığına bakılmaksızın doğru olarak serileştiren özelliği, UTC veya belirtilmemiş:</span><span class="sxs-lookup"><span data-stu-id="9fbea-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9fbea-115">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="9fbea-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="9fbea-116">Bu MDA çalışma etkilemez.</span><span class="sxs-lookup"><span data-stu-id="9fbea-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9fbea-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="9fbea-117">Output</span></span>  
 <span data-ttu-id="9fbea-118">Bu MDA etkinleştirme sonucunda özel çıkış yok., ancak, çağrı yığını konumunu belirlemek için kullanılabilir <xref:System.DateTime.ToString%2A> MDA etkinleştirilmiş çağrısı.</span><span class="sxs-lookup"><span data-stu-id="9fbea-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9fbea-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9fbea-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9fbea-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fbea-120">Example</span></span>  
 <span data-ttu-id="9fbea-121">Bir UTC dolaylı olarak serileştiren bir uygulamayı göz önünde bulundurun <xref:System.DateTime> kullanarak değer <xref:System.Xml.XmlConvert> veya <xref:System.Data.DataSet> aşağıdaki şekilde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9fbea-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="9fbea-122"><xref:System.Xml.XmlConvert> Ve <xref:System.Data.DataSet> serializations seri hale getirme için yerel biçimler varsayılan olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="9fbea-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="9fbea-123">Ek seçenekler diğer türleri serileştirmek için gereklidir, <xref:System.DateTime> UTC gibi değerler.</span><span class="sxs-lookup"><span data-stu-id="9fbea-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="9fbea-124">Bu belirli örneğin geçirin `XmlDateTimeSerializationMode.RoundtripKind` için `ToString` çağırmak `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="9fbea-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="9fbea-125">Bu veriler UTC saati olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="9fbea-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="9fbea-126">Kullanılıyorsa bir <xref:System.Data.DataSet>ayarlayın <xref:System.Data.DataColumn.DateTimeMode%2A> özelliği <xref:System.Data.DataColumn> nesnesine <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="9fbea-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fbea-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fbea-127">See Also</span></span>  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [<span data-ttu-id="9fbea-128">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="9fbea-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

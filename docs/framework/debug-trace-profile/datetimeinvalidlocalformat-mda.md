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
ms.openlocfilehash: b01f030c474e426cb87fb907f99f241eeb76a7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174764"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="9ff96-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="9ff96-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="9ff96-103">`dateTimeInvalidLocalFormat` Evrensel Eşgüdümlü Zaman <xref:System.DateTime> (UTC) olarak depolanan bir örnek yalnızca yerel <xref:System.DateTime> örnekler için kullanılmak üzere tasarlanmış bir biçim kullanılarak biçimlendirildiğinde MDA etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9ff96-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="9ff96-104">Bu MDA belirtilmeyen veya varsayılan <xref:System.DateTime> durumlar için etkinleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="9ff96-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="9ff96-105">Belirti</span><span class="sxs-lookup"><span data-stu-id="9ff96-105">Symptom</span></span>  
 <span data-ttu-id="9ff96-106">Uygulama, yerel bir biçim kullanarak <xref:System.DateTime> bir UTC örneğini el ile serihale getirerek:</span><span class="sxs-lookup"><span data-stu-id="9ff96-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="9ff96-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="9ff96-107">Cause</span></span>  
 <span data-ttu-id="9ff96-108">Yöntemin <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 'z' biçimi, Sydney saati için "+10:00" gibi yerel saat dilimi mahsuplarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9ff96-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="9ff96-109">Bu nedenle, yalnızca değeri yerel <xref:System.DateTime> ise anlamlı bir sonuç üretecektir.</span><span class="sxs-lookup"><span data-stu-id="9ff96-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="9ff96-110">Değer UTC saatiyse, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> yerel saat dilimi mahsupını içerir, ancak saat dilimi belirticisini görüntülemez veya ayarlamaz.</span><span class="sxs-lookup"><span data-stu-id="9ff96-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="9ff96-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="9ff96-111">Resolution</span></span>  
 <span data-ttu-id="9ff96-112">UTC <xref:System.DateTime> örnekleri UTC olduklarını gösteren bir şekilde biçimlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9ff96-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="9ff96-113">UTC süresini belirtmek için UTC zamanları için önerilen biçim :</span><span class="sxs-lookup"><span data-stu-id="9ff96-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="9ff96-114">Örneğin yerel, UTC veya belirtilmemiş <xref:System.DateTime> olup olmadığına <xref:System.DateTime.Kind%2A> bakılmaksızın, özelliğin kullanımını seri hale getiren bir "o" biçimi de vardır:</span><span class="sxs-lookup"><span data-stu-id="9ff96-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9ff96-115">Çalışma Süresi üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="9ff96-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="9ff96-116">Bu MDA çalışma süresini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="9ff96-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9ff96-117">Çıktı</span><span class="sxs-lookup"><span data-stu-id="9ff96-117">Output</span></span>  
 <span data-ttu-id="9ff96-118">Bu MDA etkinleştirme sonucu özel bir çıkış yoktur., Ancak, çağrı yığını MDA etkinleştirilmiş <xref:System.DateTime.ToString%2A> arama konumunu belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ff96-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9ff96-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9ff96-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9ff96-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ff96-120">Example</span></span>  
 <span data-ttu-id="9ff96-121">Utc <xref:System.DateTime> değerini dolaylı olarak serileştiren bir uygulamayı <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> aşağıdaki şekilde veya sınıfı kullanarak düşünün.</span><span class="sxs-lookup"><span data-stu-id="9ff96-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="9ff96-122">Ve <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> serileştirmeler varsayılan olarak serileştirme için yerel biçimleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ff96-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="9ff96-123">UTC gibi diğer değer türlerini <xref:System.DateTime> seri hale getirmek için ek seçenekler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9ff96-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="9ff96-124">Bu özel örnek `XmlDateTimeSerializationMode.RoundtripKind` için, `ToString` arama `XmlConvert`yı geçin.</span><span class="sxs-lookup"><span data-stu-id="9ff96-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="9ff96-125">Bu, verileri UTC zamanı olarak serihale eder.</span><span class="sxs-lookup"><span data-stu-id="9ff96-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="9ff96-126">Bir <xref:System.Data.DataSet>kullanıyorsanız, <xref:System.Data.DataColumn.DateTimeMode%2A> nesne üzerindeki <xref:System.Data.DataColumn> özelliği <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="9ff96-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ff96-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ff96-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="9ff96-128">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="9ff96-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)

---
title: Dizeleri .NET veri türlerine dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: 0cee7481f9c002f860bff7f12b8be0bb763dadb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701477"
---
# <a name="convert-strings-to-net-data-types"></a><span data-ttu-id="feacf-102">Dizeleri .NET veri türlerine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="feacf-102">Convert strings to .NET data types</span></span>

<span data-ttu-id="feacf-103">Bir dizeyi .NET veri türüne dönüştürmek istiyorsanız, uygulama gereksinimlerine uyan **XmlConvert** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="feacf-103">If you want to convert a string to a .NET data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="feacf-104">**XmlConvert** sınıfında bulunan tüm dönüştürme yöntemlerinin listesi için bkz <xref:System.Xml.XmlConvert> ..</span><span class="sxs-lookup"><span data-stu-id="feacf-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="feacf-105">**ToString** yönteminden döndürülen dize, geçirilen verilerin dize bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="feacf-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="feacf-106">Buna ek olarak, **XmlConvert** sınıfını kullanarak dönüştüren birkaç .NET türü vardır ancak **System. Convert** sınıfındaki yöntemleri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="feacf-106">Additionally, there are several .NET types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="feacf-107">**XmlConvert** sınıfı, XML ŞEMASı (xsd) veri türü belirtimini Izler ve **XmlConvert** 'in eşleyebileceğiniz bir veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="feacf-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="feacf-108">Aşağıdaki tabloda, .NET veri türleri ve XML şeması (XSD) veri türü eşlemesi kullanılarak döndürülen dize türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="feacf-108">The following table lists .NET data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="feacf-109">Bu .NET türleri **System. Convert** kullanılarak işlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="feacf-109">These .NET types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="feacf-110">.NET türü</span><span class="sxs-lookup"><span data-stu-id="feacf-110">.NET type</span></span>|<span data-ttu-id="feacf-111">Döndürülen dize</span><span class="sxs-lookup"><span data-stu-id="feacf-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="feacf-112">Boole</span><span class="sxs-lookup"><span data-stu-id="feacf-112">Boolean</span></span>|<span data-ttu-id="feacf-113">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="feacf-113">"true", "false"</span></span>|  
|<span data-ttu-id="feacf-114">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="feacf-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="feacf-115">'SI</span><span class="sxs-lookup"><span data-stu-id="feacf-115">"INF"</span></span>|  
|<span data-ttu-id="feacf-116">Tek. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="feacf-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="feacf-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="feacf-117">"-INF"</span></span>|  
|<span data-ttu-id="feacf-118">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="feacf-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="feacf-119">'SI</span><span class="sxs-lookup"><span data-stu-id="feacf-119">"INF"</span></span>|  
|<span data-ttu-id="feacf-120">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="feacf-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="feacf-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="feacf-121">"-INF"</span></span>|  
|<span data-ttu-id="feacf-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="feacf-122">DateTime</span></span>|<span data-ttu-id="feacf-123">Biçim "yyyy-MM-ddTHH: mm: sszzzzzz" ve alt kümeleridir.</span><span class="sxs-lookup"><span data-stu-id="feacf-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="feacf-124">Timespan</span><span class="sxs-lookup"><span data-stu-id="feacf-124">Timespan</span></span>|<span data-ttu-id="feacf-125">Biçim, `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10 saat, 30 dakika ve 20 saniye olmak üzere Pnazmntnhnmns 'dir</span><span class="sxs-lookup"><span data-stu-id="feacf-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="feacf-126">Tabloda listelenen herhangi bir .NET türünü **ToString** yöntemini kullanarak bir dizeye dönüştürürseniz, döndürülen dize temel tür değildir, ancak XML ŞEMASı (xsd) dize türüdür.</span><span class="sxs-lookup"><span data-stu-id="feacf-126">If converting any of the .NET types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="feacf-127">**DateTime** ve **TimeSpan** değer türü, bir **Tarih** saat içinde anlık bir zaman aralığını temsil ettiğinden, bir **TimeSpan** değeri bir zaman aralığı temsil ettiğinden farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="feacf-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="feacf-128">**DateTime** ve **TIMESPAN** biçimleri, XML şeması (xsd) veri türleri belirtiminde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="feacf-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="feacf-129">Örnek:</span><span class="sxs-lookup"><span data-stu-id="feacf-129">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="feacf-130">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="feacf-130">**Output**</span></span>  
  
 <span data-ttu-id="feacf-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="feacf-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="feacf-132">Aşağıdaki kod bir tamsayıyı bir dizeye dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="feacf-132">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="feacf-133">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="feacf-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="feacf-134">Ancak, bir dizeyi **Boolean**, **Single** veya **Double**'A dönüştürüyorsanız, döndürülen .NET türü **System. Convert** sınıfı kullanılırken döndürülen türle aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="feacf-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET type that's returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="feacf-135">Boole olarak dize</span><span class="sxs-lookup"><span data-stu-id="feacf-135">String to Boolean</span></span>  

 <span data-ttu-id="feacf-136">Aşağıdaki tabloda, **ToBoolean** yöntemi kullanılarak bir dize **Boole** değerine dönüştürülürken, verilen giriş dizeleri için hangi türün oluşturulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feacf-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="feacf-137">Geçerli dize giriş parametresi</span><span class="sxs-lookup"><span data-stu-id="feacf-137">Valid string input parameter</span></span>|<span data-ttu-id="feacf-138">.NET çıkış türü</span><span class="sxs-lookup"><span data-stu-id="feacf-138">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="feacf-139">değeri</span><span class="sxs-lookup"><span data-stu-id="feacf-139">"true"</span></span>|<span data-ttu-id="feacf-140">Boolean. true</span><span class="sxs-lookup"><span data-stu-id="feacf-140">Boolean.True</span></span>|  
|<span data-ttu-id="feacf-141">"1"</span><span class="sxs-lookup"><span data-stu-id="feacf-141">"1"</span></span>|<span data-ttu-id="feacf-142">Boolean. true</span><span class="sxs-lookup"><span data-stu-id="feacf-142">Boolean.True</span></span>|  
|<span data-ttu-id="feacf-143">yanlýþ</span><span class="sxs-lookup"><span data-stu-id="feacf-143">"false"</span></span>|<span data-ttu-id="feacf-144">Boolean. false</span><span class="sxs-lookup"><span data-stu-id="feacf-144">Boolean.False</span></span>|  
|<span data-ttu-id="feacf-145">"0"</span><span class="sxs-lookup"><span data-stu-id="feacf-145">"0"</span></span>|<span data-ttu-id="feacf-146">Boolean. false</span><span class="sxs-lookup"><span data-stu-id="feacf-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="feacf-147">Örneğin, aşağıdaki XML verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="feacf-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="feacf-148">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="feacf-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 <span data-ttu-id="feacf-149">Her ikisi de aşağıdaki kod tarafından Anlaşılabiliyorsa, **bValue** ise **System. Boolean. true**:</span><span class="sxs-lookup"><span data-stu-id="feacf-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="feacf-150">Dizeden tek</span><span class="sxs-lookup"><span data-stu-id="feacf-150">String to Single</span></span>  

 <span data-ttu-id="feacf-151">Aşağıdaki tabloda, bir dizeyi **ToSingle** yöntemi kullanılarak **tek tek** dönüştürme sırasında verilen giriş dizeleri için oluşturulan tür gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feacf-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="feacf-152">Geçerli dize giriş parametresi</span><span class="sxs-lookup"><span data-stu-id="feacf-152">Valid string input parameter</span></span>|<span data-ttu-id="feacf-153">.NET çıkış türü</span><span class="sxs-lookup"><span data-stu-id="feacf-153">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="feacf-154">'SI</span><span class="sxs-lookup"><span data-stu-id="feacf-154">"INF"</span></span>|<span data-ttu-id="feacf-155">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="feacf-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="feacf-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="feacf-156">"-INF"</span></span>|<span data-ttu-id="feacf-157">Tek. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="feacf-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="feacf-158">Double için dize</span><span class="sxs-lookup"><span data-stu-id="feacf-158">String to Double</span></span>  

 <span data-ttu-id="feacf-159">Aşağıdaki tabloda, **ToDouble** yöntemi kullanılarak bir dizeyi **tek tek** dönüştürmek için verilen giriş dizeleri için hangi türün oluşturulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feacf-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="feacf-160">Geçerli dize giriş parametresi</span><span class="sxs-lookup"><span data-stu-id="feacf-160">Valid string input parameter</span></span>|<span data-ttu-id="feacf-161">.NET çıkış türü</span><span class="sxs-lookup"><span data-stu-id="feacf-161">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="feacf-162">'SI</span><span class="sxs-lookup"><span data-stu-id="feacf-162">"INF"</span></span>|<span data-ttu-id="feacf-163">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="feacf-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="feacf-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="feacf-164">"-INF"</span></span>|<span data-ttu-id="feacf-165">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="feacf-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="feacf-166">Aşağıdaki kod yazılır `<Infinity>INF</Infinity>` :</span><span class="sxs-lookup"><span data-stu-id="feacf-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="feacf-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feacf-167">See also</span></span>

- [<span data-ttu-id="feacf-168">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="feacf-168">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="feacf-169">.NET türlerini dizelere dönüştürme</span><span class="sxs-lookup"><span data-stu-id="feacf-169">Converting .NET Types to Strings</span></span>](converting-dotnet-types-to-strings.md)

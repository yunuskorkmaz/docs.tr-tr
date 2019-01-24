---
title: .NET Framework veri türleri için dizeleri dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 376dd9df4666193f8e5a6be83f3fcaf5dc32f1a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544607"
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="4178c-102">.NET Framework veri türleri için dizeleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="4178c-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="4178c-103">Bir dizeyi bir .NET Framework veri türüne dönüştürmek istiyorsanız kullanmanız **XmlConvert** uygulama gereksinimlerine en uygun yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4178c-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="4178c-104">Kullanılabilir tüm dönüştürme yöntemleri listesi **XmlConvert** sınıfı <xref:System.Xml.XmlConvert>.</span><span class="sxs-lookup"><span data-stu-id="4178c-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="4178c-105">Döndürülen dize **ToString** yöntemi geçirilen verileri dize sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="4178c-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="4178c-106">Ayrıca, kullanarak birden fazla .NET Framework türü vardır **XmlConvert** yöntemlere kullanmayın henüz sınıfı **System.Convert** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4178c-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="4178c-107">**XmlConvert** sınıfı XML Şeması (XSD) veri türü belirtimi izler ve bir veri türü olan **XmlConvert** eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4178c-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="4178c-108">Aşağıdaki tablo, .NET Framework veri türleri ve XML Şeması (XSD) veri türü eşlemesi kullanarak döndürülen dize türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4178c-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="4178c-109">Bu .NET Framework türleri kullanılarak işlenemez **System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="4178c-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="4178c-110">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="4178c-110">.NET Framework type</span></span>|<span data-ttu-id="4178c-111">Döndürülen dize</span><span class="sxs-lookup"><span data-stu-id="4178c-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="4178c-112">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="4178c-112">Boolean</span></span>|<span data-ttu-id="4178c-113">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="4178c-113">"true", "false"</span></span>|  
|<span data-ttu-id="4178c-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="4178c-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="4178c-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="4178c-115">"INF"</span></span>|  
|<span data-ttu-id="4178c-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="4178c-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="4178c-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="4178c-117">"-INF"</span></span>|  
|<span data-ttu-id="4178c-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="4178c-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="4178c-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="4178c-119">"INF"</span></span>|  
|<span data-ttu-id="4178c-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="4178c-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="4178c-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="4178c-121">"-INF"</span></span>|  
|<span data-ttu-id="4178c-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="4178c-122">DateTime</span></span>|<span data-ttu-id="4178c-123">Biçim "yyyy-aa-ddTHH:mm:sszzzzzz" ve onun alt kümeleri.</span><span class="sxs-lookup"><span data-stu-id="4178c-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="4178c-124">Zaman aralığı</span><span class="sxs-lookup"><span data-stu-id="4178c-124">Timespan</span></span>|<span data-ttu-id="4178c-125">Biçimidir PnYnMnTnHnMnS diğer bir deyişle, `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10 saat, 30 dakika, ve 20 saniye süresidir.</span><span class="sxs-lookup"><span data-stu-id="4178c-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4178c-126">.NET Framework türlerinin herhangi biriyle dönüştürme kullanarak bir dize tablosunda listeleniyorsa **ToString** yöntemi, döndürülen dizeye temel tür, ancak XML Şeması (XSD) dize türü değil.</span><span class="sxs-lookup"><span data-stu-id="4178c-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="4178c-127">**DateTime** ve **Timespan** değer türü içinde farklı bir **DateTime** anlık süre içinde oysa temsil eder bir **TimeSpan** bir zaman aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4178c-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="4178c-128">**DateTime** ve **Timespan** biçimleri, XML Şeması (XSD) veri türleri belirtiminde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4178c-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="4178c-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4178c-129">For example:</span></span>  
  
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
  
 <span data-ttu-id="4178c-130">**Output**</span><span class="sxs-lookup"><span data-stu-id="4178c-130">**Output**</span></span>  
  
 <span data-ttu-id="4178c-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="4178c-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="4178c-132">Aşağıdaki kod bir tamsayı bir dizeye dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="4178c-132">The following code converts an integer to a string:</span></span>  
  
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
  
 <span data-ttu-id="4178c-133">**Output**</span><span class="sxs-lookup"><span data-stu-id="4178c-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="4178c-134">Ancak, bir dizeye dönüştürüyorsanız **Boole**, **tek**, veya **çift**, döndürülen .NET Framework türü kullanırken döndürülen tür ile aynı değil **System.Convert** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4178c-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="4178c-135">Boole dizesi</span><span class="sxs-lookup"><span data-stu-id="4178c-135">String to Boolean</span></span>  
 <span data-ttu-id="4178c-136">Aşağıdaki tabloda, ne tür bir dizeye dönüştürürken verilen Giriş dizeleri için oluşturulur gösterilmektedir **Boole** kullanarak **ToBoolean** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4178c-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="4178c-137">Giriş parametresi geçerli bir dize</span><span class="sxs-lookup"><span data-stu-id="4178c-137">Valid string input parameter</span></span>|<span data-ttu-id="4178c-138">.NET framework çıktı türü</span><span class="sxs-lookup"><span data-stu-id="4178c-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="4178c-139">"true"</span><span class="sxs-lookup"><span data-stu-id="4178c-139">"true"</span></span>|<span data-ttu-id="4178c-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="4178c-140">Boolean.True</span></span>|  
|<span data-ttu-id="4178c-141">"1"</span><span class="sxs-lookup"><span data-stu-id="4178c-141">"1"</span></span>|<span data-ttu-id="4178c-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="4178c-142">Boolean.True</span></span>|  
|<span data-ttu-id="4178c-143">"false"</span><span class="sxs-lookup"><span data-stu-id="4178c-143">"false"</span></span>|<span data-ttu-id="4178c-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="4178c-144">Boolean.False</span></span>|  
|<span data-ttu-id="4178c-145">"0"</span><span class="sxs-lookup"><span data-stu-id="4178c-145">"0"</span></span>|<span data-ttu-id="4178c-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="4178c-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="4178c-147">Örneğin, aşağıdaki XML verilen:</span><span class="sxs-lookup"><span data-stu-id="4178c-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="4178c-148">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="4178c-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="4178c-149">Her ikisi de aşağıdaki kodda, anlaşılabilir ve **bDeğer** olduğu **System.Boolean.True**:</span><span class="sxs-lookup"><span data-stu-id="4178c-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="4178c-150">Tek bir dizeye</span><span class="sxs-lookup"><span data-stu-id="4178c-150">String to Single</span></span>  
 <span data-ttu-id="4178c-151">Aşağıdaki tabloda, ne tür bir dizeye dönüştürürken verilen Giriş dizeleri için oluşturulur gösterir bir **tek** kullanarak **ToSingle** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4178c-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="4178c-152">Giriş parametresi geçerli bir dize</span><span class="sxs-lookup"><span data-stu-id="4178c-152">Valid string input parameter</span></span>|<span data-ttu-id="4178c-153">.NET framework çıktı türü</span><span class="sxs-lookup"><span data-stu-id="4178c-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="4178c-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="4178c-154">"INF"</span></span>|<span data-ttu-id="4178c-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="4178c-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="4178c-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="4178c-156">"-INF"</span></span>|<span data-ttu-id="4178c-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="4178c-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="4178c-158">Çift için dize</span><span class="sxs-lookup"><span data-stu-id="4178c-158">String to Double</span></span>  
 <span data-ttu-id="4178c-159">Aşağıdaki tabloda, ne tür bir dizeye dönüştürürken verilen Giriş dizeleri için oluşturulur gösterir bir **tek** kullanarak **ToDouble** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4178c-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="4178c-160">Giriş parametresi geçerli bir dize</span><span class="sxs-lookup"><span data-stu-id="4178c-160">Valid string input parameter</span></span>|<span data-ttu-id="4178c-161">.NET framework çıktı türü</span><span class="sxs-lookup"><span data-stu-id="4178c-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="4178c-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="4178c-162">"INF"</span></span>|<span data-ttu-id="4178c-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="4178c-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="4178c-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="4178c-164">"-INF"</span></span>|<span data-ttu-id="4178c-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="4178c-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="4178c-166">Aşağıdaki kod yazma `<Infinity>INF</Infinity>`:</span><span class="sxs-lookup"><span data-stu-id="4178c-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="4178c-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4178c-167">See also</span></span>

- [<span data-ttu-id="4178c-168">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="4178c-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="4178c-169">.NET Framework Türlerini Dizelere Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="4178c-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)

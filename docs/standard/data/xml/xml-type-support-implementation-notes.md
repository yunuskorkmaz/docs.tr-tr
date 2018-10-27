---
title: XML tür desteği uygulama notları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73f786c8f1080d0046889958e8b3bd3165870569
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187458"
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="71009-102">XML tür desteği uygulama notları</span><span class="sxs-lookup"><span data-stu-id="71009-102">XML Type Support Implementation Notes</span></span>
<span data-ttu-id="71009-103">Bu konu, istediğiniz bazı uygulama ayrıntılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="71009-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="71009-104">Liste eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="71009-104">List Mappings</span></span>  
 <span data-ttu-id="71009-105"><xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Türü []**, ve <xref:System.String> türleri XML Şeması Tanım Dili (XSD) liste türleri temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71009-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="71009-106">Birleşim eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="71009-106">Union Mappings</span></span>  
 <span data-ttu-id="71009-107">Birleşim türleri kullanılarak temsil edilir <xref:System.Xml.Schema.XmlAtomicValue> veya <xref:System.String> türü.</span><span class="sxs-lookup"><span data-stu-id="71009-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="71009-108">Kaynak türü veya hedef türüne bu nedenle her zaman olmalıdır <xref:System.String> veya <xref:System.Xml.Schema.XmlAtomicValue>.</span><span class="sxs-lookup"><span data-stu-id="71009-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="71009-109">Varsa <xref:System.Xml.Schema.XmlSchemaDatatype> nesnesini gösteren bir liste türü giriş dizesindeki bir veya daha fazla nesne listesi için değer nesnesi dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="71009-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="71009-110">Varsa <xref:System.Xml.Schema.XmlSchemaDatatype> giriş değeri bir birleşimin üyesi türü olarak ayrıştırmak için bir girişimde sonra bir birleşim türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71009-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="71009-111">Ayrıştırma girişimi başarısız olursa sonra dönüştürme sonraki birleşim üyesi ile vb. Dönüştürme başarılı olana veya bir özel durum, bu durumda denemek için diğer bir üye türleri atılana kadar denenir.</span><span class="sxs-lookup"><span data-stu-id="71009-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="71009-112">CLR ve XML veri türleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="71009-112">Differences Between CLR and XML Data Types</span></span>  
 <span data-ttu-id="71009-113">CLR türleri ve XML veri türleri arasında nasıl işleneceğini oluşabilecek belirli eşleşmeler aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="71009-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71009-114">`xs` Önek eşlenmiş durumda <https://www.w3.org/2001/XMLSchema> ve ad alanı URI.</span><span class="sxs-lookup"><span data-stu-id="71009-114">The `xs` prefix is mapped to the <https://www.w3.org/2001/XMLSchema> and namespace URI.</span></span>
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="71009-115">System.TimeSpan ve xs: Duration</span><span class="sxs-lookup"><span data-stu-id="71009-115">System.TimeSpan and xs:duration</span></span>  
 <span data-ttu-id="71009-116">`xs:duration` Türü, farklı belirli süre değer vardır ancak kısmen sıralandığına.</span><span class="sxs-lookup"><span data-stu-id="71009-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="71009-117">İçin diğer bir deyişle `xs:duration` türü değeri 1 ay (P1M) gibi 32 günden (P32D) (P27D) 27 gün sayısından daha büyük olduğu ve 28, 29 veya 30 gün eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="71009-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="71009-118"><xref:System.TimeSpan> Sınıfı kısmi sıralanması desteklemez.</span><span class="sxs-lookup"><span data-stu-id="71009-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="71009-119">Bunun yerine, belirli sayıda gün boyunca 1 yıl ve 1 ay seçer; 365 gün ve 30 gün sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="71009-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="71009-120">Daha fazla bilgi için `xs:duration` yazın, bkz: W3C [XML şema bölümü 2: veri türleri öneri](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="71009-120">For more information on the `xs:duration` type, see the W3C [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="71009-121">System.DateTime xs: Time ve Gregoryen tarihi türleri</span><span class="sxs-lookup"><span data-stu-id="71009-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  
 <span data-ttu-id="71009-122">Olduğunda bir `xs:time` değeri eşlenmiş durumda bir <xref:System.DateTime> nesnesi <xref:System.DateTime.MinValue> tarih özelliklerini başlatmak için kullanılan alanı <xref:System.DateTime> nesne (gibi <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, ve <xref:System.DateTime.Day%2A>) en küçük olası <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="71009-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="71009-123">Benzer şekilde, örneklerini `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` ve `xs:gMonthDay` de eşleştirilmiş bir <xref:System.DateTime> nesne.</span><span class="sxs-lookup"><span data-stu-id="71009-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="71009-124">Kullanılmayan özellikleri <xref:System.DateTime> nesne başlatıldığı olanlardan <xref:System.DateTime.MinValue>.</span><span class="sxs-lookup"><span data-stu-id="71009-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71009-125">Üzerinde güvenemezsiniz <xref:System.DateTime.Year%2A?displayProperty=nameWithType> değer olarak içerik yazıldığında `xs:gMonthDay`.</span><span class="sxs-lookup"><span data-stu-id="71009-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="71009-126"><xref:System.DateTime.Year%2A?displayProperty=nameWithType> Değeri her zaman ayarı 1904 için böyle bir durumda.</span><span class="sxs-lookup"><span data-stu-id="71009-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="71009-127">xs:anyURI ve System.Uri</span><span class="sxs-lookup"><span data-stu-id="71009-127">xs:anyURI and System.Uri</span></span>  
 <span data-ttu-id="71009-128">Örneği `xs:anyURI` temsil için göreli bir URI eşlenmiş bir <xref:System.Uri>, <xref:System.Uri> nesnesinin temel URI'sini yok.</span><span class="sxs-lookup"><span data-stu-id="71009-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71009-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71009-129">See also</span></span>

- [<span data-ttu-id="71009-130">System.Xml Sınıflarında Tür Desteği</span><span class="sxs-lookup"><span data-stu-id="71009-130">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)

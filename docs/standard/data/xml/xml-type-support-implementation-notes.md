---
title: "XML türü destek uygulama notları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e99573fc3a82db7798426172a13a78e10c65636
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="142fc-102">XML türü destek uygulama notları</span><span class="sxs-lookup"><span data-stu-id="142fc-102">XML Type Support Implementation Notes</span></span>
<span data-ttu-id="142fc-103">Bu konuda farkında olmasını istediğiniz bazı uygulama ayrıntıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="142fc-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="142fc-104">Liste eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="142fc-104">List Mappings</span></span>  
 <span data-ttu-id="142fc-105"><xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Yazın []**, ve <xref:System.String> türleri XML Şeması Tanım Dili (XSD) liste türleri temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="142fc-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="142fc-106">Birleşim eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="142fc-106">Union Mappings</span></span>  
 <span data-ttu-id="142fc-107">Birleşim türleri temsil kullanarak <xref:System.Xml.Schema.XmlAtomicValue> veya <xref:System.String> türü.</span><span class="sxs-lookup"><span data-stu-id="142fc-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="142fc-108">Kaynak türü veya hedef türü bu nedenle her zaman ya da olmalıdır <xref:System.String> veya <xref:System.Xml.Schema.XmlAtomicValue>.</span><span class="sxs-lookup"><span data-stu-id="142fc-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="142fc-109">Varsa <xref:System.Xml.Schema.XmlSchemaDatatype> nesnesini temsil eden bir liste türü giriş dizesi bir veya daha fazla nesnelerin bir listesini için değer nesnesi dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="142fc-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="142fc-110">Varsa <xref:System.Xml.Schema.XmlSchemaDatatype> giriş değeri UNION bir üye türü ayrıştırmak için bir girişimde sonra bir birleşim türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142fc-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="142fc-111">Ayrıştırma denemesi başarısız olursa sonra dönüştürme UNION sonraki üyesiyle vb. Dönüştürme başarılı olur veya; bu durumda bir özel durum denemek için başka bir üye türleri değiştirilene kadar denenir.</span><span class="sxs-lookup"><span data-stu-id="142fc-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="142fc-112">CLR ve XML veri türleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="142fc-112">Differences Between CLR and XML Data Types</span></span>  
 <span data-ttu-id="142fc-113">CLR türleri ve XML veri türleri arasında nasıl işleneceğini oluşabilir belirli uyuşmazlıkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="142fc-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="142fc-114">`xs` Http://www.w3.org/2001/XMLSchema ve ad alanı URI öneki eşlenmedi.</span><span class="sxs-lookup"><span data-stu-id="142fc-114">The `xs` prefix is mapped to the http://www.w3.org/2001/XMLSchema and namespace URI.</span></span>  
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="142fc-115">System.TimeSpan ve xs: Duration</span><span class="sxs-lookup"><span data-stu-id="142fc-115">System.TimeSpan and xs:duration</span></span>  
 <span data-ttu-id="142fc-116">`xs:duration` Türü kısmen sipariş edilen, farklı belirli süre değer vardır ancak eşdeğer.</span><span class="sxs-lookup"><span data-stu-id="142fc-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="142fc-117">Bunun için anlamı `xs:duration` türü değeri 1 ay (P1M) gibi 32 günden az (P32D) (P27D) 27 gün sayısından daha büyük olduğundan ve 28, 29 veya 30 gün olarak.</span><span class="sxs-lookup"><span data-stu-id="142fc-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="142fc-118"><xref:System.TimeSpan> Sınıfı Bu kısmi sıralanması desteklemez.</span><span class="sxs-lookup"><span data-stu-id="142fc-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="142fc-119">Bunun yerine, belirli bir gün için 1 yıl 1 ay sayısı seçer; 365 gün ve 30 gün sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="142fc-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="142fc-120">Daha fazla bilgi için `xs:duration` yazın, W3C XML Şeması Kısım 2 bkz: http://www.w3.org/TR/xmlschema-2/ adresindeki veri türleri öneri.</span><span class="sxs-lookup"><span data-stu-id="142fc-120">For more information on the `xs:duration` type, see the W3C XML Schema Part 2: Datatypes Recommendation at http://www.w3.org/TR/xmlschema-2/.</span></span>  
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="142fc-121">xs: Time, Gregoryen tarih türleri ve System.DateTime</span><span class="sxs-lookup"><span data-stu-id="142fc-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  
 <span data-ttu-id="142fc-122">Zaman bir `xs:time` değeri eşleştirilir bir <xref:System.DateTime> nesnesi <xref:System.DateTime.MinValue> alan tarih özelliklerini başlatmak için kullanılan <xref:System.DateTime> nesne (gibi <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, ve <xref:System.DateTime.Day%2A>) en küçük olası <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="142fc-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="142fc-123">Benzer şekilde, örneklerini `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` ve `xs:gMonthDay` için de eşlenen bir <xref:System.DateTime> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="142fc-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="142fc-124">Kullanılmayan özellikleri <xref:System.DateTime> nesne başlatılmış olanlardan için <xref:System.DateTime.MinValue>.</span><span class="sxs-lookup"><span data-stu-id="142fc-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="142fc-125">Bağlı olamaz <xref:System.DateTime.Year%2A?displayProperty=nameWithType> değeri olarak içerik yazıldığında `xs:gMonthDay`.</span><span class="sxs-lookup"><span data-stu-id="142fc-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="142fc-126"><xref:System.DateTime.Year%2A?displayProperty=nameWithType> Değeri her zaman ayarlanır 1904 ile bu durumda.</span><span class="sxs-lookup"><span data-stu-id="142fc-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="142fc-127">xs:anyURI ve System.Uri</span><span class="sxs-lookup"><span data-stu-id="142fc-127">xs:anyURI and System.Uri</span></span>  
 <span data-ttu-id="142fc-128">Bir örneği olduğunda `xs:anyURI` temsil için göreli URI eşlenen bir <xref:System.Uri>, <xref:System.Uri> nesnesinin bir taban URI yok.</span><span class="sxs-lookup"><span data-stu-id="142fc-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="142fc-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="142fc-129">See Also</span></span>  
 [<span data-ttu-id="142fc-130">System.Xml sınıflardaki türü desteği</span><span class="sxs-lookup"><span data-stu-id="142fc-130">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)

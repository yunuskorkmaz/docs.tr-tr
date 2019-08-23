---
title: XML Tür Desteği Uygulama Notları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 817d48e15f3a1d370e1953ca9c9aa8e10baa7f29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916029"
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="62666-102">XML Tür Desteği Uygulama Notları</span><span class="sxs-lookup"><span data-stu-id="62666-102">XML Type Support Implementation Notes</span></span>
<span data-ttu-id="62666-103">Bu konuda, farkında olmak istediğiniz bazı uygulama ayrıntıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62666-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="62666-104">Eşlemeleri Listele</span><span class="sxs-lookup"><span data-stu-id="62666-104">List Mappings</span></span>  
 <span data-ttu-id="62666-105"><xref:System.Collections.IList> ,<xref:System.Collections.ICollection>,, **Türü []** ve<xref:System.String> türleri XML şeması tanım dili (xsd) liste türlerini temsil etmek için kullanılır. <xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="62666-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="62666-106">Birleşim eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="62666-106">Union Mappings</span></span>  
 <span data-ttu-id="62666-107">Birleşim türleri <xref:System.Xml.Schema.XmlAtomicValue> veya <xref:System.String> türü kullanılarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="62666-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="62666-108">Bu nedenle, kaynak türü veya hedef türü her zaman ya <xref:System.String> <xref:System.Xml.Schema.XmlAtomicValue>da olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62666-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="62666-109"><xref:System.Xml.Schema.XmlSchemaDatatype> Nesne bir liste türünü temsil ediyorsa, nesne giriş dize değerini bir veya daha fazla nesne listesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="62666-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="62666-110">Eğer bir <xref:System.Xml.Schema.XmlSchemaDatatype> birleşim türünü temsil ediyorsa, giriş değerini birleşimin üye türü olarak ayrıştırmaya yönelik bir girişim yapılır.</span><span class="sxs-lookup"><span data-stu-id="62666-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="62666-111">Ayrıştırma denemesi başarısız olursa, dönüştürme işleminin bir sonraki üyesi ile denenir ve dönüştürme başarılı olana kadar ya da denenecek başka hiçbir üye türü yoksa, bu durumda bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="62666-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="62666-112">CLR ve XML veri türleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="62666-112">Differences Between CLR and XML Data Types</span></span>  
 <span data-ttu-id="62666-113">Aşağıda, CLR türleri ve XML veri türleri arasında oluşabilecek bazı uyuşmazlıklar ve bunların nasıl işlendiği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62666-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62666-114">Ön ek <https://www.w3.org/2001/XMLSchema> ve ad alanı URI 'sine eşlenir. `xs`</span><span class="sxs-lookup"><span data-stu-id="62666-114">The `xs` prefix is mapped to the <https://www.w3.org/2001/XMLSchema> and namespace URI.</span></span>
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="62666-115">System. TimeSpan ve xs: Duration</span><span class="sxs-lookup"><span data-stu-id="62666-115">System.TimeSpan and xs:duration</span></span>  
 <span data-ttu-id="62666-116">`xs:duration` Tür, farklı ancak eşdeğer olan belirli Duration değerleri olacak şekilde kısmen sıralanır.</span><span class="sxs-lookup"><span data-stu-id="62666-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="62666-117">Bu, 1 ay ( `xs:duration` P1M) gibi tür değeri için 32 günden (p32d), 27 günden (P27D) daha büyük ve 28, 29 veya 30 güne eşit olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="62666-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="62666-118"><xref:System.TimeSpan> Sınıfı bu kısmi sıralamayı desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="62666-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="62666-119">Bunun yerine, 1 yıl ve 1 ay için belirli sayıda gün seçer; 365 gün ve 30 gün sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="62666-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="62666-120">`xs:duration` Tür hakkında daha fazla bilgi için bkz. W3C [XML şeması Bölüm 2: Veri türleri](https://www.w3.org/TR/xmlschema-2/)önerisi.</span><span class="sxs-lookup"><span data-stu-id="62666-120">For more information on the `xs:duration` type, see the W3C [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="62666-121">xs: Time, Gregoryen tarih türleri ve System. DateTime</span><span class="sxs-lookup"><span data-stu-id="62666-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  
 <span data-ttu-id="62666-122"><xref:System.DateTime> <xref:System.DateTime.MinValue> <xref:System.DateTime.Day%2A> <xref:System.DateTime.Month%2A>Bir değer bir nesneyle eşlendiğinde, <xref:System.DateTime> nesnenin Tarihözelliklerini(örneğin,,ve)mümkünolanenküçükdeğere(,ve)başlatmakiçinalanıkullanılır<xref:System.DateTime.Year%2A> `xs:time` <xref:System.DateTime> değer.</span><span class="sxs-lookup"><span data-stu-id="62666-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="62666-123">Benzer şekilde,, `xs:gMonth`, `xs:gDay` `xs:gYearMonth` ve `xs:gYear` örnekleride<xref:System.DateTime> bir nesneye eşlenir. `xs:gMonthDay`</span><span class="sxs-lookup"><span data-stu-id="62666-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="62666-124">Nesnedeki kullanılmayan özellikler, <xref:System.DateTime> öğesinden <xref:System.DateTime.MinValue>bu bilgisayarlara başlatılır.</span><span class="sxs-lookup"><span data-stu-id="62666-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62666-125">İçerik olarak <xref:System.DateTime.Year%2A?displayProperty=nameWithType> `xs:gMonthDay`yazıldığında değere güvenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62666-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="62666-126">Bu <xref:System.DateTime.Year%2A?displayProperty=nameWithType> durumda değer her zaman 1904 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="62666-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="62666-127">xs: anyURI ve System. Uri</span><span class="sxs-lookup"><span data-stu-id="62666-127">xs:anyURI and System.Uri</span></span>  
 <span data-ttu-id="62666-128">Göreli bir URI 'yi `xs:anyURI` temsil eden öğesinin bir örneği bir <xref:System.Uri>ile eşlendiğinde, <xref:System.Uri> nesnenin temel URI 'si yoktur.</span><span class="sxs-lookup"><span data-stu-id="62666-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62666-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62666-129">See also</span></span>

- [<span data-ttu-id="62666-130">System.Xml Sınıflarında Tür Desteği</span><span class="sxs-lookup"><span data-stu-id="62666-130">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)

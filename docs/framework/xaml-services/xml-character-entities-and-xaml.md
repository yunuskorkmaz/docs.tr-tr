---
title: "XML Karakter Varlıkları ve XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
caps.latest.revision: "23"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5973c67b26e07bba69383cc625ff34493d825a41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-character-entities-and-xaml"></a><span data-ttu-id="e148e-102">XML Karakter Varlıkları ve XAML</span><span class="sxs-lookup"><span data-stu-id="e148e-102">XML Character Entities and XAML</span></span>
<span data-ttu-id="e148e-103">XAML için özel karakterler XML dosyasında tanımlanan karakter varlıkları kullanır.</span><span class="sxs-lookup"><span data-stu-id="e148e-103">XAML uses character entities defined in XML for special characters.</span></span> <span data-ttu-id="e148e-104">Bu konuda, bazı belirli karakter varlıkları ve XAML diğer XML kavramlarına genel konular açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e148e-104">This topic describes some specific character entities and general considerations for other XML concepts in XAML.</span></span>  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a><span data-ttu-id="e148e-105">Karakter varlıkları ve XAML için benzersiz kaçış sorunları</span><span class="sxs-lookup"><span data-stu-id="e148e-105">Character Entities and Escaping Issues That Are Unique to XAML</span></span>  
 <span data-ttu-id="e148e-106">XAML biçimlendirme genellikle aynı karakter varlıkları ve XML içinde tanımlanan çıkış sıraları kullanır.</span><span class="sxs-lookup"><span data-stu-id="e148e-106">XAML markup typically uses the same character entities and escape sequences that are defined in XML.</span></span>  
  
 <span data-ttu-id="e148e-107">Ana istisnadır, küme ayraçları ({ve}) tarafından ayraçlar bir karakter dizisi işaretleme uzantısı anlaşılması gereken XAML işlemci bu karakterleri bildirmek için XAML'de önemi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e148e-107">The main exception is that braces ({ and }) have significance in XAML because these characters inform a XAML processor that a character sequence enclosed by braces must be interpreted as a markup extension.</span></span> <span data-ttu-id="e148e-108">Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [işaretleme uzantılarına genel bakış XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e148e-108">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
 <span data-ttu-id="e148e-109">Ancak, yine küme ayraçları değişmez değer karakter olarak XAML XML yerine belirli bir kaçış dizisi kullanarak görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e148e-109">However, you can still display the braces as literal characters by using an escape sequence that is particular to XAML instead of XML.</span></span> <span data-ttu-id="e148e-110">Daha fazla bilgi için bkz: [{} kaçış sırası - biçimlendirme uzantısı](escape-sequence-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="e148e-110">For more information, see [{} Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).</span></span>  
  
 <span data-ttu-id="e148e-111">Unutmayın bir ters eğik çizgi (\\) bir dize olarak işlendiğinde bir kaçış sırası gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="e148e-111">Note that a backslash (\\) does not require an escape sequence when it is handled as a string.</span></span>  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a><span data-ttu-id="e148e-112">XML karakter varlıkları</span><span class="sxs-lookup"><span data-stu-id="e148e-112">XML Character Entities</span></span>  
 <span data-ttu-id="e148e-113">Daha önce belirtildiği gibi çoğu karakter varlıkları ve XAML işaretleme yazmak için genellikle kullanılan kaçış sıraları XML tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e148e-113">As mentioned previously, most character entities and escape sequences that are typically used to write XAML markup are defined by XML.</span></span> <span data-ttu-id="e148e-114">Bu konu, bu varlıkları tam listesi sağlamaz; varlıklar için ayrıntılı başvuru dış belgelerinde gibi XML belirtimleri bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e148e-114">This topic does not provide the complete list of these entities; a detailed reference for the entities can be found in external documentation, such as in XML specifications.</span></span> <span data-ttu-id="e148e-115">Ancak, kolaylık olması için bu konuda bazı XAML biçimlendirme genelde kullanılan belirli XML karakter varlıkları listelenir.</span><span class="sxs-lookup"><span data-stu-id="e148e-115">However, for convenience, this topic lists some of the specific XML character entities that are typically used in XAML markup.</span></span>  
  
|<span data-ttu-id="e148e-116">Karakter</span><span class="sxs-lookup"><span data-stu-id="e148e-116">Character</span></span>|<span data-ttu-id="e148e-117">Varlık</span><span class="sxs-lookup"><span data-stu-id="e148e-117">Entity</span></span>|<span data-ttu-id="e148e-118">Notlar</span><span class="sxs-lookup"><span data-stu-id="e148e-118">Notes</span></span>|  
|---------------|------------|-----------|  
|<span data-ttu-id="e148e-119">& (ve işareti)</span><span class="sxs-lookup"><span data-stu-id="e148e-119">& (ampersand)</span></span>|&amp;|<span data-ttu-id="e148e-120">Öznitelik değeri hem bir öğenin içeriğini kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e148e-120">Must be used both for attribute values and for content of an element.</span></span>|  
|<span data-ttu-id="e148e-121">> (büyük-karakter daha)</span><span class="sxs-lookup"><span data-stu-id="e148e-121">> (greater-than character)</span></span>|&gt;|<span data-ttu-id="e148e-122">Bir öznitelik değeri için kullanılması gereken ancak > sürece bir öğenin içeriğini olarak kabul edilebilir < önce gelmez.</span><span class="sxs-lookup"><span data-stu-id="e148e-122">Must be used for an attribute value, but > is acceptable as the content of an element as long as < does not precede it.</span></span>|  
|<span data-ttu-id="e148e-123">< (daha az-karakter daha)</span><span class="sxs-lookup"><span data-stu-id="e148e-123">< (less-than character)</span></span>|&lt;|<span data-ttu-id="e148e-124">Bir öznitelik değeri için kullanılması gereken ancak \< sürece bir öğenin içeriğini olarak kabul edilebilir > bunu izlemez.</span><span class="sxs-lookup"><span data-stu-id="e148e-124">Must be used for an attribute value, but \< is acceptable as the content of an element as long as > does not follow it.</span></span>|  
|<span data-ttu-id="e148e-125">"(düz tırnak işareti)</span><span class="sxs-lookup"><span data-stu-id="e148e-125">" (straight quotation mark)</span></span>|&quot;|<span data-ttu-id="e148e-126">Bir öznitelik değeri için kullanılması gereken ancak düz tırnak işareti (") öğenin içerik kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e148e-126">Must be used for an attribute value, but a straight quotation mark (") is acceptable as the content of an element.</span></span> <span data-ttu-id="e148e-127">Öznitelik değerleri düz tek tırnak işareti (') veya ("); düz tırnak işareti içine olduğunu unutmayın hangi karakter ilk olarak görünür öznitelik değeri muhafaza tanımlar ve alternatif teklif ardından değeri içinde bir hazır değer olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e148e-127">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="e148e-128">' (düz tek tırnak işareti)</span><span class="sxs-lookup"><span data-stu-id="e148e-128">' (single straight quotation mark)</span></span>|&apos;|<span data-ttu-id="e148e-129">Bir öznitelik değeri için kullanılması gereken ancak düz tek tırnak işareti (') öğenin içerik kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e148e-129">Must be used for an attribute value, but a single straight quotation mark (') is acceptable as the content of an element.</span></span> <span data-ttu-id="e148e-130">Öznitelik değerleri düz tek tırnak işareti (') veya ("); düz tırnak işareti içine olduğunu unutmayın hangi karakter ilk olarak görünür öznitelik değeri muhafaza tanımlar ve alternatif teklif ardından değeri içinde bir hazır değer olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e148e-130">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="e148e-131">(sayısal karakter eşlemeleri)</span><span class="sxs-lookup"><span data-stu-id="e148e-131">(numeric character mappings)</span></span>|<span data-ttu-id="e148e-132">&#*[tamsayı]* ; veya & #x*[onaltılık]*;</span><span class="sxs-lookup"><span data-stu-id="e148e-132">&#*[integer]*; or &#x*[hex]*;</span></span>|<span data-ttu-id="e148e-133">XAML etkin olan kodlama içine sayısal karakter eşlemeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="e148e-133">XAML supports numeric character mappings into the encoding that is active.</span></span>|  
|<span data-ttu-id="e148e-134">(bölünemez boşluk)</span><span class="sxs-lookup"><span data-stu-id="e148e-134">(nonbreaking space)</span></span>|<span data-ttu-id="e148e-135">&\#160; (UTF-8 kodlaması varsayılarak)</span><span class="sxs-lookup"><span data-stu-id="e148e-135">&\#160; (assuming UTF-8 encoding)</span></span>|<span data-ttu-id="e148e-136">Akış belge öğeleri ya da metin WPF gibi ele öğeleri için <xref:System.Windows.Controls.TextBox>, bölünemez boşluklar Normalleştirilmemiş biçimlendirme dışında için bile `xml:space="default"`.</span><span class="sxs-lookup"><span data-stu-id="e148e-136">For flow document elements, or elements that take text such as the WPF <xref:System.Windows.Controls.TextBox>, nonbreaking spaces are not normalized out of the markup, even for `xml:space="default"`.</span></span> <span data-ttu-id="e148e-137">(Daha fazla bilgi için bkz: [XAML'de boşluk işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span><span class="sxs-lookup"><span data-stu-id="e148e-137">(For more information, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span></span>|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a><span data-ttu-id="e148e-138">XML açıklama biçimi</span><span class="sxs-lookup"><span data-stu-id="e148e-138">XML Comment Format</span></span>  
 <span data-ttu-id="e148e-139">XAML XML açıklama biçimi kullanır: açıklama başlangıç `<!--`, yorum sonudur `-->,` ve sıra `--` içinde yorum oluşamaz.</span><span class="sxs-lookup"><span data-stu-id="e148e-139">XAML uses the XML comment format: the start of the comment is `<!--`, the end of comment is `-->,` and the sequence `--` must not occur within the comment.</span></span>  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a><span data-ttu-id="e148e-140">XML işleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e148e-140">XML Processing Instructions</span></span>  
 <span data-ttu-id="e148e-141">XAML XML işleme yönergelerini yönergeleri aracılığıyla geçirilmelidir state XML belirtimlerine uygun işler.</span><span class="sxs-lookup"><span data-stu-id="e148e-141">XAML handles XML processing instructions according to XML specifications, which state that the instructions must be passed through.</span></span> <span data-ttu-id="e148e-142">.NET Framework XAML hizmetlerinde işleme XAML işleme yönergeleri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="e148e-142">XAML processing in .NET Framework XAML Services  does not use any processing instructions.</span></span> <span data-ttu-id="e148e-143">XAML kullanmak varolan diğer çerçeveler XAML işleme yönergeleri de kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e148e-143">Other existing frameworks that use XAML also do not use processing instructions from XAML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e148e-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e148e-144">See Also</span></span>  
 [<span data-ttu-id="e148e-145">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="e148e-145">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="e148e-146">Biçimlendirme uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="e148e-146">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="e148e-147">XamlName dilbilgisi</span><span class="sxs-lookup"><span data-stu-id="e148e-147">XamlName Grammar</span></span>](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [<span data-ttu-id="e148e-148">XAML'de boşluk işleme</span><span class="sxs-lookup"><span data-stu-id="e148e-148">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)

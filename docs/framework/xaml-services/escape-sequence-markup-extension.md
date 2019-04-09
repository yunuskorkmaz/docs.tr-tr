---
title: '{} Çıkış sırası - işaretleme uzantısı'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: 9f6743dd8a82891ac2233978550e5679130de0be
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182083"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="7931b-102">{} Kaçış Dizisi / İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="7931b-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="7931b-103">XAML kaçış dizisi, öznitelik değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7931b-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="7931b-104">Kaçış sırası bundan sonraki değerlere öznitelik değişmez değer olarak yorumlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7931b-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="7931b-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7931b-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="7931b-106">XAML Özellik Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7931b-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7931b-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="7931b-107">XAML Values</span></span>  
  
|||  
|-|-|  
|*<span data-ttu-id="7931b-108">literalValue</span><span class="sxs-lookup"><span data-stu-id="7931b-108">literalValue</span></span>*|<span data-ttu-id="7931b-109">Kaçış sırası aşağıdaki değişmez değer dize.</span><span class="sxs-lookup"><span data-stu-id="7931b-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="7931b-110">Genellikle bu dize bir açma veya kapatma ayracı içeriyor ({veya}).</span><span class="sxs-lookup"><span data-stu-id="7931b-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7931b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7931b-111">Remarks</span></span>  
 <span data-ttu-id="7931b-112">Kaçış dizisi ({}) açık küme ayracı ({}) XAML değişmez bir karakter olarak kullanılabilir olacak şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7931b-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="7931b-113">XAML okuyucular açık küme ayracı ({}) genellikle bir işaretleme uzantısı giriş noktasını belirtmek için kullanılır; ancak, bunlar ilk kapanış ayracından (}) olup olmadığını belirlemek için sonraki karakteri kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="7931b-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="7931b-114">Yalnızca ne zaman iki küme ayraçları ({}) bitişik olan, bunlar bir kaçış dizisi kabul şunlardır.</span><span class="sxs-lookup"><span data-stu-id="7931b-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="7931b-115">XAML okuyucu dizenin geri kalanı, kaçış dizisi ile karşılaşırsa, bir dize olarak işlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7931b-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="7931b-116">Ancak kaçış sırası üyesi olan bir tür dönüştürücüsü uygulanırsa, XAML yazıcı tarafından yorumlandığında dize türü dönüşümünü uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7931b-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="7931b-117">Kaçış dizisi, bir işaretleme uzantısı değil ve bir sınıf tarafından yedeklenmez.</span><span class="sxs-lookup"><span data-stu-id="7931b-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="7931b-118">Ancak, XAML okuyucular (özel XAML okuyucular dahil) dikkate bir kuralı olur.</span><span class="sxs-lookup"><span data-stu-id="7931b-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="7931b-119">Tırnak işareti ("), bu şekilde bir kaçış dizisi olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7931b-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="7931b-120">Tırnak işareti noncontent bir özellik için özellik değeri olarak ayarlanacak ihtiyacınız varsa, özellik öğesi sözdizimini kullanın ve özellik öğesi içinde bir dize olarak tırnak işareti girin veya bir XML karakter varlık kullanın.</span><span class="sxs-lookup"><span data-stu-id="7931b-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="7931b-121">İçerik özelliği için tüm içeriği tırnak işareti olabilir.</span><span class="sxs-lookup"><span data-stu-id="7931b-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="7931b-122">Kaçış dizisi ({}) bir XAML işaretleme uzantısı göründüğü bir konumda bir ad alanı niteleyicisi içermelidir bir XML türü belirtirken sık gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7931b-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="7931b-123">Bu, hemen bir eşittir işaretinden sonra (=) başlangıç XAML öznitelik değeri ve bir işaretleme uzantısı içerir.</span><span class="sxs-lookup"><span data-stu-id="7931b-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="7931b-124">Aşağıdaki örnek bir XAML öznitelik değeri başlangıcında görünür bir XML ad alanı için kaçış sıralarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7931b-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="7931b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7931b-125">See also</span></span>

- [<span data-ttu-id="7931b-126">XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları</span><span class="sxs-lookup"><span data-stu-id="7931b-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions-for-xaml.md)
- [<span data-ttu-id="7931b-127">XML Karakter Varlıkları ve XAML</span><span class="sxs-lookup"><span data-stu-id="7931b-127">XML Character Entities and XAML</span></span>](xml-character-entities-and-xaml.md)

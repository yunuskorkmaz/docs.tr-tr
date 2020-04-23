---
title: '{}Kaçış Sırası - Biçimlendirme Uzantısı'
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
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071747"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="05068-102">{}Kaçış sırası / biçimlendirme uzantısı</span><span class="sxs-lookup"><span data-stu-id="05068-102">{} Escape sequence / markup extension</span></span>

<span data-ttu-id="05068-103">Öznitelik değerleri için XAML kaçış sırasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="05068-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="05068-104">Kaçış sırası özniteliksonraki değerleri bir edebi olarak yorumlanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="05068-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="05068-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="05068-105">XAML Attribute Usage</span></span>

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a><span data-ttu-id="05068-106">XAML Özellik Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="05068-106">XAML Property Element Usage</span></span>

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="05068-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="05068-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="05068-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="05068-108">*literalValue*</span></span>|<span data-ttu-id="05068-109">Kaçış sırasını izleyen gerçek dize.</span><span class="sxs-lookup"><span data-stu-id="05068-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="05068-110">Genellikle bu dize açık veya yakın bir ayraç ({ veya }) içerir.</span><span class="sxs-lookup"><span data-stu-id="05068-110">Typically this string contains an open or close brace ({ or }).</span></span>|

## <a name="remarks"></a><span data-ttu-id="05068-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05068-111">Remarks</span></span>

<span data-ttu-id="05068-112">Kaçış sırası{}( ) böylece açık bir ayraç ({) XAML'de gerçek bir karakter olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05068-112">The escape sequence ({}) is used so that an open brace ({) can be used as a literal character in XAML.</span></span>

<span data-ttu-id="05068-113">XAML okuyucuları genellikle bir biçimlendirme uzantısı giriş noktasını belirtmek için açık ayraç ({) kullanır;</span><span class="sxs-lookup"><span data-stu-id="05068-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="05068-114">Yalnızca iki parantez bitişik{}olduğunda, bir kaçış sırası olarak kabul edilirler.</span><span class="sxs-lookup"><span data-stu-id="05068-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>

<span data-ttu-id="05068-115">Kaçış sırası ile karşılaşılırsa, XAML okuyucusunun dize geri kalanını bir dize olarak işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="05068-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="05068-116">Ancak, kaçış sırası bir tür dönüştürücüse bir üyeye uygulanırsa, bir XAML yazarı tarafından yorumlandığında dize tür dönüştürmeden geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05068-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>

<span data-ttu-id="05068-117">Kaçış sırası bir biçimlendirme uzantısı değildir ve bir sınıf tarafından desteklenen değildir.</span><span class="sxs-lookup"><span data-stu-id="05068-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="05068-118">Ancak, XAML okuyucuların (özel XAML okuyucuları dahil) saygı göstermesi gereken bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="05068-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>

<span data-ttu-id="05068-119">Tırnak işareti (") bu şekilde kaçış sırası olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="05068-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="05068-120">İçerik içermeyen bir özellik için özellik değeri olarak bir teklif işareti ayarlamanız gerekiyorsa, özellik öğesi sözdizimini kullanın ve teklif işaretini özellik öğesinin içine dize olarak yerleştirin veya bir XML karakter varlığı kullanın.</span><span class="sxs-lookup"><span data-stu-id="05068-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="05068-121">Bir içerik özelliği için teklif işareti içeriğin tamamı olabilir.</span><span class="sxs-lookup"><span data-stu-id="05068-121">For a content property, the quotation mark can be the entire content.</span></span>

<span data-ttu-id="05068-122">XAML{}biçimlendirme uzantısının görünebileceği bir konumda ad alanı niteleyicisi içermesi gereken bir XML türü belirtirken kaçış sırası ( ) sık sık gereklidir.</span><span class="sxs-lookup"><span data-stu-id="05068-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="05068-123">Bu konum, bir XAML öznitelik değerinin başlangıcını ve eşit bir işaretten hemen sonra bir biçimlendirme uzantısını içerir (=).</span><span class="sxs-lookup"><span data-stu-id="05068-123">This location includes the start of a XAML attribute value, and in a markup extension immediately after an equal sign (=).</span></span> <span data-ttu-id="05068-124">Aşağıdaki örnekte, XAML öznitelik değerinin başında görünen bir XML ad alanının kaçış sıraları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05068-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a><span data-ttu-id="05068-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05068-125">See also</span></span>

- [<span data-ttu-id="05068-126">XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları</span><span class="sxs-lookup"><span data-stu-id="05068-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions.md)
- [<span data-ttu-id="05068-127">XML Karakter Varlıkları ve XAML</span><span class="sxs-lookup"><span data-stu-id="05068-127">XML Character Entities and XAML</span></span>](xml-character-entities.md)

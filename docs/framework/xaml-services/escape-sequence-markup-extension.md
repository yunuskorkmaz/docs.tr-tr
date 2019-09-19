---
title: '{}Kaçış sırası-biçimlendirme uzantısı'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053870"
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="77748-102">{} Kaçış Dizisi / İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="77748-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="77748-103">Öznitelik değerleri için XAML kaçış sırası sağlar.</span><span class="sxs-lookup"><span data-stu-id="77748-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="77748-104">Kaçış sırası, öznitelikteki sonraki değerlerin bir değişmez değer olarak yorumlanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="77748-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="77748-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="77748-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="77748-106">XAML Özellik Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="77748-106">XAML Property Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="77748-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="77748-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77748-108">*Edevalue*</span><span class="sxs-lookup"><span data-stu-id="77748-108">*literalValue*</span></span>|<span data-ttu-id="77748-109">Kaçış dizisini izleyen sabit dize.</span><span class="sxs-lookup"><span data-stu-id="77748-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="77748-110">Genellikle bu dize bir açık veya kapalı küme ayracı ({veya}) içerir.</span><span class="sxs-lookup"><span data-stu-id="77748-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77748-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77748-111">Remarks</span></span>  
 <span data-ttu-id="77748-112">Kaçış sırası ({}), XAML 'de sabit karakter olarak bir açık küme ayracı ({) kullanılabilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77748-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="77748-113">XAML okuyucuları genellikle bir biçimlendirme uzantısının giriş noktasını belirtmek için açık küme ayracı ({) kullanır; ancak, bir kapanış ayracı (}) olup olmadığını anlamak için ilk olarak bir sonraki karakteri kontrol ederler.</span><span class="sxs-lookup"><span data-stu-id="77748-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="77748-114">Yalnızca iki küme ayracı ({}) bitişik olduğunda, bir kaçış sırası olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="77748-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="77748-115">Kaçış dizisine karşılaşılırsa, XAML okuyucusu dizenin geri kalanını dize olarak işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="77748-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="77748-116">Ancak, kaçış dizisi tür dönüştürücüsü olan bir üyeye uygulanmışsa, dize bir XAML yazıcı tarafından yorumlandığı zaman tür dönüştürmeye gidebilirler.</span><span class="sxs-lookup"><span data-stu-id="77748-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="77748-117">Kaçış sırası bir işaretleme uzantısı değildir ve bir sınıf tarafından yedeklenmez.</span><span class="sxs-lookup"><span data-stu-id="77748-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="77748-118">Ancak, XAML okuyucularının (özel XAML okuyucuları dahil) dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77748-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="77748-119">Tırnak işareti (") bu şekilde kaçış sırası olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="77748-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="77748-120">İçerik olmayan bir özellik için özellik değeri olarak bir tırnak işareti ayarlamanız gerekirse, özellik öğesi söz dizimini kullanın ve tırnak işaretini özellik öğesinin içine bir dize olarak yerleştirin veya bir XML karakter varlığı kullanın.</span><span class="sxs-lookup"><span data-stu-id="77748-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="77748-121">Bir içerik özelliği için, tırnak işareti tüm içerik olabilir.</span><span class="sxs-lookup"><span data-stu-id="77748-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="77748-122">Bir XAML biçimlendirme uzantısının{}görünebileceği bir konumda bir ad alanı niteleyicisi içermesi gereken bir xml türü belirtildiğinde, kaçış sırası () sıklıkla gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77748-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="77748-123">Bu, bir XAML öznitelik değerinin başlangıcını ve bir işaretleme uzantısı içinde, bir eşittir işaretinden (=) hemen sonra içerir.</span><span class="sxs-lookup"><span data-stu-id="77748-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="77748-124">Aşağıdaki örnek, bir XAML öznitelik değerinin başlangıcında görüntülenen bir XML ad alanı için kaçış dizilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77748-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="77748-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77748-125">See also</span></span>

- [<span data-ttu-id="77748-126">XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları</span><span class="sxs-lookup"><span data-stu-id="77748-126">Type Converters and Markup Extensions for XAML</span></span>](type-converters-and-markup-extensions-for-xaml.md)
- [<span data-ttu-id="77748-127">XML Karakter Varlıkları ve XAML</span><span class="sxs-lookup"><span data-stu-id="77748-127">XML Character Entities and XAML</span></span>](xml-character-entities-and-xaml.md)

---
title: "{} Kaçış sırası - biçimlendirme uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8419a1e89d5e94b9868b0fd1fb81540253efca5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="b018c-102">{} Çıkış Dizisi / İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="b018c-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="b018c-103">XAML kaçış sırası öznitelik değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b018c-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="b018c-104">Kaçış sırası bundan sonraki değerlere sabit değer olarak yorumlanması için özniteliğini verir.</span><span class="sxs-lookup"><span data-stu-id="b018c-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b018c-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b018c-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="b018c-106">XAML Özellik Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b018c-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b018c-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="b018c-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b018c-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="b018c-108">*literalValue*</span></span>|<span data-ttu-id="b018c-109">Kaçış sırası izleyen değişmez değer dize.</span><span class="sxs-lookup"><span data-stu-id="b018c-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="b018c-110">Genellikle bu dize bir açma veya kapatma parantezi içeriyor ({veya}).</span><span class="sxs-lookup"><span data-stu-id="b018c-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b018c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b018c-111">Remarks</span></span>  
 <span data-ttu-id="b018c-112">Böylece bir açma ayracı ({}) XAML'de değişmez değer karakter olarak kullanılan kaçış sırası ({}) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b018c-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="b018c-113">XAML okuyucuları açma ayracı ({}) genellikle bir işaretleme uzantısı giriş noktasını belirtmek için kullanın; Bununla birlikte, bunlar önce bir kapanış ayracı (}) olup olmadığını belirlemek için sonraki karakteri kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="b018c-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="b018c-114">Yalnızca iki kaşlı ayraçlar bitişik olduğunda, bir kaçış sırası olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b018c-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="b018c-115">Kaçış sırası karşılaşılırsa, XAML okuyucu dizenin geri kalanı bir dize olarak işleme.</span><span class="sxs-lookup"><span data-stu-id="b018c-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="b018c-116">Ancak, kaçış sırası tür dönüştürücüsünü sahip bir üye uyguladıysanız, XAML yazıcı tarafından değerlendirdiğinde dize türü dönüştürme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b018c-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="b018c-117">Kaçış sırası biçimlendirme uzantısı değil ve bir sınıf tarafından yedeklenen değil.</span><span class="sxs-lookup"><span data-stu-id="b018c-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="b018c-118">Ancak, XAML okuyucuları (özel XAML okuyucuları dahil) saygı bir kural gerekir.</span><span class="sxs-lookup"><span data-stu-id="b018c-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="b018c-119">Tırnak işareti ("), bu şekilde bir kaçış sırası olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b018c-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="b018c-120">Tırnak işareti noncontent bir özellik için özellik değeri olarak ayarlamak gerekiyorsa, özellik öğesi sözdizimini kullanın ve özellik öğe içindeki bir dize olarak tırnak işareti koyun veya bir XML karakteri varlık kullanın.</span><span class="sxs-lookup"><span data-stu-id="b018c-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="b018c-121">İçerik özelliği için tüm içeriği tırnak işareti olabilir.</span><span class="sxs-lookup"><span data-stu-id="b018c-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="b018c-122">Kaçış sırası ({}), bir ad alanı niteleyicisi XAML biçimlendirme uzantısı burada görünebilir bir konumda içermesi gereken bir XML türü belirtirken sık gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b018c-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="b018c-123">Bu başlangıç XAML öznitelik değeri ve bir işaretleme uzantısı hemen bir eşittir işaretinden sonra (=) içerir.</span><span class="sxs-lookup"><span data-stu-id="b018c-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="b018c-124">Aşağıdaki örnek çıkış sıraları XAML öznitelik değeri başlangıcında görünür bir XML ad alanı için gösterir.</span><span class="sxs-lookup"><span data-stu-id="b018c-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="b018c-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b018c-125">See Also</span></span>  
 [<span data-ttu-id="b018c-126">XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları</span><span class="sxs-lookup"><span data-stu-id="b018c-126">Type Converters and Markup Extensions for XAML</span></span>](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [<span data-ttu-id="b018c-127">XML Karakter Varlıkları ve XAML</span><span class="sxs-lookup"><span data-stu-id="b018c-127">XML Character Entities and XAML</span></span>](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)

---
title: x:Reference Biçimlendirme Uzantısı
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071383"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="55389-102">x:Reference Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="55389-102">x:Reference Markup Extension</span></span>

<span data-ttu-id="55389-103">XAML biçimlendirmesinde başka bir yerde bildirilen bir örneğe başvurur.</span><span class="sxs-lookup"><span data-stu-id="55389-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="55389-104">Başvuru, bir `x:Name`öğenin.</span><span class="sxs-lookup"><span data-stu-id="55389-104">The reference refers to an element's `x:Name`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="55389-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="55389-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="55389-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="55389-106">XAML Object Element Usage</span></span>

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="55389-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="55389-107">XAML Values</span></span>

|||
|-|-|
|`instancexName`|<span data-ttu-id="55389-108">Başvurulan örneğin `x:Name` değeri <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>(veya tanımlanan özelliğin değeri).</span><span class="sxs-lookup"><span data-stu-id="55389-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|

## <a name="remarks"></a><span data-ttu-id="55389-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55389-109">Remarks</span></span>

<span data-ttu-id="55389-110">`x:Reference`WPF gibi belirli çerçevelerde başka türlü uygulanan bir öğe başvuru kavramı için XAML dil düzeyinde destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="55389-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>

## <a name="xreference-and-wpf"></a><span data-ttu-id="55389-111">x:Referans ve WPF</span><span class="sxs-lookup"><span data-stu-id="55389-111">x:Reference and WPF</span></span>

<span data-ttu-id="55389-112">WPF ve XAML 2006'da, eleman başvuruları <xref:System.Windows.Data.Binding.ElementName%2A> bağlayıcıçerçeve düzeyindeki özelliğiyle ele alınır.</span><span class="sxs-lookup"><span data-stu-id="55389-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="55389-113">Çoğu WPF uygulaması ve senaryosu <xref:System.Windows.Data.Binding.ElementName%2A> için bağlama yine de kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55389-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="55389-114">Bu genel kılavuzun istisnaları, veri bağlamı veya veri bağlamayı pratik hale getiren diğer kapsamlandırma konularının bulunduğu ve biçimlendirme derlemenin söz konusu olmadığı durumları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="55389-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>

<span data-ttu-id="55389-115">`x:Reference`XAML 2009'da tanımlanan bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="55389-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="55389-116">WPF'de XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca WPF biçimlendirmesi derlenmiş olmayan XAML için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55389-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="55389-117">Biçimlendirmeyle derlenmiş XAML ve XAML'nin BAML formu şu anda XAML 2009 dil anahtar kelimelerini ve özelliklerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="55389-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>

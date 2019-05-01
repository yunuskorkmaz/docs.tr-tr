---
title: x:Reference Biçimlendirme Uzantısı
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938885"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="c91b3-102">x:Reference Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="c91b3-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="c91b3-103">XAML biçimlendirme içinde başka bir yerde bildirilmiş bir örneğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="c91b3-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="c91b3-104">Bir öğenin başvurusu başvuruyor `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="c91b3-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c91b3-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c91b3-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c91b3-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c91b3-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c91b3-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="c91b3-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="c91b3-108">`x:Name` Değeri (veya değerini <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-özelliği tanımlanmış) başvurulan örnek.</span><span class="sxs-lookup"><span data-stu-id="c91b3-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c91b3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c91b3-109">Remarks</span></span>  
 <span data-ttu-id="c91b3-110">`x:Reference` Aksi takdirde WPF gibi belirli çerçeveleri içinde uygulanmış bir öğe başvurusu kavramı için XAML dili düzeyinde destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c91b3-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="c91b3-111">x: Reference ve WPF</span><span class="sxs-lookup"><span data-stu-id="c91b3-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="c91b3-112">WPF ve XAML 2006'öğesi başvuru çerçeve düzeyi özelliği tarafından gönderilen <xref:System.Windows.Data.Binding.ElementName%2A> bağlama.</span><span class="sxs-lookup"><span data-stu-id="c91b3-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="c91b3-113">Çoğu WPF uygulamaları ve senaryolar için <xref:System.Windows.Data.Binding.ElementName%2A> bağlama yine de kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c91b3-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="c91b3-114">Veri bağlamı veya veri bağlama pratik hale diğer kapsanan konular olduğu ve işaretleme derleme sürecine dahil değildir, bu genel kılavuz için özel durumlar durumları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c91b3-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="c91b3-115">`x:Reference` XAML 2009'dan bir yapı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c91b3-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="c91b3-116">WPF, XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca XAML için WPF biçimlendirme derlenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="c91b3-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="c91b3-117">Biçimlendirme derlenmiş XAML ve BAML formu, XAML, XAML 2009 dil anahtar sözcükleri ve özellikleri şu anda desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c91b3-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>

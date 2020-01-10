---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 15fdc9d093bb3efb4ea4cef5d4cdfa8474042f12
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559753"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="f14dd-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="f14dd-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="f14dd-103">Bir <xref:System.Windows.Data.RelativeSource> bağlama kaynağının özelliklerini, bir [bağlama Işaretleme uzantısı](binding-markup-extension.md)içinde kullanılmak üzere veya xaml 'de kurulu bir <xref:System.Windows.Data.Binding> öğesinin <xref:System.Windows.Data.Binding.RelativeSource%2A> özelliğini ayarlarken belirler.</span><span class="sxs-lookup"><span data-stu-id="f14dd-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="f14dd-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="f14dd-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="f14dd-105">XAML Öznitelik Kullanımı (Bağlama uzantıları içinde iç içe geçmiş)</span><span class="sxs-lookup"><span data-stu-id="f14dd-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="f14dd-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="f14dd-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="f14dd-107">veya</span><span class="sxs-lookup"><span data-stu-id="f14dd-107">-or-</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a><span data-ttu-id="f14dd-108">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="f14dd-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="f14dd-109">Şunlardan biri:</span><span class="sxs-lookup"><span data-stu-id="f14dd-109">One of the following:</span></span><br /><br /> <span data-ttu-id="f14dd-110">-Dize belirteci `Self`; <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği <xref:System.Windows.Data.RelativeSourceMode.Self>olarak ayarlanmış şekilde oluşturulmuş bir <xref:System.Windows.Data.RelativeSource> karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="f14dd-111">-Dize belirteci `TemplatedParent`; <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>olarak ayarlanmış şekilde oluşturulmuş bir <xref:System.Windows.Data.RelativeSource> karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="f14dd-112">-Dize belirteci `PreviousData`; <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği <xref:System.Windows.Data.RelativeSourceMode.PreviousData>olarak ayarlanmış şekilde oluşturulmuş bir <xref:System.Windows.Data.RelativeSource> karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="f14dd-113">-`FindAncestor` mod hakkında daha fazla bilgi için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="f14dd-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="f14dd-114">Dize belirteci `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="f14dd-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="f14dd-115">Bu belirteci kullanmak, bir `RelativeSource` üst öğe türünü ve isteğe bağlı olarak bir üst düzeyi belirten bir mod girer.</span><span class="sxs-lookup"><span data-stu-id="f14dd-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="f14dd-116">Bu, <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>olarak ayarlanmış şekilde oluşturulmuş bir <xref:System.Windows.Data.RelativeSource> karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="f14dd-117">`FindAncestor` modu için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="f14dd-118"><xref:System.Windows.Data.RelativeSource.AncestorType%2A> özelliğini dolduran bir türün adı.</span><span class="sxs-lookup"><span data-stu-id="f14dd-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="f14dd-119">`FindAncestor` modu için isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f14dd-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="f14dd-120">Öncül düzeyi (Mantıksal ağaçta üst yön doğrultusunda değerlendirilen.)</span><span class="sxs-lookup"><span data-stu-id="f14dd-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="f14dd-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f14dd-121">Remarks</span></span>

<span data-ttu-id="f14dd-122">`{RelativeSource TemplatedParent}` bağlama kullanımları, bir denetimin kullanıcı arabiriminin ve denetimin mantığının ayrılma açısından daha büyük bir kavramı adresleyen önemli bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="f14dd-123">Bu, şablon tanımı içinden şablonlu üst öğeye (şablonun uygulandığı çalışma zamanı nesnesi örneği) bağlanmaya olanak verir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="f14dd-124">Bu durumda, [TemplateBinding Biçimlendirme Uzantısı](templatebinding-markup-extension.md) aslında aşağıdaki bağlama ifadesi için bir toplu özelliktir: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="f14dd-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="f14dd-125">`TemplateBinding` veya `{RelativeSource TemplatedParent}` kullanımları, yalnızca bir şablonu tanımlayan XAML içinde ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="f14dd-126">Daha fazla bilgi için bkz. [TemplateBinding Işaretleme uzantısı](templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="f14dd-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="f14dd-127">`{RelativeSource FindAncestor}`, bir denetimin her zaman belirli bir üst türün görsel ağacında olması beklenildiği durumlarda denetim şablonlarında veya tahmin edilebilir kendiliğinden dahil edilen kullanıcı arabirimi kompozisyonlarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="f14dd-128">Örneğin, bir öğe denetiminin öğeleri kendi öğelerinin özelliklerine bağlamak için `FindAncestor` kullanımları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="f14dd-129">Ya da bir şablonda denetim kompozisyonunun parçası olan öğeler, aynı bileşim yapısındaki üst öğelere `FindAncestor` bağlamaları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="f14dd-130">XAML sözdizimi bölümlerinde gösterilen `FindAncestor` modunun nesne öğesi söz diziminde, ikinci nesne öğesi sözdizimi özellikle `FindAncestor` modu için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="f14dd-131">`FindAncestor` modu <xref:System.Windows.Data.RelativeSource.AncestorType%2A> bir değer gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="f14dd-132">Aranacak üst öğe türüne bir [X:Type Işaretleme uzantısı](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) başvurusu kullanarak bir öznitelik olarak <xref:System.Windows.Data.RelativeSource.AncestorType%2A> ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="f14dd-133"><xref:System.Windows.Data.RelativeSource.AncestorType%2A> değeri, bağlama isteği çalışma zamanında işlendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="f14dd-134">`FindAncestor` modu için, isteğe bağlı özellik <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A>, öğe ağacında var olan bir türün birden fazla üst öğesi olduğu durumlarda üst aramanın belirsizliğini ortadan kaldırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f14dd-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="f14dd-135">`FindAncestor` modunun nasıl kullanılacağı hakkında daha fazla bilgi için bkz. <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="f14dd-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="f14dd-136">`{RelativeSource Self}`, bir örneğin bir özelliğinin aynı örneğe ait başka bir özelliğin değerine bağlı olması gereken ve bu iki özellik arasında (zorlama gibi) herhangi bir genel bağımlılık özelliği ilişkisinin zaten mevcut olduğu senaryolar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="f14dd-137">Her iki özellik de değerler özdeş (ve özdeş olarak yazılmış) gibi bir nesnede mevcut olsa da, `{RelativeSource Self}`olan bir bağlamaya `Converter` parametresi uygulayabilir ve kaynak ve hedef türleri arasında dönüştürme yapmak için dönüştürücüyü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f14dd-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="f14dd-138">`{RelativeSource Self}` için başka bir senaryo <xref:System.Windows.MultiDataTrigger>bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="f14dd-139">Örneğin, aşağıdaki XAML, <xref:System.Windows.FrameworkElement.Width%2A>için hangi değerin girildiğine bakılmaksızın <xref:System.Windows.Shapes.Rectangle> bir öğesi tanımlar, <xref:System.Windows.Shapes.Rectangle> her zaman bir kare olur: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="f14dd-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="f14dd-140">`{RelativeSource PreviousData}`, veri şablonlarında ya da bağlamaların veri kaynağı olarak bir koleksiyon kullandığı durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="f14dd-141">Koleksiyondaki bitişik veri öğeleri arasındaki ilişkileri vurgulamak için `{RelativeSource PreviousData}` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f14dd-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="f14dd-142">İlgili bir teknik, veri kaynağındaki geçerli ve önceki öğeler arasında bir <xref:System.Windows.Data.MultiBinding> oluşturmak ve bu bağlama üzerinde iki öğe ve özellikleri arasındaki farkı belirlemek için bir dönüştürücü kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="f14dd-143">Aşağıdaki örnekte, öğeler şablonundaki ilk <xref:System.Windows.Controls.TextBlock> geçerli numarayı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f14dd-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="f14dd-144">İkinci <xref:System.Windows.Controls.TextBlock> bağlama, genel olarak iki <xref:System.Windows.Data.Binding> yapısal olan bir <xref:System.Windows.Data.MultiBinding>: geçerli kayıt ve `{RelativeSource PreviousData}`kullanarak önceki veri kaydını kullanan bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="f14dd-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="f14dd-145">Daha sonra, <xref:System.Windows.Data.MultiBinding> bir dönüştürücü farkı hesaplar ve bağlamaya geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="f14dd-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
```

<span data-ttu-id="f14dd-146">Kavram olarak veri bağlamayı açıklamak burada ele alınmamalıdır, bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f14dd-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="f14dd-147">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.Data.RelativeSource> sınıfı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="f14dd-148">`RelativeSource`, biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="f14dd-149">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="f14dd-150">XAML 'deki tüm biçimlendirme uzantıları, `{` ve `}` karakterlerini öznitelik sözdiziminde kullanır. Bu, XAML işlemcisinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="f14dd-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="f14dd-151">Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f14dd-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f14dd-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f14dd-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="f14dd-153">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f14dd-153">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="f14dd-154">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="f14dd-154">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="f14dd-155">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="f14dd-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="f14dd-156">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f14dd-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="f14dd-157">Bağlama Bildirimlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f14dd-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="f14dd-158">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="f14dd-158">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)

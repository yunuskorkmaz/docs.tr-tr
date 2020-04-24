---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 6301299da966ade9b5cc7ccd105c8269a486744e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646225"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="4e054-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="4e054-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="4e054-103">[Bağlayıcı Biçimlendirme](binding-markup-extension.md)Uzantısı <xref:System.Windows.Data.RelativeSource> içinde veya XAML'de kurulan bir <xref:System.Windows.Data.Binding> öğenin <xref:System.Windows.Data.Binding.RelativeSource%2A> özelliğini ayarlarken kullanılacak bağlayıcı kaynağın özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e054-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="4e054-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4e054-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="4e054-105">XAML Öznitelik Kullanımı (Bağlama uzantıları içinde iç içe geçmiş)</span><span class="sxs-lookup"><span data-stu-id="4e054-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="4e054-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4e054-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="4e054-107">-veya-</span><span class="sxs-lookup"><span data-stu-id="4e054-107">-or-</span></span>

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

## <a name="xaml-values"></a><span data-ttu-id="4e054-108">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="4e054-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="4e054-109">Aşağıdakilerden biri:</span><span class="sxs-lookup"><span data-stu-id="4e054-109">One of the following:</span></span><br /><br /> <span data-ttu-id="4e054-110">- Dize `Self`belirteci ; olarak oluşturulan <xref:System.Windows.Data.RelativeSource> bir <xref:System.Windows.Data.RelativeSource.Mode%2A> özellik için <xref:System.Windows.Data.RelativeSourceMode.Self>ayarlanır karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4e054-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="4e054-111">- Dize `TemplatedParent`belirteci ; olarak oluşturulan <xref:System.Windows.Data.RelativeSource> bir <xref:System.Windows.Data.RelativeSource.Mode%2A> özellik için <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>ayarlanır karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4e054-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="4e054-112">- Dize `PreviousData`belirteci ; olarak oluşturulan <xref:System.Windows.Data.RelativeSource> bir <xref:System.Windows.Data.RelativeSource.Mode%2A> özellik için <xref:System.Windows.Data.RelativeSourceMode.PreviousData>ayarlanır karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4e054-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="4e054-113">- Mod hakkında `FindAncestor` bilgi için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="4e054-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="4e054-114">Dize belirteci. `FindAncestor`</span><span class="sxs-lookup"><span data-stu-id="4e054-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="4e054-115">Bu belirteç kullanarak bir `RelativeSource` ata türü ve isteğe bağlı olarak bir ata düzeyi belirtir bir mod girer.</span><span class="sxs-lookup"><span data-stu-id="4e054-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="4e054-116">Bu, kendi <xref:System.Windows.Data.RelativeSource> <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği olarak ayarlanmış bir <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>olarak karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4e054-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="4e054-117">Mod `FindAncestor` için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4e054-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="4e054-118"><xref:System.Windows.Data.RelativeSource.AncestorType%2A> Özelliği dolduran bir türün adı.</span><span class="sxs-lookup"><span data-stu-id="4e054-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="4e054-119">Mod `FindAncestor` için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4e054-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="4e054-120">Öncül düzeyi (Mantıksal ağaçta üst yön doğrultusunda değerlendirilen.)</span><span class="sxs-lookup"><span data-stu-id="4e054-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e054-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e054-121">Remarks</span></span>

<span data-ttu-id="4e054-122">`{RelativeSource TemplatedParent}`bağlama kullanımları, bir denetimin UI'sinin ve denetimin mantığının ayrılmasıyla ilgili daha büyük bir kavramı ele alan önemli bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="4e054-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="4e054-123">Bu, şablon tanımı içinden şablonlu üst öğeye (şablonun uygulandığı çalışma zamanı nesnesi örneği) bağlanmaya olanak verir.</span><span class="sxs-lookup"><span data-stu-id="4e054-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="4e054-124">Bu durumda, [TemplateBinding Biçimlendirme Uzantısı](templatebinding-markup-extension.md) aslında aşağıdaki bağlama ifadesi için `{Binding RelativeSource={RelativeSource TemplatedParent}}`bir kısaltmadır: .</span><span class="sxs-lookup"><span data-stu-id="4e054-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="4e054-125">`TemplateBinding`veya `{RelativeSource TemplatedParent}` kullanımlar yalnızca şablon tanımlayan XAML içinde alakalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e054-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="4e054-126">Daha fazla bilgi için [Bkz. TemplateBinding Biçimlendirme Uzantısı.](templatebinding-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="4e054-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="4e054-127">`{RelativeSource FindAncestor}`denetimin her zaman belirli bir ata türündeki görsel bir ağaçta olması beklenen durumlarda, çoğunlukla denetim şablonlarında veya öngörülebilir bağımsız kullanıcı arabirimi kompozisyonlarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e054-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="4e054-128">Örneğin, bir öğe denetimi öğeleri, öğeleri denetim üst atalarının özelliklerine bağlamak için kullanımları kullanabilirsiniz. `FindAncestor`</span><span class="sxs-lookup"><span data-stu-id="4e054-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="4e054-129">Veya, bir şablondaki denetim kompozisyonunun bir `FindAncestor` parçası olan öğeler, aynı kompozisyon yapısındaki ana öğelere bağlamaları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="4e054-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="4e054-130">XAML Sözdizimi `FindAncestor` bölümlerinde gösterilen mod için nesne öğesi sözdiziminde, ikinci `FindAncestor` nesne öğesi sözdizimi özellikle mod için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e054-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="4e054-131">`FindAncestor`modu bir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> değer gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4e054-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="4e054-132">Bir öznitelik olarak <xref:System.Windows.Data.RelativeSource.AncestorType%2A> [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) başvuruiçin ata türü aramak için bir öznitelik olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e054-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="4e054-133">Değer, <xref:System.Windows.Data.RelativeSource.AncestorType%2A> bağlama isteği çalışma zamanında işlendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e054-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="4e054-134">Mod `FindAncestor` için, isteğe bağlı özellik, <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> öğe ağacında var olan bu türde birden fazla atanın bulunduğu durumlarda ata nın aramasını ayrıştırmada yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e054-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="4e054-135">`FindAncestor` Modun nasıl kullanılacağı hakkında daha <xref:System.Windows.Data.RelativeSource>fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="4e054-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="4e054-136">`{RelativeSource Self}`bir örneğin bir özelliğinin aynı örneğin başka bir özelliğinin değerine bağlı olması ve bu iki özellik arasında genel bağımlılık özelliği ilişkisinin (zorlama gibi) zaten bulunmadığı senaryolar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4e054-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="4e054-137">Değerlerin tam anlamıyla aynı olduğu (ve aynı şekilde yazılmış) bir nesne üzerinde iki özelliğin `Converter` bulunması nadir olsa `{RelativeSource Self}`da, kaynak ve hedef türleri arasında dönüştürme yapmak için dönüştürücükullanan bir bağlayıcıya bir parametre de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e054-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="4e054-138">Başka bir `{RelativeSource Self}` senaryo için <xref:System.Windows.MultiDataTrigger>bir parçası olarak .</span><span class="sxs-lookup"><span data-stu-id="4e054-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="4e054-139">Örneğin, aşağıdaki XAML, hangi <xref:System.Windows.Shapes.Rectangle> değer için <xref:System.Windows.FrameworkElement.Width%2A>girilirse girilen bir öğeyi tanımlar, her zaman bir <xref:System.Windows.Shapes.Rectangle> karedir:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="4e054-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="4e054-140">`{RelativeSource PreviousData}`veri şablonlarında veya bağlayıcıların bir koleksiyonu veri kaynağı olarak kullandığı durumlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4e054-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="4e054-141">Koleksiyondaki `{RelativeSource PreviousData}` bitişik veri öğeleri arasındaki ilişkileri vurgulamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e054-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="4e054-142">İlgili bir teknik, <xref:System.Windows.Data.MultiBinding> veri kaynağındaki geçerli ve önceki öğeler arasında bir öğe oluşturmak ve iki öğe ile özellikleri arasındaki farkı belirlemek için bu bağlayıcıüzerinde bir dönüştürücü kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4e054-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="4e054-143">Aşağıdaki örnekte, öğeler <xref:System.Windows.Controls.TextBlock> şablonundaki ilk geçerli sayı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4e054-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="4e054-144">İkinci <xref:System.Windows.Controls.TextBlock> bağlama nominal <xref:System.Windows.Data.MultiBinding> olarak iki <xref:System.Windows.Data.Binding> bileşeni olan birdir: geçerli kayıt ve önceki veri kaydını `{RelativeSource PreviousData}`kullanarak kasıtlı olarak kullanan bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="4e054-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="4e054-145">Daha sonra, bir <xref:System.Windows.Data.MultiBinding> dönüştürücü farkı hesaplar ve bağlama döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e054-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

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

<span data-ttu-id="4e054-146">Veri bağlamayı bir kavram olarak açıklayan burada ele alınmaz, [bkz.](../../../desktop-wpf/data/data-binding-overview.md)</span><span class="sxs-lookup"><span data-stu-id="4e054-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="4e054-147">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısı için işleme <xref:System.Windows.Data.RelativeSource> sınıf tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4e054-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="4e054-148">`RelativeSource`biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="4e054-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="4e054-149">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4e054-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="4e054-150">XAML'deki tüm biçimlendirme `{` uzantıları, bir XAML işlemcinin bir biçimlendirme uzantısıözözelliği ni işlemesi gerektiğini kabul ettiği kural olan öznitelik sözdiziminde karakterleri ve `}` karakterleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e054-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="4e054-151">Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)</span><span class="sxs-lookup"><span data-stu-id="4e054-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e054-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e054-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="4e054-153">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e054-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="4e054-154">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="4e054-154">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="4e054-155">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="4e054-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="4e054-156">Veri Bağlama Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e054-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4e054-157">Bağlama Bildirimlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e054-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="4e054-158">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="4e054-158">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)

---
title: RelativeSource MarkupExtension
description: Bir RelativeSource bağlama kaynağının özelliklerini, bir bağlama Işaretleme uzantısı içinde ya da XAML içindeki bir bağlamanın RelativeSource özelliğini ayarlarken belirtir.
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 2da702d23413651a85b45404e088f6708546cc25
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165938"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="99c89-103">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="99c89-103">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="99c89-104">Bağlama bir <xref:System.Windows.Data.RelativeSource> [Biçimlendirme Uzantısı](binding-markup-extension.md)içinde kullanılmak üzere veya <xref:System.Windows.Data.Binding.RelativeSource%2A> xaml 'de kurulu bir öğenin özelliği ayarlanırken bir bağlama kaynağının özelliklerini belirtir <xref:System.Windows.Data.Binding> .</span><span class="sxs-lookup"><span data-stu-id="99c89-104">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="99c89-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="99c89-105">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="99c89-106">XAML Öznitelik Kullanımı (Bağlama uzantıları içinde iç içe geçmiş)</span><span class="sxs-lookup"><span data-stu-id="99c89-106">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="99c89-107">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="99c89-107">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="99c89-108">-veya-</span><span class="sxs-lookup"><span data-stu-id="99c89-108">-or-</span></span>

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

## <a name="xaml-values"></a><span data-ttu-id="99c89-109">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="99c89-109">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="99c89-110">Aşağıdakilerden biri:</span><span class="sxs-lookup"><span data-stu-id="99c89-110">One of the following:</span></span><br /><br /> <span data-ttu-id="99c89-111">-Dize belirteci `Self` ;, <xref:System.Windows.Data.RelativeSource> öğesinin <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği olarak ayarlanmış olarak bir öğesine karşılık gelir <xref:System.Windows.Data.RelativeSourceMode.Self> .</span><span class="sxs-lookup"><span data-stu-id="99c89-111">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="99c89-112">-Dize belirteci `TemplatedParent` ;, <xref:System.Windows.Data.RelativeSource> öğesinin <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği olarak ayarlanmış olarak bir öğesine karşılık gelir <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent> .</span><span class="sxs-lookup"><span data-stu-id="99c89-112">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="99c89-113">-Dize belirteci `PreviousData` ;, <xref:System.Windows.Data.RelativeSource> öğesinin <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği olarak ayarlanmış olarak bir öğesine karşılık gelir <xref:System.Windows.Data.RelativeSourceMode.PreviousData> .</span><span class="sxs-lookup"><span data-stu-id="99c89-113">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="99c89-114">-Mod hakkında bilgi için aşağıya bakın `FindAncestor` .</span><span class="sxs-lookup"><span data-stu-id="99c89-114">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="99c89-115">Dize belirteci `FindAncestor` .</span><span class="sxs-lookup"><span data-stu-id="99c89-115">The string token `FindAncestor`.</span></span> <span data-ttu-id="99c89-116">Bu belirteci kullanmak `RelativeSource` , bir üst tür ve isteğe bağlı olarak bir üst düzeyi belirten bir mod girer.</span><span class="sxs-lookup"><span data-stu-id="99c89-116">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="99c89-117">Bu, özelliği olarak ayarlanmış şekilde oluşturulmuş bir öğesine karşılık gelir <xref:System.Windows.Data.RelativeSource> <xref:System.Windows.Data.RelativeSource.Mode%2A> <xref:System.Windows.Data.RelativeSourceMode.FindAncestor> .</span><span class="sxs-lookup"><span data-stu-id="99c89-117">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="99c89-118">Mod için gereklidir `FindAncestor` .</span><span class="sxs-lookup"><span data-stu-id="99c89-118">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="99c89-119">Özelliği dolduran bir türün adı <xref:System.Windows.Data.RelativeSource.AncestorType%2A> .</span><span class="sxs-lookup"><span data-stu-id="99c89-119">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="99c89-120">Mod için isteğe bağlı `FindAncestor` .</span><span class="sxs-lookup"><span data-stu-id="99c89-120">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="99c89-121">Öncül düzeyi (Mantıksal ağaçta üst yön doğrultusunda değerlendirilen.)</span><span class="sxs-lookup"><span data-stu-id="99c89-121">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="99c89-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99c89-122">Remarks</span></span>

<span data-ttu-id="99c89-123">`{RelativeSource TemplatedParent}`bağlama kullanımları, bir denetimin kullanıcı arabiriminin ve denetim mantığının ayrılma açısından daha büyük bir kavramı adresleyen bir anahtar tekniğidir.</span><span class="sxs-lookup"><span data-stu-id="99c89-123">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="99c89-124">Bu, şablon tanımı içinden şablonlu üst öğeye (şablonun uygulandığı çalışma zamanı nesnesi örneği) bağlanmaya olanak verir.</span><span class="sxs-lookup"><span data-stu-id="99c89-124">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="99c89-125">Bu durumda, [TemplateBinding Biçimlendirme Uzantısı](templatebinding-markup-extension.md) aslında aşağıdaki bağlama ifadesi için bir toplu özelliktir: `{Binding RelativeSource={RelativeSource TemplatedParent}}` .</span><span class="sxs-lookup"><span data-stu-id="99c89-125">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="99c89-126">`TemplateBinding`veya `{RelativeSource TemplatedParent}` kullanımları, yalnızca bir şablonu TANıMLAYAN XAML içinde ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="99c89-126">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="99c89-127">Daha fazla bilgi için bkz. [TemplateBinding Işaretleme uzantısı](templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="99c89-127">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="99c89-128">`{RelativeSource FindAncestor}`, bir denetimin her zaman belirli bir üst türün görsel ağacında olması beklenildiği durumlarda denetim şablonlarında veya tahmin edilebilir kendiliğinden dahil edilen kullanıcı arabirimi kompozisyonlarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99c89-128">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="99c89-129">Örneğin, bir öğe denetiminin öğeleri `FindAncestor` kendi öğelerinin özelliklerine bağlamak için kullanımları kullanır üst üst öğe.</span><span class="sxs-lookup"><span data-stu-id="99c89-129">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="99c89-130">Ya da bir şablonda denetim kompozisyonunun parçası olan öğeler, `FindAncestor` aynı bileşim yapısındaki üst öğelere bağlamaları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="99c89-130">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="99c89-131">XAML sözdizimi bölümlerinde gösterilen mod için nesne öğesi söz diziminde `FindAncestor` , ikinci nesne öğesi sözdizimi özellikle mod için kullanılır `FindAncestor` .</span><span class="sxs-lookup"><span data-stu-id="99c89-131">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="99c89-132">`FindAncestor`mod bir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> değer gerektirir.</span><span class="sxs-lookup"><span data-stu-id="99c89-132">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="99c89-133"><xref:System.Windows.Data.RelativeSource.AncestorType%2A>Aranacak üst öğe türüne bir [X:Type işaretleme uzantısı](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) başvurusu kullanarak bir öznitelik olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99c89-133">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="99c89-134"><xref:System.Windows.Data.RelativeSource.AncestorType%2A>Değer, bağlama isteği çalışma zamanında işlendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99c89-134">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="99c89-135">`FindAncestor`Mod için, isteğe bağlı özelliği, <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> öğe ağacında var olan bir türün birden fazla üst öğesi olduğu durumlarda üst aramanın belirsizliğini ortadan kaldırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="99c89-135">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="99c89-136">Modunun nasıl kullanılacağı hakkında daha fazla bilgi için `FindAncestor` bkz <xref:System.Windows.Data.RelativeSource> ..</span><span class="sxs-lookup"><span data-stu-id="99c89-136">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="99c89-137">`{RelativeSource Self}`bir örneğin bir özelliğinin aynı örneğe ait başka bir özelliğin değerine bağlı olması gereken ve bu iki özellik arasında bir genel bağımlılık özelliği ilişkisi (zorlama gibi) olması gereken senaryolar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="99c89-137">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="99c89-138">Her iki özellik de değerler özdeş (ve özdeş olarak yazılmış) gibi bir nesne üzerinde mevcut olsa da, bir `Converter` bağlamaya parametre uygulayabilir `{RelativeSource Self}` ve kaynak ve hedef türleri arasında dönüştürme yapmak için dönüştürücüyü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99c89-138">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="99c89-139">İçin başka `{RelativeSource Self}` bir senaryo, bir parçasıdır <xref:System.Windows.MultiDataTrigger> .</span><span class="sxs-lookup"><span data-stu-id="99c89-139">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="99c89-140">Örneğin, aşağıdaki XAML, <xref:System.Windows.Shapes.Rectangle> için hangi değerin girildiğine bakılmaksızın bir öğesi tanımlar <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> her zaman bir kare olur:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="99c89-140">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="99c89-141">`{RelativeSource PreviousData}`veri şablonlarında ya da bağlamaların veri kaynağı olarak bir koleksiyon kullandığı durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="99c89-141">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="99c89-142">`{RelativeSource PreviousData}`Koleksiyondaki bitişik veri öğeleri arasındaki ilişkileri vurgulamak için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99c89-142">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="99c89-143">İlgili bir teknik, <xref:System.Windows.Data.MultiBinding> veri kaynağındaki geçerli ve önceki öğeler arasında bir bağlantı kurmak ve iki öğe ve özellikleri arasındaki farkı belirlemek için o bağlama üzerinde bir dönüştürücü kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="99c89-143">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="99c89-144">Aşağıdaki örnekte, <xref:System.Windows.Controls.TextBlock> öğeler şablonundaki ilk öğe geçerli sayıyı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="99c89-144">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="99c89-145">İkinci bağlama, genel olarak <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Data.MultiBinding> iki <xref:System.Windows.Data.Binding> anaykalara sahiptir: geçerli kayıt ve kullanarak önceki veri kaydını kullanan bir bağlama `{RelativeSource PreviousData}` .</span><span class="sxs-lookup"><span data-stu-id="99c89-145">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="99c89-146">Ardından, üzerindeki bir dönüştürücü <xref:System.Windows.Data.MultiBinding> farkı hesaplar ve bağlamaya döndürür.</span><span class="sxs-lookup"><span data-stu-id="99c89-146">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

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
</ListBox>
```

<span data-ttu-id="99c89-147">Kavram olarak veri bağlamayı açıklamak burada ele alınmamalıdır, bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="99c89-147">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="99c89-148">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Xaml işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Data.RelativeSource> .</span><span class="sxs-lookup"><span data-stu-id="99c89-148">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="99c89-149">`RelativeSource`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="99c89-149">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="99c89-150">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="99c89-150">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="99c89-151">XAML 'deki tüm biçimlendirme uzantıları, `{` `}` öznitelik sözdiziminde ve karakterlerini kullanır. Bu, XAML işlemcisinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı kuraldır.</span><span class="sxs-lookup"><span data-stu-id="99c89-151">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="99c89-152">Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="99c89-152">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99c89-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99c89-153">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="99c89-154">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="99c89-154">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="99c89-155">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="99c89-155">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="99c89-156">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="99c89-156">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="99c89-157">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="99c89-157">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="99c89-158">Bağlama Bildirimlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="99c89-158">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="99c89-159">x:Type İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="99c89-159">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)

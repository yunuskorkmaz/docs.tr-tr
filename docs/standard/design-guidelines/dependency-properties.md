---
title: Bağımlılık Özellikleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: e1372b75cb6501f8bc3fec913364e9d80157ad83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741726"
---
# <a name="dependency-properties"></a><span data-ttu-id="8b45a-102">Bağımlılık Özellikleri</span><span class="sxs-lookup"><span data-stu-id="8b45a-102">Dependency Properties</span></span>
<span data-ttu-id="8b45a-103">Bağımlılık özelliği (DP), değerini bir tür değişkeninde (alan) depolamak yerine bir özellik deposunda depolayan normal bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="8b45a-104">İliştirilmiş bir bağımlılık özelliği, nesneler ve kapsayıcıları arasındaki ilişkileri açıklayan "özellikleri" temsil eden, statik get ve set yöntemleri olarak modellenen bir bağımlılık özelliği türüdür (örn. bir `Panel` kapsayıcısında bir `Button` nesnesinin konumu).</span><span class="sxs-lookup"><span data-stu-id="8b45a-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="8b45a-105">✔️, stil oluşturma, Tetikleyiciler, veri bağlama, animasyonlar, Dinamik kaynaklar ve devralma gibi WPF özelliklerini desteklemek için özelliklere ihtiyacınız varsa bağımlılık özelliklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b45a-105">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="8b45a-106">Bağımlılık özelliği tasarımı</span><span class="sxs-lookup"><span data-stu-id="8b45a-106">Dependency Property Design</span></span>
 <span data-ttu-id="8b45a-107">bağımlılık özelliklerini uygularken <xref:System.Windows.DependencyObject>veya alt türlerinden biri ✔️ devralınır.</span><span class="sxs-lookup"><span data-stu-id="8b45a-107">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="8b45a-108">Türü, bir özellik deposunun çok verimli bir uygulamasını sağlar ve otomatik olarak WPF veri bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="8b45a-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="8b45a-109">✔️, her bağımlılık özelliği için bir <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> örneğini depolayan normal bir CLR özelliği ve Public statik salt okunurdur alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b45a-109">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="8b45a-110">✔️, <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>örnek yöntemlerini çağırarak bağımlılık özellikleri uygular.</span><span class="sxs-lookup"><span data-stu-id="8b45a-110">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="8b45a-111">✔️, özelliğin adını "Property" ile düzelterek, bağımlılık özelliği statik alanını adlandırın.</span><span class="sxs-lookup"><span data-stu-id="8b45a-111">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="8b45a-112">❌ doğrudan kodda bağımlılık özelliklerinin varsayılan değerlerini ayarlamayın; Bunun yerine meta verilerde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8b45a-112">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="8b45a-113">Özelliği varsayılan olarak ayarlarsanız, bu özelliğin stil gibi bazı örtük yollarla ayarlanmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b45a-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="8b45a-114">❌ statik alana erişmek için standart koddan farklı özellik erişimcilerine kod yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="8b45a-114">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="8b45a-115">Stil bir stil gibi örtük yollarla ayarlandıysa, stil statik alanı doğrudan kullandığından bu kod yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="8b45a-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="8b45a-116">❌, güvenli verileri depolamak için bağımlılık özelliklerini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="8b45a-116">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="8b45a-117">Hatta özel bağımlılık özelliklerine herkese açık bir şekilde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-117">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="8b45a-118">İliştirilmiş bağımlılık özelliği tasarımı</span><span class="sxs-lookup"><span data-stu-id="8b45a-118">Attached Dependency Property Design</span></span>
 <span data-ttu-id="8b45a-119">Önceki bölümde açıklanan bağımlılık özellikleri, bildirim türünün iç özelliklerini temsil eder; Örneğin, `Text` özelliği bir `TextButton`özelliğidir ve bunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="8b45a-120">Özel bir tür bağımlılık özelliği, ekli bağımlılık özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-120">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="8b45a-121">Ekli özelliğe ait klasik bir örnek <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8b45a-122">Özelliği, düğmenin (Grid 'in) sütun konumunu temsil eder, ancak yalnızca düğmenin bir kılavuzda yer aldığı ve kılavuza göre düğmelere "eklenmiş" olması durumunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 <span data-ttu-id="8b45a-123">İliştirilmiş bir özelliğin tanımı, erişimcilerinin statik get ve set yöntemlerine göre temsil edildiği durumlar dışında, genellikle normal bağımlılık özelliği gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="8b45a-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a><span data-ttu-id="8b45a-124">Bağımlılık özelliği doğrulaması</span><span class="sxs-lookup"><span data-stu-id="8b45a-124">Dependency Property Validation</span></span>
 <span data-ttu-id="8b45a-125">Özellikler genellikle doğrulama olarak adlandırılan şeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="8b45a-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="8b45a-126">Bir özelliğin değerini değiştirme girişimi yapıldığında doğrulama mantığı yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8b45a-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="8b45a-127">Ne yazık ki bağımlılık özellik erişimcileri rastgele doğrulama kodu içeremez.</span><span class="sxs-lookup"><span data-stu-id="8b45a-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="8b45a-128">Bunun yerine, özellik kaydı sırasında bağımlılık özelliği doğrulama mantığının belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="8b45a-129">❌, bağımlılık özelliği doğrulama mantığını özelliğin erişimcilerine yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="8b45a-129">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="8b45a-130">Bunun yerine `DependencyProperty.Register` yöntemine bir doğrulama geri çağırması geçirin.</span><span class="sxs-lookup"><span data-stu-id="8b45a-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="8b45a-131">Bağımlılık özelliği değişiklik bildirimleri</span><span class="sxs-lookup"><span data-stu-id="8b45a-131">Dependency Property Change Notifications</span></span>
 <span data-ttu-id="8b45a-132">❌ bağımlılık özelliği erişimcilerinde değişiklik bildirimi mantığını uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="8b45a-132">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="8b45a-133">Bağımlılık özellikleri, <xref:System.Windows.PropertyMetadata>bir değişiklik bildirimi geri çağırması sağlayarak kullanılması gereken yerleşik bir değişiklik bildirimleri özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="8b45a-134">Bağımlılık özelliği değer zorlaması</span><span class="sxs-lookup"><span data-stu-id="8b45a-134">Dependency Property Value Coercion</span></span>
 <span data-ttu-id="8b45a-135">Özellik deposu gerçekten değiştirilmeden önce özellik ayarlayıcısına verilen değer ayarlayıcı tarafından değiştirilirse Özellik zorlaması gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="8b45a-136">❌ bağımlılık özelliği erişimcilerinde zorlama mantığı uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="8b45a-136">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="8b45a-137">Bağımlılık özellikleri yerleşik bir zorlama özelliğine sahiptir ve `PropertyMetadata`bir zorlama geri çağırması sağlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b45a-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="8b45a-138">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="8b45a-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8b45a-139">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="8b45a-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8b45a-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b45a-140">See also</span></span>

- [<span data-ttu-id="8b45a-141">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8b45a-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="8b45a-142">Ortak Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="8b45a-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)

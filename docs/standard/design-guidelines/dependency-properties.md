---
title: Bağımlılık Özellikleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: 476ef1bb1ac5ec1f551979c64a41cbae55c554bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280263"
---
# <a name="dependency-properties"></a><span data-ttu-id="c6ee6-102">Bağımlılık Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c6ee6-102">Dependency Properties</span></span>
<span data-ttu-id="c6ee6-103">Bağımlılık özelliği (DP), değerini bir tür değişkeninde (alan) depolamak yerine bir özellik deposunda depolayan normal bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="c6ee6-104">İliştirilmiş bir bağımlılık özelliği, nesneler ve kapsayıcıları arasındaki ilişkileri açıklayan "özellikleri" temsil eden, statik get ve set yöntemleri olarak modellenen bir bağımlılık özelliği türüdür (örn. `Button` bir kapsayıcı üzerindeki nesnenin konumu `Panel` ).</span><span class="sxs-lookup"><span data-stu-id="c6ee6-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="c6ee6-105">✔️, stil oluşturma, Tetikleyiciler, veri bağlama, animasyonlar, Dinamik kaynaklar ve devralma gibi WPF özelliklerini desteklemek için özelliklere ihtiyacınız varsa bağımlılık özelliklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-105">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="c6ee6-106">Bağımlılık özelliği tasarımı</span><span class="sxs-lookup"><span data-stu-id="c6ee6-106">Dependency Property Design</span></span>
 <span data-ttu-id="c6ee6-107"><xref:System.Windows.DependencyObject>bağımlılık özelliklerini uygularken ✔️ veya alt türlerinden birini devralma.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-107">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="c6ee6-108">Türü, bir özellik deposunun çok verimli bir uygulamasını sağlar ve otomatik olarak WPF veri bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="c6ee6-109">✔️, <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> her bağımlılık özelliği için bir örneğini depolayan normal BIR CLR özelliği ve ortak statik salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-109">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="c6ee6-110">✔️, örnek yöntemlerini ve yöntemini çağırarak bağımlılık özelliklerini <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> uygulama <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c6ee6-110">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="c6ee6-111">✔️, özelliğin adını "Property" ile düzelterek, bağımlılık özelliği statik alanını adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-111">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="c6ee6-112">❌Doğrudan kodda bağımlılık özelliklerinin varsayılan değerlerini ayarlamayın; Bunun yerine meta verilerde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-112">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="c6ee6-113">Özelliği varsayılan olarak ayarlarsanız, bu özelliğin stil gibi bazı örtük yollarla ayarlanmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="c6ee6-114">❌Statik alana erişmek için standart kod dışındaki özellik erişimcilerine kod yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-114">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="c6ee6-115">Stil bir stil gibi örtük yollarla ayarlandıysa, stil statik alanı doğrudan kullandığından bu kod yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="c6ee6-116">❌Güvenli verileri depolamak için bağımlılık özelliklerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-116">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="c6ee6-117">Hatta özel bağımlılık özelliklerine herkese açık bir şekilde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-117">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="c6ee6-118">İliştirilmiş bağımlılık özelliği tasarımı</span><span class="sxs-lookup"><span data-stu-id="c6ee6-118">Attached Dependency Property Design</span></span>
 <span data-ttu-id="c6ee6-119">Önceki bölümde açıklanan bağımlılık özellikleri, bildirim türünün iç özelliklerini temsil eder; Örneğin, `Text` özelliği `TextButton` onu bildiren bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="c6ee6-120">Özel bir tür bağımlılık özelliği, ekli bağımlılık özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-120">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="c6ee6-121">Ekli özelliğe klasik bir örnek, <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c6ee6-122">Özelliği, düğmenin (Grid 'in) sütun konumunu temsil eder, ancak yalnızca düğmenin bir kılavuzda yer aldığı ve kılavuza göre düğmelere "eklenmiş" olması durumunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

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

 <span data-ttu-id="c6ee6-123">İliştirilmiş bir özelliğin tanımı, erişimcilerinin statik get ve set yöntemlerine göre temsil edildiği durumlar dışında, genellikle normal bağımlılık özelliği gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="c6ee6-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

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

## <a name="dependency-property-validation"></a><span data-ttu-id="c6ee6-124">Bağımlılık özelliği doğrulaması</span><span class="sxs-lookup"><span data-stu-id="c6ee6-124">Dependency Property Validation</span></span>
 <span data-ttu-id="c6ee6-125">Özellikler genellikle doğrulama olarak adlandırılan şeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="c6ee6-126">Bir özelliğin değerini değiştirme girişimi yapıldığında doğrulama mantığı yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="c6ee6-127">Ne yazık ki bağımlılık özellik erişimcileri rastgele doğrulama kodu içeremez.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="c6ee6-128">Bunun yerine, özellik kaydı sırasında bağımlılık özelliği doğrulama mantığının belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="c6ee6-129">❌Bağımlılık özelliği doğrulama mantığını özelliğin erişimcilerine yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-129">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="c6ee6-130">Bunun yerine yöntemine bir doğrulama geri çağırması geçirin `DependencyProperty.Register` .</span><span class="sxs-lookup"><span data-stu-id="c6ee6-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="c6ee6-131">Bağımlılık özelliği değişiklik bildirimleri</span><span class="sxs-lookup"><span data-stu-id="c6ee6-131">Dependency Property Change Notifications</span></span>
 <span data-ttu-id="c6ee6-132">❌Bağımlılık özelliği erişimcilerinde değişiklik bildirimi mantığını uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-132">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="c6ee6-133">Bağımlılık özellikleri, için bir değişiklik bildirimi geri çağırması sağlayarak kullanılması gereken yerleşik bir değişiklik bildirimleri özelliğine sahiptir <xref:System.Windows.PropertyMetadata> .</span><span class="sxs-lookup"><span data-stu-id="c6ee6-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="c6ee6-134">Bağımlılık özelliği değer zorlaması</span><span class="sxs-lookup"><span data-stu-id="c6ee6-134">Dependency Property Value Coercion</span></span>
 <span data-ttu-id="c6ee6-135">Özellik deposu gerçekten değiştirilmeden önce özellik ayarlayıcısına verilen değer ayarlayıcı tarafından değiştirilirse Özellik zorlaması gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="c6ee6-136">❌Bağımlılık özelliği erişimcilerinde zorlama mantığı uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-136">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="c6ee6-137">Bağımlılık özellikleri yerleşik bir zorlama özelliğine sahiptir ve ' a bir zorlama geri çağırması sağlanarak kullanılabilir `PropertyMetadata` .</span><span class="sxs-lookup"><span data-stu-id="c6ee6-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="c6ee6-138">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="c6ee6-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c6ee6-139">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="c6ee6-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c6ee6-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6ee6-140">See also</span></span>

- [<span data-ttu-id="c6ee6-141">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c6ee6-141">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="c6ee6-142">Ortak tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="c6ee6-142">Common Design Patterns</span></span>](common-design-patterns.md)

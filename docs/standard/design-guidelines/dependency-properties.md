---
title: Bağımlılık özellikleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7398202cc265fbd55b9bf0b5a53367dedcab57b0
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948491"
---
# <a name="dependency-properties"></a><span data-ttu-id="719c9-102">Bağımlılık özellikleri</span><span class="sxs-lookup"><span data-stu-id="719c9-102">Dependency Properties</span></span>
<span data-ttu-id="719c9-103">Bağımlılık özelliği (DP) yerine bir türü değişkeni (alanı), örneğin bir özellik deposu değerini depolar normal bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="719c9-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="719c9-104">Ekli bağımlılık özelliği "nesneler ve onların kapsayıcılar arasındaki ilişkileri açıklayan özelliklerinin" temsil eden statik alma ve ayarlama yöntemleri olarak Modellenen bağımlılık özelliği türüdür (örn., konumunu bir `Button` nesnenin bir `Panel` kapsayıcı).</span><span class="sxs-lookup"><span data-stu-id="719c9-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="719c9-105">**✓ YAPMAK** stil, Tetikleyiciler, veri bağlama, animasyon, dinamik kaynaklar ve devralma gibi WPF özellikleri desteklemek için özellikler gerekiyorsa bağımlılık özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="719c9-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="719c9-106">Bağımlılık özelliği tasarım</span><span class="sxs-lookup"><span data-stu-id="719c9-106">Dependency Property Design</span></span>  
 <span data-ttu-id="719c9-107">**✓ YAPMAK** devralınmalıdır <xref:System.Windows.DependencyObject>, veya bağımlılık özellikleri uygularken kendi alt biri.</span><span class="sxs-lookup"><span data-stu-id="719c9-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="719c9-108">Türü bir özellik deposu çok verimli bir uygulamasını sağlar ve WPF veri bağlama otomatik olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="719c9-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="719c9-109">**✓ YAPMAK** normal CLR özellik ve bir örneğini depolamak ortak statik salt okunur alan sağlamak <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> her bağımlılık özelliği için.</span><span class="sxs-lookup"><span data-stu-id="719c9-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="719c9-110">**✓ YAPMAK** örnek yöntemleri çağırarak bağımlılık özellikleri uygulamak <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="719c9-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="719c9-111">**✓ YAPMAK** özelliğiyle"." özelliğinin adı suffixing tarafından bağımlılık özelliği static alan adı</span><span class="sxs-lookup"><span data-stu-id="719c9-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="719c9-112">**X yok** Ayarla bağımlılık özelliklerinin varsayılan değerlerini açıkça kodda; bunun yerine meta verilerde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="719c9-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="719c9-113">Özellik varsayılan açıkça ayarlarsanız, bu özellik bir stil gibi bazı örtük yollarla tarafından ayarlanan engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="719c9-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="719c9-114">**X yok** kodu statik alana erişmek için özellik erişimcisi içinde standart kod dışında koyun.</span><span class="sxs-lookup"><span data-stu-id="719c9-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="719c9-115">Özelliği bir stil gibi örtük bir yöntem ayarlanmışsa, kod stil oluşturma çünkü yürütmesine olmaz statik alanın doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="719c9-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="719c9-116">**X yok** güvenli veri depolamak için bağımlılık özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="719c9-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="719c9-117">Hatta özel bağımlılık özellikleri genel olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="719c9-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="719c9-118">Ekli bağımlılık özelliği tasarım</span><span class="sxs-lookup"><span data-stu-id="719c9-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="719c9-119">Bağımlılık özellikleri önceki bölümde açıklanan bildiri türü iç özelliklerini temsil eder; Örneğin, `Text` özelliği bir özelliğidir `TextButton`, hangi bildirir.</span><span class="sxs-lookup"><span data-stu-id="719c9-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="719c9-120">Özel türde bir bağımlılık özelliği ekli bağımlılık özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="719c9-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="719c9-121">Ekli özellik klasik bir örneği olan <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="719c9-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="719c9-122">Düğmenin (değil ızgaranın) sütun konumu özelliğini temsil eder, ancak yalnızca düğme kılavuzunda yer alıyorsa, ve "düğmelere kılavuzları tarafından bağlı olduğu için" ilgili.</span><span class="sxs-lookup"><span data-stu-id="719c9-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
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
  
 <span data-ttu-id="719c9-123">Erişimciler Get ve Set statik yöntemler tarafından temsil edilen dışında iliştirilmiş bir özellik tanımını çoğunlukla, normal bir bağımlılık özelliğinin, gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="719c9-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
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
  
## <a name="dependency-property-validation"></a><span data-ttu-id="719c9-124">Bağımlılık özelliği doğrulama</span><span class="sxs-lookup"><span data-stu-id="719c9-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="719c9-125">Özellikleri genellikle doğrulama olarak adlandırılan uygulayın.</span><span class="sxs-lookup"><span data-stu-id="719c9-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="719c9-126">Bir özelliğin değerini değiştirmek için girişiminde bulunulduğunda doğrulama mantığını yürütür.</span><span class="sxs-lookup"><span data-stu-id="719c9-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="719c9-127">Ne yazık ki bağımlılık özellik erişimcisi rasgele doğrulama kodu içeremez.</span><span class="sxs-lookup"><span data-stu-id="719c9-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="719c9-128">Bunun yerine, bağımlılık özelliği doğrulama mantığını özelliği kayıt sırasında belirtilmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="719c9-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="719c9-129">**X yok** bağımlılık özelliği doğrulama mantığını özelliğin erişimciler yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="719c9-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="719c9-130">Bunun yerine, bir doğrulama geri çağırma geçirmek `DependencyProperty.Register` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="719c9-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="719c9-131">Bağımlılık özelliği değişiklik bildirimleri</span><span class="sxs-lookup"><span data-stu-id="719c9-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="719c9-132">**X yok** bağımlılık özellik erişimcisi değişiklik bildirimi mantığı uygular.</span><span class="sxs-lookup"><span data-stu-id="719c9-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="719c9-133">Bağımlılık özelliklere sahip bir değişiklik bildirimi geri araması sağlayarak kullanılması gereken bir yerleşik değişiklik bildirimleri özelliği <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="719c9-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="719c9-134">Bağımlılık özelliği değeri zorlama</span><span class="sxs-lookup"><span data-stu-id="719c9-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="719c9-135">Özellik deposu gerçekte değiştirilmeden önce bir özellik ayarlayıcısı verilen değer kurucu tarafından değiştirildiğinde özelliği zorlama gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="719c9-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="719c9-136">**X yok** bağımlılık özellik erişimcisi zorlama mantığı uygular.</span><span class="sxs-lookup"><span data-stu-id="719c9-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="719c9-137">Bağımlılık özelliklere sahip bir yerleşik zorlama özelliği ve bir zorlama geri sağlayarak kullanılabilir `PropertyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="719c9-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="719c9-138">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="719c9-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="719c9-139">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="719c9-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="719c9-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="719c9-140">See Also</span></span>  
 [<span data-ttu-id="719c9-141">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="719c9-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="719c9-142">Ortak Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="719c9-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)

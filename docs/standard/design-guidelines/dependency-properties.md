---
title: Bağımlılık özellikleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75c83dc75d1c86c89169fcc54220ced2a195bfbe
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866864"
---
# <a name="dependency-properties"></a><span data-ttu-id="93fa5-102">Bağımlılık özellikleri</span><span class="sxs-lookup"><span data-stu-id="93fa5-102">Dependency Properties</span></span>
<span data-ttu-id="93fa5-103">Bağımlılık özelliği (DP) bir tür değişken (alan), örneğin depolamak yerine bir özellik deposu değerini depolayan bir normal bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="93fa5-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="93fa5-104">Bir ekli bağımlılık özelliği olarak "Özellikler" nesnelerini ve bunların kapsayıcılar arasındaki ilişkileri tanımlayan temsil eden statik alma ve ayarlama yöntemlerini modellenmiş bağımlılık özelliği türüdür (örneğin, konumunu bir `Button` nesnenin bir `Panel` kapsayıcı).</span><span class="sxs-lookup"><span data-stu-id="93fa5-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="93fa5-105">**✓ DO** stil, Tetikleyiciler, veri bağlama, animasyon, dinamik kaynaklar ve devralma gibi WPF özellikleri desteklemek için özellikler gerekiyorsa bağımlılık özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="93fa5-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="93fa5-106">Bağımlılık özelliği tasarımı</span><span class="sxs-lookup"><span data-stu-id="93fa5-106">Dependency Property Design</span></span>  
 <span data-ttu-id="93fa5-107">**✓ DO** devralınmalıdır <xref:System.Windows.DependencyObject>, veya bağımlılık özellikleri uygularken kendi alt biri.</span><span class="sxs-lookup"><span data-stu-id="93fa5-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="93fa5-108">Türü bir çok verimli bir özellik deposu sağlar ve otomatik olarak WPF veri bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="93fa5-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="93fa5-109">**✓ DO** normal CLR özellik ve bir örneğini depolamak ortak statik salt okunur alan sağlamak <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> her bağımlılık özelliği için.</span><span class="sxs-lookup"><span data-stu-id="93fa5-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="93fa5-110">**✓ DO** örnek yöntemleri çağırarak bağımlılık özellikleri uygulamak <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="93fa5-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="93fa5-111">**✓ DO** özelliğiyle"." özelliğinin adı suffixing tarafından bağımlılık özelliği static alan adı</span><span class="sxs-lookup"><span data-stu-id="93fa5-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="93fa5-112">**X DO NOT** Ayarla bağımlılık özelliklerinin varsayılan değerlerini açıkça kodda; bunun yerine meta verilerde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="93fa5-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="93fa5-113">Açık bir özelliği varsayılan olarak, bu özellik bir stil gibi örtük bazı araçlar tarafından ayarlanan engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="93fa5-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="93fa5-114">**X DO NOT** kodu statik alana erişmek için özellik erişimcisi içinde standart kod dışında koyun.</span><span class="sxs-lookup"><span data-stu-id="93fa5-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="93fa5-115">Özelliği bir stil gibi örtük bir şekilde ayarlanmışsa kod stili uygulanması nedeniyle yürütmesine olmaz statik alan doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="93fa5-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="93fa5-116">**X DO NOT** güvenli veri depolamak için bağımlılık özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="93fa5-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="93fa5-117">Hatta özel bağımlılık özellikleri genel olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="93fa5-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="93fa5-118">Ekli bir bağımlılık özelliği tasarımı</span><span class="sxs-lookup"><span data-stu-id="93fa5-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="93fa5-119">Bağımlılık özellikleri önceki bölümde açıklanan bildirim türü iç özelliklerini temsil eder; Örneğin, `Text` özelliktir özelliği `TextButton`, hangi bildirir.</span><span class="sxs-lookup"><span data-stu-id="93fa5-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="93fa5-120">Özel bağımlılık özelliği ekli bağımlılık özelliği türüdür.</span><span class="sxs-lookup"><span data-stu-id="93fa5-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="93fa5-121">Ekli özelliği Klasik örneğidir <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="93fa5-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="93fa5-122">Düğmenin (değil kılavuz) sütun konumu özelliğini temsil eder, ancak yalnızca düğme kılavuzunda yer alıyorsa, ve "düğmeleri Kılavuzlar tarafından eklenmiş şekilde" ilgili.</span><span class="sxs-lookup"><span data-stu-id="93fa5-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
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
  
 <span data-ttu-id="93fa5-123">Erişimciler statik alma ve ayarlama yöntemlerini tarafından temsil edilen dışında ekli özelliği tanımı normal bağımlılık özelliği, çoğunlukla, gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="93fa5-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
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
  
## <a name="dependency-property-validation"></a><span data-ttu-id="93fa5-124">Bağımlılık özelliği doğrulama</span><span class="sxs-lookup"><span data-stu-id="93fa5-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="93fa5-125">Doğrulama olarak adlandırılan özellikleri genellikle uygulayın.</span><span class="sxs-lookup"><span data-stu-id="93fa5-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="93fa5-126">Bir özelliğin değerini değiştirmek için bir deneme yapıldığında Doğrulama mantığı yürütür.</span><span class="sxs-lookup"><span data-stu-id="93fa5-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="93fa5-127">Ne yazık ki bağımlılık özellik erişimcileri, rastgele bir doğrulama kodu içeremez.</span><span class="sxs-lookup"><span data-stu-id="93fa5-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="93fa5-128">Bunun yerine, bağımlılık özelliği Doğrulama mantığı özelliği kayıt sırasında belirtilmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="93fa5-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="93fa5-129">**X DO NOT** bağımlılık özelliği doğrulama mantığını özelliğin erişimciler yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="93fa5-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="93fa5-130">Bunun yerine, doğrulama geri çağırma işlevi için geçirin `DependencyProperty.Register` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93fa5-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="93fa5-131">Bağımlılık özellik değişikliği bildirimleri</span><span class="sxs-lookup"><span data-stu-id="93fa5-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="93fa5-132">**X DO NOT** bağımlılık özellik erişimcisi değişiklik bildirimi mantığı uygular.</span><span class="sxs-lookup"><span data-stu-id="93fa5-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="93fa5-133">Bağımlılık özelliklerine sahip bir değişiklik bildirimi geri araması için sağlanarak kullanılmalıdır bir yerleşik değişiklik bildirimleri özellik <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="93fa5-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="93fa5-134">Bağımlılık özelliği değer zorlama</span><span class="sxs-lookup"><span data-stu-id="93fa5-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="93fa5-135">Özellik zorlama özellik deposu gerçekten değiştirilmeden önce ayarlayıcı tarafından verilen bir özellik ayarlayıcı değer değiştirildiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="93fa5-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="93fa5-136">**X DO NOT** bağımlılık özellik erişimcisi zorlama mantığı uygular.</span><span class="sxs-lookup"><span data-stu-id="93fa5-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="93fa5-137">Bağımlılık özelliklerine sahip yerleşik zorlama özelliği ve zorlama geri çağırmaya sağlanarak kullanılabilir `PropertyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="93fa5-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="93fa5-138">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="93fa5-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="93fa5-139">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="93fa5-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fa5-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93fa5-140">See also</span></span>

- [<span data-ttu-id="93fa5-141">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="93fa5-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="93fa5-142">Ortak Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="93fa5-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)

---
title: "DependencyObjects için Güvenli Oluşturucu Desenleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db1b7f47ef135b1a174eecef7e53b41e6996256d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="b674c-102">DependencyObjects için Güvenli Oluşturucu Desenleri</span><span class="sxs-lookup"><span data-stu-id="b674c-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="b674c-103">Genellikle, sınıf oluşturucular oluşturucular türetilmiş bir sınıf için temel oluşturucular başlatma çağrılabilir olduğundan sanal yöntemler veya temsilciler gibi geri çağırmaları çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="b674c-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="b674c-104">Sanal girme verilen herhangi bir nesnenin bir tamamlanmamış başlatma durumu yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b674c-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="b674c-105">Ancak, özellik sistemi çağırır ve geri çağırmaları dahili olarak, bağımlılık özelliği sisteminin bir parçası kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="b674c-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="b674c-106">Bir bağımlılık özelliği değerle ayarlamakla kadar basit bir işlem <xref:System.Windows.DependencyObject.SetValue%2A> çağrısı potansiyel olarak içeren bir geri çağırma yere belirleme.</span><span class="sxs-lookup"><span data-stu-id="b674c-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="b674c-107">Bu nedenle, bağımlılık türünüz temel sınıf olarak kullanılıyorsa, sorunlu olabilecek bir oluşturucu gövdesi içinde özellik değerlerini ayarlarken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b674c-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="b674c-108">Uygulama için belirli bir desene yoktur <xref:System.Windows.DependencyObject> oluşturucular ve burada belgelenen bağımlılık özelliği durumlar ve devralınmış geri çağırmalar ile belirli sorunları önler.</span><span class="sxs-lookup"><span data-stu-id="b674c-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="b674c-109">Özellik sistem sanal yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b674c-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="b674c-110">Aşağıdaki sanal yöntemler veya geri aramalar hesaplamaları sırasında adı verilir <xref:System.Windows.DependencyObject.SetValue%2A> bir bağımlılık özelliği değerini ayarlayan çağrısı: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="b674c-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="b674c-111">Bu sanal yöntemler veya geri aramalar her biri, çok yönlülük genişletme belirli bir amaca hizmet eder [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sistemi ve bağımlılık özellikleri.</span><span class="sxs-lookup"><span data-stu-id="b674c-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="b674c-112">Bu sanalların özellik değeri belirlemeyi özelleştirmek için nasıl kullanılacağı hakkında daha fazla bilgi için bkz: [bağımlılık özelliği geri çağrıları ve doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="b674c-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="b674c-113">FXCop Kural zorlama vs. Özellik sistem sanalları</span><span class="sxs-lookup"><span data-stu-id="b674c-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="b674c-114">Yapı işleminizin bir parçası olarak Microsoft aracı FXCop kullanırsanız ve belirli ya da türetilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel oluşturucuyu çağıran framework sınıfları veya türetilmiş sınıflar üzerinde kendi bağımlılık özellikleri uygulamak, belirli bir karşılaşabilirsiniz FXCop kuralı ihlali.</span><span class="sxs-lookup"><span data-stu-id="b674c-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="b674c-115">Bu ihlali adı dizesi değil:</span><span class="sxs-lookup"><span data-stu-id="b674c-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="b674c-116">Bu varsayılan genel kural kümesi için FXCop parçası olan kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="b674c-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="b674c-117">Ne bu kural izleme sonunda bir bağımlılık özelliği sistem sanal yöntemini çağıran bağımlılık özellik sistemi aracılığıyla raporlama olması.</span><span class="sxs-lookup"><span data-stu-id="b674c-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="b674c-118">Bu kural ihlali bile devre dışı bırakın veya bu kuralda FXCop Kural kümesi yapılandırmanızı bastır gerekebilir için bu konudaki belgelenen önerilen oluşturucu desenler izledikten sonra görüntülenmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="b674c-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="b674c-119">Çoğu sorunu varolan sınıfları kullanarak değil türetilmiş sınıflardan gelir</span><span class="sxs-lookup"><span data-stu-id="b674c-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="b674c-120">Bu kural tarafından bildirilen sorunlar, kendi oluşturma dizisinde sanal yöntemlerle uygulayan bir sınıf sonra türetilir oluşur.</span><span class="sxs-lookup"><span data-stu-id="b674c-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="b674c-121">Sınıfınızı veya aksi halde biliyorsanız veya sınıfınız alanından elde edilir değil, zorunlu, burada açıklanan önemli noktalar ve FXCop kuralının motive sorunlarını sizin için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b674c-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="b674c-122">Ancak, bunlar temel sınıflar olarak örneği için kullanılmak üzere tasarlanmıştır şekilde sınıfları yazıyorsanız şablonları oluşturma veya Genişletilebilir denetim kitaplığı ayarlarsanız oluşturucular için burada önerilen desenleri uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="b674c-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="b674c-123">Varsayılan oluşturucu geri çağırmalar tarafından istenen tüm değerleri başlatmalıdır</span><span class="sxs-lookup"><span data-stu-id="b674c-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="b674c-124">Bu değerlerden bazıları "gerçek" değerlerle doldurulur olsa bile, sınıfın varsayılan oluşturucusunu sınıfı geçersiz kılmalar veya geri aramalar (listeden geri çağırmalar özellik sistem sanalları bölümünde) tarafından kullanılan hiçbir örnek üyesinin başlatılması gerekir Varsayılan olmayan oluşturucular parametreleri.</span><span class="sxs-lookup"><span data-stu-id="b674c-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class default constructor, even if some of those values are filled by "real" values through parameters of the nondefault constructors.</span></span>  
  
 <span data-ttu-id="b674c-125">Aşağıdaki örnek kod (ve sonraki örnekleri bir sözde değilse)-bu kural ihlal ediyor ve sorun anlatan C# Örnek:</span><span class="sxs-lookup"><span data-stu-id="b674c-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
```  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 <span data-ttu-id="b674c-126">Uygulama kodu çağırdığında `new MyClass(objectvalue)`, bu varsayılan oluşturucuyu ve temel çağırır sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="b674c-126">When application code calls `new MyClass(objectvalue)`, this calls the default constructor and base class constructors.</span></span> <span data-ttu-id="b674c-127">Bu ayarlar daha sonra `Property1 = object1`, sanal bir yöntem çağırır `OnPropertyChanged` sorumlu üzerinde `MyClass` <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="b674c-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="b674c-128">Geçersiz kılma başvurduğu `_myList`, hangi başlatılmadı henüz.</span><span class="sxs-lookup"><span data-stu-id="b674c-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="b674c-129">Bu sorunları önlemek için bir geri aramalar yalnızca diğer bağımlılık özelliklerini kullanın ve her tür bağımlılık özelliği kayıtlı meta verilerini bir parçası olarak oluşturulmuş varsayılan bir değere sahip olduğundan emin olmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="b674c-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="b674c-130">Güvenli oluşturucu desenler</span><span class="sxs-lookup"><span data-stu-id="b674c-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="b674c-131">Sınıfınız temel sınıf olarak kullanılıyorsa, tamamlanmamış başlatma risklerini önlemek için bu desenleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="b674c-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="default-constructors-calling-base-initialization"></a><span data-ttu-id="b674c-132">Temel başlatma çağıran varsayılan oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b674c-132">Default constructors calling base initialization</span></span>  
 <span data-ttu-id="b674c-133">Temel varsayılan çağıran bu oluşturucuları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="b674c-133">Implement these constructors calling the base default:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="b674c-134">Temel bir imza ile eşleşmeyen varsayılan olmayan (kullanışlı) oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b674c-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="b674c-135">Bu oluşturucular başlatma içinde bağımlılık özelliklerini ayarlamak için parametreleri kullanırsanız, ilk başlatma için kendi sınıfın varsayılan oluşturucusunu çağırın ve bağımlılık özelliklerini ayarlamak için parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b674c-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class default constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="b674c-136">Bunlar ya da bağımlılık özellikleri sınıfı tarafından tanımlanan veya bağımlılık özellikler taban sınıflardan devralınır, ancak her iki durumda da şu biçimi kullanın:</span><span class="sxs-lookup"><span data-stu-id="b674c-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="b674c-137">Temel imzalarla eşleşmeyen varsayılan olmayan (kullanışlı) oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b674c-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="b674c-138">Aynı parametrelemeyi ile temel oluşturucuyu çağırmak yerine, kendi sınıfı varsayılan oluşturucu yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="b674c-138">Instead of calling the base constructor with the same parameterization, again call your own class' default constructor.</span></span> <span data-ttu-id="b674c-139">Temel başlatıcıyı çağırmayın; Bunun yerine çağırmalıdır `this()`.</span><span class="sxs-lookup"><span data-stu-id="b674c-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="b674c-140">Sonra özgün Oluşturucu davranışını ilgili özellikleri ayarlamak için değerler olarak geçirilen parametreleri kullanarak yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b674c-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="b674c-141">Belirli parametreleri olan özellikleri belirlemede rehberlik için özgün temel oluşturucu belgeleri ayarlamak için hedeflenen kullanın:</span><span class="sxs-lookup"><span data-stu-id="b674c-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="b674c-142">Tüm imzalar eşleşmelidir</span><span class="sxs-lookup"><span data-stu-id="b674c-142">Must match all signatures</span></span>  
 <span data-ttu-id="b674c-143">Temel türü birden fazla imzaya sahip olduğu durumlarda, sonraki özellikleri ayarlamadan önce sınıfı varsayılan oluşturucu çağırarak önerilen desenini kullanan bir oluşturucu uygulaması kendi tüm olası imzalar kasıtlı olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b674c-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class default constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="b674c-144">SetValue ile bağımlılık özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="b674c-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="b674c-145">Özellik ayarlama kolaylığı için sarmalayıcı sahip, ve değerlerini içeren bir özelliği ayarlıyorsanız aynı desenler uygulanır <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="b674c-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="b674c-146">Aramalarınız <xref:System.Windows.DependencyObject.SetValue%2A> Oluşturucu parametreleri bu geçiş başlatma için sınıf varsayılan oluşturucusunu da çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b674c-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' default constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b674c-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b674c-147">See Also</span></span>  
 [<span data-ttu-id="b674c-148">Özel Bağımlılık Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b674c-148">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="b674c-149">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b674c-149">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="b674c-150">Bağımlılık Özelliği Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b674c-150">Dependency Property Security</span></span>](../../../../docs/framework/wpf/advanced/dependency-property-security.md)

---
title: DependencyObjects için Güvenli Oluşturucu Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: ba8b0a48b2b75a9191553392d5ec0a1f66575807
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086734"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="41c4e-102">DependencyObjects için Güvenli Oluşturucu Desenleri</span><span class="sxs-lookup"><span data-stu-id="41c4e-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="41c4e-103">Genel olarak, sınıf oluşturucuları türetilmiş bir sınıf için temel oluşturucuları başlatma oluşturucular çağrılamayacağından sanal yöntemler veya temsilciler gibi geri çağırmaları çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="41c4e-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="41c4e-104">Herhangi bir nesne bir eksik başlatma durumuna girmek sanal yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="41c4e-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="41c4e-105">Ancak, özellik sistemi çağırır ve geri çağırmaları dahili olarak, bağımlılık özelliği sisteminin bir parçası kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="41c4e-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="41c4e-106">Bir bağımlılık özelliği değer ile ayarı olarak basit bir işlem <xref:System.Windows.DependencyObject.SetValue%2A> çağrı potansiyel olarak içeren bir geri çağırma yere belirlenmesi.</span><span class="sxs-lookup"><span data-stu-id="41c4e-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="41c4e-107">Bu nedenle, bağımlılık türünüz temel sınıf olarak kullanılırsa, sorunlu olabilecek bir oluşturucu gövdesi içinde özellik değerlerini ayarlarken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="41c4e-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="41c4e-108">Uygulama için belirli bir desene yoktur <xref:System.Windows.DependencyObject> Oluşturucular, burada belgelenmektedir bağımlılık özelliği durumlar ve devralınmış geri çağırmalar belirli sorunları önler.</span><span class="sxs-lookup"><span data-stu-id="41c4e-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="41c4e-109">Özellik sistemi sanal yöntemleri</span><span class="sxs-lookup"><span data-stu-id="41c4e-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="41c4e-110">Sanal yöntemleri veya geri çağırmaları hesaplamaları sırasında adı verilir <xref:System.Windows.DependencyObject.SetValue%2A> bir bağımlılık özelliğinin değerini ayarlayan çağrı: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="41c4e-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="41c4e-111">Bu sanal yöntemler veya geri çağırmaları her biri çeşitlikleri genişletme belirli bir amaca hizmet eder [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sistemi ve bağımlılık özellikleri.</span><span class="sxs-lookup"><span data-stu-id="41c4e-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="41c4e-112">Özellik değeri belirlemeyi özelleştirmek için bu sanalları kullanma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri aramaları ve doğrulama](dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="41c4e-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="41c4e-113">FXCop Kural zorlama vs. Özellik sistemi Uygula</span><span class="sxs-lookup"><span data-stu-id="41c4e-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="41c4e-114">Yapı işleminizin bir parçası olarak Microsoft FXCop aracı kullanıyorsanız ve bu belirli ya da türetilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework sınıflarını temel oluşturucu, arama veya kendi bağımlılık özellikleri türetilen sınıflarda uygulamak, belirli bir karşılaşabileceğiniz FXCop kuralı ihlali.</span><span class="sxs-lookup"><span data-stu-id="41c4e-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="41c4e-115">Bu ihlalin adı dize şöyledir:</span><span class="sxs-lookup"><span data-stu-id="41c4e-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="41c4e-116">Bu varsayılan genel kural kümesi için FXCop parçası olan bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="41c4e-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="41c4e-117">Bu kural bir izleme sonunda bir bağımlılık özelliği sistem sanal yöntemini çağırır bağımlılık özelliği sistem aracılığıyla raporlama nedir olması.</span><span class="sxs-lookup"><span data-stu-id="41c4e-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="41c4e-118">Bu kuralı ihlal devre dışı bırakın veya bu kuralda, FXCop Kural kümesi yapılandırması bastırmak ihtiyacınız olabilecek şekilde bu konu başlığında, belgelenen önerilen oluşturucu desenler izledikten sonra bile görüntülenmeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="41c4e-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="41c4e-119">Varolan sınıfları kullanarak değil, türetilmiş sınıflardan çoğu sorunu gelir</span><span class="sxs-lookup"><span data-stu-id="41c4e-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="41c4e-120">Bu kural tarafından bildirilen sorunları, kendi yapı dizisi sanal yöntemleri uygulayan bir sınıf ardından türetilir oluşur.</span><span class="sxs-lookup"><span data-stu-id="41c4e-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="41c4e-121">Sınıfınızı veya aksi halde biliyorsanız veya sınıfınıza nesnesinden türetilmesi değil, zorunlu, burada açıklanan önemli noktalar ve FXCop Kural motive sorunları için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="41c4e-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="41c4e-122">Ancak, bunlar örneği için temel sınıf olarak kullanılacak yöneliktir şekilde sınıfları yazıyorsanız şablonları oluşturmakta olduğunuz ya da genişletilebilir denetim kitaplığı ayarlayın, Oluşturucular için burada önerilen desenleri izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="41c4e-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="41c4e-123">Varsayılan Oluşturucu tüm değerleri geri çağırmalar tarafından istenen başlatmalıdır</span><span class="sxs-lookup"><span data-stu-id="41c4e-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="41c4e-124">Bu değerlerden bazıları "gerçek" değerlerle doldurulur olsa bile, sınıf varsayılan oluşturucusuna sınıf geçersiz kılmalarını veya geri çağırmaları (geri aramalar özellik sistem sanalları bölümündeki listeden) tarafından kullanılan tüm örnek üyeleri başlatılmalıdır Varsayılan olmayan oluşturucular parametreleri.</span><span class="sxs-lookup"><span data-stu-id="41c4e-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class default constructor, even if some of those values are filled by "real" values through parameters of the nondefault constructors.</span></span>  
  
 <span data-ttu-id="41c4e-125">Aşağıdaki örnek kodu (ve sonraki örneklerde) pseudo - olanC# bu kuralı ihlal ediyor ve sorunu anlatan örnek:</span><span class="sxs-lookup"><span data-stu-id="41c4e-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
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
  
 <span data-ttu-id="41c4e-126">Uygulama kodu çağırdığında `new MyClass(objectvalue)`, bu çağrı varsayılan oluşturucuyu ve temel sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="41c4e-126">When application code calls `new MyClass(objectvalue)`, this calls the default constructor and base class constructors.</span></span> <span data-ttu-id="41c4e-127">Bu ayarlar sonra `Property1 = object1`, sanal yöntemini çağırır `OnPropertyChanged` sahip olan üzerinde `MyClass` <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="41c4e-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="41c4e-128">Geçersiz kılma başvurduğu `_myList`, hangi başlatılmamış henüz.</span><span class="sxs-lookup"><span data-stu-id="41c4e-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="41c4e-129">Bu sorunlardan kaçınmak için bir yolu geri çağırmaları yalnızca diğer bağımlılık özellikleri kullanmak ve böyle her bir bağımlılık özelliği meta verilerini kayıtlı bir parçası olarak oluşturulmuş varsayılan bir değere sahip olduğundan emin olmaktır.</span><span class="sxs-lookup"><span data-stu-id="41c4e-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="41c4e-130">Güvenli Oluşturucu desenleri</span><span class="sxs-lookup"><span data-stu-id="41c4e-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="41c4e-131">Sınıfınızın bir temel sınıf olarak kullanılırsa, tamamlanmamış başlatma risklerini önlemek için bu desenleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="41c4e-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="default-constructors-calling-base-initialization"></a><span data-ttu-id="41c4e-132">Varsayılan oluşturucular temel başlatma çağırma</span><span class="sxs-lookup"><span data-stu-id="41c4e-132">Default constructors calling base initialization</span></span>  
 <span data-ttu-id="41c4e-133">Temel varsayılan çağıran bu oluşturucular uygulayın:</span><span class="sxs-lookup"><span data-stu-id="41c4e-133">Implement these constructors calling the base default:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="41c4e-134">Varsayılan olmayan (kullanışlı) oluşturucuları, hiçbir temel imza ile eşleşmiyor</span><span class="sxs-lookup"><span data-stu-id="41c4e-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="41c4e-135">Bu oluşturucular ayarlamak için parametreleri kullanıyorsanız başlatma işlemindeki bağımlılık özellikleri için başlatma kendi sınıfın varsayılan oluşturucusunu çağırın ve ardından bağımlılık özellikleri ayarlamak için parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="41c4e-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class default constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="41c4e-136">Bunlar ya da bağımlılık özellikleri, sınıf tarafından tanımlanan veya temel sınıftan devralınan bağımlılık özellikleri ancak her iki durumda da şu biçimi kullanın:</span><span class="sxs-lookup"><span data-stu-id="41c4e-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="41c4e-137">Temel imzaları eşleşen varsayılan (kullanışlı) olmayan oluşturucular</span><span class="sxs-lookup"><span data-stu-id="41c4e-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="41c4e-138">Aynı Parametreleştirme ile temel oluşturucuyu çağırmak yerine, kendi sınıf varsayılan oluşturucusuna yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="41c4e-138">Instead of calling the base constructor with the same parameterization, again call your own class' default constructor.</span></span> <span data-ttu-id="41c4e-139">Temel Başlatıcı çağırmaz; Bunun yerine çağırmalısınız `this()`.</span><span class="sxs-lookup"><span data-stu-id="41c4e-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="41c4e-140">Ardından özgün Oluşturucusu davranışı, ilgili özellikleri ayarlamak için değerleri olarak geçirilen parametreleri kullanarak yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="41c4e-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="41c4e-141">Belirli parametreleri olan özellikleri belirlemede rehberlik için özgün temel oluşturucu belgeleri ayarlamak için hedeflenen kullanın:</span><span class="sxs-lookup"><span data-stu-id="41c4e-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="41c4e-142">Tüm imzaları eşleşmelidir</span><span class="sxs-lookup"><span data-stu-id="41c4e-142">Must match all signatures</span></span>  
 <span data-ttu-id="41c4e-143">Temel tür çoklu imzalara sahip olduğu durumlarda, tüm olası sonraki özellikleri ayarlamadan önce sınıfın varsayılan oluşturucusunu çağırma önerilen desen kullanan bir oluşturucu uygulaması kendi imzalar kasıtlı olarak eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="41c4e-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class default constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="41c4e-144">SetValue bağımlılık özellikleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="41c4e-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="41c4e-145">Özellik ayarı kolaylık sağlamak için bir sarmalayıcı üretilmesini, ve değerleri ile ayarlanır bir özelliği ayarlıyorsanız bu aynı desenleri uygulamak <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="41c4e-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="41c4e-146">Aramalarınız <xref:System.Windows.DependencyObject.SetValue%2A> Oluşturucu parametresi bu geçiş başlatma için de sınıfının varsayılan oluşturucusunu çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41c4e-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' default constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c4e-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41c4e-147">See also</span></span>

- [<span data-ttu-id="41c4e-148">Özel Bağımlılık Özellikleri</span><span class="sxs-lookup"><span data-stu-id="41c4e-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="41c4e-149">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="41c4e-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="41c4e-150">Bağımlılık Özelliği Güvenliği</span><span class="sxs-lookup"><span data-stu-id="41c4e-150">Dependency Property Security</span></span>](dependency-property-security.md)

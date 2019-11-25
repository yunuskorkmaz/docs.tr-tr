---
title: DependencyObjects için Güvenli Oluşturucu Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 66e380a9428395c772d0dcfe45a995374774aec6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283826"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="5e81a-102">DependencyObjects için Güvenli Oluşturucu Desenleri</span><span class="sxs-lookup"><span data-stu-id="5e81a-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="5e81a-103">Genellikle, sınıf oluşturucular, türetilmiş bir sınıf için oluşturucuların temel başlatması olarak çağrılabilmesi için sanal yöntemler veya temsilciler gibi geri çağırmaları çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e81a-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="5e81a-104">Sanal alanının girilmesi, belirli bir nesnenin tamamlanmamış bir başlatma durumunda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e81a-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="5e81a-105">Ancak, özellik sistemi, bağımlılık özellik sisteminin bir parçası olarak, geri çağırmaları dahili olarak çağırır ve kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="5e81a-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="5e81a-106">Bir bağımlılık özelliği değerini <xref:System.Windows.DependencyObject.SetValue%2A> çağrısı ile ayarlamaya yönelik basit bir işlem, belirlemenin bir yerinde geri çağırma içerir.</span><span class="sxs-lookup"><span data-stu-id="5e81a-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="5e81a-107">Bu nedenle, türü temel sınıf olarak kullanılıyorsa sorunlu olabilecek bir oluşturucunun gövdesinde bağımlılık özelliği değerlerini ayarlarken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e81a-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="5e81a-108">Bağımlılık özelliği durumlarıyla ilgili belirli sorunları ve burada belgelenen devralınan geri çağırmaları önleyen <xref:System.Windows.DependencyObject> oluşturucuları uygulamak için belirli bir model vardır.</span><span class="sxs-lookup"><span data-stu-id="5e81a-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="5e81a-109">Özellik sistemi sanal yöntemleri</span><span class="sxs-lookup"><span data-stu-id="5e81a-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="5e81a-110">Aşağıdaki sanal yöntemler veya geri çağrılar, bir bağımlılık özelliği değeri ayarlayan <xref:System.Windows.DependencyObject.SetValue%2A> çağrısının hesaplamaları sırasında çağrılabilir: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="5e81a-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="5e81a-111">Bu sanal yöntemlerin veya geri aramaların her biri, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sisteminin ve bağımlılık özelliklerinin çok yönlülüğünü genişlemede belirli bir amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="5e81a-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="5e81a-112">Özellik değeri belirlemeyi özelleştirmek için bu sanallaştırmaların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="5e81a-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="5e81a-113">FXCop kural zorlaması ve özellik sistemi sanalları karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="5e81a-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="5e81a-114">Yapı işleminizin bir parçası olarak Microsoft araç FXCop ' yi kullanırsanız ve temel oluşturucuyu çağıran belirli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Framework sınıflarından türetirsiniz ya da türetilmiş sınıflarda kendi bağımlılık özelliklerinizi uygularsanız, belirli bir FXCop kural ihlaliyle karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e81a-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="5e81a-115">Bu ihlalin ad dizesi:</span><span class="sxs-lookup"><span data-stu-id="5e81a-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="5e81a-116">Bu, FXCop için varsayılan genel kural kümesinin bir parçası olan bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="5e81a-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="5e81a-117">Bu kuralın Raporlama işlemi, son olarak bağımlılık özellik sistemi sanal yöntemi çağıran bağımlılık özellik sistemi aracılığıyla yapılan bir izdir.</span><span class="sxs-lookup"><span data-stu-id="5e81a-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="5e81a-118">Bu kural ihlali, bu konuda belgelenen önerilen Oluşturucu desenlerinden sonra bile görünmeye devam edebilir. bu nedenle, FXCop kural kümesi yapılandırmanızda bu kuralı devre dışı bırakmanız veya gizetmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5e81a-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="5e81a-119">Çoğu sorun, mevcut sınıfları kullanmadan değil, türetilen sınıflardan gelir</span><span class="sxs-lookup"><span data-stu-id="5e81a-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="5e81a-120">Bu kural tarafından bildirilen sorunlar, yapı dizisinde sanal yöntemlerle uyguladığınız bir sınıf daha sonra öğesinden türetilmişse oluşur.</span><span class="sxs-lookup"><span data-stu-id="5e81a-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="5e81a-121">Sınıfınızı mühürlemek veya sınıfınızın türetilemeyeceğini bilmeniz veya uygulamanız durumunda, burada açıklanan noktalar ve FXCop kuralını zorlayan sorunlar sizin için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="5e81a-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="5e81a-122">Ancak, sınıfları temel sınıf olarak kullanılmak üzere tasarlanan bir şekilde yazıyorsanız, örneğin, şablonlar oluşturuyorsanız veya Genişletilebilir bir denetim kitaplığı ayarlandıysa, oluşturucular için burada önerilen desenleri izlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5e81a-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="5e81a-123">Varsayılan oluşturucular, geri çağırmalar tarafından Istenen tüm değerleri başlatmalıdır</span><span class="sxs-lookup"><span data-stu-id="5e81a-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="5e81a-124">Sınıfınız tarafından kullanılan tüm örnek üyeleri (örneğin, özellik sistemi sanalları bölümündeki listeden geri çağırmalar), bu değerlerden bazıları ile "gerçek" değerler tarafından doldurulsa bile, Sınıfınal Oluşturucu içinde başlatılmalıdır. Parametresiz oluşturucuların parametreleri.</span><span class="sxs-lookup"><span data-stu-id="5e81a-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class parameterless constructor, even if some of those values are filled by "real" values through parameters of the nonparameterless constructors.</span></span>  
  
 <span data-ttu-id="5e81a-125">Aşağıdaki örnek kod (ve sonraki örnekler), bu kuralı ihlal edenC# ve sorunu açıklayan bir sözde örnektir:</span><span class="sxs-lookup"><span data-stu-id="5e81a-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="5e81a-126">Uygulama kodu `new MyClass(objectvalue)`çağırdığında, bu, parametresiz oluşturucuyu ve temel sınıf oluşturucularını çağırır.</span><span class="sxs-lookup"><span data-stu-id="5e81a-126">When application code calls `new MyClass(objectvalue)`, this calls the parameterless constructor and base class constructors.</span></span> <span data-ttu-id="5e81a-127">Daha sonra, sahip olan `MyClass` <xref:System.Windows.DependencyObject>sanal yöntemi `OnPropertyChanged` çağıran `Property1 = object1`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5e81a-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="5e81a-128">Geçersiz kılma, henüz başlatılmamış `_myList`anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5e81a-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="5e81a-129">Bu sorunlardan kaçınmanın bir yolu, geri çağırmaların yalnızca diğer bağımlılık özelliklerini kullanmasını ve bu tür bağımlılık özelliklerinin kayıtlı meta verilerin bir parçası olarak belirlenen bir varsayılan değere sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e81a-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="5e81a-130">Güvenli Oluşturucu desenleri</span><span class="sxs-lookup"><span data-stu-id="5e81a-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="5e81a-131">Sınıfınız temel sınıf olarak kullanılıyorsa tamamlanmamış başlatmanın risklerinden kaçınmak için şu desenleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="5e81a-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a><span data-ttu-id="5e81a-132">Temel başlatmayı çağıran parametresiz oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5e81a-132">Parameterless constructors calling base initialization</span></span>  
 <span data-ttu-id="5e81a-133">Temel varsayılanı çağıran bu oluşturucuları Uygula:</span><span class="sxs-lookup"><span data-stu-id="5e81a-133">Implement these constructors calling the base default:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="5e81a-134">Hiçbir temel imzayı eşleştirmeyen varsayılan olmayan (kolay) oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5e81a-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="5e81a-135">Bu oluşturucular başlatma içindeki bağımlılık özelliklerini ayarlamak için parametreleri kullanıyorsa, önce başlatma için kendi sınıf parametresiz oluşturucuyu çağırın ve ardından bağımlılık özelliklerini ayarlamak için parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e81a-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class parameterless constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="5e81a-136">Bunlar, sınıfınız tarafından tanımlanan bağımlılık özellikleri ya da temel sınıflardan devralınan bağımlılık özellikleridir, ancak her iki durumda da aşağıdaki kalıbı kullanır:</span><span class="sxs-lookup"><span data-stu-id="5e81a-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="5e81a-137">Taban imzalarıyla eşleşen varsayılan olmayan (kolay) oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5e81a-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="5e81a-138">Temel oluşturucuyu aynı Parametreleştirme ile çağırmak yerine kendi sınıfınızın ' parametresiz oluşturucuyu çağırın.</span><span class="sxs-lookup"><span data-stu-id="5e81a-138">Instead of calling the base constructor with the same parameterization, again call your own class' parameterless constructor.</span></span> <span data-ttu-id="5e81a-139">Temel başlatıcıyı çağırmayın; Bunun yerine `this()`çağırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="5e81a-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="5e81a-140">Ardından, ilgili özellikleri ayarlamak için geçirilen parametreleri değerler olarak kullanarak özgün Oluşturucu davranışını yeniden üretin.</span><span class="sxs-lookup"><span data-stu-id="5e81a-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="5e81a-141">Belirli parametrelerin ayarlanması amaçlanan özellikleri belirlemede rehberlik için özgün temel Oluşturucu belgelerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="5e81a-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="5e81a-142">Tüm imzalarla eşleşmelidir</span><span class="sxs-lookup"><span data-stu-id="5e81a-142">Must match all signatures</span></span>  
 <span data-ttu-id="5e81a-143">Temel türün birden çok imzaya sahip olduğu durumlarda, daha fazla ayarlamadan önce parametresiz oluşturucuyu çağırmak için önerilen kalıbı kullanan tüm olası imzaları kendi Oluşturucu uygulamasıyla eşleştirmelidir özelliklerinin.</span><span class="sxs-lookup"><span data-stu-id="5e81a-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class parameterless constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="5e81a-144">DeğerBelirle ile bağımlılık özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="5e81a-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="5e81a-145">Bu aynı desenler, özellik ayarı kolaylığı için sarmalayıcı içermeyen bir özelliği ayarlıyorsanız ve değerleri <xref:System.Windows.DependencyObject.SetValue%2A>olarak ayarlarsanız geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5e81a-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="5e81a-146">Oluşturucu parametreleri üzerinden geçen <xref:System.Windows.DependencyObject.SetValue%2A> çağrılarınız, başlatma için sınıf ' parametresiz oluşturucuyu de çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e81a-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' parameterless constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e81a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e81a-147">See also</span></span>

- [<span data-ttu-id="5e81a-148">Özel Bağımlılık Özellikleri</span><span class="sxs-lookup"><span data-stu-id="5e81a-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="5e81a-149">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e81a-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="5e81a-150">Bağımlılık Özelliği Güvenliği</span><span class="sxs-lookup"><span data-stu-id="5e81a-150">Dependency Property Security</span></span>](dependency-property-security.md)

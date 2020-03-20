---
title: DependencyObjects için Güvenli Oluşturucu Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 6d6ff444b99ca893e687731c56a48ea3ac072dd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187225"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="72a55-102">DependencyObjects için Güvenli Oluşturucu Desenleri</span><span class="sxs-lookup"><span data-stu-id="72a55-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="72a55-103">Genellikle, sınıf oluşturucular sanal yöntemler veya temsilciler gibi geri aramaları çağırmamalıdır, çünkü oluşturucular türemiş bir sınıf için oluşturucuların temel başlatması olarak adlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="72a55-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="72a55-104">Sanal girilse, belirli bir nesnenin eksik bir başlatma durumunda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="72a55-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="72a55-105">Ancak, özellik sisteminin kendisi, bağımlılık özelliği sisteminin bir parçası olarak çağrıları çağırır ve dahili olarak ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="72a55-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="72a55-106">Bir bağımlılık özelliği değerini arama yla <xref:System.Windows.DependencyObject.SetValue%2A> ayarlamak kadar basit bir işlem, olası bir şekilde belirlemede bir yerde bir geri arama içerir.</span><span class="sxs-lookup"><span data-stu-id="72a55-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="72a55-107">Bu nedenle, bir oluşturucu gövdesi içinde bağımlılık özelliği değerlerini ayarlarken dikkatli olmalısınız, bu da türünüz taban sınıf olarak kullanıldığında sorun yaratabilir.</span><span class="sxs-lookup"><span data-stu-id="72a55-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="72a55-108">Bağımlılık özelliği durumları ve <xref:System.Windows.DependencyObject> burada belgelenmiş olan doğal geri aramalarla ilgili belirli sorunları önleyen yapıcıları uygulamak için özel bir model vardır.</span><span class="sxs-lookup"><span data-stu-id="72a55-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  

<a name="Property_System_Virtual_Methods"></a>
## <a name="property-system-virtual-methods"></a><span data-ttu-id="72a55-109">Emlak Sistemi Sanal Yöntemler</span><span class="sxs-lookup"><span data-stu-id="72a55-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="72a55-110">Aşağıdaki sanal yöntemler veya geri aramalar, bağımlılık özelliği değerini <xref:System.Windows.DependencyObject.SetValue%2A> belirleyen çağrının hesaplamaları <xref:System.Windows.ValidateValueCallback>sırasında <xref:System.Windows.PropertyChangedCallback> <xref:System.Windows.CoerceValueCallback>potansiyel <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>olarak çağrılır: , , .</span><span class="sxs-lookup"><span data-stu-id="72a55-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="72a55-111">Bu sanal yöntemlerin veya geri aramaların her biri, özellik sisteminin ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bağımlılık özelliklerinin çok yönlülüğünü genişletmek için belirli bir amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="72a55-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="72a55-112">Özellik değeri belirlemeyi özelleştirmek için bu sanalların nasıl kullanılacağı hakkında daha fazla bilgi için Bkz. [Bağımlılık Özelliği Geri Aramaları ve Doğrulama.](dependency-property-callbacks-and-validation.md)</span><span class="sxs-lookup"><span data-stu-id="72a55-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="72a55-113">FXCop Kural Uygulama vs Emlak Sistemi Sanallar</span><span class="sxs-lookup"><span data-stu-id="72a55-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="72a55-114">Microsoft aracı FXCop'u yapı işleminizin bir parçası olarak kullanırsanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve temel oluşturucuyu çağıran belirli çerçeve sınıflarından türetilirseniz veya türetilmiş sınıflarda kendi bağımlılık özelliklerinizi uygularsanız, belirli bir FXCop kural ihlaliyle karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72a55-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="72a55-115">Bu ihlalin ad dizesi:</span><span class="sxs-lookup"><span data-stu-id="72a55-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="72a55-116">Bu, FXCop için belirlenen varsayılan genel kuralın bir parçası olan bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="72a55-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="72a55-117">Bu kuralın bildirdiği şey, sonunda bağımlılık özelliği sistemi sanal yöntemi çağıran bağımlılık özelliği sistemi üzerinden bir izlemedir.</span><span class="sxs-lookup"><span data-stu-id="72a55-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="72a55-118">Bu kural ihlali, bu konuda belgelenen önerilen yapıcı desenleri takip ettikten sonra bile görünmeye devam edebilir, bu nedenle FXCop kural kümesi yapılandırmanızda bu kuralı devre dışı bırakamanız veya bastırmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="72a55-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="72a55-119">Sorunların çoğu Varolan Sınıfları Kullanmadan Gelen Sınıflar</span><span class="sxs-lookup"><span data-stu-id="72a55-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="72a55-120">Bu kural tarafından bildirilen sorunlar, yapı dizisinde sanal yöntemlerle uyguladığınız bir sınıf türetildiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="72a55-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="72a55-121">Sınıfınızı mühürlerseniz veya sınıfınızdan türetilmeyeceğini bilir veya uygularsanız, burada açıklanan hususlar ve FXCop kuralını motive eden konular sizin için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="72a55-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="72a55-122">Ancak, sınıfları temel sınıflar olarak kullanılmak üzere tasarlanacak şekilde yazarsanız, örneğin şablonlar veya genişletilebilir denetim kitaplığı kümesi oluşturuyorsanız, burada oluşturucular için önerilen desenleri izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="72a55-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="72a55-123">Varsayılan Oluşturucular Geri Aramalar Tarafından İstenen Tüm Değerleri Başlatmalı</span><span class="sxs-lookup"><span data-stu-id="72a55-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="72a55-124">Sınıfınız tarafından kullanılan tüm örnek üyeler geçersiz kılar veya geri aramaları (Özellik Sistemi Sanalları bölümündeki listeden geri çağırmalar) sınıfınızda parametresiz oluşturucunuzda başharfe alınmalıdır, bu değerlerden bazıları "gerçek" değerler aracılığıyla doldurulsa bile parametresiz yapıcıların parametreleri.</span><span class="sxs-lookup"><span data-stu-id="72a55-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class parameterless constructor, even if some of those values are filled by "real" values through parameters of the nonparameterless constructors.</span></span>  
  
 <span data-ttu-id="72a55-125">Aşağıdaki örnek kod (ve sonraki örnekler) bu kuralı ihlal eden ve sorunu açıklayan bir sözde C# örneğidir:</span><span class="sxs-lookup"><span data-stu-id="72a55-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
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
  
 <span data-ttu-id="72a55-126">Uygulama kodu `new MyClass(objectvalue)`aradığında, bu parametresiz yapıcı ve taban sınıf oluşturucuları çağırır.</span><span class="sxs-lookup"><span data-stu-id="72a55-126">When application code calls `new MyClass(objectvalue)`, this calls the parameterless constructor and base class constructors.</span></span> <span data-ttu-id="72a55-127">Sonra ayarlar `Property1 = object1`, hangi sahip `OnPropertyChanged` sanal `MyClass` <xref:System.Windows.DependencyObject>yöntem çağırır .</span><span class="sxs-lookup"><span data-stu-id="72a55-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="72a55-128">Geçersiz `_myList`kılma, henüz başharfe edilmemiş olan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="72a55-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="72a55-129">Bu sorunları önlemenin bir yolu, geri aramaların yalnızca diğer bağımlılık özelliklerini kullandığından ve bu tür bağımlılık özelliğinin kayıtlı meta verilerinin bir parçası olarak belirlenmiş bir varsayılan değere sahip olduğundan emin olmaktır.</span><span class="sxs-lookup"><span data-stu-id="72a55-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>
## <a name="safe-constructor-patterns"></a><span data-ttu-id="72a55-130">Güvenli Yapıcı Desenler</span><span class="sxs-lookup"><span data-stu-id="72a55-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="72a55-131">Sınıfınız taban sınıf olarak kullanılıyorsa eksik başlatma risklerini önlemek için aşağıdaki desenleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="72a55-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a><span data-ttu-id="72a55-132">Parametresiz oluşturucular baz başlatma çağrı</span><span class="sxs-lookup"><span data-stu-id="72a55-132">Parameterless constructors calling base initialization</span></span>  
 <span data-ttu-id="72a55-133">Temel varsayılan olarak adlandıran bu oluşturucuları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="72a55-133">Implement these constructors calling the base default:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="72a55-134">Varsayılan olmayan (kolaylık) oluşturucular, herhangi bir temel imza yla eşleşmez</span><span class="sxs-lookup"><span data-stu-id="72a55-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="72a55-135">Bu oluşturucular, başlatmada bağımlılık özelliklerini ayarlamak için parametreleri kullanıyorsa, önce başlatma için kendi sınıf parametresiz oluşturucunuzu arayın ve ardından bağımlılık özelliklerini ayarlamak için parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="72a55-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class parameterless constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="72a55-136">Bunlar, sınıfınız tarafından tanımlanan bağımlılık özellikleri veya temel sınıflardan devralınan bağımlılık özellikleri olabilir, ancak her iki durumda da aşağıdaki deseni kullanın:</span><span class="sxs-lookup"><span data-stu-id="72a55-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="72a55-137">Temel imzalarla eşleşen varsayılan olmayan (kolaylık) oluşturucular</span><span class="sxs-lookup"><span data-stu-id="72a55-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="72a55-138">Temel oluşturucuyu aynı parametrelendirmeye sahip çağırmak yerine, yine kendi sınıfınızın parametresiz oluşturucusu olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="72a55-138">Instead of calling the base constructor with the same parameterization, again call your own class' parameterless constructor.</span></span> <span data-ttu-id="72a55-139">Üs initializer'ı aramayın; bunun yerine `this()`aramalısınız.</span><span class="sxs-lookup"><span data-stu-id="72a55-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="72a55-140">Ardından, ilgili özellikleri ayarlamak için geçirilen parametreleri değerler olarak kullanarak özgün oluşturucu davranışı yeniden üretin.</span><span class="sxs-lookup"><span data-stu-id="72a55-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="72a55-141">Belirli parametrelerin ayarlamak üzere tasarlandığı özellikleri belirlerken kılavuz için özgün temel oluşturucu belgelerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="72a55-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="72a55-142">Tüm imzalarla eşleşmeli</span><span class="sxs-lookup"><span data-stu-id="72a55-142">Must match all signatures</span></span>  
 <span data-ttu-id="72a55-143">Temel türün birden çok imzası olduğu durumlarda, daha fazla ayarlamadan önce sınıf parametresiz oluşturucuyu çağırma nın önerilen deseni kullanan kendi oluşturucunuzla tüm olası imzaları kasıtlı olarak eşleştirmeniz gerekir Özellikler.</span><span class="sxs-lookup"><span data-stu-id="72a55-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class parameterless constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="72a55-144">SetValue ile bağımlılık özelliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="72a55-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="72a55-145">Bu aynı desenler, özellik ayarı kolaylığı için sarıcı olmayan bir özelliği ayarlıyorsanız ve değerleri <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="72a55-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="72a55-146">Bu geçiş <xref:System.Windows.DependencyObject.SetValue%2A> için çağrılarınızı oluşturucu parametreleri ile de başlatma için sınıfın parametresiz oluşturucu çağırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="72a55-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' parameterless constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a55-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72a55-147">See also</span></span>

- [<span data-ttu-id="72a55-148">Özel Bağımlılık Özellikleri</span><span class="sxs-lookup"><span data-stu-id="72a55-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="72a55-149">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="72a55-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="72a55-150">Bağımlılık Özelliği Güvenliği</span><span class="sxs-lookup"><span data-stu-id="72a55-150">Dependency Property Security</span></span>](dependency-property-security.md)

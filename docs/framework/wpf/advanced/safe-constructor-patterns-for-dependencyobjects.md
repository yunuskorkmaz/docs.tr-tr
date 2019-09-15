---
title: DependencyObjects için Güvenli Oluşturucu Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: fce17979fbd43df0496f972cac525fd79dcbfe32
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991816"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>DependencyObjects için Güvenli Oluşturucu Desenleri
Genellikle, sınıf oluşturucular, türetilmiş bir sınıf için oluşturucuların temel başlatması olarak çağrılabilmesi için sanal yöntemler veya temsilciler gibi geri çağırmaları çağırmamalıdır. Sanal alanının girilmesi, belirli bir nesnenin tamamlanmamış bir başlatma durumunda yapılabilir. Ancak, özellik sistemi, bağımlılık özellik sisteminin bir parçası olarak, geri çağırmaları dahili olarak çağırır ve kullanıma sunar. Tek bir işlem, çağrı ile <xref:System.Windows.DependencyObject.SetValue%2A> bağımlılık özelliği değerini ayarlamaya yönelik bir işlemin büyük olasılıkla, belirlemenin bir yerinde geri çağırma içermesi. Bu nedenle, türü temel sınıf olarak kullanılıyorsa sorunlu olabilecek bir oluşturucunun gövdesinde bağımlılık özelliği değerlerini ayarlarken dikkatli olmanız gerekir. Bağımlılık özelliği durumlarıyla ilgili belirli sorunları ve <xref:System.Windows.DependencyObject> burada belgelenen devralınan geri çağırmaları engelleyen oluşturucular uygulamak için belirli bir model vardır.  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Özellik sistemi sanal yöntemleri  
 Aşağıdaki sanal yöntemler veya geri çağrılar, bir <xref:System.Windows.DependencyObject.SetValue%2A> bağımlılık özelliği değeri ayarlayan çağrının hesaplamaları sırasında çağrılabilir: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Bu sanal yöntemlerin veya geri aramaların her biri, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sisteminin ve bağımlılık özelliklerinin çok yönlülüğünü genişletmede belirli bir amaca hizmet eder. Özellik değeri belirlemeyi özelleştirmek için bu sanallaştırmaların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>FXCop kural zorlaması ile Özellik sistemi sanal öğeleri  
 Yapı işleminizin bir parçası olarak Microsoft araç FxCop ' yi kullanırsanız ve temel oluşturucuyu çağıran belirli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çerçeve sınıflarından türetirsiniz ya da türetilmiş sınıflarda kendi bağımlılık özelliklerinizi uygularsanız, belirli bir sorunla karşılaşabilirsiniz FXCop kural ihlali. Bu ihlalin ad dizesi:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Bu, FXCop için varsayılan genel kural kümesinin bir parçası olan bir kuraldır. Bu kuralın Raporlama işlemi, son olarak bağımlılık özellik sistemi sanal yöntemi çağıran bağımlılık özellik sistemi aracılığıyla yapılan bir izdir. Bu kural ihlali, bu konuda belgelenen önerilen Oluşturucu desenlerinden sonra bile görünmeye devam edebilir. bu nedenle, FXCop kural kümesi yapılandırmanızda bu kuralı devre dışı bırakmanız veya gizetmeniz gerekebilir.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Çoğu sorun, mevcut sınıfları kullanmadan değil, türetilen sınıflardan gelir  
 Bu kural tarafından bildirilen sorunlar, yapı dizisinde sanal yöntemlerle uyguladığınız bir sınıf daha sonra öğesinden türetilmişse oluşur. Sınıfınızı mühürlemek veya sınıfınızın türetilemeyeceğini bilmeniz veya uygulamanız durumunda, burada açıklanan noktalar ve FXCop kuralını zorlayan sorunlar sizin için uygun değildir. Ancak, sınıfları temel sınıf olarak kullanılmak üzere tasarlanan bir şekilde yazıyorsanız, örneğin, şablonlar oluşturuyorsanız veya Genişletilebilir bir denetim kitaplığı ayarlandıysa, oluşturucular için burada önerilen desenleri izlemelisiniz.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Varsayılan oluşturucular, geri çağırmalar tarafından Istenen tüm değerleri başlatmalıdır  
 Sınıfınız tarafından kullanılan tüm örnek üyeleri (örneğin, özellik sistemi sanalları bölümündeki listeden geri çağırmalar), bu değerlerden bazıları ile "gerçek" değerler tarafından doldurulsa bile, Sınıfınal Oluşturucu içinde başlatılmalıdır. Parametresiz oluşturucuların parametreleri.  
  
 Aşağıdaki örnek kod (ve sonraki örnekler), bu kuralı ihlal edenC# ve sorunu açıklayan bir sözde örnektir:  
  
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
  
 Uygulama kodu çağırdığında `new MyClass(objectvalue)`, bu, parametresiz oluşturucuyu ve temel sınıf oluşturucularını çağırır. Ardından, sahip `Property1 = object1` `OnPropertyChanged` `MyClass` olduğu sanal yöntemi çağıranayarlar.<xref:System.Windows.DependencyObject>  Override, henüz başlatılmamış `_myList`olan öğesine başvuruyor.  
  
 Bu sorunlardan kaçınmanın bir yolu, geri çağırmaların yalnızca diğer bağımlılık özelliklerini kullanmasını ve bu tür bağımlılık özelliklerinin kayıtlı meta verilerin bir parçası olarak belirlenen bir varsayılan değere sahip olmasını sağlar.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Güvenli Oluşturucu desenleri  
 Sınıfınız temel sınıf olarak kullanılıyorsa tamamlanmamış başlatmanın risklerinden kaçınmak için şu desenleri izleyin:  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a>Temel başlatmayı çağıran parametresiz oluşturucular  
 Temel varsayılanı çağıran bu oluşturucuları Uygula:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Hiçbir temel imzayı eşleştirmeyen varsayılan olmayan (kolay) oluşturucular  
 Bu oluşturucular başlatma içindeki bağımlılık özelliklerini ayarlamak için parametreleri kullanıyorsa, önce başlatma için kendi sınıf parametresiz oluşturucuyu çağırın ve ardından bağımlılık özelliklerini ayarlamak için parametreleri kullanın. Bunlar, sınıfınız tarafından tanımlanan bağımlılık özellikleri ya da temel sınıflardan devralınan bağımlılık özellikleridir, ancak her iki durumda da aşağıdaki kalıbı kullanır:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Taban imzalarıyla eşleşen varsayılan olmayan (kolay) oluşturucular  
 Temel oluşturucuyu aynı Parametreleştirme ile çağırmak yerine kendi sınıfınızın ' parametresiz oluşturucuyu çağırın. Temel başlatıcıyı çağırmayın; Bunun yerine, öğesini `this()`çağırmanız gerekir. Ardından, ilgili özellikleri ayarlamak için geçirilen parametreleri değerler olarak kullanarak özgün Oluşturucu davranışını yeniden üretin. Belirli parametrelerin ayarlanması amaçlanan özellikleri belirlemede rehberlik için özgün temel Oluşturucu belgelerini kullanın:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Tüm imzalarla eşleşmelidir  
 Temel türün birden çok imzaya sahip olduğu durumlarda, daha fazla ayarlamadan önce parametresiz oluşturucuyu çağırmak için önerilen kalıbı kullanan tüm olası imzaları kendi Oluşturucu uygulamasıyla eşleştirmelidir özelliklerinin.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>DeğerBelirle ile bağımlılık özelliklerini ayarlama  
 Bu aynı desenler özellik ayarı kolaylığı için sarmalayıcı içermeyen bir özellik ayarlıyorsanız ve değerlerini ile <xref:System.Windows.DependencyObject.SetValue%2A>ayarlarsanız geçerlidir. <xref:System.Windows.DependencyObject.SetValue%2A> Bu geçiş Oluşturucu parametrelerine yapılan çağrılarınız, başlatma için sınıf ' parametresiz oluşturucuyu de çağırmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Bağımlılık Özelliği Güvenliği](dependency-property-security.md)

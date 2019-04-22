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
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>DependencyObjects için Güvenli Oluşturucu Desenleri
Genel olarak, sınıf oluşturucuları türetilmiş bir sınıf için temel oluşturucuları başlatma oluşturucular çağrılamayacağından sanal yöntemler veya temsilciler gibi geri çağırmaları çağırmalıdır değil. Herhangi bir nesne bir eksik başlatma durumuna girmek sanal yapılabilir. Ancak, özellik sistemi çağırır ve geri çağırmaları dahili olarak, bağımlılık özelliği sisteminin bir parçası kullanıma sunar. Bir bağımlılık özelliği değer ile ayarı olarak basit bir işlem <xref:System.Windows.DependencyObject.SetValue%2A> çağrı potansiyel olarak içeren bir geri çağırma yere belirlenmesi. Bu nedenle, bağımlılık türünüz temel sınıf olarak kullanılırsa, sorunlu olabilecek bir oluşturucu gövdesi içinde özellik değerlerini ayarlarken dikkatli olmanız gerekir. Uygulama için belirli bir desene yoktur <xref:System.Windows.DependencyObject> Oluşturucular, burada belgelenmektedir bağımlılık özelliği durumlar ve devralınmış geri çağırmalar belirli sorunları önler.  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Özellik sistemi sanal yöntemleri  
 Sanal yöntemleri veya geri çağırmaları hesaplamaları sırasında adı verilir <xref:System.Windows.DependencyObject.SetValue%2A> bir bağımlılık özelliğinin değerini ayarlayan çağrı: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Bu sanal yöntemler veya geri çağırmaları her biri çeşitlikleri genişletme belirli bir amaca hizmet eder [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sistemi ve bağımlılık özellikleri. Özellik değeri belirlemeyi özelleştirmek için bu sanalları kullanma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri aramaları ve doğrulama](dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>FXCop Kural zorlama vs. Özellik sistemi Uygula  
 Yapı işleminizin bir parçası olarak Microsoft FXCop aracı kullanıyorsanız ve bu belirli ya da türetilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework sınıflarını temel oluşturucu, arama veya kendi bağımlılık özellikleri türetilen sınıflarda uygulamak, belirli bir karşılaşabileceğiniz FXCop kuralı ihlali. Bu ihlalin adı dize şöyledir:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Bu varsayılan genel kural kümesi için FXCop parçası olan bir kuraldır. Bu kural bir izleme sonunda bir bağımlılık özelliği sistem sanal yöntemini çağırır bağımlılık özelliği sistem aracılığıyla raporlama nedir olması. Bu kuralı ihlal devre dışı bırakın veya bu kuralda, FXCop Kural kümesi yapılandırması bastırmak ihtiyacınız olabilecek şekilde bu konu başlığında, belgelenen önerilen oluşturucu desenler izledikten sonra bile görüntülenmeye devam edebilir.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Varolan sınıfları kullanarak değil, türetilmiş sınıflardan çoğu sorunu gelir  
 Bu kural tarafından bildirilen sorunları, kendi yapı dizisi sanal yöntemleri uygulayan bir sınıf ardından türetilir oluşur. Sınıfınızı veya aksi halde biliyorsanız veya sınıfınıza nesnesinden türetilmesi değil, zorunlu, burada açıklanan önemli noktalar ve FXCop Kural motive sorunları için geçerli değildir. Ancak, bunlar örneği için temel sınıf olarak kullanılacak yöneliktir şekilde sınıfları yazıyorsanız şablonları oluşturmakta olduğunuz ya da genişletilebilir denetim kitaplığı ayarlayın, Oluşturucular için burada önerilen desenleri izlemelidir.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Varsayılan Oluşturucu tüm değerleri geri çağırmalar tarafından istenen başlatmalıdır  
 Bu değerlerden bazıları "gerçek" değerlerle doldurulur olsa bile, sınıf varsayılan oluşturucusuna sınıf geçersiz kılmalarını veya geri çağırmaları (geri aramalar özellik sistem sanalları bölümündeki listeden) tarafından kullanılan tüm örnek üyeleri başlatılmalıdır Varsayılan olmayan oluşturucular parametreleri.  
  
 Aşağıdaki örnek kodu (ve sonraki örneklerde) pseudo - olanC# bu kuralı ihlal ediyor ve sorunu anlatan örnek:  
  
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
  
 Uygulama kodu çağırdığında `new MyClass(objectvalue)`, bu çağrı varsayılan oluşturucuyu ve temel sınıf oluşturucu. Bu ayarlar sonra `Property1 = object1`, sanal yöntemini çağırır `OnPropertyChanged` sahip olan üzerinde `MyClass` <xref:System.Windows.DependencyObject>.  Geçersiz kılma başvurduğu `_myList`, hangi başlatılmamış henüz.  
  
 Bu sorunlardan kaçınmak için bir yolu geri çağırmaları yalnızca diğer bağımlılık özellikleri kullanmak ve böyle her bir bağımlılık özelliği meta verilerini kayıtlı bir parçası olarak oluşturulmuş varsayılan bir değere sahip olduğundan emin olmaktır.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Güvenli Oluşturucu desenleri  
 Sınıfınızın bir temel sınıf olarak kullanılırsa, tamamlanmamış başlatma risklerini önlemek için bu desenleri izleyin:  
  
#### <a name="default-constructors-calling-base-initialization"></a>Varsayılan oluşturucular temel başlatma çağırma  
 Temel varsayılan çağıran bu oluşturucular uygulayın:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Varsayılan olmayan (kullanışlı) oluşturucuları, hiçbir temel imza ile eşleşmiyor  
 Bu oluşturucular ayarlamak için parametreleri kullanıyorsanız başlatma işlemindeki bağımlılık özellikleri için başlatma kendi sınıfın varsayılan oluşturucusunu çağırın ve ardından bağımlılık özellikleri ayarlamak için parametreleri kullanın. Bunlar ya da bağımlılık özellikleri, sınıf tarafından tanımlanan veya temel sınıftan devralınan bağımlılık özellikleri ancak her iki durumda da şu biçimi kullanın:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Temel imzaları eşleşen varsayılan (kullanışlı) olmayan oluşturucular  
 Aynı Parametreleştirme ile temel oluşturucuyu çağırmak yerine, kendi sınıf varsayılan oluşturucusuna yeniden çağırın. Temel Başlatıcı çağırmaz; Bunun yerine çağırmalısınız `this()`. Ardından özgün Oluşturucusu davranışı, ilgili özellikleri ayarlamak için değerleri olarak geçirilen parametreleri kullanarak yeniden oluşturun. Belirli parametreleri olan özellikleri belirlemede rehberlik için özgün temel oluşturucu belgeleri ayarlamak için hedeflenen kullanın:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Tüm imzaları eşleşmelidir  
 Temel tür çoklu imzalara sahip olduğu durumlarda, tüm olası sonraki özellikleri ayarlamadan önce sınıfın varsayılan oluşturucusunu çağırma önerilen desen kullanan bir oluşturucu uygulaması kendi imzalar kasıtlı olarak eşleşmesi gerekir.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>SetValue bağımlılık özellikleri ayarlama  
 Özellik ayarı kolaylık sağlamak için bir sarmalayıcı üretilmesini, ve değerleri ile ayarlanır bir özelliği ayarlıyorsanız bu aynı desenleri uygulamak <xref:System.Windows.DependencyObject.SetValue%2A>. Aramalarınız <xref:System.Windows.DependencyObject.SetValue%2A> Oluşturucu parametresi bu geçiş başlatma için de sınıfının varsayılan oluşturucusunu çağırmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Bağımlılık Özelliği Güvenliği](dependency-property-security.md)

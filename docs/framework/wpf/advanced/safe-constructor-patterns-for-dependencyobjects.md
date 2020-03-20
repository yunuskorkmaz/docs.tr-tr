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
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>DependencyObjects için Güvenli Oluşturucu Desenleri
Genellikle, sınıf oluşturucular sanal yöntemler veya temsilciler gibi geri aramaları çağırmamalıdır, çünkü oluşturucular türemiş bir sınıf için oluşturucuların temel başlatması olarak adlandırılabilir. Sanal girilse, belirli bir nesnenin eksik bir başlatma durumunda yapılabilir. Ancak, özellik sisteminin kendisi, bağımlılık özelliği sisteminin bir parçası olarak çağrıları çağırır ve dahili olarak ortaya çıkarır. Bir bağımlılık özelliği değerini arama yla <xref:System.Windows.DependencyObject.SetValue%2A> ayarlamak kadar basit bir işlem, olası bir şekilde belirlemede bir yerde bir geri arama içerir. Bu nedenle, bir oluşturucu gövdesi içinde bağımlılık özelliği değerlerini ayarlarken dikkatli olmalısınız, bu da türünüz taban sınıf olarak kullanıldığında sorun yaratabilir. Bağımlılık özelliği durumları ve <xref:System.Windows.DependencyObject> burada belgelenmiş olan doğal geri aramalarla ilgili belirli sorunları önleyen yapıcıları uygulamak için özel bir model vardır.  

<a name="Property_System_Virtual_Methods"></a>
## <a name="property-system-virtual-methods"></a>Emlak Sistemi Sanal Yöntemler  
 Aşağıdaki sanal yöntemler veya geri aramalar, bağımlılık özelliği değerini <xref:System.Windows.DependencyObject.SetValue%2A> belirleyen çağrının hesaplamaları <xref:System.Windows.ValidateValueCallback>sırasında <xref:System.Windows.PropertyChangedCallback> <xref:System.Windows.CoerceValueCallback>potansiyel <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>olarak çağrılır: , , . Bu sanal yöntemlerin veya geri aramaların her biri, özellik sisteminin ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bağımlılık özelliklerinin çok yönlülüğünü genişletmek için belirli bir amaca hizmet eder. Özellik değeri belirlemeyi özelleştirmek için bu sanalların nasıl kullanılacağı hakkında daha fazla bilgi için Bkz. [Bağımlılık Özelliği Geri Aramaları ve Doğrulama.](dependency-property-callbacks-and-validation.md)  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>FXCop Kural Uygulama vs Emlak Sistemi Sanallar  
 Microsoft aracı FXCop'u yapı işleminizin bir parçası olarak kullanırsanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve temel oluşturucuyu çağıran belirli çerçeve sınıflarından türetilirseniz veya türetilmiş sınıflarda kendi bağımlılık özelliklerinizi uygularsanız, belirli bir FXCop kural ihlaliyle karşılaşabilirsiniz. Bu ihlalin ad dizesi:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Bu, FXCop için belirlenen varsayılan genel kuralın bir parçası olan bir kuraldır. Bu kuralın bildirdiği şey, sonunda bağımlılık özelliği sistemi sanal yöntemi çağıran bağımlılık özelliği sistemi üzerinden bir izlemedir. Bu kural ihlali, bu konuda belgelenen önerilen yapıcı desenleri takip ettikten sonra bile görünmeye devam edebilir, bu nedenle FXCop kural kümesi yapılandırmanızda bu kuralı devre dışı bırakamanız veya bastırmanız gerekebilir.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Sorunların çoğu Varolan Sınıfları Kullanmadan Gelen Sınıflar  
 Bu kural tarafından bildirilen sorunlar, yapı dizisinde sanal yöntemlerle uyguladığınız bir sınıf türetildiğinde oluşur. Sınıfınızı mühürlerseniz veya sınıfınızdan türetilmeyeceğini bilir veya uygularsanız, burada açıklanan hususlar ve FXCop kuralını motive eden konular sizin için geçerli değildir. Ancak, sınıfları temel sınıflar olarak kullanılmak üzere tasarlanacak şekilde yazarsanız, örneğin şablonlar veya genişletilebilir denetim kitaplığı kümesi oluşturuyorsanız, burada oluşturucular için önerilen desenleri izlemeniz gerekir.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Varsayılan Oluşturucular Geri Aramalar Tarafından İstenen Tüm Değerleri Başlatmalı  
 Sınıfınız tarafından kullanılan tüm örnek üyeler geçersiz kılar veya geri aramaları (Özellik Sistemi Sanalları bölümündeki listeden geri çağırmalar) sınıfınızda parametresiz oluşturucunuzda başharfe alınmalıdır, bu değerlerden bazıları "gerçek" değerler aracılığıyla doldurulsa bile parametresiz yapıcıların parametreleri.  
  
 Aşağıdaki örnek kod (ve sonraki örnekler) bu kuralı ihlal eden ve sorunu açıklayan bir sözde C# örneğidir:  
  
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
  
 Uygulama kodu `new MyClass(objectvalue)`aradığında, bu parametresiz yapıcı ve taban sınıf oluşturucuları çağırır. Sonra ayarlar `Property1 = object1`, hangi sahip `OnPropertyChanged` sanal `MyClass` <xref:System.Windows.DependencyObject>yöntem çağırır .  Geçersiz `_myList`kılma, henüz başharfe edilmemiş olan anlamına gelir.  
  
 Bu sorunları önlemenin bir yolu, geri aramaların yalnızca diğer bağımlılık özelliklerini kullandığından ve bu tür bağımlılık özelliğinin kayıtlı meta verilerinin bir parçası olarak belirlenmiş bir varsayılan değere sahip olduğundan emin olmaktır.  
  
<a name="Safe_Constructor_Patterns"></a>
## <a name="safe-constructor-patterns"></a>Güvenli Yapıcı Desenler  
 Sınıfınız taban sınıf olarak kullanılıyorsa eksik başlatma risklerini önlemek için aşağıdaki desenleri izleyin:  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a>Parametresiz oluşturucular baz başlatma çağrı  
 Temel varsayılan olarak adlandıran bu oluşturucuları uygulayın:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Varsayılan olmayan (kolaylık) oluşturucular, herhangi bir temel imza yla eşleşmez  
 Bu oluşturucular, başlatmada bağımlılık özelliklerini ayarlamak için parametreleri kullanıyorsa, önce başlatma için kendi sınıf parametresiz oluşturucunuzu arayın ve ardından bağımlılık özelliklerini ayarlamak için parametreleri kullanın. Bunlar, sınıfınız tarafından tanımlanan bağımlılık özellikleri veya temel sınıflardan devralınan bağımlılık özellikleri olabilir, ancak her iki durumda da aşağıdaki deseni kullanın:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Temel imzalarla eşleşen varsayılan olmayan (kolaylık) oluşturucular  
 Temel oluşturucuyu aynı parametrelendirmeye sahip çağırmak yerine, yine kendi sınıfınızın parametresiz oluşturucusu olarak adlandırın. Üs initializer'ı aramayın; bunun yerine `this()`aramalısınız. Ardından, ilgili özellikleri ayarlamak için geçirilen parametreleri değerler olarak kullanarak özgün oluşturucu davranışı yeniden üretin. Belirli parametrelerin ayarlamak üzere tasarlandığı özellikleri belirlerken kılavuz için özgün temel oluşturucu belgelerini kullanın:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Tüm imzalarla eşleşmeli  
 Temel türün birden çok imzası olduğu durumlarda, daha fazla ayarlamadan önce sınıf parametresiz oluşturucuyu çağırma nın önerilen deseni kullanan kendi oluşturucunuzla tüm olası imzaları kasıtlı olarak eşleştirmeniz gerekir Özellikler.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>SetValue ile bağımlılık özelliklerini ayarlama  
 Bu aynı desenler, özellik ayarı kolaylığı için sarıcı olmayan bir özelliği ayarlıyorsanız ve değerleri <xref:System.Windows.DependencyObject.SetValue%2A>. Bu geçiş <xref:System.Windows.DependencyObject.SetValue%2A> için çağrılarınızı oluşturucu parametreleri ile de başlatma için sınıfın parametresiz oluşturucu çağırmalısınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Bağımlılık Özelliği Güvenliği](dependency-property-security.md)

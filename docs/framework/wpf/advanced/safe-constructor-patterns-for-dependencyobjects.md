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
ms.openlocfilehash: 43a38406a3c9cc171944448fce2fa2f70c483baa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>DependencyObjects için Güvenli Oluşturucu Desenleri
Genellikle, sınıf oluşturucular oluşturucular türetilmiş bir sınıf için temel oluşturucular başlatma çağrılabilir olduğundan sanal yöntemler veya temsilciler gibi geri çağırmaları çağırmalıdır değil. Sanal girme verilen herhangi bir nesnenin bir tamamlanmamış başlatma durumu yapılabilir. Ancak, özellik sistemi çağırır ve geri çağırmaları dahili olarak, bağımlılık özelliği sisteminin bir parçası kullanıma sunar. Bir bağımlılık özelliği değerle ayarlamakla kadar basit bir işlem <xref:System.Windows.DependencyObject.SetValue%2A> çağrısı potansiyel olarak içeren bir geri çağırma yere belirleme. Bu nedenle, bağımlılık türünüz temel sınıf olarak kullanılıyorsa, sorunlu olabilecek bir oluşturucu gövdesi içinde özellik değerlerini ayarlarken dikkatli olmanız gerekir. Uygulama için belirli bir desene yoktur <xref:System.Windows.DependencyObject> oluşturucular ve burada belgelenen bağımlılık özelliği durumlar ve devralınmış geri çağırmalar ile belirli sorunları önler.  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Özellik sistem sanal yöntemleri  
 Aşağıdaki sanal yöntemler veya geri aramalar hesaplamaları sırasında adı verilir <xref:System.Windows.DependencyObject.SetValue%2A> bir bağımlılık özelliği değerini ayarlayan çağrısı: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Bu sanal yöntemler veya geri aramalar her biri, çok yönlülük genişletme belirli bir amaca hizmet eder [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sistemi ve bağımlılık özellikleri. Bu sanalların özellik değeri belirlemeyi özelleştirmek için nasıl kullanılacağı hakkında daha fazla bilgi için bkz: [bağımlılık özelliği geri çağrıları ve doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>FXCop Kural zorlama vs. Özellik sistem sanalları  
 Yapı işleminizin bir parçası olarak Microsoft aracı FXCop kullanırsanız ve belirli ya da türetilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel oluşturucuyu çağıran framework sınıfları veya türetilmiş sınıflar üzerinde kendi bağımlılık özellikleri uygulamak, belirli bir karşılaşabilirsiniz FXCop kuralı ihlali. Bu ihlali adı dizesi değil:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Bu varsayılan genel kural kümesi için FXCop parçası olan kuralıdır. Ne bu kural izleme sonunda bir bağımlılık özelliği sistem sanal yöntemini çağıran bağımlılık özellik sistemi aracılığıyla raporlama olması. Bu kural ihlali bile devre dışı bırakın veya bu kuralda FXCop Kural kümesi yapılandırmanızı bastır gerekebilir için bu konudaki belgelenen önerilen oluşturucu desenler izledikten sonra görüntülenmeye devam edebilir.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Çoğu sorunu varolan sınıfları kullanarak değil türetilmiş sınıflardan gelir  
 Bu kural tarafından bildirilen sorunlar, kendi oluşturma dizisinde sanal yöntemlerle uygulayan bir sınıf sonra türetilir oluşur. Sınıfınızı veya aksi halde biliyorsanız veya sınıfınız alanından elde edilir değil, zorunlu, burada açıklanan önemli noktalar ve FXCop kuralının motive sorunlarını sizin için geçerli değil. Ancak, bunlar temel sınıflar olarak örneği için kullanılmak üzere tasarlanmıştır şekilde sınıfları yazıyorsanız şablonları oluşturma veya Genişletilebilir denetim kitaplığı ayarlarsanız oluşturucular için burada önerilen desenleri uygulamalısınız.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Varsayılan oluşturucu geri çağırmalar tarafından istenen tüm değerleri başlatmalıdır  
 Bu değerlerden bazıları "gerçek" değerlerle doldurulur olsa bile, sınıfın varsayılan oluşturucusunu sınıfı geçersiz kılmalar veya geri aramalar (listeden geri çağırmalar özellik sistem sanalları bölümünde) tarafından kullanılan hiçbir örnek üyesinin başlatılması gerekir Varsayılan olmayan oluşturucular parametreleri.  
  
 Aşağıdaki örnek kod (ve sonraki örnekleri bir sözde değilse)-bu kural ihlal ediyor ve sorun anlatan C# Örnek:  
  
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
  
 Uygulama kodu çağırdığında `new MyClass(objectvalue)`, bu varsayılan oluşturucuyu ve temel çağırır sınıf oluşturucu. Bu ayarlar daha sonra `Property1 = object1`, sanal bir yöntem çağırır `OnPropertyChanged` sorumlu üzerinde `MyClass` <xref:System.Windows.DependencyObject>.  Geçersiz kılma başvurduğu `_myList`, hangi başlatılmadı henüz.  
  
 Bu sorunları önlemek için bir geri aramalar yalnızca diğer bağımlılık özelliklerini kullanın ve her tür bağımlılık özelliği kayıtlı meta verilerini bir parçası olarak oluşturulmuş varsayılan bir değere sahip olduğundan emin olmak için yoludur.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Güvenli oluşturucu desenler  
 Sınıfınız temel sınıf olarak kullanılıyorsa, tamamlanmamış başlatma risklerini önlemek için bu desenleri izleyin:  
  
#### <a name="default-constructors-calling-base-initialization"></a>Temel başlatma çağıran varsayılan oluşturucular  
 Temel varsayılan çağıran bu oluşturucuları uygulayın:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Temel bir imza ile eşleşmeyen varsayılan olmayan (kullanışlı) oluşturucular  
 Bu oluşturucular başlatma içinde bağımlılık özelliklerini ayarlamak için parametreleri kullanırsanız, ilk başlatma için kendi sınıfın varsayılan oluşturucusunu çağırın ve bağımlılık özelliklerini ayarlamak için parametrelerini kullanın. Bunlar ya da bağımlılık özellikleri sınıfı tarafından tanımlanan veya bağımlılık özellikler taban sınıflardan devralınır, ancak her iki durumda da şu biçimi kullanın:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Temel imzalarla eşleşmeyen varsayılan olmayan (kullanışlı) oluşturucular  
 Aynı parametrelemeyi ile temel oluşturucuyu çağırmak yerine, kendi sınıfı varsayılan oluşturucu yeniden çağırın. Temel başlatıcıyı çağırmayın; Bunun yerine çağırmalıdır `this()`. Sonra özgün Oluşturucu davranışını ilgili özellikleri ayarlamak için değerler olarak geçirilen parametreleri kullanarak yeniden oluşturun. Belirli parametreleri olan özellikleri belirlemede rehberlik için özgün temel oluşturucu belgeleri ayarlamak için hedeflenen kullanın:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Tüm imzalar eşleşmelidir  
 Temel türü birden fazla imzaya sahip olduğu durumlarda, sonraki özellikleri ayarlamadan önce sınıfı varsayılan oluşturucu çağırarak önerilen desenini kullanan bir oluşturucu uygulaması kendi tüm olası imzalar kasıtlı olarak eşleşmelidir.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>SetValue ile bağımlılık özelliklerini ayarlama  
 Özellik ayarlama kolaylığı için sarmalayıcı sahip, ve değerlerini içeren bir özelliği ayarlıyorsanız aynı desenler uygulanır <xref:System.Windows.DependencyObject.SetValue%2A>. Aramalarınız <xref:System.Windows.DependencyObject.SetValue%2A> Oluşturucu parametreleri bu geçiş başlatma için sınıf varsayılan oluşturucusunu da çağırmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Bağımlılık özelliği güvenlik](../../../../docs/framework/wpf/advanced/dependency-property-security.md)

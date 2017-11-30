---
title: "Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Constructor
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime [Visual Basic], objects
- Sub New constructor, object lifetime
- Finalize method [Visual Basic], object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method [Visual Basic], object lifetime
- Class_Initialize
- object creation [Visual Basic], object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection [Visual Basic], Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f985d6bf7b26ec22d6e533eae1f1d7ea0682e56c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme (Visual Basic)
Bir nesne bir sınıfının bir örneği kullanılarak oluşturulan `New` anahtar sözcüğü. Bunlar kullanılmadan önce başlatma görevlerini genellikle yeni nesneler üzerinde gerçekleştirilmesi gerekir. Veritabanlarına bağlanma ve kayıt defteri anahtarlarının değerlerini okuma dosyaları açma ortak başlatma görevlerini içerir. Visual Basic denetimleri adlı yordamları kullanarak yeni nesnelerin başlatılması *oluşturucular* (başlatma denetime izin veren özel yöntemleri).  
  
 Bir nesne kapsam dışına çıktığında sonra ortak dil çalışma zamanı tarafından (CLR) serbest bırakılır. Visual Basic denetimleri yayın adı verilen yordamları kullanarak sistem kaynaklarını *Yıkıcılar*. Birlikte oluşturucular ve Yıkıcılar sağlam ve tahmin edilebilir sınıf kitaplıkları oluşturulmasını destekler.  
  
## <a name="using-constructors-and-destructors"></a>Oluşturucular ve yıkıcıları kullanma  
 Oluşturucular ve Yıkıcılar oluşturma ve yok etme nesnelerin denetler. `Sub New` Ve `Sub Finalize` Visual Basic'de yordamlar başlatmak ve nesneleri yok; bunlar Değiştir `Class_Initialize` ve `Class_Terminate` kullanılan yöntemleri [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 6.0 ve önceki sürümleri.  
  
### <a name="sub-new"></a>Yeni alt  
 `Sub New` Oluşturucusu yalnızca bir sınıf oluşturulduğunda bir kez çalıştırabilirsiniz. Dışında açıkça herhangi bir yere çağrılamaz başka bir oluşturucusu aynı sınıfın veya türetilmiş bir sınıf kodunu ilk satırda. Ayrıca, kodda `Sub New` yöntemi bir sınıftaki başka bir kod önce her zaman çalışır. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]ve sonraki sürümler örtük olarak oluşturma bir `Sub New` Oluşturucusu değil açıkça tanımlarsanız çalışma zamanında bir `Sub New` yordamı için bir sınıf.  
  
 Bir sınıf için bir oluşturucu oluşturmak için adlandırılmış bir yordam oluşturma `Sub New` sınıf tanımı başka bir yerindeki. Parametreli bir oluşturucu oluşturmak için bağımsız değişken adları ve veri türlerini belirtin `Sub New` gibi aşağıdaki kodu olduğu gibi diğer tüm yordam bağımsız değişkenleri belirtmeniz gerekir:  
  
 [!code-vb[VbVbalrOOP#42](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_1.vb)]  
  
 Oluşturucular sık, olduğu gibi aşağıdaki kodu aşırı:  
  
 [!code-vb[VbVbalrOOP#116](../../../../visual-basic/misc/codesnippet/VisualBasic/object-lifetime-how-objects-are-created-and-destroyed_2.vb)]  
  
 Başka bir sınıfından türetilmiş bir sınıf tanımladığınızda, temel sınıf parametre almayan bir erişilebilir yapıcı olmadıkça bir oluşturucu ilk satırını temel sınıf için bir çağrı olmalıdır. Örneğin, yukarıdaki Oluşturucusu içeren temel sınıf için bir çağrı olabilir `MyBase.New(s)`. Aksi takdirde, `MyBase.New` isteğe bağlıdır ve [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] çalışma zamanı çağırır, örtük olarak.  
  
 Üst nesnenin oluşturucuyu çağırmak için kodu yazdıktan sonra herhangi bir ek başlatma kod ekleyebilirsiniz `Sub New` yordamı. `Sub New`Parametreli Oluşturucusu çağrıldığında bağımsız değişkenleri kabul edebilir. Bu gibi bir durumda oluşturucuyu çağıran yordamdan geçilen Bu parametreler `Dim AnObject As New ThisClass(X)`.  
  
### <a name="sub-finalize"></a>Sub Finalize  
 Nesneleri serbest bırakmadan önce CLR otomatik olarak çağırır `Finalize` yöntemi tanımlayan nesneleri için bir `Sub Finalize` yordamı. `Finalize` Yöntemi yalnızca bir nesne, dosyaları kapatma ve durum bilgilerini kaydetmek için kod gibi kaldırıldığı önce yürütmek için gereken kodu içerebilir. Bulunmaktadır yürütmek küçük bir performans `Sub Finalize`, tanımlamanız gerekir böylece bir `Sub Finalize` nesneleri açıkça serbest gerektiğinde yöntemi.  
  
> [!NOTE]
>  Çöp toplayıcı CLR'de elden desteklemez ve olamaz *yönetilmeyen nesneleri*, işletim sistemini doğrudan CLR ortamı dışında yürütür nesneleri. Bu durum, farklı yönetilmeyen nesneleri, farklı şekillerde çıkarılması gerekir çünkü. Bu bilgileri yönetilmeyen nesne ile doğrudan ilişkili değildir; Nesne belgelerindeki bulunması gerekir. Yönetilmeyen nesneleri kullanan bir sınıfı bunları elden gerekir, `Finalize` yöntemi.  
  
 `Finalize` Yıkıcı yalnızca ait sınıfından veya türetilmiş sınıflarından çağrılabilen bir yöntemdir korumalı. Sistem çağrıları `Finalize` otomatik olarak ne zaman bir nesne yok, açıkça arama şekilde `Finalize` öğesinden türetilmiş sınıf dışında `Finalize` uygulaması.  
  
 Farklı `Class_Terminate`, bir nesne için hiçbir şey ayarlanmış hemen yürütür, genellikle bir nesne kapsam zaman kaybeder ve Visual Basic çağırdığında arasında bir gecikme olur `Finalize` yıkıcı. [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]ve sonraki sürümler yıkıcı, ikinci bir tür için izin <xref:System.IDisposable.Dispose%2A>, hangi açıkça çağrılabilir hemen kaynakları serbest bırakmak için herhangi bir zamanda.  
  
> [!NOTE]
>  A `Finalize` yıkıcı değil throw özel durumlar, çünkü bunlar uygulama tarafından işlenemez ve sonlandırmak uygulamanın neden olabilir.  
  
### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Yeni ve sınıf hiyerarşisi yöntemleri iş Sonlandır  
 Her bir sınıfının örneği oluşturulduğunda, ortak dil çalışma zamanı (CLR) adlı bir yordam yürütmeyi denediğinde `New`, söz konusu nesne varsa. `New`çağrılan yordam türünde bir `constructor` nesnede başka bir kod yürütülmeden önce yeni nesneler başlatmak için kullanılır. A `New` oluşturucusu, açık dosyalar, veritabanlarına bağlanmak, değişkenlerini başlatmak ve ilgilenebilmek nesnenin kullanılabilmesi için önce yerine getirilmesi gereken diğer görevler için kullanılabilir.  
  
 Türetilmiş bir sınıf örneği oluşturulduğunda, `Sub New` temel sınıfın Oluşturucusu yürütülmeden önce türetilmiş sınıflarda oluşturucular ve ardından. Çünkü böyle kod ilk satırı bir `Sub New` Oluşturucusu sözdizimini kullanan `MyBase.New()`sınıf hiyerarşisinde hemen kendisi üzerinde sınıf çağırmak için. `Sub New` Oluşturucusu sonra çağrılır sınıf hiyerarşisindeki her sınıf için kadar oluşturucusu için temel sınıf ulaştı. Bu noktada, temel sınıf yürütür için tüm türetilen sınıflar her oluşturucuda kodda Oluşturucusu kodda arkasından ve en çok türetilen sınıflar kodda son yürütülür.  
  
 ![Oluşturucular ve devralma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance.gif "vaConstructorsInheritance")  
  
 Bir nesne artık gerekli olmadığında CLR çağırır <xref:System.Object.Finalize%2A> kendi bellek boşaltma önce bu nesne için yöntem. <xref:System.Object.Finalize%2A> Yöntemi çağrıldığında bir `destructor` durum bilgilerini kaydetme gibi temizleme görevleri gerçekleştirdiğinden dosyaları ve veritabanları ve nesneyi serbest bırakmadan önce gerçekleştirilmesi gereken diğer görevlere bağlantılar kapatma.  
  
 ![Oluşturucular Inheritance2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/media/vaconstructorsinheritance_2.gif "vaConstructorsInheritance_2")  
  
## <a name="idisposable-interface"></a>IDisposable arabirimi  
 Sınıf örnekleri genellikle Windows tanıtıcıları ve veritabanı bağlantıları gibi CLR tarafından yönetilmeyen kaynakları denetler. Bu kaynaklar olarak da elden gerekir `Finalize` sınıfının yöntemi böylece nesne atık toplayıcısı tarafından bozulduğunda bunlar yayınlanacaktır. Ancak, yalnızca CLR daha fazla boş bellek gerektirdiğinde atık toplayıcı nesneleri yok eder. Bu nesne kapsam dışında devam ettiği sürece sonra kaynakları kadar yayımlanmayabilir olduğunu anlamına gelir.  
  
 Çöp toplama desteklemek üzere sınıflarınızı uyguladıkları sistem kaynaklarının etkin bir şekilde yönetmek için bir mekanizma sağlayabilir <xref:System.IDisposable> arabirimi. <xref:System.IDisposable>bir yöntem, sahip <xref:System.IDisposable.Dispose%2A>, nesneyi kullanmayı bitirdiğinizde hangi istemcilerin çağrı. Kullanabileceğiniz <xref:System.IDisposable.Dispose%2A> hemen kaynakları serbest bırakmak ve dosyaları kapatma gibi görevleri gerçekleştirmek ve bağlantıları veritabanı yöntemi. Farklı `Finalize` yıkıcı <xref:System.IDisposable.Dispose%2A> yöntemi otomatik olarak çağrılmaz. İstemciler bir sınıfın açıkça çağırmalıdır <xref:System.IDisposable.Dispose%2A> hemen kaynakları serbest bırakmak istediğinizde.  
  
### <a name="implementing-idisposable"></a>IDisposable uygulayan  
 Uygulayan bir sınıf <xref:System.IDisposable> arabirimi, bu kodun bölümlerini içermelidir:  
  
-   Nesne atıldı olup olmadığını izlemek için bir alan:  
  
    ```  
    Protected disposed As Boolean = False  
    ```  
  
-   Bir aşırı yüklemesini <xref:System.IDisposable.Dispose%2A> sınıfının kaynakları serbest bırakır. Bu yöntem çağrılmalıdır <xref:System.IDisposable.Dispose%2A> ve `Finalize` taban sınıf yöntemlerini:  
  
    ```  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposed Then  
            If disposing Then  
                ' Insert code to free managed resources.  
            End If  
            ' Insert code to free unmanaged resources.  
        End If  
        Me.disposed = True  
    End Sub  
    ```  
  
-   Uygulaması <xref:System.IDisposable.Dispose%2A> , yalnızca aşağıdaki kod içerir:  
  
    ```  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
    ```  
  
-   Geçersiz kılma `Finalize` yalnızca aşağıdaki kodu içeren yöntemi:  
  
    ```  
    Protected Overrides Sub Finalize()  
        Dispose(False)  
        MyBase.Finalize()  
    End Sub  
    ```  
  
### <a name="deriving-from-a-class-that-implements-idisposable"></a>IDisposable uygulayan bir sınıftan türetme  
 Arabirimini uygulayan bir taban sınıftan türeyen bir sınıf <xref:System.IDisposable> çıkarılması gereken ek kaynakları kullanmadıkça temel yöntemlerden herhangi birini geçersiz kılmak arabirimi gerekmez. Bu durumda, temel sınıfın türetilmiş sınıf kılmalıdır `Dispose(disposing)` türetilen sınıfın kaynaklarını silmek için yöntem. Bu temel sınıfın çağırmalıdır `Dispose(disposing)` yöntemi.  
  
```  
Protected Overrides Sub Dispose(ByVal disposing As Boolean)  
    If Not Me.disposed Then  
        If disposing Then  
            ' Insert code to free managed resources.  
        End If  
        ' Insert code to free unmanaged resources.  
    End If  
    MyBase.Dispose(disposing)  
End Sub  
```  
  
 Türetilmiş bir sınıf, temel sınıfın kılmalıdır değil <xref:System.IDisposable.Dispose%2A> ve `Finalize` yöntemleri. Türetilmiş sınıf bir örnekten bu yöntem çağrıldığında bu yöntemlerden birini temel sınıfın uygulamayı çağırması türetilen sınıfın geçersiz kılma `Dispose(disposing)` yöntemi.  
  
## <a name="garbage-collection-and-the-finalize-destructor"></a>Çöp toplama ve yıkıcı Sonlandır  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Kullanan *başvuru izleme çöp toplama* düzenli aralıklarla kullanılmayan kaynakları serbest bırakmak için sistem. Visual Basic 6.0 ve önceki sürümlerinde kullanılan olarak adlandırılan farklı bir sistem *başvuru sayımı* kaynakları yönetmek için. Her iki sistemle otomatik olarak aynı işlevi gerçekleştirir olmasa da, bazı önemli farklar vardır.  
  
 Sistem bu tür nesneler artık gerekli olduğunu belirlediğinde CLR düzenli aralıklarla nesneleri yok eder. Sistem kaynakları kısa tedarik ve daha az sıklıkta Aksi durumda olduğunda nesneleri daha hızlı bir şekilde yayınlanır. Ne zaman bir nesne kapsam kaybeder ve ne zaman CLR bırakması arasındaki gecikme aksine, Visual Basic 6.0 ve önceki sürümlerinde, nesnelerle, tam olarak ne zaman nesne yok edilir belirleyemiyor, anlamına gelir. Böyle bir durumda nesneleri sahip söylenir *belirleyici ömrü*. Unutmamanız sürece çoğu durumda, belirleyici olmayan ömrü uygulamaları yazma biçimini değişmeyen `Finalize` yıkıcı değil hemen çalıştırılacak bir nesne kapsam kaybettiğinde.  
  
 Çöp toplama sistemleri arasında başka bir fark kullanmayı içerir `Nothing`. Atanan bazen Programcı Başvuru Visual Basic 6.0 ve önceki sürümlerinde sayım yararlanmak için `Nothing` değişkenlere başvurularını serbest bırakmak için değişkenleri nesnesine tutulan. Değişkeni son nesnesine başvuru sahipse, nesnenin kaynakları hemen serbest bırakıldı. Bu yordamı hala değerli olduğu durumlar olsa Visual Basic sonraki sürümlerde, gerçekleştirmek hiçbir zaman hemen kaynaklarını serbest bırakmak referans verilen nesnenin neden olur. Hemen kaynakları serbest bırakmak için nesnenin kullanın <xref:System.IDisposable.Dispose%2A> yöntemi, varsa. Yalnızca bir kez bir değişken ayarlamalıdır `Nothing` yaşam atık toplayıcı yalnız bırakılmış nesneleri algılamak için süresini için uzun göreli olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IDisposable.Dispose%2A>  
 [Başlatma ve sonlandırma bileşenleri](http://msdn.microsoft.com/library/58444076-a9d2-4c91-b3f6-0e180dc0695d)  
 [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Yönetilmeyen kaynakları temizleme](../../../../standard/garbage-collection/unmanaged.md)  
 [Hiçbir şey](../../../../visual-basic/language-reference/nothing.md)

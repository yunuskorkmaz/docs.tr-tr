---
title: 'Nesne Ömrü: Nesneler nasıl oluşturulur ve yok (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Constructor
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
ms.openlocfilehash: 430041f5f4315c5ad20cd2495f01a6f776f239c7
ms.sourcegitcommit: 56ac30a336668124cb7d95d8ace16bd985875147
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469699"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Nesne Ömrü: Nesneler nasıl oluşturulur ve yok (Visual Basic)
Bir sınıf, bir nesne örneği kullanılarak oluşturulan `New` anahtar sözcüğü. Bunlar kullanılmadan önce başlatma görevleri genellikle yeni nesneler üzerinde gerçekleştirilmelidir. Genel başlangıç görevleri, veritabanlarına bağlanma ve kayıt defteri anahtarlarının okumanızı dosyalarını açma içerir. Visual Basic denetimleri adı verilen yordamları kullanarak yeni nesnelerin başlatılmasını *oluşturucular* (başlatma denetime izin veren özel yöntemleri).  
  
 Bir nesne kapsam dışına çıktığında sonra ortak dil çalışma zamanı tarafından (CLR) serbest bırakılır. Visual Basic denetimleri yayın adı verilen yordamları kullanarak sistem kaynaklarının *yok ediciler*. Oluşturucular ve Yıkıcılar birlikte, güçlü ve öngörülebilir sınıf kitaplıkları oluşturulmasını destekler.  
  
## <a name="using-constructors-and-destructors"></a>Oluşturucular ve Yıkıcılar kullanma  
 Oluşturucular ve Yıkıcılar oluşturulmasını ve nesnelerin yok edilmesi denetler. `Sub New` Ve `Sub Finalize` Visual Basic'de yordamlar başlatmak ve nesneleri yok; bunlar değiştirir `Class_Initialize` ve `Class_Terminate` Visual Basic 6.0 ve önceki sürümlerinde kullanılan yöntemleri.  
  
### <a name="sub-new"></a>Yeni alt  
 `Sub New` Sonra yalnızca bir sınıf oluşturulduğunda Oluşturucu çalıştırabilirsiniz. Dışında herhangi bir yere açıkça çağrılamaz ilk satırında başka bir oluşturucunun aynı sınıftaki veya türetilmiş sınıftan kod. Ayrıca, kodda `Sub New` yöntemi bir sınıftaki herhangi bir kod önce her zaman çalışır. Visual Basic ve sonraki sürümleri, örtülü olarak oluşturma bir `Sub New` oluşturucusu olmayan açıkça tanımlarsanız çalışma zamanında bir `Sub New` yordamı için bir sınıf.  
  
 Bir sınıf için oluşturucu oluşturmak için adlandırılmış bir yordam oluşturma `Sub New` sınıf tanımında herhangi bir yerde. Parametreli bir kurucu oluşturmak için bağımsız değişken adları ve veri türlerini belirtin `Sub New` gibi aşağıdaki kodda gösterildiği gibi diğer her türlü yordam bağımsız değişkenleri belirtmeniz gerekir:  
  
 [!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]  
  
 Oluşturucular sık, aşağıdaki kodda gösterildiği gibi aşırı:  
  
 [!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]  
  
 Başka bir sınıftan türetilmiş bir sınıf tanımladığınızda, ilk satır bir oluşturucunun taban sınıf parametre almayan bir erişilebilir oluşturucuya sahip olmadığı sürece temel sınıf oluşturucusuna bir çağrı olması gerekir. Örneğin, yukarıdaki oluşturucu içeren temel sınıf için bir çağrı olabilir `MyBase.New(s)`. Aksi takdirde, `MyBase.New` isteğe bağlıdır ve Visual Basic çalışma zamanı örtük olarak çağırır.  
  
 Üst nesnenin oluşturucuyu çağırmak için kod yazma sonra herhangi bir ek başlatma kod ekleyebilirsiniz `Sub New` yordamı. `Sub New` parametreli bir kurucu çağrıldığında bağımsız değişken kabul edebilir. Bu parametre, örneğin, yapılandırıcının yordamdan geçirilen `Dim AnObject As New ThisClass(X)`.  
  
### <a name="sub-finalize"></a>Sub Finalize  
 CLR nesneleri serbest bırakmadan önce otomatik olarak çağıran `Finalize` yöntemi tanımlayan nesneler için bir `Sub Finalize` yordamı. `Finalize` Yöntemi yalnızca bir nesne, dosyaları kapatma ve durum bilgilerini kaydetmek için kod gibi edildiğinde önce yürütmek için gereken kodu içerebilir. Yürütme için küçük bir performans cezası yoktur `Sub Finalize`tanımlamanız gerekir böylece bir `Sub Finalize` nesneleri açıkça serbest gerektiğinde yöntemi.  
  
> [!NOTE]
>  Çöp toplayıcı, CLR elden desteklemez ve olamaz *yönetilmeyen nesneleri*, işletim sistemi CLR ortamın dışında doğrudan yürüten nesneleri. Bu durum, farklı yönetilmeyen nesneleri farklı şekilde elden gerekir çünkü. Bu bilgileri doğrudan yönetilmeyen nesneyle ilişkilendirilmemiş; nesne için belgelerinde bulunması gerekir. Yönetilmeyen nesneleri kullanan bir sınıf, dispose gerekir, `Finalize` yöntemi.  
  
 `Finalize` Yok Edicisi olan yalnızca ait sınıftaki veya türetilmiş sınıflar adlandırılan Korumalı bir yöntem. Sistem çağrıları `Finalize` otomatik olarak ne zaman bir nesnesi yok edildiğinde, böylece değil açıkça çağırmalıdır `Finalize` öğesinden türetilmiş bir sınıfın dışında `Finalize` uygulaması.  
  
 Farklı `Class_Terminate`, bir nesne için hiçbir şey ayarlanır hemen sonra yürütür, genellikle nesnenin kapsamı ne zaman kaybeder ve Visual Basic çağırdığında arasında bir gecikme olur `Finalize` yıkıcı. Visual Basic ve sonraki sürümler izin yok Edicisi, ikinci bir tür için <xref:System.IDisposable.Dispose%2A>, hangi açıkça çağrılabilir kaynakları hemen serbest bırakmak istediğiniz zaman.  
  
> [!NOTE]
>  A `Finalize` yok Edicisi, uygulama tarafından işlenemezler ve uygulamanın sonlandırılmasına neden olabilir çünkü özel durum, oluşturmamalıdır.  
  
### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Yeni ve bir sınıf hiyerarşisindeki yöntemleri iş Sonlandır  
 Bir sınıfın bir örneği oluşturulduğunda, ortak dil çalışma zamanı (CLR) adlı bir yordam yürütmeyi denediğinde `New`, o nesnenin varsa. `New` çağrılan yordam türünde bir `constructor` yeni nesneler bir nesne içindeki herhangi bir kod yürütülmeden önce başlatmak için kullanılır. A `New` oluşturucusu, dosyaları açma, veritabanlarına bağlanmak, değişkenlerini başlatmak ve ölçeklendirilmesini nesnenin kullanılabilmesi için önce yapmanız gereken diğer görevler için kullanılabilir.  
  
 Türetilmiş bir sınıfın bir örneği oluşturulduğunda `Sub New` temel sınıfın Oluşturucusu yürütülmeden önce türetilen sınıflardaki oluşturucular tarafından izlenen. Çünkü böyle ilk kod satırı bir `Sub New` Oluşturucusu sözdizimini kullanan `MyBase.New()`hemen kendisi üzerinde sınıfının oluşturucusu, sınıf hiyerarşisini, çağırmak için. `Sub New` Oluşturucusu sonra çağrılır sınıf hiyerarşisindeki her sınıf için oluşturucu kadar için temel sınıf ulaşıldı. Bu noktada, temel sınıf yürütür için Oluşturucudaki kod her Oluşturucu tüm türetilmiş sınıflarda kodda ardından ve en çok türetilen sınıfları kodda son yürütülür.  
  
 ![Sınıf hiyerarşisi oluşturucuları ve devralma gösteren ekran görüntüsü.](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)  
  
 CLR nesne artık gerekmediğinde çağırır <xref:System.Object.Finalize%2A> kendi bellek boşaltma önce bu nesne için yöntemi. <xref:System.Object.Finalize%2A> Yöntemi çağrıldığında bir `destructor` durumu bilgilerini kaydetme gibi temizleme görevlerini gerçekleştirdiğinden, dosyalar ve veritabanları ve nesneyi serbest bırakmadan önce gerçekleştirilmesi gereken diğer görevlere bağlantılar kapatma.  
  
 ![Finalize yöntemi yok Edicisi gösteren ekran görüntüsü.](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)  
  
## <a name="idisposable-interface"></a>IDisposable arabirimi  
 Sınıf örneği, genellikle Windows tanıtıcıları ve veritabanı bağlantıları gibi CLR tarafından yönetilmeyen kaynakları denetler. Bu kaynaklar, içinde çıkarılması gerekir `Finalize` sınıfının yöntemi böylece nesnenin çöp toplayıcısı tarafından kaldırıldığında bunlar kullanıma sunulacaktır. Ancak, CLR daha fazla bellek gerektiğinde çöp toplayıcısı nesneleri yok eder. Bu nesne kapsam dışına uzun süre geçtikten sonra kaynakları kadar serbest bırakılmayabilir olduğunu anlamına gelir.  
  
 Çöp toplama desteklemek için sınıflarınızı uyguladıkları sistem kaynaklarının etkin bir şekilde yönetmek için bir mekanizma sağlayabilir <xref:System.IDisposable> arabirimi. <xref:System.IDisposable> bir yöntemi, <xref:System.IDisposable.Dispose%2A>, bir nesneyi kullanmayı bitirdikten sonra hangi istemcilerin çağırmalıdır. Kullanabileceğiniz <xref:System.IDisposable.Dispose%2A> hemen kaynakları serbest bırakmak ve dosyaları kapatma gibi görevleri gerçekleştirmek ve veritabanı bağlantıları için yöntem. Farklı `Finalize` yıkıcı <xref:System.IDisposable.Dispose%2A> yöntemi otomatik olarak çağrılmaz. İstemciler bir sınıfın açıkça çağırmalıdır <xref:System.IDisposable.Dispose%2A> kaynakları hemen serbest istediğinizde.  
  
### <a name="implementing-idisposable"></a>IDisposable uygulayan  
 Uygulayan bir sınıf <xref:System.IDisposable> arabirimi, bu kod bölümlerini içermelidir:  
  
- Nesne atıldı olmadığını izlemek için bir alan:  
  
    ```  
    Protected disposed As Boolean = False  
    ```  
  
- Bir aşırı yüklemesini <xref:System.IDisposable.Dispose%2A> , sınıfın kaynaklarını serbest bırakır. Bu yöntem çağrılmalıdır <xref:System.IDisposable.Dispose%2A> ve `Finalize` temel sınıf yöntemleri:  
  
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
  
- Uygulanışı <xref:System.IDisposable.Dispose%2A> , yalnızca aşağıdaki kodu içerir:  
  
    ```  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
    ```  
  
- Geçersiz kılma `Finalize` yalnızca aşağıdaki kodu içeren yöntemi:  
  
    ```  
    Protected Overrides Sub Finalize()  
        Dispose(False)  
        MyBase.Finalize()  
    End Sub  
    ```  
  
### <a name="deriving-from-a-class-that-implements-idisposable"></a>IDisposable uygulayan bir sınıftan türetme  
 Uygulayan bir taban sınıftan türetilen bir sınıf <xref:System.IDisposable> çıkarılması gereken ek kaynakları kullanmadığı sürece herhangi bir taban yöntemleri geçersiz kılmak arabirimi gerekmez. Böyle bir durumda, temel sınıfın türetilmiş sınıf geçersiz kılmalıdır `Dispose(disposing)` türetilen sınıfın kaynaklarını silmek için yöntemi. Bu temel sınıfın çağırmalıdır `Dispose(disposing)` yöntemi.  
  
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
  
 Türetilmiş bir sınıf temel sınıfın kılmamak <xref:System.IDisposable.Dispose%2A> ve `Finalize` yöntemleri. Bu yöntemler temel sınıfın uygulaması türetilen sınıfın bir örneğinden bu yöntemler çağrıldığında, türetilmiş sınıfın geçersiz çağrı `Dispose(disposing)` yöntemi.  
  
## <a name="garbage-collection-and-the-finalize-destructor"></a>Çöp toplama ve Finalize yıkıcısı  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Kullanan *izleme başvurusu atık toplama* sistem düzenli aralıklarla kullanılmayan kaynaklar serbest bırakılacaksa. Visual Basic 6.0 ve önceki sürümlerinde kullanılan adlı farklı bir sistem *başvuru sayımı* kaynakları yönetmek için. Her iki sistem otomatik olarak aynı işlevi gerçekleştirir ancak bazı önemli farklar vardır.  
  
 Sistem belirlediğinde bu tür nesneler artık gerekmeyen CLR düzenli aralıklarla nesnelerini yok eder. Sistem kaynakları arz ve daha az sıklıkta Aksi durumda olduğunda nesneleri daha hızlı serbest bırakılır. Nesnenin kapsamı ne zaman kaybeder ve ne zaman CLR sürümleri arasındaki gecikmeyi aksine Visual Basic 6.0 ve önceki sürümlerinde, nesnelerle, tam olarak ne zaman nesne yok edileceği belirlenemiyor, anlamına gelir. Böyle bir durumda, nesneler olduğu söylenir ve *belirleyici ömrü*. Unutmamanız sürece çoğu durumda, belirleyici ömrü uygulamaları nasıl yazdığınız değiştirmez `Finalize` yıkıcı bir nesne kapsam kaybettiğinde hemen çalışmayabilir.  
  
 Çöp toplama sistemleri arasında başka bir fark kullanımını gerektirir `Nothing`. Atanan bazen programcılar başvuru Visual Basic 6.0 ve önceki sürümlerinde sayımı yararlanmak için `Nothing` değişkenleri başvuruları serbest bırakmak için bu değişkenleri nesnesinin tutulan. Son nesne başvuru değişkenini tutulan, nesnenin kaynaklarını hemen kullanıma sunulmuştur. Olsa da bu yordamı hala değerlidir olduğu durumlarda Visual Basic sonraki sürümlerinde, bunu gerçekleştirmek hiçbir zaman, kaynakları hemen serbest bırakmak başvurulan nesnenin neden olur. Kaynakları hemen serbest bırakmak için nesnenin kullanın <xref:System.IDisposable.Dispose%2A> varsa yöntemi. Yalnızca bir kez bir değişken ayarlamalıdır `Nothing` ömrü atık toplayıcı yalnız bırakılmış nesneleri algılama süresini için uzun göreli olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable.Dispose%2A>
- [Başlatma ve sonlandırma bileşenleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [New İşleci](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Yönetilmeyen Kaynakları Temizleme](../../../../standard/garbage-collection/unmanaged.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)

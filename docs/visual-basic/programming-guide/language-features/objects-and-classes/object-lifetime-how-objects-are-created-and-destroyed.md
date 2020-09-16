---
title: 'Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme'
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
ms.openlocfilehash: a32a5d075b5b1d02632c80216e7c2c12920bf4a2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544147"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme (Visual Basic)

Bir sınıf örneği, bir nesnesi, `New` anahtar sözcüğü kullanılarak oluşturulur. Başlatma görevleri genellikle yeni nesnelerde kullanılmadan önce gerçekleştirilmelidir. Ortak başlatma görevleri, dosyaları açmayı, veritabanlarına bağlanmayı ve kayıt defteri anahtarlarının değerlerini okumayı içerir. Visual Basic, *oluşturucular* (başlatma üzerinde denetime izin veren özel yöntemler) adlı yordamları kullanarak yeni nesnelerin başlatılmasını denetler.

Bir nesne kapsamdan ayrıldığında, ortak dil çalışma zamanı (CLR) tarafından serbest bırakılır. Visual Basic, yok *ediciler*adlı yordamları kullanarak sistem kaynakları sürümünü denetler. Birlikte, oluşturucular ve Yıkıcılar sağlam ve öngörülebilir sınıf kitaplıklarının oluşturulmasını destekler.

## <a name="using-constructors-and-destructors"></a>Oluşturucular ve yıkıcıları kullanma

Oluşturucular ve Yıkıcılar nesnelerin oluşturulmasını ve yok edilmesini denetler. `Sub New`Visual Basic ve, `Sub Finalize` nesneleri başlatma ve yok etme ' daki ve yordamları, `Class_Initialize` `Class_Terminate` Visual Basic 6,0 ve önceki sürümlerde kullanılan ve yöntemlerini değiştirir.

### <a name="sub-new"></a>Yeni Sub

`Sub New`Oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir. Aynı sınıftan ya da türetilmiş bir sınıftan başka bir oluşturucunun kod ilk satırında dışında, açıkça çağrılamaz. Ayrıca, yöntemi içindeki kod `Sub New` her zaman bir sınıftaki diğer koddan önce çalışır. `Sub New`Bir sınıf için açıkça bir yordam tanımlamadıysanız Visual Basic, çalışma zamanında örtük olarak bir Oluşturucu oluşturur `Sub New` .

Bir sınıf için Oluşturucu oluşturmak için, `Sub New` sınıf tanımında herhangi bir yerde adlı bir yordam oluşturun. Parametreli bir Oluşturucu oluşturmak için, `Sub New` aşağıdaki kodda olduğu gibi, diğer herhangi bir yordam için bağımsız değişkenler belirttiğinizde olduğu gibi, bağımsız değişkenlerin adlarını ve veri türlerini belirtin:

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

Oluşturucular, aşağıdaki kodda olduğu gibi sıklıkla aşırı yüklenmiştir:

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

Başka bir sınıftan türetilmiş bir sınıf tanımladığınızda, temel sınıfın hiçbir parametre alan erişilebilir bir Oluşturucusu yoksa, oluşturucunun ilk satırı temel sınıfın oluşturucusuna bir çağrı olmalıdır. Yukarıdaki oluşturucuyu içeren temel sınıfa yapılan bir çağrı (örneğin,) `MyBase.New(s)` . Aksi takdirde, `MyBase.New` isteğe bağlıdır ve Visual Basic çalışma zamanı onu örtülü olarak çağırır.

Üst nesnenin oluşturucusunu çağırmak için kodu yazdıktan sonra, yordama ek başlatma kodu ekleyebilirsiniz `Sub New` . `Sub New` Parametreli bir Oluşturucu olarak çağrıldığında bağımsız değişkenleri kabul edebilir. Bu parametreler, Oluşturucu çağıran yordamdan geçirilir, örneğin, `Dim AnObject As New ThisClass(X)` .

### <a name="sub-finalize"></a>Sub Finalize

Nesneleri serbest bırakmadan önce CLR, `Finalize` bir yordamı tanımlayan nesneler için yöntemini otomatik olarak çağırır `Sub Finalize` . `Finalize`Yöntemi, dosyaları kapatmak ve durum bilgilerini kaydetmek için kod gibi bir nesne yok etmeden önce yürütülmesi gereken kodu içerebilir. Yürütmeye yönelik hafif bir performans cezası var `Sub Finalize` , bu nedenle `Sub Finalize` yalnızca nesneleri açıkça serbest bırakmanız gerektiğinde bir yöntemi tanımlamanız gerekir.

> [!NOTE]
> CLR içindeki çöp toplayıcı *yönetilmeyen nesneleri*, işletim sisteminin doğrudan ÇALıŞTıRDıĞı nesneleri clr ortamının dışında vermez (ve kullanamaz). Bunun nedeni, farklı yönetilmeyen nesnelerin farklı yollarla atılmalıdır. Bu bilgiler, yönetilmeyen nesneyle doğrudan ilişkili değildir; nesnenin belgelerinde bulunması gerekir. Yönetilmeyen nesneler kullanan bir sınıf, kendi metodunda onları atmalıdır `Finalize` .

`Finalize`Yıkıcı, yalnızca ait olduğu sınıftan veya türetilmiş sınıflardan çağrılabilen, korunan bir yöntemdir. `Finalize`Bir nesne yok edildiğinde sistem otomatik olarak çağrılır, bu nedenle `Finalize` türetilmiş sınıfın uygulamasının dışından açık bir şekilde çağırmamalıdır `Finalize` .

`Class_Terminate`Bir nesne hiçbir şey olarak ayarlandığında çalıştırılan bir şekilde, genellikle bir nesnenin kapsam kaybettiğinde ve Visual Basic yıkıcıyı çağırdığında bir gecikme vardır `Finalize` . Visual Basic .NET, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> kaynakları hemen serbest bırakmak için herhangi bir zamanda açıkça çağrılabilecek ikinci bir yıkıcı türü sağlar.

> [!NOTE]
> `Finalize`Yıkıcı, uygulama tarafından işlenemediği ve uygulamanın sonlandırılmasına neden olabileceği için özel durumlar oluşturmaz.

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Yeni ve sonlandırma yöntemlerinin bir sınıf hiyerarşisinde çalışması

Bir sınıf örneği oluşturulduğunda, ortak dil çalışma zamanı (CLR), bu nesnede varsa adlı bir yordamı yürütmeye çalışır `New` . `New` , bir `constructor` nesne içindeki diğer herhangi bir kod yürütülmeden önce yeni nesneleri başlatmak için kullanılan adlı bir yordam türüdür. Bir `New` Oluşturucu, dosyaları açmak, veritabanlarına bağlanmak, değişkenleri başlatmak ve bir nesne kullanılmadan önce gerçekleştirilmesi gereken diğer görevlerden yararlanmak için kullanılabilir.

Türetilmiş bir sınıfın bir örneği oluşturulduğunda, `Sub New` önce temel sınıfın Oluşturucusu yürütülür ve ardından türetilmiş sınıflardaki oluşturucular tarafından yürütülür. Bu durum, bir oluşturucudaki ilk kod satırı, sınıf `Sub New` `MyBase.New()` hiyerarşisinde kendisinin hemen üzerinde bulunan sınıfının oluşturucusunu çağırmak için sözdizimini kullandığından oluşur. `Sub New`Daha sonra Oluşturucu, temel sınıfa yönelik oluşturucuya ulaşılana kadar sınıf hiyerarşisindeki her sınıf için çağrılır. Bu noktada, temel sınıf için oluşturucudaki kod yürütülür ve ardından tüm türetilmiş sınıflarda bulunan kod ve en son türetilen sınıflardaki kod son olarak yürütülür.

![Sınıf hiyerarşisi oluşturucularını ve devralmayı gösteren ekran görüntüsü.](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

Bir nesne artık gerekli olmadığında, CLR <xref:System.Object.Finalize%2A> bellekten boşaltmadan önce bu nesnenin yöntemini çağırır. <xref:System.Object.Finalize%2A>Yöntemi, `destructor` durum bilgilerini kaydetme, veritabanlarına yönelik dosya ve veritabanına bağlantı kapatma gibi temizleme görevlerini gerçekleştirdiğinden ve nesneyi serbest bırakmadan önce gerçekleştirilmesi gereken diğer görevlere yönelik olarak adlandırılır.

![Finalize yöntemi yıkıcısını gösteren ekran görüntüsü.](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a>IDisposable arabirimi

Sınıf örnekleri genellikle Windows işleyicileri ve veritabanı bağlantıları gibi CLR tarafından yönetilmeyen kaynakları denetler. Bu kaynaklar, `Finalize` nesne çöp toplayıcı tarafından yok edildiğinde yayımlanabilmeleri için sınıfının yönteminde atılmalıdır. Ancak çöp toplayıcı yalnızca CLR daha fazla boş bellek gerektirdiğinde nesneleri yok eder. Bu, nesnenin kapsam dışına çıkana kadar uzun sürebileceği anlamına gelir.

Atık toplamayı tamamlamak için sınıflarınız, arabirimi uygularsa sistem kaynaklarını etkin bir şekilde yönetmeye yönelik bir mekanizma sağlayabilir <xref:System.IDisposable> . <xref:System.IDisposable> , <xref:System.IDisposable.Dispose%2A> istemcileri bir nesne kullanmayı tamamlarsa çağrı gereken tek bir yöntemine sahiptir. <xref:System.IDisposable.Dispose%2A>Yöntemi, kaynakları hemen serbest bırakmak ve dosya ve veritabanı bağlantıları kapatma gibi görevleri gerçekleştirmek için kullanabilirsiniz. `Finalize`Yok edicinin aksine, <xref:System.IDisposable.Dispose%2A> yöntemi otomatik olarak çağrılmaz. Bir sınıfın istemcileri <xref:System.IDisposable.Dispose%2A> , kaynakları hemen serbest bırakmak istediğinizde açıkça çağırmalıdır.

### <a name="implementing-idisposable"></a>IDisposable uygulama

Arabirimi uygulayan bir sınıf <xref:System.IDisposable> Şu kod bölümlerini içermelidir:

- Nesnenin atılmış olup olmadığını izlemek için bir alan:

  ```vb
  Protected disposed As Boolean = False
  ```

- <xref:System.IDisposable.Dispose%2A>Sınıfının kaynaklarını serbest bırakır. Bu yöntem, <xref:System.IDisposable.Dispose%2A> `Finalize` taban sınıfının ve yöntemleri tarafından çağrılmalıdır:

  ```vb
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

- <xref:System.IDisposable.Dispose%2A>Yalnızca aşağıdaki kodu içeren bir uygulamasıdır:

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- `Finalize`Yalnızca aşağıdaki kodu içeren yöntemi geçersiz kılma:

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a>IDisposable uygulayan bir sınıftan türetme

Arabirimi uygulayan bir taban sınıftan türetilen bir sınıf, <xref:System.IDisposable> atılmalıdır ek kaynaklar kullanmadığı takdirde hiçbir temel yöntemi geçersiz kılmalıdır. Bu durumda, türetilmiş sınıf `Dispose(disposing)` türetilmiş sınıfın kaynaklarını atmak için temel sınıfın yöntemini geçersiz kılmalıdır. Bu geçersiz kılma, temel sınıfın yöntemini çağırmalıdır `Dispose(disposing)` .

```vb
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

Türetilmiş bir sınıf temel sınıfın <xref:System.IDisposable.Dispose%2A> ve yöntemlerinin üzerine içermemelidir `Finalize` . Bu yöntemler türetilmiş sınıfın bir örneğinden çağrıldığında, taban sınıfın bu yöntemlerin uygulanması, türetilmiş sınıfın yönteminin geçersiz kılmasını çağırır `Dispose(disposing)` .

## <a name="garbage-collection-and-the-finalize-destructor"></a>Çöp toplama ve sonlandırma yıkıcısı

.NET Framework, kullanılmayan kaynakları düzenli aralıklarla serbest bırakmak için *başvuru izleme atık toplama* sistemini kullanır. Visual Basic 6,0 ve önceki sürümler, kaynakları yönetmek için *başvuru sayımı* adlı farklı bir sistem kullandı. Her iki sistem de aynı işlevi otomatik olarak gerçekleştirse de, bazı önemli farklılıklar vardır.

Sistem bu nesne nesnelerinin artık gerekli olmadığını belirlediğinde CLR nesneleri düzenli olarak yok eder. Sistem kaynakları kısa tedarik edildiğinde nesneler daha hızlı serbest bırakılır ve aksi takdirde daha az sıklıkta yayımlanır. Bir nesne kapsamı kaybettiğinde ve CLR yayımlandığında, Visual Basic 6,0 ve önceki sürümlerde bulunan nesnelerden farklı olarak, nesnenin yok edileceği tam olarak belirleyemeyeceğiniz anlamına gelir. Böyle bir durumda, nesneler *belirleyici olmayan bir ömrüne*sahip olarak kabul edilir. Çoğu durumda, belirleyici olmayan ömür, `Finalize` bir nesne kapsamı kaybettiğinde, yıkıcının hemen yürütülmeyeceğini hatırlayabileceğiniz sürece uygulamaları nasıl yazacağınız değişmez.

Çöp toplama sistemleri arasındaki başka bir farklılık, ' nin kullanımını içerir `Nothing` . Visual Basic 6,0 ve önceki sürümlerde başvuru saymadan yararlanmak için, programcılar bazen `Nothing` nesne değişkenlerine, bu değişkenlerin tuttuğu başvuruları serbest bırakmak için atanır. Değişken nesneye en son başvuruyu içeriyorsa, nesnenin kaynakları hemen serbest bırakılır. Visual Basic sonraki sürümlerinde, bu yordamın hala değerli olduğu durumlar olabilir, ancak bunun gerçekleştirilmesi hiçbir zaman başvurulan nesnenin kaynaklarını hemen serbest bırakmaya neden olmaz. Kaynakları hemen serbest bırakmak için, <xref:System.IDisposable.Dispose%2A> varsa nesnenin yöntemini kullanın. ' A bir değişken ayarlamanız gereken tek zaman `Nothing` ömrü, çöp toplayıcının yalnız bırakılmış nesneleri algılamak için aldığı zamana göreli bir süredir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable.Dispose%2A>
- [Bileşenlerin başlatılması ve sonlandırılması](/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [New Işleci](../../../language-reference/operators/new-operator.md)
- [Yönetilmeyen Kaynakları Temizleme](../../../../standard/garbage-collection/unmanaged.md)
- [Yapma](../../../language-reference/nothing.md)

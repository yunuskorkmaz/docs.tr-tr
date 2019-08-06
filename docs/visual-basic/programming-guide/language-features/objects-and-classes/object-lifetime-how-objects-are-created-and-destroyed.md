---
title: 'Nesne Ömrü: Nesneler oluşturma ve yok etme (Visual Basic)'
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
ms.openlocfilehash: 932f56a9a277360b11c551aaa1faf819f8e07fe6
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796679"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a>Nesne Ömrü: Nesneler oluşturma ve yok etme (Visual Basic)

Bir sınıf örneği, bir nesnesi, `New` anahtar sözcüğü kullanılarak oluşturulur. Başlatma görevleri genellikle yeni nesnelerde kullanılmadan önce gerçekleştirilmelidir. Ortak başlatma görevleri, dosyaları açmayı, veritabanlarına bağlanmayı ve kayıt defteri anahtarlarının değerlerini okumayı içerir. Visual Basic, *oluşturucular* (başlatma üzerinde denetime izin veren özel yöntemler) adlı yordamları kullanarak yeni nesnelerin başlatılmasını denetler.

Bir nesne kapsamdan ayrıldığında, ortak dil çalışma zamanı (CLR) tarafından serbest bırakılır. Visual Basic, yok *ediciler*adlı yordamları kullanarak sistem kaynakları sürümünü denetler. Birlikte, oluşturucular ve Yıkıcılar sağlam ve öngörülebilir sınıf kitaplıklarının oluşturulmasını destekler.

## <a name="using-constructors-and-destructors"></a>Oluşturucular ve yıkıcıları kullanma

Oluşturucular ve Yıkıcılar nesnelerin oluşturulmasını ve yok edilmesini denetler. Visual Basic `Sub New` ve `Sub Finalize` , nesneleribaşlatma`Class_Terminate` ve yok etme ' daki ve yordamları, Visual Basic 6,0 ve önceki sürümlerde kullanılan veyöntemlerinideğiştirir.`Class_Initialize`

### <a name="sub-new"></a>Yeni Sub

Oluşturucu `Sub New` , bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir. Aynı sınıftan ya da türetilmiş bir sınıftan başka bir oluşturucunun kod ilk satırında dışında, açıkça çağrılamaz. Ayrıca, `Sub New` yöntemi içindeki kod her zaman bir sınıftaki diğer koddan önce çalışır. Bir sınıf için açıkça `Sub New` bir `Sub New` yordam tanımlamadıysanız Visual Basic, çalışma zamanında örtük olarak bir Oluşturucu oluşturur.

Bir sınıf için Oluşturucu oluşturmak için, sınıf tanımında herhangi bir yerde `Sub New` adlı bir yordam oluşturun. Parametreli bir Oluşturucu oluşturmak için, aşağıdaki kodda olduğu gibi, diğer herhangi bir yordam `Sub New` için bağımsız değişkenler belirttiğinizde olduğu gibi, bağımsız değişkenlerin adlarını ve veri türlerini belirtin:

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

Oluşturucular, aşağıdaki kodda olduğu gibi sıklıkla aşırı yüklenmiştir:

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

Başka bir sınıftan türetilmiş bir sınıf tanımladığınızda, temel sınıfın hiçbir parametre alan erişilebilir bir Oluşturucusu yoksa, oluşturucunun ilk satırı temel sınıfın oluşturucusuna bir çağrı olmalıdır. Yukarıdaki oluşturucuyu içeren temel sınıfa yapılan bir çağrı (örneğin, `MyBase.New(s)`). Aksi takdirde `MyBase.New` , isteğe bağlıdır ve Visual Basic çalışma zamanı onu örtülü olarak çağırır.

Üst nesnenin oluşturucusunu çağırmak için kodu yazdıktan sonra, `Sub New` yordama ek başlatma kodu ekleyebilirsiniz. `Sub New`Parametreli bir Oluşturucu olarak çağrıldığında bağımsız değişkenleri kabul edebilir. Bu parametreler, Oluşturucu çağıran yordamdan geçirilir, örneğin, `Dim AnObject As New ThisClass(X)`.

### <a name="sub-finalize"></a>Sub Finalize

Nesneleri serbest bırakmadan önce clr, bir `Finalize` `Sub Finalize` yordamı tanımlayan nesneler için yöntemini otomatik olarak çağırır. `Finalize` Yöntemi, dosyaları kapatmak ve durum bilgilerini kaydetmek için kod gibi bir nesne yok etmeden önce yürütülmesi gereken kodu içerebilir. Yürütmeye `Sub Finalize`yönelik hafif bir performans cezası var, bu nedenle yalnızca nesneleri açıkça `Sub Finalize` serbest bırakmanız gerektiğinde bir yöntemi tanımlamanız gerekir.

> [!NOTE]
> CLR içindeki çöp toplayıcı *yönetilmeyen nesneleri*, işletim sisteminin doğrudan ÇALıŞTıRDıĞı nesneleri clr ortamının dışında vermez (ve kullanamaz). Bunun nedeni, farklı yönetilmeyen nesnelerin farklı yollarla atılmalıdır. Bu bilgiler, yönetilmeyen nesneyle doğrudan ilişkili değildir; nesnenin belgelerinde bulunması gerekir. Yönetilmeyen nesneler kullanan bir sınıf, kendi `Finalize` metodunda onları atmalıdır.

`Finalize` Yıkıcı, yalnızca ait olduğu sınıftan veya türetilmiş sınıflardan çağrılabilen, korunan bir yöntemdir. Bir nesne yok `Finalize` edildiğinde sistem otomatik olarak çağrılır, bu nedenle türetilmiş sınıfın `Finalize` uygulamasının dışından açık `Finalize` bir şekilde çağırmamalıdır.

Bir nesne hiçbir şey olarak ayarlandığında çalıştırılan bir şekilde, genellikle bir nesnenin kapsam kaybettiğinde ve Visual Basic `Finalize` yıkıcıyı çağırdığında bir gecikme vardır. `Class_Terminate` Visual Basic .net, kaynakları hemen serbest bırakmak için herhangi bir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>zamanda açıkça çağrılabilecek ikinci bir yıkıcı türü sağlar.

> [!NOTE]
> `Finalize` Yıkıcı, uygulama tarafından işlenemediği ve uygulamanın sonlandırılmasına neden olabileceği için özel durumlar oluşturmaz.

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a>Yeni ve sonlandırma yöntemlerinin bir sınıf hiyerarşisinde çalışması

Bir sınıf örneği oluşturulduğunda, ortak dil çalışma zamanı (CLR), bu nesnede varsa adlı `New`bir yordamı yürütmeye çalışır. `New`, bir nesne içindeki diğer herhangi bir `constructor` kod yürütülmeden önce yeni nesneleri başlatmak için kullanılan adlı bir yordam türüdür. Bir `New` Oluşturucu, dosyaları açmak, veritabanlarına bağlanmak, değişkenleri başlatmak ve bir nesne kullanılmadan önce gerçekleştirilmesi gereken diğer görevlerden yararlanmak için kullanılabilir.

Türetilmiş bir sınıfın bir örneği oluşturulduğunda, `Sub New` önce temel sınıfın Oluşturucusu yürütülür ve ardından türetilmiş sınıflardaki oluşturucular tarafından yürütülür. Bu durum, bir `Sub New` oluşturucudaki ilk kod satırı, sınıf hiyerarşisinde kendisinin hemen üzerinde bulunan sınıfının oluşturucusunu çağırmak için sözdizimini `MyBase.New()`kullandığından oluşur. Daha `Sub New` sonra Oluşturucu, temel sınıfa yönelik oluşturucuya ulaşılana kadar sınıf hiyerarşisindeki her sınıf için çağrılır. Bu noktada, temel sınıf için oluşturucudaki kod yürütülür ve ardından tüm türetilmiş sınıflarda bulunan kod ve en son türetilen sınıflardaki kod son olarak yürütülür.

![Sınıf hiyerarşisi oluşturucularını ve devralmayı gösteren ekran görüntüsü.](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

Bir nesne artık gerekli olmadığında, CLR bellekten boşaltmadan önce bu <xref:System.Object.Finalize%2A> nesnenin yöntemini çağırır. Yöntemi, durum bilgilerini kaydetme `destructor` , veritabanlarına yönelik dosya ve veritabanına bağlantı kapatma gibi temizleme görevlerini gerçekleştirdiğinden ve nesneyi serbest bırakmadan önce gerçekleştirilmesi gereken diğer görevlere yönelik olarak adlandırılır. <xref:System.Object.Finalize%2A>

![Finalize yöntemi yıkıcısını gösteren ekran görüntüsü.](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a>IDisposable arabirimi

Sınıf örnekleri genellikle Windows işleyicileri ve veritabanı bağlantıları gibi CLR tarafından yönetilmeyen kaynakları denetler. Bu kaynaklar, nesne çöp toplayıcı tarafından yok `Finalize` edildiğinde yayımlanabilmeleri için sınıfının yönteminde atılmalıdır. Ancak çöp toplayıcı yalnızca CLR daha fazla boş bellek gerektirdiğinde nesneleri yok eder. Bu, nesnenin kapsam dışına çıkana kadar uzun sürebileceği anlamına gelir.

Atık toplamayı tamamlamak için sınıflarınız, <xref:System.IDisposable> arabirimi uygularsa sistem kaynaklarını etkin bir şekilde yönetmeye yönelik bir mekanizma sağlayabilir. <xref:System.IDisposable>, istemcileri bir nesne <xref:System.IDisposable.Dispose%2A>kullanmayı tamamlarsa çağrı gereken tek bir yöntemine sahiptir. Yöntemi, <xref:System.IDisposable.Dispose%2A> kaynakları hemen serbest bırakmak ve dosya ve veritabanı bağlantıları kapatma gibi görevleri gerçekleştirmek için kullanabilirsiniz. Yok edicinin aksine, yöntemi otomatik olarak çağrılmaz. <xref:System.IDisposable.Dispose%2A> `Finalize` Bir sınıfın istemcileri, kaynakları hemen serbest <xref:System.IDisposable.Dispose%2A> bırakmak istediğinizde açıkça çağırmalıdır.

### <a name="implementing-idisposable"></a>IDisposable uygulama

<xref:System.IDisposable> Arabirimi uygulayan bir sınıf şu kod bölümlerini içermelidir:

- Nesnenin atılmış olup olmadığını izlemek için bir alan:

  ```vb
  Protected disposed As Boolean = False
  ```

- <xref:System.IDisposable.Dispose%2A> Sınıfının kaynaklarını serbest bırakır. Bu yöntem, <xref:System.IDisposable.Dispose%2A> taban sınıfının ve `Finalize` yöntemleri tarafından çağrılmalıdır:

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

- Yalnızca aşağıdaki kodu <xref:System.IDisposable.Dispose%2A> içeren bir uygulamasıdır:

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- Yalnızca aşağıdaki kodu içeren `Finalize` yöntemi geçersiz kılma:

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a>IDisposable uygulayan bir sınıftan türetme

<xref:System.IDisposable> Arabirimi uygulayan bir taban sınıftan türetilen bir sınıf, atılmalıdır ek kaynaklar kullanmadığı takdirde hiçbir temel yöntemi geçersiz kılmalıdır. Bu durumda, türetilmiş sınıf türetilmiş sınıfın kaynaklarını atmak için temel sınıfın `Dispose(disposing)` yöntemini geçersiz kılmalıdır. Bu geçersiz kılma, temel sınıfın `Dispose(disposing)` yöntemini çağırmalıdır.

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

Türetilmiş bir sınıf temel sınıfın <xref:System.IDisposable.Dispose%2A> ve `Finalize` yöntemlerinin üzerine içermemelidir. Bu yöntemler türetilmiş sınıfın bir örneğinden çağrıldığında, taban sınıfın bu yöntemlerin uygulanması, türetilmiş sınıfın `Dispose(disposing)` yönteminin geçersiz kılmasını çağırır.

## <a name="garbage-collection-and-the-finalize-destructor"></a>Çöp toplama ve sonlandırma yıkıcısı

.NET Framework, kullanılmayan kaynakları düzenli aralıklarla serbest bırakmak için *başvuru izleme atık toplama* sistemini kullanır. Visual Basic 6,0 ve önceki sürümler, kaynakları yönetmek için *başvuru sayımı* adlı farklı bir sistem kullandı. Her iki sistem de aynı işlevi otomatik olarak gerçekleştirse de, bazı önemli farklılıklar vardır.

Sistem bu nesne nesnelerinin artık gerekli olmadığını belirlediğinde CLR nesneleri düzenli olarak yok eder. Sistem kaynakları kısa tedarik edildiğinde nesneler daha hızlı serbest bırakılır ve aksi takdirde daha az sıklıkta yayımlanır. Bir nesne kapsamı kaybettiğinde ve CLR yayımlandığında, Visual Basic 6,0 ve önceki sürümlerde bulunan nesnelerden farklı olarak, nesnenin yok edileceği tam olarak belirleyemeyeceğiniz anlamına gelir. Böyle bir durumda, nesneler *belirleyici olmayan bir ömrüne*sahip olarak kabul edilir. Çoğu durumda, belirleyici olmayan ömür, bir nesne kapsamı kaybettiğinde, `Finalize` yıkıcının hemen yürütülmeyeceğini hatırlayabileceğiniz sürece uygulamaları nasıl yazacağınız değişmez.

Çöp toplama sistemleri arasındaki başka bir farklılık, ' nin `Nothing`kullanımını içerir. Visual Basic 6,0 ve önceki sürümlerde başvuru saymadan yararlanmak için, programcılar bazen nesne değişkenlerine, `Nothing` bu değişkenlerin tuttuğu başvuruları serbest bırakmak için atanır. Değişken nesneye en son başvuruyu içeriyorsa, nesnenin kaynakları hemen serbest bırakılır. Visual Basic sonraki sürümlerinde, bu yordamın hala değerli olduğu durumlar olabilir, ancak bunun gerçekleştirilmesi hiçbir zaman başvurulan nesnenin kaynaklarını hemen serbest bırakmaya neden olmaz. Kaynakları hemen serbest bırakmak için, varsa nesnenin <xref:System.IDisposable.Dispose%2A> yöntemini kullanın. ' A bir değişken `Nothing` ayarlamanız gereken tek zaman ömrü, çöp toplayıcının yalnız bırakılmış nesneleri algılamak için aldığı zamana göreli bir süredir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable.Dispose%2A>
- [Bileşenlerin başlatılması ve sonlandırılması](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))
- [New İşleci](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Yönetilmeyen Kaynakları Temizleme](../../../../standard/garbage-collection/unmanaged.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)

---
title: Nesneler ve sınıflar
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 589b0b362cc25fd10e2780fd541cf9f7cfb546a9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344632"
---
# <a name="objects-and-classes-in-visual-basic"></a>Visual Basic içindeki nesneler ve sınıflar

Bir *nesne* , bir birim olarak kabul edilebilir kod ve verilerin bir birleşimidir. Bir nesne, bir denetim veya form gibi bir uygulamanın parçası olabilir. Tüm uygulama da bir nesne olabilir.

Visual Basic bir uygulama oluşturduğunuzda, sürekli olarak nesnelerle çalışırsınız. Denetim, form ve veri erişim nesneleri gibi Visual Basic tarafından sunulan nesneleri kullanabilirsiniz. Ayrıca, Visual Basic uygulamanızdaki diğer uygulamalardan da nesneleri kullanabilirsiniz. Hatta kendi nesnelerinizi oluşturabilir ve bunlara yönelik ek özellikler ve Yöntemler tanımlayabilirsiniz. Nesneler, programlar için önceden yazılmış derleme blokları gibi davranır; bir kez kod parçası yazmanızı ve üzerinde ve üzerinde yeniden kullanmanıza olanak tanır.

Bu konu, nesneleri ayrıntılı bir şekilde ele alır.

## <a name="objects-and-classes"></a>Nesneler ve sınıflar

Visual Basic içindeki her nesne bir *sınıf*tarafından tanımlanır. Bir sınıf, bir nesnenin değişkenlerini, özelliklerini, yordamlarını ve olaylarını açıklar. Nesneler sınıfların örnekleridir; bir sınıfı tanımladıktan sonra ihtiyacınız olan sayıda nesne oluşturabilirsiniz.

Bir nesne ve sınıfı arasındaki ilişkiyi anlamak için tanımlama bilgisi cutters ve tanımlama bilgilerini düşünün. Tanımlama bilgisi kesici sınıftır. Her tanımlama bilgisinin, örneğin boyut ve şekil özelliklerini tanımlar. Sınıfı, nesneleri oluşturmak için kullanılır. Nesneler tanımlama bilgileri.

Üyelerine erişebilmek için önce bir nesnesi oluşturmanız gerekir.

### <a name="to-create-an-object-from-a-class"></a>Bir sınıftan bir nesne oluşturmak için

1. Hangi sınıftan bir nesne oluşturmak istediğinizi belirleme.

2. Bir sınıf örneği atayabilmeniz için bir değişken oluşturmak üzere bir [Dim bildirisi](../../../../visual-basic/language-reference/statements/dim-statement.md) yazın. Değişken, istenen sınıfın türünden olmalıdır.

   ```vb
   Dim nextCustomer As customer
   ```

3. Değişkeni sınıfının yeni bir örneğine başlatmak için [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü ekleyin.

   ```vb
   Dim nextCustomer As New customer
   ```

4. Artık nesne değişkeni aracılığıyla sınıfın üyelerine erişebilirsiniz.

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> Mümkün olduğunda, değişkeni atamak istediğiniz sınıf türünde olacak şekilde bildirmeniz gerekir. Bu, *erken bağlama*olarak adlandırılır. Derleme zamanında sınıf türünü bilmiyorsanız, değişkeni [nesne veri türünde](../../../../visual-basic/language-reference/data-types/object-data-type.md)olacak şekilde bildirerek *geç bağlamayı* çağırabilirsiniz. Ancak, geç bağlama performansı daha yavaş yapabilir ve çalışma zamanı nesnesinin üyelerine erişimi sınırlayabilir. Daha fazla bilgi için bkz. [nesne değişkeni bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Birden çok örnek

Bir sınıftan yeni oluşturulan nesneler genellikle birbirleriyle aynıdır. Ancak, ayrı nesneler olarak varolduktan sonra, değişkenleri ve özellikleri diğer örneklerden bağımsız olarak değiştirilebilir. Örneğin, bir forma üç onay kutusu eklerseniz, her onay kutusu nesnesi <xref:System.Windows.Forms.CheckBox> sınıfının bir örneğidir. Bireysel <xref:System.Windows.Forms.CheckBox> nesneleri, sınıf tarafından tanımlanan ortak bir özellik ve özellik kümesini (özellikler, değişkenler, yordamlar ve olaylar) paylaşır. Ancak, her birinin kendi adı vardır, bağımsız olarak etkinleştirilebilir ve devre dışı bırakılabilir ve formda farklı bir konuma yerleştirilebilir.

## <a name="object-members"></a>Nesne üyeleri

Bir nesne, bir sınıfın *örneğini* temsil eden bir uygulamanın öğesidir. Alanlar, özellikler, Yöntemler ve olaylar, nesnelerin yapı taşlarıdır ve *üyelerini*oluşturur.

### <a name="member-access"></a>Üye Erişimi

Bir nesnenin üyesine, nesne değişkeninin adını, bir nokta (`.`) ve üyenin adını belirterek erişirsiniz. Aşağıdaki örnek, bir <xref:System.Windows.Forms.Label> nesnesinin <xref:System.Windows.Forms.Control.Text%2A> özelliğini ayarlar.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>Üyelerin IntelliSense listesi

IntelliSense, liste üyeleri seçeneğini çağırdığınızda bir sınıfın üyelerini listeler, örneğin, üye erişim işleci olarak bir nokta (`.`) yazdığınızda. Bu sınıfın bir örneği olarak belirtilen değişkenin adını izleyen bir süre yazarsanız, IntelliSense tüm örnek üyelerini ve paylaşılan üyelerin hiçbirini listeler. Sınıf adının kendisini izleyen dönemi yazarsanız, IntelliSense tüm paylaşılan üyeleri ve örnek üyelerinden hiçbirini listeler. Daha fazla bilgi için [IntelliSense kullanarak](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Alanlar ve Özellikler

*Alanlar* ve *Özellikler* bir nesnesinde depolanan bilgileri temsil eder. Değerlerini atama deyimleriyle alır ve bir yordamda yerel değişkenleri ayarladığınız şekilde ayarlarsınız. Aşağıdaki örnek <xref:System.Windows.Forms.Control.Width%2A> özelliğini alır ve bir <xref:System.Windows.Forms.Label> nesnesinin <xref:System.Windows.Forms.Control.ForeColor%2A> özelliğini ayarlar.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Bir alana *üye değişkeni*olarak da adlandırıldığını unutmayın.

Şu durumlarda özellik yordamlarını kullan:

- Değerin ne zaman ve nasıl ayarlanacağını veya alındığını kontrol etmeniz gerekir.

- Özelliğin doğrulanması gereken, iyi tanımlanmış bir değer kümesi vardır.

- Değerin ayarlanması, nesnenin durumunda bir `IsVisible` özelliği gibi bazı algılanabilir değişmesine neden olur.

- Özelliği ayarlamak, diğer iç değişkenlerde veya diğer özelliklerin değerlerine değişikliklere neden olur.

- Özelliğin ayarlanamayacağını veya alınabilmesi için önce bir adım kümesi gerçekleştirilmelidir.

Şu durumlarda alanları kullan:

- Değer kendi kendine doğrulama türüdür. Örneğin, bir `Boolean` değişkenine `True` veya `False` dışında bir değer atanırsa bir hata veya otomatik veri dönüştürme gerçekleşir.

- Veri türü tarafından desteklenen aralıktaki herhangi bir değer geçerlidir. Bu, `Single` veya `Double`türündeki birçok özellik için geçerlidir.

- Özelliği bir `String` veri türüdür ve dizenin boyutu veya değerinde bir kısıtlama yoktur.

- Daha fazla bilgi için bkz. [özellik yordamları](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

### <a name="methods"></a>Yöntemler

Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir. Örneğin <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, bir açılan kutuya yeni bir giriş ekleyen <xref:System.Windows.Forms.ComboBox> nesnesinin bir yöntemidir.

Aşağıdaki örnekte, bir <xref:System.Windows.Forms.Timer> nesnesinin <xref:System.Windows.Forms.Timer.Start%2A> yöntemi gösterilmektedir.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Bir yöntemin yalnızca bir nesne tarafından sunulan bir *yordam* olduğunu unutmayın.

Daha fazla bilgi için bkz. [yordamlar](../../../../visual-basic/programming-guide/language-features/procedures/index.md).

### <a name="events"></a>Olaylar

Bir olay, fareyi tıklatmak veya bir tuşa basmak ve yanıt vermek için kod yazabileceğiniz gibi bir nesne tarafından tanınan bir eylemdir. Olaylar, bir kullanıcı eylemi veya program kodu sonucu olarak veya sistem tarafından neden olabileceği için oluşabilir. Bir olaya işaret eden kod, olayı *yükseltmek* ve kendisine yanıt veren kod onu *işleyecek* şekilde söylenir.

Ayrıca, kendi özel olaylarınızı kendi nesneleriniz tarafından da geliştirebilirsiniz ve diğer nesneler tarafından işlenebilir. Daha fazla bilgi için bkz. [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md).

### <a name="instance-members-and-shared-members"></a>Örnek üyeleri ve paylaşılan Üyeler

Bir sınıftan bir nesne oluşturduğunuzda, sonuç bu sınıfın bir örneğidir. [Paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) anahtar sözcükle bildirilmeyen Üyeler *örnek üyeleridir*ve bu belirli örneğe tamamen aittir. Bir örnekteki örnek üye, aynı sınıfın başka bir örneğindeki aynı Üyeden bağımsız. Örneğin, örnek üye değişkeni farklı örneklerde farklı değerlere sahip olabilir.

`Shared` anahtar sözcüğüyle belirtilen Üyeler, belirli bir örneğe değil, bir bütün olarak sınıfa ait olan *paylaşılan üyeleridir*. Paylaşılan bir üye yalnızca bir kez bulunur, sınıfının kaç örneği oluşturabileceğiniz ve hatta örnek oluştursanız bile. Örneğin, bir paylaşılan üye değişkeni, sınıfına erişebilen tüm kodlar için kullanılabilen yalnızca bir değere sahiptir.

#### <a name="accessing-nonshared-members"></a>Paylaşılmayan üyelere erişme

##### <a name="to-access-a-nonshared-member-of-an-object"></a>Bir nesnenin paylaşılmayan üyesine erişmek için

1. Nesnesinin sınıfından oluşturulduğundan ve bir nesne değişkenine atandığından emin olun.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. Üyeye erişen ifadede, nesne değişkeni adını *üye erişim işleci* (`.`) ve ardından üye adı ile birlikte izleyin.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Paylaşılan üyelere erişme

##### <a name="to-access-a-shared-member-of-an-object"></a>Bir nesnenin paylaşılan üyesine erişmek için

- *Üye erişim işleci* (`.`) ve ardından üye adı ile sınıf adını izleyin. Nesnenin `Shared` üyesine her zaman doğrudan sınıf adı aracılığıyla erişmeniz gerekir.

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- Sınıfından zaten bir nesne oluşturduysanız, nesne değişkeni aracılığıyla bir `Shared` üyeye erişebilirsiniz.

### <a name="differences-between-classes-and-modules"></a>Sınıflar ve modüller arasındaki farklılıklar

Sınıflar ve modüller arasındaki temel fark, sınıfların standart modüller kullanılamadığı sürece nesneler olarak örneklenebilir. Standart modülün verilerinin yalnızca bir kopyası olduğundan, programınızın bir kısmı standart bir modülde ortak bir değişkeni değiştirdiğinde, programın başka bir kısmı o değişkeni okuduğunda aynı değeri alır. Buna karşılık, nesne verileri her bir örneklenmiş nesne için ayrı olarak mevcuttur. Diğer bir farklılık ise standart modüllerin aksine sınıfların arabirimler uygulayabildiği bir farktır.

> [!NOTE]
> `Shared` değiştiricisi bir sınıf üyesine uygulandığında, sınıfının belirli bir örneği yerine sınıfın kendisiyle ilişkilendirilir. Üyeye doğrudan sınıf adı kullanılarak erişilir, modül üyelerine aynı şekilde erişilir.

Sınıflar ve modüller, üyeleri için farklı kapsamlar da kullanır. Bir sınıf içinde tanımlanan Üyeler, sınıfın belirli bir örneği içinde kapsamlandırılır ve yalnızca nesnenin ömrü için mevcuttur. Sınıf üyelerine bir sınıfın dışından erişmek için, *nesne*biçiminde tam nitelikli adlar kullanmanız gerekir. *Üye*.

Öte yandan, bir modül içinde bildirilen üyelere varsayılan olarak genel olarak erişilebilir ve modüle erişebilen herhangi bir kod tarafından erişilebilir. Bu, bir standart modüldeki değişkenlerin, projenizdeki herhangi bir yerden görünedikleri ve programın ömrü için mevcut olduğu için etkin olmayan genel değişkenler olduğu anlamına gelir.

## <a name="reusing-classes-and-objects"></a>Sınıfları ve nesneleri yeniden kullanma

Nesneler, değişkenleri ve yordamları bir kez bildirmenizi ve sonra gerektiğinde bunları yeniden kullanmayı sağlar. Örneğin, bir uygulamaya yazım denetleyicisi eklemek istiyorsanız, yazım denetimi işlevselliği sağlamak için tüm değişkenleri ve destek işlevlerini tanımlayabilirsiniz. Yazım denetimcisini bir sınıf olarak oluşturursanız, derlenen derlemeye bir başvuru ekleyerek diğer uygulamalarda onu yeniden kullanabilirsiniz. Daha iyi bir şekilde, başka birinin zaten geliştirildiği bir yazım denetleyicisi sınıfını kullanarak kendi çalışmalarınızı kaydedebilirsiniz.

.NET Framework, kullanılabilir bileşenlere birçok örnek sağlar. Aşağıdaki örnek, <xref:System> ad alanındaki <xref:System.TimeZone> sınıfını kullanır. <xref:System.TimeZone>, geçerli bilgisayar sisteminin saat dilimi hakkında bilgi almanıza izin veren Üyeler sağlar.

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

Önceki örnekte, ilk [Dim ifadesinde](../../../../visual-basic/language-reference/statements/dim-statement.md) <xref:System.TimeZone> türünde bir nesne değişkeni bildirilir ve <xref:System.TimeZone.CurrentTimeZone%2A> özelliği tarafından döndürülen <xref:System.TimeZone> nesnesine atanır.

## <a name="relationships-among-objects"></a>Nesneler arasındaki ilişkiler

Nesneler birbirleriyle çeşitli yollarla ilişkili olabilir. Asıl ilişki türleri *hiyerarşik* ve *kapsamlardır*.

### <a name="hierarchical-relationship"></a>Hiyerarşik ilişki

Sınıflar daha temel sınıflardan türetildiklerinde *hiyerarşik bir ilişkiye*sahip oldukları söylenir. Sınıf hiyerarşileri, daha genel bir sınıfın alt türü olan öğeleri açıklayarak yararlıdır.

Aşağıdaki örnekte, normal <xref:System.Windows.Forms.Button> gibi davranan ve ayrıca ön plan ve arka plan renklerini tersine getiren bir yöntemi gösteren özel bir <xref:System.Windows.Forms.Button> türünü tanımlamak istediğinizi varsayalım.

#### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>Bir sınıf tanımlamak için zaten var olan bir sınıftan türetilmiş

1. İhtiyaç duyduğunuz nesnenin oluşturulacağı bir sınıf tanımlamak için bir [Class ifadesini](../../../../visual-basic/language-reference/statements/class-statement.md) kullanın.

   ```vb
   Public Class reversibleButton
   ```

   `End Class` deyimin sınıfınızın son kod satırını izlediği emin olun. Varsayılan olarak, tümleşik geliştirme ortamı (IDE), bir `Class` bildiriminde girdiğinizde otomatik olarak bir `End Class` oluşturur.

2. [Inherits ifadesiyle](../../../../visual-basic/language-reference/statements/inherits-statement.md)hemen `Class` ifadesini izleyin. Yeni sınıfınızın türetildiği sınıfı belirtin.

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   Yeni sınıfınız, temel sınıf tarafından tanımlanan tüm üyeleri devralır.

3. Türetilmiş sınıfınızın sunduğu ek Üyeler için kodu ekleyin. Örneğin, bir `reverseColors` yöntemi ekleyebilirsiniz ve türetilmiş sınıfınız aşağıdaki gibi görünebilir:

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   `reversibleButton` sınıfından bir nesne oluşturursanız, bu, <xref:System.Windows.Forms.Button> sınıfının tüm üyelerine, ayrıca `reverseColors` yöntemi ve `reversibleButton`üzerinde tanımladığınız diğer yeni üyelere erişebilir.

Türetilmiş sınıflar, bir sınıf hiyerarşisinde ilerlemeniz sırasında karmaşıklık eklemenize olanak sağlayan, temel alınan sınıftan üyeleri devralınır. Daha fazla bilgi için bkz. [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

### <a name="compile-the-code"></a>Kod derleme

Derleyicinin yeni sınıfınızı türettiğiniz sınıfa erişip erişemeyeceğini unutmayın. Bu, önceki örnekte olduğu gibi adını tam olarak niteleyen veya [Imports ifadesinde (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ad alanını tanımlayan anlamına gelebilir. Sınıf farklı bir projem ise, bu projeye bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için [bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Kapsama ilişkisi

Nesnelerin ilişkili olduğu başka bir yol da *kapsama ilişkisidir*. Kapsayıcı nesneleri diğer nesneleri mantıksal olarak kapsüllendirir. Örneğin, <xref:System.OperatingSystem> nesnesi mantıksal olarak <xref:System.OperatingSystem.Version%2A> özelliğini döndüren bir <xref:System.Version> nesnesi içerir. Kapsayıcı nesnesinin fiziksel olarak başka bir nesne içermediğini unutmayın.

#### <a name="collections"></a>Koleksiyonlar

Nesne *kapsamaların*belirli bir türü koleksiyonlar tarafından temsil edilir. Koleksiyonlar, numaralandırılabilir benzer nesne gruplarıdır. Visual Basic her biri Için içindeki belirli bir sözdizimini destekler [... ](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)Bir koleksiyonun öğeleri arasında yineleme yapmanızı sağlayan Next bildirisi. Ayrıca, Koleksiyonlar genellikle öğeleri dizine göre almak veya benzersiz bir dizeyle ilişkilendirerek bir <xref:Microsoft.VisualBasic.Collection.Item%2A> kullanmanıza olanak tanır. Koleksiyonlar, dizinleri kullanmadan öğeleri eklemenize veya kaldırmanıza izin verdiklerinden, dizilerden kullanımı daha kolay olabilir. Kullanım kolaylığı nedeniyle, Koleksiyonlar genellikle formları ve denetimleri depolamak için kullanılır.

## <a name="related-topics"></a>İlgili konular

[Izlenecek yol: sınıfları tanımlama](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)\
Sınıfının nasıl oluşturulacağı hakkında adım adım bir açıklama sağlar.

[Aşırı yüklenmiş Özellikler ve yöntemler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)\
Aşırı Yüklenmiş Özellikler ve Yöntemler

[Devralma temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)\
Devralma değiştiricilerini, yöntemleri ve özellikleri geçersiz kılmayı, MyClass ve MyBase 'yi içerir.

[Nesne ömrü: nesneleri oluşturma ve yok etme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)\
Sınıf örneklerinin oluşturulmasını ve elden atılanışını açıklar.

[Anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)\
Veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanıza izin veren anonim türlerin nasıl oluşturulduğunu ve kullanıldığını açıklar.

[Nesne başlatıcıları: adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)\
Tek bir ifade kullanarak adlandırılmış ve anonim türlerin örneklerini oluşturmak için kullanılan nesne başlatıcılarını açıklar.

[Nasıl yapılır: anonim tür bildirimlerinde özellik adlarını ve türleri çıkarçıkar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)\
Anonim tür bildirimlerinde özellik adlarının ve türlerin nasıl çıkarılacağını açıklar. Başarılı ve başarısız çıkarım örneklerini sağlar.

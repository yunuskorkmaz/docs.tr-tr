---
title: Nesneler ve sınıflar
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 10e257a1cbc8778565a9838aeef423522f9d2970
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290622"
---
# <a name="objects-and-classes-in-visual-basic"></a>Visual Basic içindeki nesneler ve sınıflar

Bir *nesne* , bir birim olarak kabul edilebilir kod ve verilerin bir birleşimidir. Bir nesne, bir denetim veya form gibi bir uygulamanın parçası olabilir. Tüm uygulama da bir nesne olabilir.

Visual Basic bir uygulama oluşturduğunuzda, sürekli olarak nesnelerle çalışırsınız. Denetim, form ve veri erişim nesneleri gibi Visual Basic tarafından sunulan nesneleri kullanabilirsiniz. Ayrıca, Visual Basic uygulamanızdaki diğer uygulamalardan da nesneleri kullanabilirsiniz. Hatta kendi nesnelerinizi oluşturabilir ve bunlara yönelik ek özellikler ve Yöntemler tanımlayabilirsiniz. Nesneler, programlar için önceden yazılmış derleme blokları gibi davranır; bir kez kod parçası yazmanızı ve üzerinde ve üzerinde yeniden kullanmanıza olanak tanır.

Bu konu, nesneleri ayrıntılı bir şekilde ele alır.

## <a name="objects-and-classes"></a>Nesneler ve sınıflar

Visual Basic içindeki her nesne bir *sınıf*tarafından tanımlanır. Bir sınıf, bir nesnenin değişkenlerini, özelliklerini, yordamlarını ve olaylarını açıklar. Nesneler sınıfların örnekleridir; bir sınıfı tanımladıktan sonra ihtiyacınız olan sayıda nesne oluşturabilirsiniz.

Bir nesne ve sınıfı arasındaki ilişkiyi anlamak için tanımlama bilgisi cutters ve tanımlama bilgilerini düşünün. Tanımlama bilgisi kesici sınıftır. Her tanımlama bilgisinin, örneğin boyut ve şekil özelliklerini tanımlar. Sınıfı, nesneleri oluşturmak için kullanılır. Nesneler tanımlama bilgileri.

Bir nesnesi, [`Shared`](../../../language-reference/modifiers/shared.md) sınıfının bir nesnesi olmadan erişilebilen Üyeler hariç, üyelerine erişebilmek için önce bir nesne oluşturmanız gerekir.

### <a name="create-an-object-from-a-class"></a>Bir sınıftan nesne oluşturma

1. Hangi sınıftan bir nesne oluşturmak istediğinizi belirleyin veya kendi sınıfınızı tanımlayın. Örneğin:

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. Bir sınıf örneği atayabilmeniz için bir değişken oluşturmak üzere bir [Dim bildirisi](../../../language-reference/statements/dim-statement.md) yazın. Değişken, istenen sınıfın türünden olmalıdır.

   ```vb
   Dim nextCustomer As Customer
   ```

3. Değişkeni sınıfının yeni bir örneğine başlatmak için [New Operator](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü ekleyin.

   ```vb
   Dim nextCustomer As New Customer
   ```

4. Artık nesne değişkeni aracılığıyla sınıfın üyelerine erişebilirsiniz.

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> Mümkün olduğunda, değişkeni atamak istediğiniz sınıf türünde olacak şekilde bildirmeniz gerekir. Bu, *erken bağlama*olarak adlandırılır. Derleme zamanında sınıf türünü bilmiyorsanız, değişkeni [nesne veri türünde](../../../language-reference/data-types/object-data-type.md)olacak şekilde bildirerek *geç bağlamayı* çağırabilirsiniz. Ancak, geç bağlama performansı daha yavaş yapabilir ve çalışma zamanı nesnesinin üyelerine erişimi sınırlayabilir. Daha fazla bilgi için bkz. [nesne değişkeni bildirimi](../variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Birden çok örnek

Bir sınıftan yeni oluşturulan nesneler genellikle birbirleriyle aynıdır. Ancak, ayrı nesneler olarak varolduktan sonra, değişkenleri ve özellikleri diğer örneklerden bağımsız olarak değiştirilebilir. Örneğin, bir forma üç onay kutusu eklerseniz, her onay kutusu nesnesi sınıfının bir örneğidir <xref:System.Windows.Forms.CheckBox> . Ayrı <xref:System.Windows.Forms.CheckBox> nesneler, sınıf tarafından tanımlanan ortak bir özellik ve özellik kümesini (özellikler, değişkenler, yordamlar ve olaylar) paylaşır. Ancak, her birinin kendi adı vardır, bağımsız olarak etkinleştirilebilir ve devre dışı bırakılabilir ve formda farklı bir konuma yerleştirilebilir.

## <a name="object-members"></a>Nesne üyeleri

Bir nesne, bir sınıfın *örneğini* temsil eden bir uygulamanın öğesidir. Alanlar, özellikler, Yöntemler ve olaylar, nesnelerin yapı taşlarıdır ve *üyelerini*oluşturur.

### <a name="member-access"></a>Üye Erişimi

Bir nesnenin üyesine, nesne değişkeninin adını, bir nokta ( `.` ) ve üyenin adını belirterek erişirsiniz. Aşağıdaki örnek <xref:System.Windows.Forms.Control.Text%2A> bir nesnesinin özelliğini ayarlar <xref:System.Windows.Forms.Label> .

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>Üyelerin IntelliSense listesi

IntelliSense, liste üyeleri seçeneğini çağırdığınızda bir sınıfın üyelerini listeler, örneğin, `.` üye erişim operatörü olarak bir nokta () yazdığınızda. Bu sınıfın bir örneği olarak belirtilen değişkenin adını izleyen bir süre yazarsanız, IntelliSense tüm örnek üyelerini ve paylaşılan üyelerin hiçbirini listeler. Sınıf adının kendisini izleyen dönemi yazarsanız, IntelliSense tüm paylaşılan üyeleri ve örnek üyelerinden hiçbirini listeler. Daha fazla bilgi için bkz. [IntelliSense kullanma](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Alanlar ve Özellikler

*Alanlar* ve *Özellikler* bir nesnesinde depolanan bilgileri temsil eder. Değerlerini atama deyimleriyle alır ve bir yordamda yerel değişkenleri ayarladığınız şekilde ayarlarsınız. Aşağıdaki örnek, özelliğini alır <xref:System.Windows.Forms.Control.Width%2A> ve <xref:System.Windows.Forms.Control.ForeColor%2A> bir nesnenin özelliğini ayarlar <xref:System.Windows.Forms.Label> .

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Bir alana *üye değişkeni*olarak da adlandırıldığını unutmayın.

Şu durumlarda özellik yordamlarını kullan:

- Değerin ne zaman ve nasıl ayarlanacağını veya alındığını kontrol etmeniz gerekir.

- Özelliğin doğrulanması gereken, iyi tanımlanmış bir değer kümesi vardır.

- Değerin ayarlanması nesnenin durumunda bir özellik gibi bazı algılanabilir değişmesine neden olur `IsVisible` .

- Özelliği ayarlamak, diğer iç değişkenlerde veya diğer özelliklerin değerlerine değişikliklere neden olur.

- Özelliğin ayarlanamayacağını veya alınabilmesi için önce bir adım kümesi gerçekleştirilmelidir.

Şu durumlarda alanları kullan:

- Değer kendi kendine doğrulama türüdür. Örneğin, bir değişken ya da `True` `False` bir değişkene atanan bir değer varsa, bir hata veya otomatik veri dönüştürme gerçekleşir `Boolean` .

- Veri türü tarafından desteklenen aralıktaki herhangi bir değer geçerlidir. Bu, veya türündeki birçok özellik için geçerlidir `Single` `Double` .

- Özelliği bir `String` veri türüdür ve dizenin boyutu veya değerinde bir kısıtlama yoktur.

- Daha fazla bilgi için bkz. [özellik yordamları](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

> [!TIP]
> Her zaman sabit olmayan alanları özel tutun. Ortak hale getirmek istediğinizde, bunun yerine bir özellik kullanın.

### <a name="methods"></a>Yöntemler

Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir. Örneğin, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> <xref:System.Windows.Forms.ComboBox> bir Birleşik giriş kutusuna yeni bir giriş ekleyen nesnenin bir yöntemidir.

Aşağıdaki örnek <xref:System.Windows.Forms.Timer.Start%2A> bir nesnesinin yöntemini gösterir <xref:System.Windows.Forms.Timer> .

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Bir yöntemin yalnızca bir nesne tarafından sunulan bir *yordam* olduğunu unutmayın.

Daha fazla bilgi için bkz. [yordamlar](../procedures/index.md).

### <a name="events"></a>Ekinlikler

Bir olay, fareyi tıklatmak veya bir tuşa basmak ve yanıt vermek için kod yazabileceğiniz gibi bir nesne tarafından tanınan bir eylemdir. Olaylar, bir kullanıcı eylemi veya program kodu sonucu olarak veya sistem tarafından neden olabileceği için oluşabilir. Bir olaya işaret eden kod, olayı *yükseltmek* ve kendisine yanıt veren kod onu *işleyecek* şekilde söylenir.

Ayrıca, kendi özel olaylarınızı kendi nesneleriniz tarafından da geliştirebilirsiniz ve diğer nesneler tarafından işlenebilir. Daha fazla bilgi için bkz. [Olaylar](../events/index.md).

### <a name="instance-members-and-shared-members"></a>Örnek üyeleri ve paylaşılan Üyeler

Bir sınıftan bir nesne oluşturduğunuzda, sonuç bu sınıfın bir örneğidir. [Paylaşılan](../../../language-reference/modifiers/shared.md) anahtar sözcükle bildirilmeyen Üyeler *örnek üyeleridir*ve bu belirli örneğe tamamen aittir. Bir örnekteki örnek üye, aynı sınıfın başka bir örneğindeki aynı Üyeden bağımsız. Örneğin, örnek üye değişkeni farklı örneklerde farklı değerlere sahip olabilir.

Anahtar sözcüğüyle belirtilen Üyeler `Shared` , belirli bir örneğe değil, bir bütün olarak sınıfa ait olan *paylaşılan üyeleridir*. Paylaşılan bir üye yalnızca bir kez bulunur, sınıfının kaç örneği oluşturabileceğiniz ve hatta örnek oluştursanız bile. Örneğin, bir paylaşılan üye değişkeni, sınıfına erişebilen tüm kodlar için kullanılabilen yalnızca bir değere sahiptir.

#### <a name="accessing-non-shared-members"></a>Paylaşılan olmayan üyelere erişme

1. Nesnesinin sınıfından oluşturulduğundan ve bir nesne değişkenine atandığından emin olun.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. Üyeye erişen ifadede, nesne değişkeni adını *üye erişim işleci* ( `.` ) ve ardından üye adı ile birlikte izleyin.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Paylaşılan üyelere erişme

- *Üye erişim işleci* ( `.` ) ve ardından üye adı ile sınıf adını izleyin. `Shared`Doğrudan sınıf adı aracılığıyla nesnenin üyesine her zaman erişmeniz gerekir.

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- Sınıfından zaten bir nesne oluşturduysanız, başka bir `Shared` üyeye de nesnenin değişkeni aracılığıyla erişebilirsiniz.

### <a name="differences-between-classes-and-modules"></a>Sınıflar ve modüller arasındaki farklılıklar

Sınıflar ve modüller arasındaki temel fark, sınıfların standart modüller kullanılamadığı sürece nesneler olarak örneklenebilir. Standart modülün verilerinin yalnızca bir kopyası olduğundan, programınızın bir kısmı standart bir modülde ortak bir değişkeni değiştirdiğinde, programın başka bir kısmı o değişkeni okuduğunda aynı değeri alır. Buna karşılık, nesne verileri her bir örneklenmiş nesne için ayrı olarak mevcuttur. Diğer bir farklılık ise standart modüllerin aksine sınıfların arabirimler uygulayabildiği bir farktır. Bir sınıf, [MustInherit](../../../language-reference/modifiers/mustinherit.md) değiştiricisi ile işaretlenmişse doğrudan başlatılamaz. Ancak, modüller devralınabileceğinden Devralındığı için bir modülden hala farklılık vardır.

> [!NOTE]
> `Shared`Değiştirici bir sınıf üyesine uygulandığında, sınıfının belirli bir örneği yerine sınıfın kendisiyle ilişkilendirilir. Üyeye doğrudan sınıf adı kullanılarak erişilir, modül üyelerine aynı şekilde erişilir.

Sınıflar ve modüller, üyeleri için farklı kapsamlar da kullanır. Bir sınıf içinde tanımlanan Üyeler, sınıfın belirli bir örneği içinde kapsamlandırılır ve yalnızca nesnenin ömrü için mevcuttur. Sınıf üyelerine bir sınıfın dışından erişmek için, *nesne*biçiminde tam nitelikli adlar kullanmanız gerekir. *Üye*.

Öte yandan, bir modül içinde bildirilen üyelere varsayılan olarak genel olarak erişilebilir ve modüle erişebilen herhangi bir kod tarafından erişilebilir. Bu, bir standart modüldeki değişkenlerin, projenizdeki herhangi bir yerden görünedikleri ve programın ömrü için mevcut olduğu için etkin olmayan genel değişkenler olduğu anlamına gelir.

## <a name="reusing-classes-and-objects"></a>Sınıfları ve nesneleri yeniden kullanma

Nesneler, değişkenleri ve yordamları bir kez bildirmenizi ve sonra gerektiğinde bunları yeniden kullanmayı sağlar. Örneğin, bir uygulamaya yazım denetleyicisi eklemek istiyorsanız, yazım denetimi işlevselliği sağlamak için tüm değişkenleri ve destek işlevlerini tanımlayabilirsiniz. Yazım denetimcisini bir sınıf olarak oluşturursanız, derlenen derlemeye bir başvuru ekleyerek diğer uygulamalarda onu yeniden kullanabilirsiniz. Daha iyi bir şekilde, başka birinin zaten geliştirildiği bir yazım denetleyicisi sınıfını kullanarak kendi çalışmalarınızı kaydedebilirsiniz.

.NET, kullanıma açık olan bileşenlere birçok örnek sağlar. Aşağıdaki örnek, <xref:System.TimeZone> <xref:System> ad alanındaki sınıfını kullanır. <xref:System.TimeZone>geçerli bilgisayar sisteminin saat dilimi hakkında bilgi almanıza izin veren Üyeler sağlar.

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

Önceki örnekte, ilk [Dim ifadesinde](../../../language-reference/statements/dim-statement.md) , türünde bir nesne değişkeni <xref:System.TimeZone> bildirilir ve bu nesneye <xref:System.TimeZone> , özelliği tarafından döndürülen bir nesne atanır <xref:System.TimeZone.CurrentTimeZone%2A> .

## <a name="relationships-among-objects"></a>Nesneler arasındaki ilişkiler

Nesneler birbirleriyle çeşitli yollarla ilişkili olabilir. Asıl ilişki türleri *hiyerarşik* ve *kapsamlardır*.

### <a name="hierarchical-relationship"></a>Hiyerarşik ilişki

Sınıflar daha temel sınıflardan türetildiklerinde *hiyerarşik bir ilişkiye*sahip oldukları söylenir. Sınıf hiyerarşileri, daha genel bir sınıfın alt türü olan öğeleri açıklayarak yararlıdır.

Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> normal gibi davranan <xref:System.Windows.Forms.Button> ve ayrıca ön plan ve arka plan renklerini tersine getiren bir yöntemi ortaya çıkaran özel bir tür tanımlamak istediğinizi varsayalım.

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a>Zaten var olan bir sınıftan türetilmiş bir sınıf tanımlayın

1. İhtiyaç duyduğunuz nesnenin oluşturulacağı bir sınıf tanımlamak için bir [Class ifadesini](../../../language-reference/statements/class-statement.md) kullanın.

   ```vb
   Public Class ReversibleButton
   ```

   Bir `End Class` deyimin sınıfınıza ait son kod satırını takip ettiğinizden emin olun. Varsayılan olarak, tümleşik geliştirme ortamı (IDE) bir ifade girdiğinizde otomatik olarak bir üretir `End Class` `Class` .

2. `Class`Bir [Inherits ifadesiyle](../../../language-reference/statements/inherits-statement.md)ifadeyi hemen izleyin. Yeni sınıfınızın türetildiği sınıfı belirtin.

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   Yeni sınıfınız, temel sınıf tarafından tanımlanan tüm üyeleri devralır.

3. Türetilmiş sınıfınızın sunduğu ek Üyeler için kodu ekleyin. Örneğin, bir `ReverseColors` Yöntem ekleyebilirsiniz ve türetilmiş sınıfınız aşağıdaki gibi görünebilir:

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   Sınıfından bir nesne oluşturursanız `ReversibleButton` , sınıfın tüm üyelerine <xref:System.Windows.Forms.Button> ve ' `ReverseColors` de tanımladığınız diğer tüm yeni üyelere erişebilir `ReversibleButton` .

Türetilmiş sınıflar, bir sınıf hiyerarşisinde ilerlemeniz sırasında karmaşıklık eklemenize olanak sağlayan, temel alınan sınıftan üyeleri devralınır. Daha fazla bilgi için bkz. [Devralma Temelleri](inheritance-basics.md).

### <a name="compile-the-code"></a>Kodu derle

Derleyicinin yeni sınıfınızı türettiğiniz sınıfa erişip erişemeyeceğini unutmayın. Bu, önceki örnekte olduğu gibi adını tam olarak niteleyen veya [Imports ifadesinde (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)ad alanını tanımlayan anlamına gelebilir. Sınıf farklı bir projem ise, bu projeye bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Kapsama ilişkisi

Nesnelerin ilişkili olduğu başka bir yol da *kapsama ilişkisidir*. Kapsayıcı nesneleri diğer nesneleri mantıksal olarak kapsüllendirir. Örneğin, <xref:System.OperatingSystem> nesnesi mantıksal <xref:System.Version> olarak kendi özelliği aracılığıyla döndürülen bir nesnesi içerir <xref:System.OperatingSystem.Version%2A> . Kapsayıcı nesnesinin fiziksel olarak başka bir nesne içermediğini unutmayın.

#### <a name="collections"></a>Koleksiyonlar

Nesne *kapsamaların*belirli bir türü koleksiyonlar tarafından temsil edilir. Koleksiyonlar, numaralandırılabilir benzer nesne gruplarıdır. Visual Basic her biri Için içindeki belirli bir sözdizimini destekler [... ](../../../language-reference/statements/for-each-next-statement.md)Bir koleksiyonun öğeleri arasında yineleme yapmanızı sağlayan Next bildirisi. Ayrıca, Koleksiyonlar genellikle <xref:Microsoft.VisualBasic.Collection.Item%2A> öğelerini dizine göre almak için veya bunları benzersiz bir dizeyle ilişkilendirerek kullanmanıza izin verir. Koleksiyonlar, dizinleri kullanmadan öğeleri eklemenize veya kaldırmanıza izin verdiklerinden, dizilerden kullanımı daha kolay olabilir. Kullanım kolaylığı nedeniyle, Koleksiyonlar genellikle formları ve denetimleri depolamak için kullanılır.

## <a name="related-topics"></a>İlgili konular

[İzlenecek yol: sınıfları tanımlama](walkthrough-defining-classes.md)\
Sınıfının nasıl oluşturulacağı hakkında adım adım bir açıklama sağlar.

[Aşırı yüklenmiş Özellikler ve Yöntemler](overloaded-properties-and-methods.md)\
Aşırı Yüklenmiş Özellikler ve Yöntemler

[Devralma Temelleri](inheritance-basics.md)\
Devralma değiştiricilerini, yöntemleri ve özellikleri geçersiz kılmayı, MyClass ve MyBase 'yi içerir.

[Nesne ömrü: nesneleri oluşturma ve yok etme](object-lifetime-how-objects-are-created-and-destroyed.md)\
Sınıf örneklerinin oluşturulmasını ve elden atılanışını açıklar.

[Anonim türler](anonymous-types.md)\
Veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanıza izin veren anonim türlerin nasıl oluşturulduğunu ve kullanıldığını açıklar.

[Nesne başlatıcıları: adlandırılmış ve anonim türler](object-initializers-named-and-anonymous-types.md)\
Tek bir ifade kullanarak adlandırılmış ve anonim türlerin örneklerini oluşturmak için kullanılan nesne başlatıcılarını açıklar.

[Nasıl yapılır: anonim tür bildirimlerinde özellik adlarını ve türleri Çıkarçıkar](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)\
Anonim tür bildirimlerinde özellik adlarının ve türlerin nasıl çıkarılacağını açıklar. Başarılı ve başarısız çıkarım örneklerini sağlar.

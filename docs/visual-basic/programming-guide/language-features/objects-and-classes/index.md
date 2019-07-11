---
title: Nesneler ve sınıflar Visual Basic'te
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: dd2968f7ab528fa07ef0c5af85f2a7f07147a76e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755157"
---
# <a name="objects-and-classes-in-visual-basic"></a>Nesneler ve sınıflar Visual Basic'te

Bir *nesne* kod ve bir birim olarak davranılıp veri birleşimidir. Bir nesne gibi bir denetim veya form uygulamanın bir parçası olabilir. Tüm uygulama ayrıca bir nesne olabilir.

Visual Basic'te bir uygulama oluşturduğunuzda, sürekli nesnelerle çalışırsınız. Visual Basic tarafından sağlanan gibi denetimleri, formlar ve veri erişim nesneleri nesnelerini kullanabilirsiniz. Visual Basic uygulamanızdaki diğer uygulamalardan nesneler de kullanabilirsiniz. Hatta, kendi nesnelerinizi oluşturma ve ek özellikleri ve yöntemleri için bunları tanımlayın. Nesneler davranır gibi prefabricated programlar için yapı taşları — bunlar, bir parça kodu bir kere yazıp, onu tekrar tekrar tekrar olanak tanır.

Bu konuda, nesneleri ayrıntılı ele alınmıştır.

## <a name="objects-and-classes"></a>Nesneler ve sınıflar

Visual Basic'te her nesne tarafından tanımlanan bir *sınıfı*. Bir sınıf, değişkenleri, özellikleri, yordamları ve olayları bir nesnenin açıklar. Sınıfların örneklerini nesnelerdir; bir sınıf tanımlandıktan ihtiyacınız kadar nesne oluşturabilirsiniz.

Bir nesne ve onun sınıfı arasındaki ilişkiyi anlamak için tanımlama bilgisi cutters ve tanımlama bilgileri düşünün. Tanımlama Bilgisi kesici sınıftır. Bu özellikleri her tanımlama bilgisi boyutu ve şekli tanımlar. Sınıf nesneleri oluşturmak için kullanılır. Tanımlama bilgilerini nesneleridir.

Üyeleri erişebilmeniz için önce bir nesne oluşturmanız gerekir.

### <a name="to-create-an-object-from-a-class"></a>Nesne öğesinden bir sınıf oluşturmak için

1. Hangi sınıfından bir nesne oluşturmak istediğinize karar verin.

2. Yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) bir sınıf örneği atamak bir değişken oluşturmak için. Değişkeni istenen sınıf türünde olmalıdır.

   ```vb
   Dim nextCustomer As customer
   ```

3. Ekleme [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) değişkene sınıfının yeni bir örneğini başlatmak için anahtar sözcüğü.

   ```vb
   Dim nextCustomer As New customer
   ```

4. Nesne değişkeni sınıf üyeleri artık erişebilirsiniz.

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> Mümkün olduğunda, atamak istediğiniz sınıf türünün olmasını değişkeni bildirmelidir. Bu adlandırılır *erken bağlama*. Derleme zamanında tür sınıfı bilmiyorsanız, çağırabilirsiniz *geç bağlama* olmaya değişken bildirme tarafından [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md). Ancak geç bağlama performans daha yavaş hale ve çalışma zamanı nesnenin üyelerine erişimi sınırlayın. Daha fazla bilgi için [nesne değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Birden çok örneği

Yeni bir sınıftan oluşturulan nesneler genellikle birbirinin. Bireysel nesne olarak oldukları sonra Bununla birlikte, kendi değişkenleri ve özellikleri diğer örneklerin bağımsız olarak değiştirilebilir. Üç onay kutusunu forma eklerseniz, örneğin, onay kutusu her bir nesne örneğidir <xref:System.Windows.Forms.CheckBox> sınıfı. Tek tek <xref:System.Windows.Forms.CheckBox> nesneleri özellikleri ve sınıf tarafından tanımlanan özellikleri (özellikleri, değişkenleri, yordamları ve olayları) ortak bir kümesini paylaşır. Ancak, her kendi adına sahip, ayrı ayrı etkinleştirilebilir ve devre dışı bırakıldı ve form üzerinde farklı bir konumda yerleştirilebilir.

## <a name="object-members"></a>Nesne üyeleri

Bir uygulamanın bir öğe bir nesnedir temsil eden bir *örneği* bir sınıf. Alanlar, özellikler, yöntemler ve olaylar yapı taşlarıdır nesnelerin ve oluşturan kendi *üyeleri*.

### <a name="member-access"></a>Üye Erişimi

Sırasıyla nesne değişkeni adını belirterek bir nesnenin bir üyesine erişmek bir süre (`.`) ve üyesinin adı. Aşağıdaki örnek kümeleri <xref:System.Windows.Forms.Control.Text%2A> özelliği bir <xref:System.Windows.Forms.Label> nesne.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>IntelliSense üye listesi

IntelliSense, bir nokta yazın, örneğin, üyeleri Listele seçeneğini çağırdığınızda, bir sınıfın üyeleri listeler (`.`) üye erişim işleci olarak. Bu sınıfın bir örneği bildirilen bir değişken adını ardından nokta yazarsanız, IntelliSense, tüm örnek üyeleri ve paylaşılan üyeler hiçbiri listeler. Sınıf adı nokta yazarsanız, IntelliSense, tüm paylaşılan üyeleri ve örnek üyeleri hiçbiri listeler. Daha fazla bilgi için [IntelliSense kullanarak](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Alanlar ve Özellikler

*Alanları* ve *özellikleri* bir nesnede depolanan bilgileri temsil eder. Alabilir ve aynı şekilde almak ve bir yordamda yerel değişkenleri ayarlamak değerlerine atama deyimleri ile ayarlayın. Aşağıdaki örnek alır <xref:System.Windows.Forms.Control.Width%2A> özelliği ve kümelerini <xref:System.Windows.Forms.Control.ForeColor%2A> özelliği bir <xref:System.Windows.Forms.Label> nesne.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Bir alan da çağrıldığını unutmayın bir *üye değişkeni*.

Özellik yordamları kullanın. zaman:

- Ne zaman ve nasıl bir değer alındı veya ayarlandığında denetlemek gerekir.

- Doğrulanması gereken, iyi tanımlanmış bir dizi özelliği vardır.

- Ayar değeri neden olan bazı bir algılanabilir değişiklik nesnenin durumda gibi bir `IsVisible` özelliği.

- Özelliğini, diğer iç değişkenler veya diğer özelliklerin değerlerine değişiklikler neden olur.

- Özelliği ayarlamak veya alınan adımlar gerçekleştirilmelidir.

Alanları kullanın:

- Kendi kendine doğrulama türü değerdir. Örneğin, bir hata veya otomatik veri dönüştürme dışında bir değere oluşur `True` veya `False` atanan bir `Boolean` değişkeni.

- Veri türü tarafından desteklenen aralıkta herhangi bir değer geçerli değil. Bu tür birçok özelliği true `Single` veya `Double`.

- Özelliği bir `String` veri türünü ve boyutunu veya dize değeri hiçbir kısıtlaması yoktur.

- Daha fazla bilgi için [özellik yordamları](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

### <a name="methods"></a>Yöntemler

A *yöntemi* , nesnenin gerçekleştirebileceği bir eylemdir. Örneğin, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> bir yöntemidir <xref:System.Windows.Forms.ComboBox> nesnesini bir birleşik giriş kutusuna yeni bir giriş ekler.

Aşağıdaki örnek, gösterir <xref:System.Windows.Forms.Timer.Start%2A> yöntemi bir <xref:System.Windows.Forms.Timer> nesne.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Yalnızca bir yöntem olduğunu unutmayın bir *yordamı* nesne tarafından gösterilir.

Daha fazla bilgi için [yordamları](../../../../visual-basic/programming-guide/language-features/procedures/index.md).

### <a name="events"></a>Olaylar

Bir olay yanıt vermesi için kod yazabilirsiniz ve fareyle tıklamak veya bir tuşuna basmak gibi bir nesne tarafından tanınan bir eylemdir. Olayları bir kullanıcı eylemi veya program kodu sonucunda oluşabilir veya sistem tarafından kaynaklanabilir. Bir olay sinyalini verir kod söyledi *yükseltmek* olay ve buna yanıt diyor ki kod *işlemek* bu.

Nesnelerinizi tarafından oluşturulur ve diğer nesneleri tarafından işlenen özel kendi olaylarınızı da geliştirebilirsiniz. Daha fazla bilgi için [olayları](../../../../visual-basic/programming-guide/language-features/events/index.md).

### <a name="instance-members-and-shared-members"></a>Örnek üyeleri ve paylaşılan üyeler

Öğesinden bir sınıf bir nesne oluşturduğunuzda, bu sınıfın bir örneğini sonucudur. İle bildirilmiş üyeleri [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) anahtar sözcüğünü *örnek üyeleri*, ait oldukları kesinlikle, belirli bir örneğine. Bir örnek üyesi bir örneği, başka bir örneğinin aynı sınıfta aynı üye bağımsızdır. Bir örnek üye değişkeni, örneğin, farklı durumlarda farklı değerleri olabilir.

Bildirilen üyeleri ile `Shared` anahtar sözcüğünü *üyeleri Paylaşılan*, bir bütün olarak sınıfı ve herhangi belirli bir örneğine ait. Paylaşılan üye sınıfının kaç tane ne olursa olsun, oluşturduktan sonra ya da hiçbir örneği oluşturmak olsa bile var. Paylaşılan üye değişkeni, örneğin, sınıf erişebilen tüm kod için kullanılabilir olan yalnızca bir değer var.

#### <a name="accessing-nonshared-members"></a>Paylaşılmayan üyelerine erişme

##### <a name="to-access-a-nonshared-member-of-an-object"></a>Bir nesnenin paylaşılmayan bir üyesine erişmek için

1. Nesnenin kendi sınıfından oluşturulur ve bir nesne değişkenine atanan emin olun.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. Nesnenin değişken adıyla üye erişen deyiminde izleyin *üye erişim işleci* (`.`) ve ardından üye adı.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Paylaşılan üyelerine erişme

##### <a name="to-access-a-shared-member-of-an-object"></a>Bir nesnenin paylaşılan bir üyesine erişmek için

- Sınıf adını izleyin *üye erişim işleci* (`.`) ve ardından üye adı. Her zaman erişmeli bir `Shared` nesnenin sınıf adı aracılığıyla doğrudan üyesi.

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- Sınıfından bir nesne zaten oluşturduysanız, alternatif olarak erişebileceğiniz bir `Shared` üye nesne değişkeni aracılığıyla.

### <a name="differences-between-classes-and-modules"></a>Sınıflar ve modüller arasındaki farklar

Sınıflar ve modüller arasındaki temel fark, standart modüller işleyemez sınıfları nesneler olarak oluşturulabilir ' dir. Standart Modül içindeki genel bir değişken, programın bir parçası değiştiğinde verileri standart bir modülün, yalnızca bir kopyası olduğundan daha sonra bu değişkene okur, herhangi bir programın parçası aynı değerini alır. Buna karşılık, nesne verileri, her örneklenen bir nesne için ayrı olarak bulunmaktadır. Standart modüller, sınıflar arabirimleri uygulayabilir başka bir farktır.

> [!NOTE]
> Zaman `Shared` değiştiricisi bir sınıf üyesine uygulandığında, sınıfın kendisi yerine belirli bir sınıfın örneğini ile ilişkilidir. Üye sınıfı adı kullanarak doğrudan erişilir, aynı şekilde modülü üyeleri erişilir.

Sınıflar ve modüller de üyeleri için farklı kapsamlar kullanın. Bir sınıf içinde tanımlanmış üyeler içinde belirli bir sınıfın örneğini kapsamlı ve nesne ömrü boyunca yalnızca mevcut. Sınıf üyeleri sınıf dışındaki erişmek için tam olarak nitelenmiş adlar biçiminde kullanmalısınız *nesne*. *Üye*.

İçinde bir modül olarak bildirilen üyeler Öte yandan, varsayılan olarak genel olarak erişilebilir olduğundan emin olun ve modül erişebilen herhangi kod tarafından erişilebilir. Standart Modül içindeki değişkenler etkili bir şekilde genel değişkenler, projenizdeki herhangi bir yerde görünür olduklarını ve bunlar program süresince mevcut olduğu bu anlamına gelir.

## <a name="reusing-classes-and-objects"></a>Sınıfları ve nesneleri yeniden kullanma

Nesneler, değişkenler ve yordamlar bildirmek ve daha sonra gerektiğinde bunları yeniden olanak tanır. Örneğin, yazım denetleyicisi uygulama eklemek istiyorsanız, tüm değişkenleri tanımlayın ve yazım denetimi işlevselliği sağlamak için işlevleri destekler. Yazım sınıf olarak oluşturursanız, ardından onu diğer uygulamalarda derlenmiş derlemesine bir başvuru ekleyerek tekrar kullanabilirsiniz. Üstelik başka birisi zaten geliştirmiştir bir yazım denetleyicisi sınıfını kullanarak bazı iş kendiniz kaydetmek mümkün olabilir.

.NET Framework, pek çok kullanımı için uygun olan bileşenleri örnekleri sağlar. Aşağıdaki örnekte <xref:System.TimeZone> sınıfını <xref:System> ad alanı. <xref:System.TimeZone> Geçerli bilgisayar sisteminin saat dilimi hakkında bilgi almanıza olanak tanıyan üyeleri sağlar.

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

Yukarıdaki örnekte, ilk [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) türünde bir nesne değişkeni bildirir <xref:System.TimeZone> ve buna atayan bir <xref:System.TimeZone> tarafından döndürülen nesne <xref:System.TimeZone.CurrentTimeZone%2A> özelliği.

## <a name="relationships-among-objects"></a>Nesneleri arasındaki ilişki

Çeşitli yollarla nesneleri birbirleriyle ilişkilendirilebilir. İlişki asıl türde *hiyerarşik* ve *kapsama*.

### <a name="hierarchical-relationship"></a>Hiyerarşi ilişkisi

Daha fazla temel sınıftan türetilmiş sınıflar, bunlar olduğu söylenir ve bir *hiyerarşik ilişkiyi*. Sınıf Hiyerarşiler daha genel bir sınıf türünün bir alt öğeleri açıklayan yararlı olur.

Aşağıdaki örnekte, özel bir tür tanımlamak istediğiniz varsayalım <xref:System.Windows.Forms.Button> normal gibi davranır <xref:System.Windows.Forms.Button> ancak aynı zamanda ön ve arka plan renkleri tersine bir yöntemi gösterir.

#### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>Zaten varolan bir sınıftan türetildiği durumda olduğu bir sınıf tanımlamak için

1. Kullanım bir [Class deyimi](../../../../visual-basic/language-reference/statements/class-statement.md) , nesneyi oluşturmak için ihtiyacınız olan bir sınıf tanımlamak için.

   ```vb
   Public Class reversibleButton
   ```

   Mutlaka bir `End Class` deyimini sınıfınıza kodda son satırının izler. Varsayılan olarak, tümleşik geliştirme ortamı (IDE) otomatik olarak oluşturduğu bir `End Class` girdiğinizde bir `Class` deyimi.

2. İzleyin `Class` deyimiyle hemen bir [devralan deyimi](../../../../visual-basic/language-reference/statements/inherits-statement.md). Yeni sınıfınıza türetildiği sınıf belirtin.

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   Yeni sınıfınıza taban sınıfı tarafından tanımlanan tüm üyelerini devralır.

3. Kod, türetilmiş sınıf üzerinden kullanıma sunan ek üyelerini ekleyin. Örneğin, eklemiş olabileceğiniz bir `reverseColors` yöntemi ve türetilmiş sınıfınızın görünebilir gibi:

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

   Bir nesneden oluşturursanız `reversibleButton` sınıfı, bunu tüm üyelerine erişebilir <xref:System.Windows.Forms.Button> sınıfı, hem de `reverseColors` yöntemi ve tanımladığınız üzerinde diğer herhangi bir yeni üye `reversibleButton`.

Türetilen sınıfların üyeleri, siz ilerledikçe karmaşıklığı bir sınıf hiyerarşisi içinde eklemenize olanak sağlayan temel sınıfından devralır. Daha fazla bilgi için [devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

### <a name="compiling-the-code"></a>Kod derleme

Derleyici, yeni bir sınıf türetmek istediğinize sınıfı erişebildiğinden emin olun. Bu tam adı, önceki örnekte olduğu gibi uygun veya kendi ad alanında tanımlayan gelebilir bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Farklı bir projedeki sınıf ise bu projeye bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için [bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Kapsama ilişkisi

Nesnenin ilgili başka bir yolu ise bir *kapsama ilişkisi*. Kapsayıcı nesneleri, diğer nesnelerin mantıksal kapsüller. Örneğin, <xref:System.OperatingSystem> nesne mantıksal olarak içeren bir <xref:System.Version> aracılığıyla döndüren bir nesne kendi <xref:System.OperatingSystem.Version%2A> özelliği. Not kapsayıcı nesne fiziksel olarak herhangi bir nesne içermiyor.

#### <a name="collections"></a>Koleksiyonlar

Nesne kapsama belirli bir tür tarafından temsil edilen *koleksiyonları*. Numaralandırılabilir benzer nesne koleksiyonlarıdır. Visual Basic, belirli bir söz dizimi destekler [her biri için... Sonraki deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) bir koleksiyonun öğeleri yineleme yapmak sağlar. Ayrıca, koleksiyonlar çoğunlukla kullanmanıza olanak sağlayan bir <xref:Microsoft.VisualBasic.Collection.Item%2A> kendi dizini veya benzersiz bir dize ile ilişkilendirerek öğeleri almak için. Koleksiyonlar eklemek veya dizinleri kullanmadan öğeleri kaldırmak izin verdiğinden dizileri kullanmak daha kolay olabilir. Kendi kullanım kolaylığı nedeniyle, koleksiyonlar genellikle formlar ve denetimler depolamak için kullanılır.

## <a name="related-topics"></a>İlgili konular

[İzlenecek yol: Sınıfları tanımlama](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)\
Bir sınıf oluşturma adım adım bir açıklamasını sağlar.

[Aşırı yüklenmiş özellikler ve yöntemler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)\
Aşırı Yüklenmiş Özellikler ve Yöntemler

[Devralma temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)\
Devralma değiştiriciler, yöntemleri ve özellikleri ve MyClass MyBase geçersiz kılma kapsar.

[Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)\
Oluşturma ve sınıf örneklerini disposing açıklanır.

[Anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)\
Veri türü için bir sınıf tanımı yazmak zorunda kalmadan nesneleri oluşturmanızı sağlayan anonim türler oluşturup kullanacağınızı açıklar.

[Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)\
Tek bir ifade kullanarak adlandırılmış ve anonim türlerin örneklerini oluşturmak için kullanılan nesne başlatıcıları açıklanır.

[Nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)\
Özellik adları ve türleri anonim türde bildirimlerden çıkarma açıklanmaktadır. Başarılı ve başarısız çıkarımı örnekleri sağlar.

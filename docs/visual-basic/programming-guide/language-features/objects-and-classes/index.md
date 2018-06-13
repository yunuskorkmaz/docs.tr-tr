---
title: Nesneler ve sınıflar Visual Basic'te
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 2917a698f9aa7828c201a048f443f5941797c704
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655869"
---
# <a name="objects-and-classes-in-visual-basic"></a>Nesneler ve sınıflar Visual Basic'te
Bir *nesne* kod ve bir birim olarak kabul veri birleşimidir. Bir nesne bir denetim veya formun gibi bir uygulama bir parçası olabilir. Tüm uygulama aynı zamanda bir nesne olabilir.

Visual Basic'te bir uygulama oluşturduğunuzda, sürekli nesneleri ile çalışma. Visual Basic tarafından sağlanan gibi denetimleri, formlar ve veri erişim nesneleri nesnelerini kullanabilirsiniz. Visual Basic uygulamanızdaki diğer uygulamalardan nesne de kullanabilirsiniz. Hatta kendi nesneleri oluşturmak ve ek özellikleri ve yöntemleri kendileri için tanımlayın. Nesneleri hareket gibi prefabricated programlar için yapı taşları —, paylaştırılabilen bir kod kez yazma ve onu tekrar tekrar tekrar olanak tanır.  
  
Bu konuda nesneleri ayrıntılı ele alınmıştır.  

## <a name="objects-and-classes"></a>Nesneler ve sınıflar
Visual Basic'te her nesne tarafından tanımlanan bir *sınıfı*. Bir sınıf değişkenleri, özellikleri, yordamlar ve olayları bir nesnenin açıklar. Nesneleri sınıfların örnekleri olan; bir sınıf tanımladıktan sonra gereksinim duyduğunuz kadar çok nesneleri oluşturabilirsiniz.

Bir nesne ve kendi sınıfı arasındaki ilişkiyi anlamak için tanımlama bilgisi cutters ve tanımlama bilgileri düşünün. Tanımlama Bilgisi kesici sınıftır. Örneğin boyutu ve şekli her tanımlama bilgisi özelliklerini tanımlar. Sınıf nesneleri oluşturmak için kullanılır. Tanımlama bilgilerini nesneleridir.

Üyeleri erişebilmeniz için önce bir nesne oluşturmanız gerekir.  

#### <a name="to-create-an-object-from-a-class"></a>Bir nesne öğesinden bir sınıf oluşturmak için

1. Hangi sınıfından bir nesne oluşturmak istediğinize karar verin.  

2. Yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) bir sınıf örneği atamak bir değişken oluşturmak için. Değişkeni istenen sınıfı türünde olmalıdır.

   ```vb
   Dim nextCustomer As customer
   ```

3. Ekleme [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) sınıfının yeni bir örneğini değişkenine başlatmak için anahtar sözcüğü.

   ```vb
   Dim nextCustomer As New customer
   ```

4. Bu gibi durumlarda, sınıf üyeleri şimdi nesne değişkeni erişebilirsiniz.  

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1  
   ```

> [!NOTE]
>  Mümkün olduğunda, değişkenin kendisine atamak istiyorsanız sınıf türü olmasını bildirmeniz gerekir. Bu adlı *erken bağlama*. Derleme zamanında yazın sınıfı bilmiyorsanız, çağırabileceği *geç bağlama* olması için değişken bildirme tarafından [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md). Ancak, geç bağlama yavaş performans yapabilir ve çalışma zamanı nesnenin üyelerine erişimi sınırlamak. Daha fazla bilgi için bkz: [nesne değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).

### <a name="multiple-instances"></a>Birden çok örneği
Yeni bir sınıftan oluşturulan genellikle birbirinin nesneleridir. Bireysel nesne olarak mevcut sonra ancak bunların değişkenlerin ve özelliklerin bağımsız olarak diğer örnekleri değiştirilebilir. Üç onay kutularını bir forma eklerseniz, örneğin, her onay kutusu örneği nesnesidir <xref:System.Windows.Forms.CheckBox> sınıfı. Tek tek <xref:System.Windows.Forms.CheckBox> nesneleri özellikleri ve yetenekleri (özellikleri, değişkenleri, yordamlar ve olaylar) sınıf tarafından tanımlanan ortak bir dizi paylaşır. Ancak, her biri kendi adına sahip, ayrı olarak etkinleştirilebilir ve devre dışı bırakıldı ve form üzerinde farklı bir konumda yerleştirilebilir.

## <a name="object-members"></a>Nesne üyeleri
Bir nesne bir uygulamanın bir öğedir temsil eden bir *örneği* bir sınıf. Alanlar, özellikleri, yöntemleri ve olayları nesnelerin yapı taşlarıdır ve oluşturan kendi *üyeleri*.

### <a name="member-access"></a>Üye Erişimi
Sırayla nesne değişkeninin adını belirterek bir nesnenin bir üyeye erişme bir süre (`.`) ve üyenin adı. Aşağıdaki örnek kümeleri <xref:System.Windows.Forms.Control.Text%2A> özelliği bir <xref:System.Windows.Forms.Label> nesnesi.

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a>Üyeleri IntelliSense listesi
Bir süre yazdığınızda, örneğin kendi listesi üyeleri seçeneği çağırdığınızda, IntelliSense listeler bir sınıf üyeleri (`.`) olarak bir üye erişimi işleci. Ardından nokta bu sınıfının bir örneği bildirilen bir değişken adını yazarsanız, IntelliSense tüm örnek üyelerin ve paylaşılan üyeler hiçbiri listeler. Sınıf adı şu süre yazarsanız, IntelliSense paylaşılan tüm üyeleri ve hiçbir örnek üyesinin listeler. Daha fazla bilgi için bkz: [kullanarak IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="fields-and-properties"></a>Alanlar ve Özellikler
*Alanları* ve *özellikleri* bir nesnesinde depolanan bilgiler temsil eder. Alabilir ve değerlerine atama deyimleri ile almak ve bir yordamda yerel değişkenleri ayarlamak aynı şekilde ayarlayın. Aşağıdaki örnek alır <xref:System.Windows.Forms.Control.Width%2A> özelliği ve kümelerini <xref:System.Windows.Forms.Control.ForeColor%2A> özelliği bir <xref:System.Windows.Forms.Label> nesnesi.

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

Bir alan da adlandırılır Not bir *üye değişkeni*.
  
Özellik yordamları kullanın zaman:

- Ne zaman ve nasıl bir değer alınan ya da denetlemeniz gerekir.

- Doğrulanması gereken değerleri iyi tanımlanmış bir dizi özelliği vardır.

- Ayar değeri neden olan bazı algılanabilir değişiklik nesnenin durumda gibi bir `IsVisible` özelliği.

- Özellik ayarı değişiklikleri diğer iç değişkenler veya diğer özelliklerin değerlerine neden olur.

- Özelliği ayarlamak veya alınan önce adımlar gerçekleştirilmelidir.

Alanları kullanın:  

- Kendi kendine doğrulama türü değerdir. Örneğin, bir hata veya otomatik veri dönüştürme dışında bir değere saptanmışsa `True` veya `False` atanmış bir `Boolean` değişkeni.

- Veri türü tarafından desteklenen aralıkta herhangi bir değer geçerli değil. Bu tür birçok özelliği true ise `Single` veya `Double`.

- Özelliği bir `String` veri türü ve boyutunu veya dize değeri hiçbir kısıtlama yoktur.

- Daha fazla bilgi için bkz: [özellik yordamları](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).

### <a name="methods"></a>Yöntemler
A *yöntemi* bir nesne gerçekleştirebileceğiniz bir eylemdir. Örneğin, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> bir yöntemi <xref:System.Windows.Forms.ComboBox> açılan kutuya yeni bir giriş eklemeden nesnesi.

Aşağıdaki örnekte gösterilmiştir <xref:System.Windows.Forms.Timer.Start%2A> yöntemi bir <xref:System.Windows.Forms.Timer> nesnesi.

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

Bir yöntem yalnızca olduğuna dikkat edin bir *yordam* bir nesne tarafından gösterilir.

Daha fazla bilgi için bkz: [yordamları](../../../../visual-basic/programming-guide/language-features/procedures/index.md).

### <a name="events"></a>Olaylar
Olaya yanıt vermesi için kod yazabilirsiniz ve fareyi tıklatarak veya bir tuşa basılması gibi bir nesne tarafından tanınan bir eylemdir. Olayları bir kullanıcı eylemi veya program kodunun sonucu olarak ortaya çıkabilir veya sistem tarafından kaynaklanabilir. Bir olay sinyalleri kod söyledi *yükseltmek* olay ve buna yanıt söyledi kodu *işlemek* onu.

Nesneleri tarafından oluşturulur ve diğer nesneleri tarafından işlenen için kendi özel olaylar da geliştirebilirsiniz. Daha fazla bilgi için bkz: [olayları](../../../../visual-basic/programming-guide/language-features/events/index.md).

### <a name="instance-members-and-shared-members"></a>Örnek üyelerin ve paylaşılan üyeler
Bir sınıftan bir nesneyi oluşturduğunuzda, bu sınıfın örneğini sonucudur. İle bildirilmemiş üyeleri [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) bir anahtar sözcüktür *örnek üyeleri*, ait oldukları kesinlikle için belirli Bu örneği. Örnek üyesine bir örneği aynı sınıfın başka bir örneği aynı üye bağımsızdır. Bir örnek üye değişkeni Örneğin, farklı durumlarda farklı değerlere sahip olabilir.

Üyeleri olarak bildirilen ile `Shared` bir anahtar sözcüktür *üyeleri Paylaşılan*, belirli bir örneği değil de, bir bütün olarak sınıfına ait. Paylaşılan bir üyeye kaç sınıfın örnekleri, kendi olsun, oluşturduktan sonra ya da hiçbir örnekleri oluşturmak olsa bile bulunmaktadır. Paylaşılan üye değişkeni, örneğin, sınıf erişebilen tüm kod için kullanılabilir olan tek bir değer vardır.

#### <a name="accessing-nonshared-members"></a>Paylaşılmayan üyelere erişme  

###### <a name="to-access-a-nonshared-member-of-an-object"></a>Paylaşılmayan bir nesne üyesi erişmek için

1. Nesne kendi sınıfından oluşturulur ve bir nesne değişkenine atanan emin olun.

   ```vb
   Dim secondForm As New System.Windows.Forms.Form  
   ```  

2. Nesne değişken adında üye erişen deyiminde izleyin *üye erişimi işleci* (`.`) ve sonra üye adı.

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a>Paylaşılan üyelere erişme

###### <a name="to-access-a-shared-member-of-an-object"></a>Paylaşılan bir nesne üyesi erişmek için

- Sınıf adıyla izleyin *üye erişimi işleci* (`.`) ve sonra üye adı. Her zaman erişim bir `Shared` nesnesinin sınıf adı aracılığıyla doğrudan üyesi.

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)  
   ```

- Sınıfından bir nesne zaten oluşturduysanız, alternatif olarak erişebileceğiniz bir `Shared` nesne değişkeni aracılığıyla üye.

### <a name="differences-between-classes-and-modules"></a>Sınıfları ve modülleri arasındaki farklar
Sınıfları ve modülleri arasındaki temel fark, standart modüller işleyemez sınıfları nesneler olarak oluşturulabilir ' dir. Programınızı bir bölümünü standart modül ortak bir değişkende değiştiğinde standart modülünün verilerin yalnızca bir kopya olduğundan daha sonra bu değişkeni okur varsa herhangi bir programın parçası aynı değeri alır. Buna karşılık, nesne verileri başlatılan her nesne için ayrı olarak bulunmaktadır. Standart modüller, sınıflar arabirimleri uygulayabilir başka bir farktır.

> [!NOTE]
> Zaman `Shared` değiştiricisi sınıf üyesi uygulandığında, sınıfın kendisi yerine belirli bir sınıfın örneği ile ilişkilidir. Üye doğrudan sınıf adı kullanılarak erişilir, aynı şekilde modülü üyeleri erişilir.

Sınıfları ve modüller de üyeleri için farklı kapsamlar kullanır. Üyeleri bir sınıf içinde tanımlanan belirli bir sınıfın örneği içinde kapsamlı ve yalnızca nesne yaşam süresi için mevcut. Sınıf dışındaki sınıfı üyelerinden erişmek için tam olarak nitelenmiş adlar biçiminde kullanmalısınız *nesne*. *Üye*.

Öte yandan, bir modül içinde bildirilen üyeleri varsayılan olarak genel olarak erişilebilir ve modülü erişmek için herhangi bir kod erişilebilir. Standart modülde değişkenleri etkili bir şekilde genel değişkenler herhangi bir yere projenizde görünür olduğundan ve program ömrü için var olan anlamına gelir.

## <a name="reusing-classes-and-objects"></a>Sınıfları ve nesneleri yeniden kullanma  
Nesneleri, değişken ve yordamların bir kez bildirme ve bunları gerektiğinde yeniden olanak tanır. Örneğin, yazım denetleyicisi uygulama eklemek istiyorsanız, tüm değişkenleri tanımlayın ve yazım denetimi işlevselliği sağlamak için işlevleri destekler. Yazım bir sınıf olarak oluşturursanız, daha sonra onu diğer uygulamalarda derlenmiş derlemesine başvuru ekleyerek tekrar kullanabilirsiniz. Daha iyi henüz başka birisi zaten geliştirmiştir yazım sınıfını kullanarak kendiniz bazı iş kaydetmek mümkün olabilir.

[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Kullanılabilir bileşenleri birçok örnekler sağlar. Aşağıdaki örnek kullanır <xref:System.TimeZone> sınıfını <xref:System> ad alanı. <xref:System.TimeZone> Geçerli bilgisayar sistemi saat dilimi hakkında bilgi almaya izin üyeleri sağlar.

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

Önceki örnekte, ilk [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) türünde bir nesne değişkeni bildirir <xref:System.TimeZone> ve atar bir <xref:System.TimeZone> tarafından döndürülen nesne <xref:System.TimeZone.CurrentTimeZone%2A> özelliği.

## <a name="relationships-among-objects"></a>Nesneleri arasındaki ilişki  
Nesneler birbirine çeşitli yollarla ilişkilendirilebilir. İlişkinin asıl türleridir *hiyerarşik* ve *kapsama*.

### <a name="hierarchical-relationship"></a>Hiyerarşik bir ilişki
Daha fazla temel sınıflarından türetilmiş sınıfları, bunlar sahip söylenir bir *hiyerarşik bir ilişki*. Sınıf hiyerarşileri daha genel bir sınıfın alt öğeleri açıklayan yararlı olur.

Aşağıdaki örnekte, bir özel tür tanımlamak istediğiniz varsayalım <xref:System.Windows.Forms.Button> normal gibi davranır <xref:System.Windows.Forms.Button> ancak aynı zamanda ön ve arka plan renkleri ters çevirir bir yöntemi gösterir.

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a>Bir sınıf tanımlama zaten varolan bir sınıftan türetilen

1. Kullanım bir [Class deyimi](../../../../visual-basic/language-reference/statements/class-statement.md) , nesneyi oluşturmak için gereksinim duyduğunuz bir sınıf tanımlamak için.

   ```vb
   Public Class reversibleButton
   ```

   Mutlaka bir `End Class` deyimi sınıfınızda kodu son satırının izler. Varsayılan olarak, tümleşik geliştirme ortamı (IDE) otomatik olarak oluşturan bir `End Class` girdiğinizde bir `Class` deyimi.

2. İzleyin `Class` deyimiyle hemen bir [Inherits deyimi](../../../../visual-basic/language-reference/statements/inherits-statement.md). Yeni sınıfınıza türetilen sınıf belirtin.  
  
   ```vb
   Inherits System.Windows.Forms.Button
   ```

  Yeni sınıfınıza temel sınıf tarafından tanımlanan tüm üyeleri devralır.

3. Kodu ek üyeler için türetilmiş sınıf çıkarır ekleyin. Örneğin, eklemiş olabileceğiniz bir `reverseColors` yöntemi ve türetilmiş sınıf görünebilir gibi:

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

   Bir nesneden oluşturursanız `reversibleButton` sınıfı, tüm üyeleri erişebilir <xref:System.Windows.Forms.Button> sınıfı, yanı sıra `reverseColors` yöntemi ve tanımladığınız üzerindeki diğer yeni üyeler `reversibleButton`.

Türetilen sınıflar, ilerledikçe karmaşıklık sınıf hiyerarşisinde eklemenize olanak sağlayan temel sınıfı üyeleri devralınmalıdır. Daha fazla bilgi için bkz: [devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

#### <a name="compiling-the-code"></a>Kod derleme
Derleyici, yeni bir sınıf türetin istediğiniz sınıfı erişebildiğinden emin olun. Bu tam adı, önceki örnekte olduğu gibi niteleme veya kendi ad alanında tanımlayan anlamına gelebilir bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Sınıf farklı projesiyse, bu proje bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için bkz: [bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project).

### <a name="containment-relationship"></a>Kapsama ilişkisi
Nesneleri ilgili başka bir yolu bir *kapsama ilişkisi*. Kapsayıcı nesneleri diğer nesnelerin mantıksal olarak kapsüller. Örneğin, <xref:System.OperatingSystem> nesnesini mantıksal olarak içeren bir <xref:System.Version> aracılığıyla döndürür nesne, kendi <xref:System.OperatingSystem.Version%2A> özelliği. Kapsayıcı nesne fiziksel olarak başka bir nesneyi içermiyor unutmayın.

#### <a name="collections"></a>Koleksiyonlar
Belirli bir nesne kapsama türü ile temsil edilir *koleksiyonları*. Koleksiyonları sıralanabilecek nesneleri gruplarıdır. Visual Basic destekler içindeki belirli bir sözdizimi [For Each... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) koleksiyonu öğeler arasında yinelemek izin verir. Ayrıca, koleksiyonlar çoğunlukla kullanmanıza olanak sağlayan bir <xref:Microsoft.VisualBasic.Collection.Item%2A> kendi dizini veya benzersiz bir dize ile ilişkilendirerek öğeleri alınamadı. Koleksiyonlar eklemek veya dizinleri kullanmadan öğeleri kaldırmak izin verdiğinden diziler kullanmak daha kolay olabilir. Bunların kullanım kolaylığı nedeniyle, koleksiyonlar çoğunlukla formlar ve denetimler depolamak için kullanılır.

## <a name="related-topics"></a>İlgili konular  
 [İzlenecek Yol: Sınıfları Tanımlama](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Bir sınıfın nasıl oluşturulacağı hakkında adım adım bir açıklaması verilmiştir.  

 [Aşırı Yüklenmiş Özellikler ve Yöntemler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 Aşırı Yüklenmiş Özellikler ve Yöntemler  

 [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 Devralma değiştiriciler, yöntemleri ve özellikleri, MyClass ve MyBase geçersiz kılma kapsar.  

 [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 Oluşturma ve sınıf örneklerini atma açıklanır.  

 [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 Oluşturma ve veri türü için bir sınıf tanımı yazmadan nesneleri oluşturmanıza izin anonim türler kullanma açıklar.  

 [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 Tek bir ifade kullanarak adlandırılmış ve anonim türler örneklerini oluşturmak için kullanılan nesne başlatıcıları açıklanır.  

 [Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 Özellik adlarını ve türlerini anonim türde bildirimlerden çıkarma açıklanmaktadır. Başarılı ve başarısız çıkarım örnekleri sağlar.

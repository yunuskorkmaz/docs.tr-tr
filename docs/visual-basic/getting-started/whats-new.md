---
title: Visual Basic yenilikler
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: 2798c436ddfabc8fedf1f2c36c25e8ee2651b476
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191987"
---
# <a name="whats-new-for-visual-basic"></a>Visual Basic yenilikler

Bu konu, dilin en son sürümlerindeki yeni ve geliştirilmiş özelliklerin ayrıntılı açıklamaları ile her bir Visual Basic sürümü için temel özellik adlarını listeler.

## <a name="current-version"></a>Güncel sürüm

Visual Basic 16,0/Visual Studio 2019 sürüm 16,0 \
Yeni özellikler için bkz. [Visual Basic 16,0](#visual-basic-160).

## <a name="previous-versions"></a>Önceki sürümler

Visual Basic 15,8/Visual Studio 2017 sürüm 15,8 \
Yeni özellikler için bkz. [Visual Basic 15,8](#visual-basic-158).

Visual Basic 15,5/Visual Studio 2017 sürüm 15,5 \
Yeni özellikler için bkz. [Visual Basic 15,5](#visual-basic-155).

Visual Basic 15,3/Visual Studio 2017 sürüm 15,3 \
Yeni özellikler için bkz. [Visual Basic 15,3](#visual-basic-153).

Visual Basic 2017/Visual Studio 2017 \
Yeni özellikler için bkz. [Visual Basic 2017](#visual-basic-2017).

Visual Basic/Visual Studio 2015 \
Yeni özellikler için bkz. [Visual Basic 14](#visual-basic-14).

Visual Basic/Visual Studio 2013 \
.NET Compiler Platform teknoloji önizlemeleri ("Roslyn")

Visual Basic/Visual Studio 2012 \
`Async` ve `await` anahtar sözcükleri, yineleyiciler, çağıran bilgi öznitelikleri

Visual Basic, Visual Studio 2010 \
Otomatik uygulanan özellikler, koleksiyon başlatıcıları, örtük satır devamlılığı, dinamik, genel ortak/Contra varyansı, genel ad alanı erişimi

Visual Basic/Visual Studio 2008 \
Dil ile tümleşik sorgu (LINQ), XML değişmez değerleri, yerel tür çıkarımı, nesne başlatıcıları, anonim türler, uzantı yöntemleri, yerel `var` tür çıkarımı, lambda ifadeleri, `if` işleci, kısmi Yöntemler, null yapılabilir değer türleri

Visual Basic/Visual Studio 2005 \
`My` türü ve yardımcı türleri (uygulama, bilgisayar, dosya sistemi ve ağa erişim)

Visual Basic/Visual Studio .NET 2003 \
Bit kaydırma işleçleri, döngü değişkeni bildirimi

Visual Basic/Visual Studio .NET 2002 \
Visual Basic .NET ilk sürümü

## <a name="visual-basic-160"></a>Visual Basic 16,0

Visual Basic 16,0, .NET Core 'a Visual Basic çalışma zamanının (Microsoft. VisualBasic. dll) özelliklerinin daha fazlasını sağlamaya odaklanır ve Visual Basic .NET Core 'a odaklanmış ilk sürümüdür. Visual Basic çalışma zamanının pek çok bölümü WinForms bağımlıdır ve bu, Visual Basic daha sonraki bir sürümüne eklenecektir.

**Deyimler içinde daha fazla yerde izin verilen açıklamalar**

Visual Basic 15,8 ve önceki sürümlerde, açıklamalara yalnızca boş satırlarda, bir deyimin sonunda veya örtük bir satır devamlılığı bulunan bir bildirimde belirli yerlerde izin verilir. Visual Basic 16,0 ' den başlayarak, açık satır devamlılıkları ve bir alt çizgi ile başlayan bir satırdaki bir deyimin içinde açıklamalara de izin verilir.

```vb
Public Sub Main()
    cmd.CommandText = ' Comment is allowed here without _
        "SELECT * FROM Titles JOIN Publishers " _ ' This is a comment
        & "ON Publishers.PubId = Titles.PubID " _
 _ ' This is a comment on a line without code
        & "WHERE Publishers.State = 'CA'"
End Sub
```

## <a name="visual-basic-158"></a>Visual Basic 15,8

**En iyileştirilmiş kayan noktalı tamsayı dönüştürme**

Visual Basic önceki sürümlerinde, [çift](../language-reference/data-types/double-data-type.md) ve [tek](../language-reference/data-types/single-data-type.md) değerlerin tamsayılara, görece düşük performansa göre dönüştürülmesi gerekir. Visual Basic 15,8, aşağıdaki yöntemlerden herhangi biri tarafından döndürülen değeri [iç Visual Basic tamsayı dönüştürme işlevlerinden](../language-reference/functions/type-conversion-functions.md) birine geçirdiğinizde (CByte, CShort, CInt,) kayan nokta dönüştürmelerinden oluşan performansı önemli ölçüde artırır. CLng, CSByte, CUShort, CUInt, Külng) ya da aşağıdaki yöntemlerin herhangi biri tarafından döndürülen değer, [kesin seçenek](../language-reference/statements/option-strict-statement.md) `Off` olarak ayarlandığında tam sayı türüne dolaylı olarak dönüştürülebilir:

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Bu iyileştirme kodun çok daha hızlı bir şekilde çalışmasını sağlar ve tamsayı türlerine çok sayıda dönüştürme yapan kod için hızlı bir şekilde daha hızlı çalışır. Aşağıdaki örnek, bu iyileştirmeden etkilenen bazı basit yöntem çağrılarını göstermektedir:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

Bu, kayan nokta değerlerini yuvarlar değil, bu fazlağa göz atar.

## <a name="visual-basic-155"></a>Visual Basic 15,5

[Girintili olmayan adlandırılmış bağımsız değişkenler](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

Visual Basic 15,3 ve önceki sürümlerde, bir yöntem bağımsız değişkenleri yalnızca konuma ve ada göre çağırarak, Konumsal bağımsız değişkenlerin adlandırılmış bağımsız değişkenlerden önce gelmesi gerekiyordu. Visual Basic 15,5 ' den başlayarak, son Konumsal bağımsız değişkene kadar olan tüm bağımsız değişkenler doğru konumda olduğu sürece konumsal ve adlandırılmış bağımsız değişkenler herhangi bir sırada görünebilir. Bu özellikle, kodu daha okunabilir hale getirmek için adlandırılmış bağımsız değişkenler kullanıldığında yararlıdır.

Örneğin, aşağıdaki yöntem çağrısının adlandırılmış bir bağımsız değişken arasında iki Konumsal bağımsız değişkeni vardır. Adlandırılmış bağımsız değişken, 19 değerinin bir yaşı temsil ettiğini açık hale getirir.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected` üye erişim değiştiricisi](../language-reference/modifiers/private-protected.md)

Bu yeni anahtar sözcük birleşimi, kapsayan sınıf içindeki tüm üyeler tarafından erişilebilen bir üyeyi ve kapsayan sınıftan türetilmiş türleri, ancak yalnızca kapsayan derlemede bulunduklarında tanımlar. Yapılar devralınamadığı için `Private Protected` yalnızca bir sınıfın üyelerine uygulanabilir.

**Baştaki onaltılık/ikili/sekizlik ayırıcı**

Visual Basic 2017 alt çizgi karakteri (`_`) için bir rakam ayırıcısı olarak destek ekledi. Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ön ek ve onaltılık, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak kullanabilirsiniz. Aşağıdaki örnek, 3.271.948.384 onaltılık bir sayı olarak tanımlamak için önde gelen bir rakam ayırıcısı kullanır:

```vb
Dim number As Integer = &H_C305_F860
```

Alt çizgi karakterini baştaki ayırıcı olarak kullanmak için, Visual Basic projesi (\*. vbproj) dosyanıza aşağıdaki öğeyi eklemeniz gerekir:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15,3

[**Adlandırılmış demet çıkarımı**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Kayıt düzeni öğelerinin değerini değişkenlerden atadığınızda, Visual Basic demet öğelerinin adını karşılık gelen değişken adlarından anlar. bir demet öğesini açıkça adlandırmak zorunda değilsiniz. Aşağıdaki örnek, üç adlandırılmış öğe, `state`, `stateName` ve `capital` içeren bir tanımlama grubu oluşturmak için çıkarımı kullanır.

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Ek derleyici anahtarları**

Visual Basic komut satırı derleyicisi artık başvuru derlemelerinin çıkışını denetlemek için [ **-refout**](../reference/command-line-compiler/refout-compiler-option.md) ve [ **-refonly**](../reference/command-line-compiler/refonly-compiler-option.md) derleyici seçeneklerini desteklemektedir. **-refout** , başvuru derlemesinin çıkış dizinini tanımlar ve **-refonly** yalnızca bir başvuru derlemesinin derleme tarafından çıkış olduğunu belirtir.

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Diziler**](../programming-guide/language-features/data-types/tuples.md)

Tanımlama grupları, en yaygın olarak tek bir yöntem çağrısından birden çok değer döndürmek için kullanılan hafif bir veri yapısıdır. Genellikle, bir yöntemden birden çok değer döndürmek için aşağıdakilerden birini yapmanız gerekir:

- Özel bir tür (`Class` veya `Structure`) tanımlayın. Bu, ağır bir çözümdür.

- Yönteminden bir değer döndürmenin yanı sıra bir veya daha fazla `ByRef` parametresi tanımlayın.

Visual Basic, tanımlama gruplarını hızlıca tanımlamanızı, isteğe bağlı olarak anlam adlarını kendi değerlerine atamanızı ve değerlerini hızlıca almanızı sağlar. Aşağıdaki örnek, <xref:System.Int32.TryParse%2A> yöntemine yapılan çağrıyı sarmalanmış ve bir tanımlama grubu döndürüyor.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Daha sonra yöntemi çağırabilir ve döndürülen kayıt grubunu aşağıdaki gibi kodla işleyebilirsiniz.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**İkili sabit değerler ve basamak ayırıcıları**

`&B` veya `&b`önekini kullanarak bir ikili sabit değeri tanımlayabilirsiniz. Ayrıca, okunabilirliği iyileştirmek için `_`alt çizgi karakterini bir rakam ayırıcısı olarak kullanabilirsiniz. Aşağıdaki örnek her iki özelliği de bir `Byte` değeri atamak ve bunu bir Decimal, onaltılı ve ikili sayı olarak göstermek için kullanır.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Daha fazla bilgi için [byte](../language-reference/data-types/byte-data-type.md#literal-assignments), [Integer](../language-reference/data-types/integer-data-type.md#literal-assignments), [Long](../language-reference/data-types/long-data-type.md#literal-assignments), [Short](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [UInteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ulong](../language-reference/data-types/ulong-data-type.md#literal-assignments)ve [ushort](../language-reference/data-types/ushort-data-type.md#literal-assignments) veri türlerindeki "değişmez değer atamaları" bölümüne bakın.

[**Başvuru dönüş C# değerleri için destek**](../programming-guide/language-features/procedures/ref-return-values.md)

7,0 ile C# başlayarak, C# başvuru dönüş değerlerini destekler. Diğer bir deyişle, çağırma yöntemi başvuruya göre döndürülen bir değer aldığında, başvurunun değerini değiştirebilir. Visual Basic, başvuru dönüş değerleri olan Yöntemler yazmanıza izin vermez, ancak başvuru dönüş değerlerini kullanmanıza ve değiştirmenize izin verir.

Örneğin, içinde C# yazılan aşağıdaki `Sentence` sınıfı, belirtilen bir alt dizeyle başlayan bir tümcedeki sonraki sözcüğü bulan bir `FindNext` yöntemi içerir. Dize bir başvuru dönüş değeri olarak döndürülür ve yöntemine başvuruya göre geçirilen bir `Boolean` değişkeni, aramanın başarılı olup olmadığını gösterir. Bu, arayanın yalnızca döndürülen değeri okuyamayacağı anlamına gelir; aynı zamanda değiştirebilir ve bu değişiklik `Sentence` sınıfında yansıtılır.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

En basit biçimde, aşağıdaki gibi bir kod kullanarak tümcede bulunan kelimeyi değiştirebilirsiniz. Yöntemine bir değer atamayabileceğinizi, ancak yöntemin döndürdüğü ifadeye bunun yerine, başvuru dönüş değeri olduğunu unutmayın.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Bu kodla ilgili bir sorun olsa da, bir eşleşme bulunmazsa yöntemin ilk sözcüğü döndürmesinin nedeni budur. Örnek, bir eşleşmenin bulunup bulunmadığını anlamak için `Boolean` bağımsız değişkeninin değerini incelemediğinden, eşleşme yoksa ilk sözcüğü değiştirir. Aşağıdaki örnek, eşleşme yoksa ilk sözcüğü kendisiyle değiştirerek bunu düzeltir.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Daha iyi bir çözüm, başvuru dönüş değerinin başvuruya göre geçirildiği bir yardımcı yöntem kullanmaktır. Yardımcı yöntemi daha sonra başvuruya göre kendisine geçirilen bağımsız değişkeni değiştirebilir. Aşağıdaki örnek bunu yapar.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Daha fazla bilgi için bkz. [Başvuru dönüş değerleri](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[NameOf](../language-reference/operators/nameof.md)

Bir hata iletisinde kullanılmak üzere bir tür veya üyenin Nitelenmemiş dize adını bir dizeyi sabit kodlamadan alabilirsiniz.  Bu, yeniden düzenleme sırasında kodunuzun doğru kalmasını sağlar.  Bu özellik ayrıca Model-View-Controller MVC bağlantıları ve tetikleme özelliği değiştirilen olaylarını aramak için de kullanışlıdır.

[Dize ilişkilendirme](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)

Dizeler oluşturmak için dize ilişkilendirme ifadeleri kullanabilirsiniz.  Enterpolasyonlu bir dize ifadesi ifade içeren bir şablon dizesi gibi görünür.  Enterpolasyonlu bir dizenin, [bileşik biçimlendirmeye](../../standard/base-types/composite-format.md)göre bağımsız değişkenlere göre anlaşılması daha kolay.

[Null koşullu üye erişimi ve dizin oluşturma](../language-reference/operators/null-conditional-operators.md)

Üye erişimi (`?.`) veya dizin (`?[]`) işlemini gerçekleştirmeden önce çok hafif bir şekilde null için test edebilirsiniz.  Bu işleçler, özellikle veri yapılarına göre azalan şekilde null denetimleri işlemek için daha az kod yazmanıza yardımcı olur.  Sol işlenen veya nesne başvurusu null ise, işlemler null döndürür.

[Çok satırlı dize sabit değerleri](../../visual-basic/programming-guide/language-features/strings/string-basics.md)

Dize sabit değerleri, yeni satır dizileri içerebilir.  Artık `<xml><![CDATA[...text with newlines...]]></xml>.Value` kullanmanın eski çalışmaına ihtiyacınız yoktur

**Açıklamalar**

Örtük satır devamlılıkları, başlatıcı ifadeleri içinde ve LINQ ifade terimleri arasında açıklama koyabilirsiniz.

**Daha akıllı tam ad çözümlemesi**

"Threading" ad alanını aramak için kullanılan Visual Basic `Threading.Thread.Sleep(1000)` gibi bilinen kod, System. Threading ve System. Windows. Threading arasında belirsizliğe sahip olup bir hata bildirin.  Visual Basic artık olası ad alanlarını birlikte kabul eder.  Tamamlanma listesini gösterdiğinizde, Visual Studio Düzenleyicisi tamamlama listesindeki her iki türden üyeleri listeler.

**Yıl-ilk tarih sabit değerleri**

Tarih sabit değerlerini YYYY-AA-GG biçiminde (`#2015-03-17 16:10 PM#`) kullanabilirsiniz.

**ReadOnly arabirim özellikleri**

Salt okunur Arabirim özelliklerini bir ReadWrite özelliğini kullanarak uygulayabilirsiniz. Arabirim minimum işlevselliği garanti eder ve bir uygulama sınıfının ayarlanmasının izin vermesini durdurmaz.

[TypeOf \<expr > IsNot \<type >](../../visual-basic/language-reference/operators/typeof-operator.md)

Kodunuzun daha okunaklı olması için artık `IsNot` `TypeOf` kullanabilirsiniz.

[#Disable uyarı \<ID > ve #Enable uyarı \<ID >](../../visual-basic/language-reference/directives/index.md)

Kaynak dosya içindeki bölgeler için belirli uyarıları devre dışı bırakabilir ve etkinleştirebilirsiniz.

**XML belgesi açıklaması geliştirmeleri**

Belge açıklamalarını yazarken, akıllı Düzenleyici ve parametre adlarını doğrulama, `crefs` (genel türler, işleçler, vb.), renklendirme ve yeniden düzenleme işlemleri için derleme desteği alırsınız.

[Kısmi modül ve arabirim tanımları](../../visual-basic/language-reference/modifiers/partial.md)

Sınıfların ve yapıların yanı sıra, kısmi modüller ve arabirimler bildirebilirsiniz.

[Yöntem gövdeleri içinde #Region yönergeleri](../../visual-basic/language-reference/directives/region-directive.md)

#Region... #End bölge sınırlayıcılarını bir dosyada, işlevlerin içine, hatta işlev gövdelerine yayılan bir yere koyabilirsiniz.

[Geçersiz kılmalar tanımları örtük aşırı yüklemelerdir](../../visual-basic/language-reference/modifiers/overrides.md)

`Overrides` değiştiricisini bir tanıma eklerseniz, derleyici ortak durumlarda daha az kod yazabileceğiniz şekilde `Overloads` dolaylı olarak ekler.

**Öznitelikler bağımsız değişkenlerinde CObj 'a izin verilir**

Derleyici, kurulumlarını özniteliğinde kullanıldığında CObj (...) öğesinin sabit olmadığı bir hata vermek için kullanılır.

**Farklı arabirimlerde belirsiz Yöntemler bildirme ve kullanma**

Daha önce aşağıdaki kod, `IMock` veya çağırma `GetDetails` (bunlar ' de C#bildirilmişse) bildirmesinin önlendiğine yönelik hatalara sahiptir:

```vb
Interface ICustomer
  Sub GetDetails(x As Integer)
End Interface

Interface ITime
  Sub GetDetails(x As String)
End Interface

Interface IMock : Inherits ICustomer, ITime
  Overloads Sub GetDetails(x As Char)
End Interface

Interface IMock2 : Inherits ICustomer, ITime
End Interface
```

Artık derleyici, çağrı yapılacak en uygun `GetDetails` seçmek için normal aşırı yükleme çözümleme kurallarını kullanacaktır ve örnekte gösterilenler gibi Visual Basic arabirim ilişkilerini bildirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017 ' deki yenilikler](/visualstudio/ide/whats-new-visual-studio-2017)

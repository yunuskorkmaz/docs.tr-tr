---
title: Visual Basic için yenilikler
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: 3ab468f6c68429a3a5cb8706152288afae520df3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187136"
---
# <a name="whats-new-for-visual-basic"></a>Visual Basic için yenilikler

Bu konu, Visual Basic'in her sürümü için anahtar özellik adlarını listeler ve dilin en son sürümlerindeki yeni ve geliştirilmiş özelliklerin ayrıntılı açıklamalarını listeler.

## <a name="current-version"></a>Geçerli sürüm

Visual Basic 16.0 / Visual Studio 2019 sürüm 16.0\
Yeni özellikler için [Visual Basic 16.0'a](#visual-basic-160)bakın.

## <a name="previous-versions"></a>Önceki sürümler

Visual Basic 15.8 / Visual Studio 2017 sürüm 15.8\
Yeni özellikler için [Visual Basic 15.8'e](#visual-basic-158)bakın.

Visual Basic 15.5 / Visual Studio 2017 sürüm 15.5\
Yeni özellikler için [Visual Basic 15.5'e](#visual-basic-155)bakın.

Visual Basic 15.3 / Visual Studio 2017 sürüm 15.3\
Yeni özellikler için [Visual Basic 15.3'e](#visual-basic-153)bakın.

Visual Basic 2017 / Visual Studio 2017\
Yeni özellikler için [Visual Basic 2017'ye](#visual-basic-2017)bakın.

Visual Basic / Visual Studio 2015\
Yeni özellikler için [Visual Basic 14'e](#visual-basic-14)bakın.

Visual Basic / Visual Studio 2013\
.NET Derleyici Platformu'nun teknoloji önizlemeleri ("Roslyn")

Visual Basic / Visual Studio 2012\
`Async`ve `await` anahtar kelimeler, yineleyiciler, arayan bilgi öznitelikleri

Visual Basic, Visual Studio 2010\
Otomatik olarak uygulanan özellikler, koleksiyon başlatıcıları, örtük çizgi devamı, dinamik, genel co/kontra varyans, genel ad alanı erişimi

Visual Basic / Visual Studio 2008\
Dil Tümleşik Sorgu (LINQ), XML literals, yerel tür çıkarım, nesne `var` başlatma, anonim türleri, uzantı `if` yöntemleri, yerel tür çıkarım, lambda ifadeler, operatör, kısmi yöntemler, nullable değer türleri

Visual Basic / Visual Studio 2005\
Tür `My` ve yardımcı türleri (uygulamaya, bilgisayara, dosya sistemine, ağa erişim)

Visual Basic / Visual Studio .NET 2003\
Bit kaydırma işleçleri, döngü değişken bildirimi

Visual Basic / Visual Studio .NET 2002\
Visual Basic .NET'in ilk sürümü

## <a name="visual-basic-160"></a>Görsel Temel 16.0

Visual Basic 16.0, .NET Core'a Visual Basic Runtime (microsoft.visualbasic.dll) özelliklerinin daha fazlasını sağlamaya odaklanır ve Visual Basic'in .NET Core'a odaklanan ilk sürümüdür. Visual Basic Runtime'ın birçok bölümü WinForms'a bağlıdır ve bunlar Visual Basic'in sonraki bir sürümüne eklenir.

**Açıklamalar içinde daha fazla yerde izin verilen yorumlar**

Visual Basic 15.8 ve önceki sürümlerinde, yorumlara yalnızca boş satırlarda, deyimin sonunda veya örtülü satır devamına izin verilen bir deyim içinde belirli yerlerde izin verilir. Visual Basic 16.0 ile başlayarak, açık satır devamlarından sonra ve bir alt çizgi ile başlayan bir satırda bir deyim içinde yorumlara da izin verilir.

```vb
Public Sub Main()
    cmd.CommandText = ' Comment is allowed here without _
        "SELECT * FROM Titles JOIN Publishers " _ ' This is a comment
        & "ON Publishers.PubId = Titles.PubID " _
 _ ' This is a comment on a line without code
        & "WHERE Publishers.State = 'CA'"
End Sub
```

## <a name="visual-basic-158"></a>Görsel Temel 15.8

**En iyi leştirilmiş kayan nokta ile tümer dönüştürme**

Visual Basic'in önceki sürümlerinde, [Çift](../language-reference/data-types/double-data-type.md) ve [Tek](../language-reference/data-types/single-data-type.md) değerlerin integer'lara dönüştürülmesi nispeten düşük performans sunar. Visual Basic 15.8, aşağıdaki yöntemlerden herhangi biri tarafından döndürülen değeri [içsel Visual Basic integer dönüşüm işlevlerinden](../language-reference/functions/type-conversion-functions.md) birine (CByte, CShort, CInt, CLng, CSByte, CUShort, CUInt, CUShort, CUInt, CULng) aktardığınızda veya aşağıdaki yöntemlerden herhangi biri `Off`tarafından döndürülen [değer, katı](../language-reference/statements/option-strict-statement.md) bir seçenek olarak belirlenen bir integral türüne aktarıldığında kayan nokta dönüşümlerinin performansını önemli ölçüde artırır :

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

Bu optimizasyon, kodun daha hızlı çalışmasına olanak tanır -- çok sayıda tamsayı türüne dönüşüm yapan kod için iki kata kadar daha hızlı. Aşağıdaki örnek, bu optimizasyondan etkilenen bazı basit yöntem çağrılarını göstermektedir:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

Bu, kayan nokta değerlerini yuvarlamaktan çok doyurur.

## <a name="visual-basic-155"></a>Görsel Temel 15.5

[Girintili olmayan adlandırılmış bağımsız değişkenler](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

Visual Basic 15.3 ve önceki sürümlerinde, bir yöntem çağrısı hem konuma hem de ada göre bağımsız değişkenler içeriyorsa, konumsal bağımsız değişkenler adlandırılmış bağımsız değişkenler önce gelmek zorunda kaldı. Visual Basic 15.5 ile başlayarak, son konumsal bağımsız değişkene kadar tüm bağımsız değişkenler doğru konumda olduğu sürece konumsal ve adlandırılmış bağımsız değişkenler herhangi bir sırada görünebilir. Bu, özellikle kod daha okunabilir hale getirmek için adlandırılmış bağımsız değişkenler kullanıldığında yararlıdır.

Örneğin, aşağıdaki yöntem çağrısı, adlandırılmış bir bağımsız değişken arasında iki konumsal bağımsız değişkene sahiptir. Adlandırılmış bağımsız değişken, 19 değerinin bir çağı temsil ettiğini açıkça ortaya koyuyor.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected`üye erişim değiştirici](../language-reference/modifiers/private-protected.md)

Bu yeni anahtar kelime birleşimi, içerdiği sınıftaki tüm üyelerin yanı sıra içeren sınıftan türetilen türler tarafından erişilebilen, ancak yalnızca içeren derlemede de bulunursa erişilebilen bir üyetanımlar. Yapılar devralınamadığından, `Private Protected` yalnızca bir sınıfın üyelerine uygulanabilir.

**Önde gelen hex/ikili/oktal ayırıcı**

Visual Basic 2017, alt skor`_`karakteri için bir basamak ayırıcısı olarak destek ekledi. Visual Basic 15.5 ile başlayarak, önek ve heksadecimal, ikili veya sekizli basamaklar arasında alt çizici karakteri önde gelen ayırıcı olarak kullanabilirsiniz. Aşağıdaki örnek, 3.271.948.384'ü hexadecimal sayı olarak tanımlamak için önde gelen bir basamak ayırıcısı kullanır:

```vb
Dim number As Integer = &H_C305_F860
```

Alt alt seperatifkarakterini önde gelen ayırıcı olarak kullanmak için\*Visual Basic projenize (.vbproj) aşağıdaki öğeyi eklemeniz gerekir:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Görsel Temel 15.3

[**Adlandırılmış tuple çıkarım**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Değişkenlerden tuple elemanlarının değerini atadığınızda, Visual Basic tuple elemanlarının adını ilgili değişken adlarından çıkar; bir tuple öğesini açıkça adlandırmanız gerekmez. Aşağıdaki örnek, üç adlandırılmış öğeile bir tuple `state` `stateName`oluşturmak `capital`için çıkarım kullanır, , ve .

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Ek derleyici anahtarları**

Visual Basic komut satırı derleyicisi artık başvuru derlemelerinin çıktısını denetlemek için [**-refout**](../reference/command-line-compiler/refout-compiler-option.md) ve [**-refonly**](../reference/command-line-compiler/refonly-compiler-option.md) derleyici seçeneklerini destekler. **-refout,** başvuru derlemesinin çıktı dizini tanımlar ve **-refonly yalnızca** bir başvuru derlemesinin çıktı olacağını belirtir.

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Dizilerini**](../programming-guide/language-features/data-types/tuples.md)

Tuples, tek bir yöntem çağrısından birden çok değer döndürmek için en sık kullanılan hafif bir veri yapısıdır. Normalde, bir yöntemden birden çok değer döndürmek için aşağıdakilerden birini yapmanız gerekir:

- Özel bir tür `Class` (a `Structure`veya a) tanımlayın. Bu ağır siklet bir çözüm.

- Yöntemden bir `ByRef` değer döndürmeye ek olarak bir veya daha fazla parametre tanımlayın.

Visual Basic'in tuples desteği, bir tuple'ı hızlı bir şekilde tanımlamanızı, isteğe bağlı olarak değerlere anlamsal adlar atamanızı ve değerlerini hızla almanıza olanak tanır. Aşağıdaki örnek, <xref:System.Int32.TryParse%2A> yönteme bir çağrı yıkıyor ve bir tuple döndürür.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Daha sonra yöntemi arayabilir ve aşağıdaki gibi kodile döndürülen tuple işleyebilir.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**İkili edebi ve basamak ayırıcıları**

Önek `&B` veya `&b`. Buna ek olarak, okunabilirliği artırmak `_`için bir basamak ayırıcı olarak alt karakter kullanabilirsiniz. Aşağıdaki örnek, bir `Byte` değeri atamak ve ondalık, hexadecimal ve ikili sayı olarak görüntülemek için her iki özelliği kullanır.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Daha fazla bilgi için, [Byte,](../language-reference/data-types/byte-data-type.md#literal-assignments) [Tümsa,](../language-reference/data-types/integer-data-type.md#literal-assignments) [Uzun,](../language-reference/data-types/long-data-type.md#literal-assignments) [Kısa,](../language-reference/data-types/short-data-type.md#literal-assignments) [SByte,](../language-reference/data-types/sbyte-data-type.md#literal-assignments) [UInteger,](../language-reference/data-types/uinteger-data-type.md#literal-assignments) [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments)ve [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) veri türlerinin "Literal atamaları" bölümüne bakın.

[**C# referans iade değerleri için destek**](../programming-guide/language-features/procedures/ref-return-values.md)

C# 7.0 ile başlayarak, C# referans dönüş değerlerini destekler. Diğer bir süre, arama yöntemi başvuru yla döndürülen bir değer aldığında, başvurunun değerini değiştirebilir. Visual Basic, başvuru iade değerleriyle yöntemler yazmanıza izin vermez, ancak başvuru döndürme değerlerini tüketmenize ve değiştirmenize olanak sağlar.

Örneğin, C# `Sentence` ile yazılmış bir `FindNext` sonraki sınıf, belirtilen bir alt dizeyle başlayan bir cümlede bir sonraki sözcüğü bulan bir yöntem içerir. Dize bir başvuru dönüş değeri olarak `Boolean` döndürülür ve yönteme başvuru ile geçirilen bir değişken aramanın başarılı olup olmadığını gösterir. Bu, döndürülen değeri okumanın yanı sıra, arayanın da değiştirebileceği ve `Sentence` bu değişikliğin sınıfa yansıttığı anlamına gelir.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

En basit haliyle, cümlede bulunan sözcüğü aşağıdaki gibi kod kullanarak değiştirebilirsiniz. Yönteme bir değer atamadığınızı değil, yöntemin döndürdüğü ifadeye, yani referans iade değişimi olduğunusını unutmayın.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Ancak bu kodla ilgili bir sorun, bir eşleşme bulunamazsa, yöntemin ilk sözcüğü döndürmesidir. Örnek, eşleşme bulunup bulunmadığını `Boolean` belirlemek için bağımsız değişkenin değerini incelemediğinden, eşleşme yoksa ilk sözcüğü değiştirir. Aşağıdaki örnek, eşleşme yoksa ilk sözcüğü kendisiyle değiştirerek bunu düzeltir.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Daha iyi bir çözüm, başvuru iade değerinin başvuru yla geçirildiği bir yardımcı yöntemi kullanmaktır. Yardımcı yöntemi daha sonra başvuru ile ona geçirilen bağımsız değişkeni değiştirebilirsiniz. Aşağıdaki örnek bunu yapar.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Daha fazla bilgi için [Bkz. Başvuru İade Değerleri.](../programming-guide/language-features/procedures/ref-return-values.md)

## <a name="visual-basic-14"></a>Görsel Temel 14

[İsim](../language-reference/operators/nameof.md)

Bir dize kodlama olmadan bir hata iletisinde kullanılmak üzere bir türün veya üyenin niteliksiz dize adını alabilirsiniz.  Bu, yeniden düzenleme yaparken kodunuzun doğru kalmasını sağlar.  Bu özellik, model görünümü denetleyicim MVC bağlantılarını bağlamak ve değiştirilen olayları ateşlemek için de yararlıdır.

[Dize ilişkilendirme](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)

Dizeleri oluşturmak için dize enterpolasyon ifadeleri kullanabilirsiniz.  Enterpolasyonlu dize ifadesi, ifadeler içeren bir şablon dizegibi görünür.  Enterpolasyonlu bir dize, bağımsız değişkenlerle ilgili olarak bileşik [biçimlendirmeden](../../standard/base-types/composite-formatting.md)daha kolaydır.

[Null-koşullu üye erişimi ve dizinleme](../language-reference/operators/null-conditional-operators.md)

Bir üye erişimi ( ) veya dizin (`?.``?[]`) işlemini gerçekleştirmeden önce çok hafif bir sözdizimdizimi ile null için test edebilirsiniz.  Bu işleçler, özellikle veri yapılarına inmek için null denetimleri işlemek için daha az kod yazmanıza yardımcı olur.  Sol operand veya nesne başvurusu null ise, işlemler null döndürür.

[Çok çizgili dize edebi](../../visual-basic/programming-guide/language-features/strings/string-basics.md)

String literals newline dizileri içerebilir.  Artık kullanma etrafında eski çalışma gerekir`<xml><![CDATA[...text with newlines...]]></xml>.Value`

**Açıklamalar**

Örtük satır devamlarından sonra, baş harf ifadelerin in içine ve LINQ ifade terimlerine yorum koyabilirsiniz.

**Daha akıllı tam nitelikli ad çözünürlüğü**

"Threading" `Threading.Thread.Sleep(1000)`ad alanını aramak için kullanılan Visual Basic gibi kodlar göz önüne alındığında, System.Threading ve System.Windows.Threading arasında belirsiz olduğunu keşfedin ve ardından bir hata bildirin.  Visual Basic artık her iki olası ad alanlarını birlikte ele alır.  Tamamlanma listesini gösterirseniz, Visual Studio düzenleyicisi tamamlanma listesinde ki her iki türdeki üyeleri listeler.

**Yıl-ilk tarih literals**

Tarih edebi yy-mm-dd formatında `#2015-03-17 16:10 PM#`olabilir.

**Readonly arabirim özellikleri**

Readwrite özelliğini kullanarak readonly arabirim özelliklerini uygulayabilirsiniz. Arabirim minimum işlevselliği garanti eder ve uygulama sınıfının özelliğin ayarlanmasına izin vermesini engellemez.

[TypeOf \<expr> \<IsNot türü>](../../visual-basic/language-reference/operators/typeof-operator.md)

Kodunuzu daha fazla okunabilirlik için, `TypeOf` `IsNot`artık .

[#Disable \<Uyarı Kimliği> \<ve #Enable Uyarı Kimliği>](../../visual-basic/language-reference/directives/index.md)

Kaynak dosyadaki bölgeler için belirli uyarıları devre dışı bırakıp etkinleştirebilirsiniz.

**XML doc yorum geliştirmeleri**

Doküman yorumları yazarken, akıllı düzenleyici alır sınız ve parametre adlarını doğrulamak, `crefs` (genel ler, operatörler, vb.) doğru şekilde işlemek, renklendirme kılabilir ve yeniden düzenleme için destek oluşturursunuz.

[Kısmi modül ve arayüz tanımları](../../visual-basic/language-reference/modifiers/partial.md)

Sınıflara ve yapılara ek olarak, kısmi modülleri ve arabirimleri bildirebilirsiniz.

[yöntem gövdeleri içinde #Region direktifleri](../../visual-basic/language-reference/directives/region-directive.md)

#Region...#End Bölge sınırlayıcılarını bir dosyanın herhangi bir yerine, işlevlerin içinde ve hatta işlev gövdeleri arasında yayılan herhangi bir yere koyabilirsiniz.

[Geçersiz kılar tanımlar örtülü olarak aşırı yükler](../../visual-basic/language-reference/modifiers/overrides.md)

`Overrides` Değiştiriciyi bir tanıma eklerseniz, derleyici genellikle `Overloads` daha az kod yazabilmeniz için dolaylı olarak ekler.

**CObj öznitelikleri bağımsız değişkenlerde izin**

Derleyici, öznitelik yapılarında kullanıldığında CObj(...) sabit olmadığı hatasını vermek için kullanılır.

**Farklı arabirimlerden belirsiz yöntemleri bildirme ve tüketme**

Daha önce aşağıdaki kod, bildirmenizi `IMock` veya aramanızı `GetDetails` engelleyen hatalar ortaya çıkar (bunlar C#'da bildirilmişse):

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

Şimdi derleyici, aramak için en uygun `GetDetails` olanı seçmek için normal aşırı yük çözümleme kurallarını kullanır ve örnekte gösterildiği gibi Visual Basic'te arabirim ilişkilerini bildirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017'de Yenilikler](/visualstudio/ide/whats-new-visual-studio-2017)
- [Visual Studio 2019'da Yenilikler](/visualstudio/ide/whats-new-visual-studio-2019)

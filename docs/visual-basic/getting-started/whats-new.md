---
title: Visual Basic'teki yenilikler
ms.date: 10/04/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07e6b201056614237a433ed7a297d40eab23da59
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122654"
---
# <a name="whats-new-for-visual-basic"></a>Visual Basic'teki yenilikler

Bu konu, her bir Visual Basic sürümü ile dil en son sürümlerindeki yeni ve geliştirilmiş özellikler ayrıntılı açıklamaları için anahtar özellik adlarını listeler.
  
## <a name="current-version"></a>Geçerli sürüm

Visual Basic 15.5 / Visual Studio 2017 sürüm 15.5  
Yeni özellikler için bkz: [Visual Basic 15.5](#visual-basic-155)

## <a name="previous-versions"></a>Önceki sürümler

Visual Basic 15.3 / Visual Studio 2017 sürüm 15.3  
Yeni özellikler için bkz: [Visual Basic 15.3](#visual-basic-153)

Visual Basic 2017 / Visual Studio 2017  
Yeni özellikler için bkz: [Visual Basic 2017](#visual-basic-2017)

Visual Basic / Visual Studio 2015   
Yeni özellikler için bkz: [Visual Basic 14](#visual-basic-14)

Visual Basic / Visual Studio 2013  
.NET derleyici Platformu ("Roslyn") teknolojisi önizlemeleri

Visual Basic / Visual Studio 2012   
`Async` ve `await` anahtar sözcükler, yineleyiciler, arayan bilgileri öznitelikleri

Visual Basic, Visual Studio 2010   
Otomatik uygulanan özellikler, koleksiyon başlatıcıları, örtük satır devamlılığı, dinamik, genel co/karşıt fark, genel ad alanı erişim

Visual Basic / Visual Studio 2008   
Dil tümleşik sorgu (LINQ), XML değişmez değerleri, yerel tür çıkarımı, nesne başlatıcıları, anonim türler, genişletme yöntemleri, yerel `var` anlam çıkarma, lambda ifadeleri `if` işleci, kısmi yöntemler, boş değer atanabilen değer türleri  

Visual Basic / Visual Studio 2005   
`My` Türü ve yardımcı türleri (uygulama, bilgisayar, dosya sistemi, ağ erişimi)

Visual Basic / Visual Studio .NET 2003   
Bit düzeyinde kaydırma işleçleri, döngü değişken bildirimi

Visual Basic / Visual Studio .NET 2002   
Visual Basic .NET ilk sürümü

## <a name="visual-basic-155"></a>Visual Basic 15.5

[Olmayan trailing-adlandırılmış bağımsız değişkenler](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

Bir yöntem çağrısının hem konuma ve ada göre bağımsız değişkenleri eklendiğinde Visual Basic 15.3 ve önceki sürümlerinde, konumsal bağımsız değişkenler adlandırılmış bağımsız değişkenler önünde gerekiyordu. Visual Basic 15.5 ile başlayarak, doğru konumda son konumsal bağımsız değişken kadar tüm bağımsız değişkenler olarak konumsal ve adlandırılmış bağımsız değişkenler herhangi bir sırada görünebilir. Bu, özellikle kod daha okunabilir yapmak için adlandırılmış bağımsız değişkenler kullanıldığında yararlıdır.

Örneğin, aşağıdaki yöntem çağrısını bir adlandırılmış bağımsız değişken arasında iki konumsal bağımsız değişkenlere sahiptir. Adlandırılmış bağımsız değişkeni, Temizle 19 değeri temsil eden bir geçerlilik süresi sağlar.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected` üye erişim değiştiricisi](../language-reference/modifiers/private-protected.md)

Bu yeni anahtar sözcüğü birleşimi içeren sınıfındaki tüm üyeleri veya içeren sınıfından türetilen türler tarafından erişilebilir, ancak yalnızca de içeren derlemede bulunan bir üye tanımlar. Yapıları devralınamaz çünkü `Private Protected` yalnızca bir sınıf üyelerine uygulanabilir.

**Önde gelen onaltılık/ikili/sekizlik ayırıcı**

Visual Basic 2017, alt çizgi karakterini desteği eklendi (`_`) basamak ayırıcı olarak. Visual Basic 15.5 ile başlayarak, önek ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak alt çizgi karakterini kullanabilirsiniz. Aşağıdaki örnek, bir ilk basamak ayıracı 3,271,948,384 onaltılık bir sayı olarak tanımlamak için kullanır:

```vb
Dim number As Integer = &H_C305_F860
``` 
Önde gelen bir ayırıcı olarak alt çizgi karakterini kullanmak için aşağıdaki öğe Visual Basic projenize eklemeniz gerekir (\*.vbproj) dosya:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15.3

[**Adlandırılmış demet çıkarımı**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Değişkenleri tanımlama grubu öğelerinin değerini atadığınızda, Visual Basic karşılık gelen değişken adları tanımlama grubu öğe adı algılar; açıkça bir tanımlama grubu öğe adı gerekmez. Aşağıdaki örnek, üç adlandırılmış öğeleri bir kayıt düzeni oluşturmak için çıkarım kullanır. `state`, `stateName`, ve `capital`.

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Ek derleyici anahtarları**  

Visual Basic komut satırı derleyicisi artık aşağıdakileri destekler [ **- refonly** ](../reference/command-line-compiler/refout-compiler-option.md) ve [ **- refonly** ](../reference/command-line-compiler/refonly-compiler-option.md) çıktısını denetlemek için derleyici seçenekleri başvuru bütünleştirilmiş kodları. **-refonly** başvuru bütünleştirilmiş kodu çıktı dizinine tanımlar ve **- refonly** yalnızca bir başvuru bütünleştirilmiş kodu çıkış derleme olması gerektiğini belirtir.

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Diziler**](../programming-guide/language-features/data-types/tuples.md)

Tanımlama grubu olan basit bir veri yapısı tek yöntem çağrısından birden çok değerleri döndürülecek en yaygın olarak kullanılır. Normalde, bir yöntemden birden çok değer döndürmek için aşağıdakilerden birini yapmanız gerekir:

- Özel tür tanımlama (bir `Class` veya `Structure`). Bu ağır çözümüdür.

- Bir veya daha fazla tanımlama `ByRef` yöntemden bir değer döndüren ek parametreler.
 
Visual Basic'ın desteği diziler için bir demet hızlıca tanımlamak, anlam adları için değerleri isteğe bağlı olarak atayabilirsiniz ve hızlıca değerlerini almak olanak sağlar. Aşağıdaki örnek bir çağrı sarılır <xref:System.Int32.TryParse%2A> yöntemi ve bir tanımlama grubu döndürür.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Ardından yöntemi çağırın ve aşağıdaki gibi kod ile döndürülen dizi işlemek.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)] 

**İkili sabit değerler ve basamak ayırıcılar**

Önekini kullanarak bir ikili değişmez değer tanımlayabilirsiniz `&B` veya `&b`. Ayrıca, alt çizgi karakterini kullanabilirsiniz `_`, okunabilirliği artırmak için basamak ayırıcı olarak. Aşağıdaki örnek, atamak için her iki özellik kullanır. bir `Byte` değeri ve ondalık, onaltılık ve ikili sayı olarak görüntüler.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Daha fazla bilgi için "Değişmez değer atamaları" bölümüne bakın. [bayt](../language-reference/data-types/byte-data-type.md#literal-assignments), [tamsayı](../language-reference/data-types/integer-data-type.md#literal-assignments), [uzun](../language-reference/data-types/long-data-type.md#literal-assignments), [kısa](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte ](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [Uınteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments), ve [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) veri türleri.

[**C# başvuru dönüş değerleri için destek**](../programming-guide/language-features/procedures/ref-return-values.md)

C# 7.0 ile başlayarak, C# destekler başvuru dönüş değerleri. Diğer bir deyişle, çağıran Metoda başvuru ile döndürülen bir değer aldığında, başvuru değeri değiştirebilirsiniz. Visual Basic başvurusu yöntemleriyle yazmanızı dönüş değerleri ancak kullanma ve başvuru dönüş değerleri değiştirmenize olanak tanır izin vermez.

Örneğin, aşağıdaki `Sentence` C# dilinde yazılmış bir sınıf içeren bir `FindNext` sonraki sözcüğe bulur, belirtilen bir alt dizesi ile başlayan bir cümle yöntemi. Bir başvuru döndürmeyi olarak değer ve bir dize döndürülür `Boolean` yönteme başvuru tarafından geçirilen değişkeni arama başarılı olup olmadığını gösterir. Başka bir deyişle, çağırana döndürülen değer yalnızca okunamıyor; isterse de değiştirebilirsiniz ve bu değişikliği yansıtılır `Sentence` sınıfı.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

En basit şekliyle, aşağıdaki gibi bir kod kullanarak bir tümce içinde bulunan word değiştirebilirsiniz. Bir değer yöntemi, ancak bunun yerine ifade başvuru yöntemi döndürür dönüş değeri atadığınız değil olduğunu unutmayın.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Bu kod ile ilgili bir sorun yine de bir eşleşme bulunmazsa, yöntemin ilk sözcük döndürmesidir. Örneğin değerini incelemez beri `Boolean` herhangi bir eşleşme olup olmadığını değiştirdiği ilk sözcük eşleşme yoksa belirlemek için bağımsız değişken. Aşağıdaki örnek bu eşleşme yoksa ilk sözcük kendisi ile değiştirerek düzeltir.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Başvuru dönüş değeri başvuru tarafından geçirilmediğine bir yardımcı yöntemi daha iyi bir çözümdür. Yardımcı yöntemi, başvuru tarafından geçirilen bağımsız değişken olarak daha sonra değiştirebilirsiniz. Aşağıdaki örnek yapar.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Daha fazla bilgi için [başvuru dönüş değerleri](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[Nameof](../../csharp/language-reference/keywords/nameof.md)  
 Bir tür veya üye nitelenmemiş dize adını bir dize sabit kodlama olmadan kullanılmak üzere bir hata iletisi alabilirsiniz.  Bu, kodunuzu yeniden düzenlemede doğru kalmasını sağlar.  Bu özellik ayrıca, model-view-controller MVC bağlantılar takma ve özellik değişti olayları tetikleme için yararlıdır.  
  
[Dize ilişkilendirme](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)  
 Dize ilişkilendirme ifadeleri dizeleri oluşturmak için kullanabilirsiniz.  İlişkilendirilmiş dize ifadesi, ifadeler içeren bir şablon dize gibi görünüyor.  İlişkilendirilmiş dize bağımsız değişkenleri ile ilgili anlaşılması kolaydır [bileşik biçimlendirme](../../standard/base-types/composite-format.md).  
  
[Null koşullu üye erişimi ve dizin oluşturma](../../csharp/language-reference/operators/null-conditional-operators.md)  
Null üye erişimi gerçekleştirmeden önce söz dizimsel çok açık bir şekilde test edebilirsiniz (`?.`) ya da dizin (`?[]`) işlemi.  Bu işleçler null işlemek için daha az kod denetler, özellikle azalan düzende veri yapılarda yazmanıza yardımcı olur.  Sol işlenen ya da nesne başvuru null ise, işlemler null döndürür.  
  
[Çok satırlı dize değişmez değerleri](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 Dize değişmez değerleri, yeni satır dizileri içerebilir.  Artık eski geçici bir çözüm kullanarak çalışma `<xml><![CDATA[...text with newlines...]]></xml>.Value`  
  
**Açıklamalar**  
Başlatıcı ifadeleri içinde ve LINQ ifadesi hüküm arasında örtük satır devamlılıklar sonra açıklamaları koyabilirsiniz.  
  
**Daha Akıllı tam olarak nitelenmiş ad çözümlemesi**  
 Kod gibi verilen `Threading.Thread.Sleep(1000)`, Visual Basic kullanılan ad alanı aramak için "İş parçacığı," System.Threading ile System.Windows.Threading arasında belirsiz olduğu bulabilir ve ardından bir hatayı bildirin.  Visual Basic artık birlikte her iki olası ad değerlendirir.  Tamamlanma listesi gösterirse, Visual Studio Düzenleyicisi tamamlama listesinde iki tür üyeleri listeler.  
  
 **Başta yıl tarih değişmez değerleri**  
 Tarih değişmez değerleri, yyyy-aa-gg biçiminde olabilir `#2015-03-17 16:10 PM#`.  
  
 **Salt okunur arabirimi özellikleri**  
 Salt okunur arabirimi özellikleri readwrite özelliğini kullanarak uygulayabilirsiniz.  En düşük işlevsellik arabirimi garanti eder ve izin verme özelliği ayarlamak gelen uygulayan bir sınıfa durdurmaz.  
  
 [TypeOf \<expr > IsNot \<türü >](../../visual-basic/language-reference/operators/typeof-operator.md)  
 Artık kullanabilirsiniz, kodunuzun daha fazla okunabilirlik açısından, `TypeOf` ile `IsNot`.  
  
 [#Disable uyarı \<kimliği > ve #Enable uyarı \<kimliği >](../../visual-basic/language-reference/directives/index.md)  
 Devre dışı bırakabilir ve bölgelerin bir kaynak dosyası içindeki belirli uyarıları etkinleştirin.  
  
 **XML belge açıklaması geliştirmeleri**  
 Belge açıklamaları yazarken, akıllı Düzenleyici almanıza ve parametre adları, işleme uygun doğrulamak için destek yapı `crefs` (genel türler, işleçler, vb.), renklendirme ve yeniden düzenleme.  
  
 [Kısmi modülü ve arabirimi tanımları](../../visual-basic/language-reference/modifiers/partial.md)  
 Sınıflar ve yapılar ek olarak, kısmi modüller ve arabirimleri bildirebilirsiniz.  
  
 [#Region yönergesi içinde metot gövdeleri](../../visual-basic/language-reference/directives/region-directive.md)  
 #Region... koyabilirsiniz #End Region sınırlayıcıları içinde işlevler ve hatta üzerinden yayılan bir dosyayı başka bir yerindeki işlev gövdeleri.  
  
 [Geçersiz kılmalar tanımlardır örtük aşırı yüklemeleri](../../visual-basic/language-reference/modifiers/overrides.md)  
 Eklerseniz `Overrides` tanımına değiştiricisi, derleyicinin dolaylı olarak ekler `Overloads` ortak daha az kod yazın, böylece servis talebi.  
  
 **İzin öznitelikleri değişkenlerinde CObj**  
 Derleyici bir hata CObj(...) özniteliği yapılarındaki kullanıldığında bir sabit değil vermek için kullanılan.  
  
 **Bildirme ve farklı arabirimlerinden belirsiz yöntemlerini kullanma**  
 Daha önce aşağıdaki kodu bildirme dan engelleyen hatalar veriyor `IMock` veya arama `GetDetails` (Bu C# içinde bildirilmiş ise):  
  
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
  
 Derleyici, normal aşırı yükleme çözünürlüğü kuralları en uygun seçmek için kullanacağı artık `GetDetails` çağırmak için ve Visual Basic'te arabirimi ilişkileri gibi bu örnekte gösterilen bildirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio 2017'deki yenilikler](/visualstudio/ide/whats-new-in-visual-studio)

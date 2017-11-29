---
title: Visual Basic for yenilikler nelerdir?
ms.date: 04/27/2017
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: "145"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d26eb23aae6e5baec98e27a246d06af6b78e0802
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-for-visual-basic"></a>Visual Basic for yenilikler nelerdir?

Bu konu, her sürümüyle Visual Basic Dil en son sürümündeki yeni ve geliştirilmiş özelliklerine ayrıntılı açıklamaları için anahtar özellik adlarını listeler.
  
## <a name="current-version"></a>Geçerli Sürüm

Visual Basic / Visual Studio .NET 2017   
Yeni özellikler için bkz: [Visual Basic 2017](#visual-basic-2017)

## <a name="previous-versions"></a>Önceki sürümler

Visual Basic / Visual Studio .NET 2015   
Yeni özellikler için bkz: [Visual Basic 14](#visual-basic-14)

Visual Basic / Visual Studio .NET 2013  
.NET derleme Platformu ("Roslyn") teknolojisi önizlemeleri

Visual Basic / Visual Studio .NET 2012   
`Async`ve `await` anahtar sözcükler, yineleyiciler, arayan bilgileri öznitelikleri

Visual Basic, Visual Studio .NET 2010   
Otomatik uygulanan özellikler, koleksiyon başlatıcıları, örtük satır devamlılığı, dinamik, genel co/karşıt fark, genel ad alanı erişim

Visual Basic / Visual Studio .NET 2008   
Dil tümleşik sorgu (LINQ), XML değişmez değerleri, yerel türü çıkarımı nesne başlatıcılar, anonim türler, genişletme yöntemleri, yerel `var` yazın çıkarım, lambda ifadeleri `if` işleci, kısmi yöntemler, boş değer atanabilen değer türleri  

Visual Basic / Visual Studio .NET 2005   
`My` Türü ve yardımcı türleri (uygulama, bilgisayar, dosya sistemi, ağ erişimi)

Visual Basic / Visual Studio .NET 2003   
Bit kaydırma işleçleri, döngü değişken bildirimi

Visual Basic / Visual Studio .NET 2002   
Visual Basic .NET'in ilk sürümü

## <a name="visual-basic-2017"></a>Visual Basic 2017

[Diziler](../programming-guide/language-features/data-types/tuples.md)

Diziler olan basit bir veri yapısı en yaygın olarak tek bir yöntem çağrısından birden çok değer döndürmek için kullanılır. Normalde, bir yöntemin birden çok değer döndürmek için aşağıdakilerden birini yapmanız gerekir:

- Özel tür tanımlama (bir `Class` veya `Structure`). Bu bir ağır çözümüdür.

- Bir veya daha fazla tanımlama `ByRef` yönteminden değer döndürme ek parametreler.
 
Visual Basic'ın desteği diziler için bir tanımlama grubu hızla tanımlamanıza, isteğe bağlı olarak değerlerini anlamsal adları atamak ve hızlı bir şekilde değerlerini almak olanak sağlar. Aşağıdaki örnekte bir çağrı sarmalar <xref:System.Int32.TryParse%2A> yöntemi ve bir tanımlama grubu döndürür.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Ardından, yöntemini çağırın ve aşağıdaki gibi kod ile döndürülen tanımlama grubu tanıtıcı.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)] 

**İkili değişmez değerleri ve basamak ayırıcıları**

Önek kullanarak değişmez değer bir ikili tanımlayabilirsiniz `&B` veya `&b`. Ayrıca, alt çizgi karakterini kullanabilirsiniz `_`, okunabilirliğini artırmak için basamak ayırıcı olarak. Aşağıdaki örnek, atamak için her iki özellik kullanır. bir `Byte` değer bir ondalık, onaltılık ve ikili sayı olarak görüntülenecek ve.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Daha fazla bilgi için "Değişmez değer atamaları" bölümüne bakın [bayt](../language-reference/data-types/byte-data-type.md#literal-assignments), [tamsayı](../language-reference/data-types/integer-data-type.md#literal-assignments), [uzun](../language-reference/data-types/long-data-type.md#literal-assignments), [kısa](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte ](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [Uınteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments), ve [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) veri türleri.

**C# başvurusu dönüş değerleri için destek**

C# 7 ile başlayan, C# destekler başvurusu dönüş değerleri. Diğer bir deyişle, çağrıyı yapan yöntemini başvuru tarafından döndürülen bir değeri aldığında, başvuru değeri değiştirebilirsiniz. Visual Basic başvurusu yöntemleriyle yazmak için dönüş değerleri ancak kullanabilir ve başvuru dönüş değerlerini değiştirmek olanak izin vermiyor.

Örneğin, aşağıdaki `Sentence` C# ile yazılmış sınıfı içeren bir `FindNext` belirtilen bir alt dizesi ile başlayan bir tümcedeki sonraki sözcüğü bulur yöntemi. Bir başvuru döndürmek gibi değer ve bir dize döndürdü `Boolean` başvuruya yöntemine geçirilen değişken gösterir arama başarılı olup olmadığını. Bu, çağrıyı yapan yalnızca döndürülen değeri okunamıyor anlamına gelir; çözemiyorsa de değiştirebilirsiniz ve bu değişikliği yansıtılmıştır `Sentence` sınıfı.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

En basit biçimiyle cümlede aşağıdaki gibi kod kullanarak bulduğu sözcüğün değiştirebilirsiniz. Bir değer yöntemi, ancak bunun yerine ifade için başvuru yöntemi döndürür dönüş değeri atadığınız değil olduğunu unutmayın.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Bu kodu ile ilgili bir sorun yine de bir eşleşme bulunmazsa yöntemi ilk word döndürmesidir. Örnek değerini inceleyin değil bu yana `Boolean` herhangi bir eşleşme olup olmadığını değiştirdiği ilk word eşleşme yoksa belirlemek için bağımsız değişken. Aşağıdaki örnekte bu eşleşme yoksa ilk word kendisiyle değiştirerek düzeltir.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Başvuruya göre geçirilen başvuru dönüş değeri için bir yardımcı yöntemi daha iyi bir çözümdür. Yardımcı yöntemi, başvuruya göre geçirilen bağımsız değişken olarak daha sonra değiştirebilirsiniz. Aşağıdaki örnek, yapar.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Daha fazla bilgi için bkz: [başvuru dönüş değerleri](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[Nameof](../../csharp/language-reference/keywords/nameof.md)  
 Bir dize sabit kodlama olmadan bir hata iletisi kullanmak için bir tür veya üye nitelenmemiş dize adını elde edebilirsiniz.  Bu, kodunuzu yeniden düzenleme, doğru kalmasını sağlar.  Bu özellik ayrıca model-view-controller MVC bağlantıları takma ve özellik değişti olayları tetikleme için yararlıdır.  
  
[Dize ilişkilendirme](../../csharp/language-reference/keywords/interpolated-strings.md)  
 Dize ilişkilendirme ifadeler dizeleri oluşturmak için kullanabilirsiniz.  Ara değerli dize ifadesi ifadeleri içeren bir şablon dize gibi görünüyor.  Ara değerli bir dize bağımsız değişkenleri göre anlamak daha kolay [bileşik biçimlendirme](../../standard/base-types/composite-format.md).  
  
[Null-conditional üye erişimi ve dizin oluşturma](../../csharp/language-reference/operators/null-conditional-operators.md)  
Null üye erişimi gerçekleştirmeden önce çok açık bir söz dizim şekilde test edebilirsiniz (`?.`) veya dizin (`?[]`) işlemi.  Bu işleçleri özellikle veri yapılara azalan düzen için null işlemek için daha az kod denetler yazmanıza yardımcı olur.  Sol işleneni veya nesne başvurusu null ise, işlemler null döndürür.  
  
[Çok satırlı dize değişmez değerleri](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 Dize değişmez değerleri yeni satır dizileri içerebilir.  Artık eski kullanarak çözmek`<xml><![CDATA[...text with newlines...]]></xml>.Value`  
  
Açıklamalar  
Örtük satır devamlılıklar, başlatıcı ifadeleri içinde ve arasında LINQ ifadesi koşulları sonra açıklama koyabilirsiniz.  
  
 Daha Akıllı tam ad çözümlemesi  
 Kod gibi verilen `Threading.Thread.Sleep(1000)`, Visual Basic kullanılan ad alanı aramak için "İş parçacığı oluşturma", onu System.Threading ve System.Windows.Threading arasında belirsiz bulmak ve bir hatayı bildirin.  Visual Basic artık olası her iki ad alanı birlikte göz önünde bulundurur.  Tamamlanma listesi gösterirse, Visual Studio düzenleyicisinde tamamlama listesindeki her iki tür üyeleri listeler.  
  
 Yılın ilk tarih değişmez değerleri  
 Tarih değişmez değerleri yyyy-aa-gg biçiminde olabilir `#2015-03-17 16:10 PM#`.  
  
 Salt okunur arabirimi özellikleri  
 Salt okunur arabirimi özellikleri readwrite özelliğini kullanarak uygulayabilirsiniz.  En düşük işlevselliği arabirimi güvence altına alır ve ayarlanacak özelliği sağlayan bir uygulama sınıfı durdurmaz.  
  
 [TypeOf \<expr > IsNot \<türü >](../../visual-basic/language-reference/operators/typeof-operator.md)  
 Artık kullanabilirsiniz için daha fazla okunabilirlik kodunuzun `TypeOf` ile `IsNot`.  
  
 [#Disable uyarı \<kimliği > ve #Enable uyarı \<kimliği >](../../visual-basic/language-reference/directives/directives.md)  
 Devre dışı bırakın ve bir kaynak dosyası içinde bölgeler için belirli uyarıları etkinleştirin.  
  
 XML Belge açıklama geliştirmeleri  
 Doc açıklamaları yazarken, akıllı Düzenleyicisi almanıza ve yapı parametre adları, işleme uygun doğrulama desteği `crefs` (genel türler, işleçler, vb.), renklendirme ve yeniden düzenleme.  
  
 [Kısmi modülü ve arabirim tanımları](../../visual-basic/language-reference/modifiers/partial.md)  
 Sınıflar ve yapılar ek olarak, kısmi modülleri ve arabirimleri bildirebilirsiniz.  
  
 [Yöntem gövdeleri içinde #Region yönergesi](../../visual-basic/language-reference/directives/region-directive.md)  
 #Region... koyabilirsiniz #End Region sınırlayıcıları işlevleri, iç ve hatta üzerinden yayılan bir dosyayı başka bir yerindeki işlev gövdesi.  
  
 [Örtük olarak Overloads geçersiz kılmaları tanımı verilmiştir](../../visual-basic/language-reference/modifiers/overrides.md)  
 Eklerseniz `Overrides` değiştiricisi bir tanımı derleyici örtük olarak ekler `Overloads` durumlarda böylece daha az kod ortak yazabilirsiniz.  
  
 Öznitelikleri değişkenlerinde izin CObj  
 Bir hata CObj(...) özniteliği kurulumlarını kullanıldığında bir sabit olmadığını vermek için kullanılan derleyicisi.  
  
 Bildirme ve farklı arabirimlerinden belirsiz yöntemlerini kullanma  
 Aşağıdaki kod bildirme gelen engelleyen hatalar önceden belirlenmiştir `IMock` veya arama `GetDetails` (bunlar C# ' ta bildirilmiş değilse):  
  
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
  
 Derleyici normal aşırı çözümleme kurallarını en uygun seçmek için kullanacağı artık `GetDetails` çağırmak için ve Visual Basic arabirimi ilişkiye benzer örnekte gösterilen bildirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio 2017 yenilikler](/visualstudio/ide/whats-new-in-visual-studio)

---
title: "Genişletme ve Daraltma Dönüşümleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2cf1f8d956935a9a363211abf94b4f1c2f538074
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Genişletme ve Daraltma Dönüşümleri (Visual Basic)
Önemli bir tür dönüştürmesi ile dönüştürme işleminin sonucu hedef veri türü aralık içinde olup olmadığını konudur.  
  
 A *dönüştürme genişletme* özgün veriler için bir olası değer sağlayan bir veri türü için bir değer değiştirir.  Genişletme dönüşümleri kaynak değerin koruma, ancak kendi gösterimi değiştirebilirsiniz. İçin bir tam sayı türünden dönüştürürseniz, bu gerçekleşir `Decimal`, veya `Char` için `String`.  
  
 A *dönüştürme daraltma* bazı olası değerleri tutun mümkün olmayabilir veri türü için bir değer değiştirir. Örneğin, bir tam sayı türü ve dönüştürülen sayısal bir tür dönüştürüldüğünde bir kesir değerini yuvarlanır `Boolean` ya da daha azdır `True` veya `False`.  
  
## <a name="widening-conversions"></a>Dönüştürmeleri Genişletme  
 Aşağıdaki tabloda dönüşümleri standart gösterir.  
  
|Veri türü|Veri türleri için widens <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Bayt](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Kısa](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Tamsayı](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Uınteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Uzun](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Ondalık](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Tek](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Çift](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Herhangi bir numaralandırılmış türü ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|Temel alınan tam sayı türünü ve olduğu temel alınan tür widens herhangi bir tür.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char`dizi|`Char`dizi,`String`|  
|Herhangi bir türü|[Nesne](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Türetilmiş bir tür|Herhangi bir temel türü, türetilmiş <sup>3</sup>.|  
|Herhangi bir türü|Bunu uygulayan herhangi bir arabirim.|  
|[Hiçbir şey](../../../../visual-basic/language-reference/nothing.md)|Tüm veri türü veya nesne türü.|  
  
 <sup>1</sup> tanım olarak, her veri türü kendisine widens.  
  
 <sup>2</sup> gelen dönüşümleri `Integer`, `UInteger`, `Long`, `ULong`, veya `Decimal` için `Single` veya `Double` duyarlık kaybına, ancak hiçbir zaman büyüklük kaybına neden olabilir. Bu anlamda bunlar bilgi kaybına neden değil.  
  
 <sup>3</sup> türetilmiş bir tür dönüştürme temel türlerinden birine genişletme, şaşırtıcı görünebilir. Gerekçeyi temel türün bir örneği olarak niteleyen şekilde türetilmiş bir tür temel türdeki tüm üyelerin içermesidir. Ters yönde temel türü türetilen türü tarafından tanımlanan herhangi bir yeni üye içermiyor.  
  
 Genişletme dönüşümleri çalışma zamanında her zaman başarılı ve hiçbir zaman veri kaybına neden. Her zaman bunları örtük olarak gerçekleştirebileceğiniz olsun [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) anahtara denetimi türünü ayarlar `On` veya `Off`.  
  
## <a name="narrowing-conversions"></a>Daraltma dönüşümleri  
 Standart daraltma dönüşümleri aşağıdakileri içerir:  
  
-   (Her türün kendisine widens dışında) önceki içinde genişletme dönüşümleri ters yönleri tablo  
  
-   Dönüşümler arasında herhangi bir yönde [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) ve herhangi bir sayısal tür  
  
-   Herhangi bir sayısal her tür dönüşümleri numaralandırılan türü (`Enum`)  
  
-   Dönüşümler arasında herhangi bir yönde [dize](../../../../visual-basic/language-reference/data-types/string-data-type.md) ve herhangi bir sayısal tür `Boolean`, veya [tarihi](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   Ondan türetilmiş bir tür için bir veri türü veya nesne dönüşümleri yazın  
  
 Daraltma dönüşümleri her zaman çalışma zamanında başarılı ve başarısız veya veri kaybına neden. Hedef veri türüne dönüştürülecek değer alırsanız hata oluşur. Örneğin, bir sayısal dönüşüm taşmayla neden olabilir. Derleyici sürece örtük olarak daraltma dönüşümleri gerçekleştirmenize izin vermiyor [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) anahtara denetimi türünü ayarlar `Off`.  
  
> [!NOTE]
>  Daraltma dönüştürme hatası öğelerde bulunan dönüştürmeleri için gizlenen bir `For Each…Next` for döngüsü denetim değişkeni koleksiyonu. Daha fazla bilgi ve örnekler için "Daraltma dönüşümleri" bölümüne bakın [For Each... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Daraltma Dönüşümleri kullanma zamanı  
 Kaynak değerin hatası veya veri kaybı olmadan hedef veri türüne dönüştürülebilir bildiğinizde daraltma dönüşümü kullanın. Örneğin, bir `String` kullanabileceğiniz içeren "True" veya "False" bildiğinizden, `CBool` öğesine dönüştürmek için anahtar sözcüğü `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Dönüşüm sırasında özel durumlar  
 Her zaman dönüşümleri başarılı olması için özel durumlar oluşturmayın. Daraltma dönüşümleri, bunlar başarısız olduğunda, genellikle aşağıdaki özel durumlar oluşturma:  
  
-   <xref:System.InvalidCastException>— iki tür arasında dönüştürme tanımlanmışsa  
  
-   <xref:System.OverflowException>— (yalnızca integral türleri) dönüştürülen değer hedef türü çok büyük ise  
  
 Bir sınıf veya yapı tanımlıyorsa bir [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) Bu sınıf veya yapı, bilgisayardan veya bir dönüşüm işleci olarak hizmet verecek, `CType` onu uymak açısından gerekli olduğunu uygun herhangi bir özel durum. Ayrıca, `CType` çağırabilirsiniz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] işlevleri veya [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] özel durumlar, çeşitli sırayla throw yöntemleri.  
  
## <a name="changes-during-reference-type-conversions"></a>Başvuru türü dönüşümleri sırasında değişiklikleri  
 Bir dönüştürme bir *başvuru türüne* yalnızca işaretçi değeri kopyalar. Değer ne kopyalanan ya da herhangi bir şekilde değiştirilmez. Değiştirebilirsiniz tek şey işaretçinin bulunduran değişkeni veri türüdür. Aşağıdaki örnekte, veri türü türetilmiş sınıftan devralınabilir. taban sınıfı için dönüştürülür, ancak her iki değişken şimdi işaret nesnesi değiştirilmez.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Örtük ve açık dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Dizeler ve diğer türleri arasında dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Dizi dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür dönüşüm işlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)

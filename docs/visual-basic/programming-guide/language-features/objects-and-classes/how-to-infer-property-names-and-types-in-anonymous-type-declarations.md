---
title: 'Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 89a39e8e9cd66b1d774da70be47c7c6824cccef2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350031"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma (Visual Basic)

Anonim türler, özelliklerin veri türlerini doğrudan belirtmek için bir mekanizma sağlar. Tüm özelliklerin türleri algılanır. Aşağıdaki örnekte, `Name` ve `Price` türleri, bunları başlatmak için kullanılan değerlerden doğrudan algılanır.

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

Anonim türler Ayrıca diğer kaynaklardan özellik adlarını ve türlerini de çıkarabilir. Aşağıdaki bölümler, çıkarım mümkün olduğu durumların bir listesini ve olmadığı durumlara örnekler sağlar.

## <a name="successful-inference"></a>Başarılı çıkarım

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Anonim türler, aşağıdaki kaynaklardan özellik adlarını ve türlerini çıkarabilir:

- Değişken adlarından. Anonim tür `anonProduct`, `productName` ve `productPrice`iki özelliğe sahip olur. Veri türleri, sırasıyla `String` ve `Double`orijinal değişkenlerle olur.

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- Diğer nesnelerin özelliğinden veya alan adlarından. Örneğin, `Name` ve `ID` özelliklerini içeren bir `CarClass` türünün `car` nesnesini düşünün. `car1`yeni bir anonim tür örneği oluşturmak için, `Name` ve `car` nesnesinden değerler ile başlatılan `ID` özellikleriyle şunları yazabilirsiniz:

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  Önceki bildirim, `car2`anonim tür tanımlayan daha uzun kod satırıyla eşdeğerdir.

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- XML üye adlarından.

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  `anon` için sonuç türü, <xref:System.Collections.IEnumerable>(Of XElement) türünde bir `Book`bir özelliğe sahiptir.

- Aşağıdaki örnekte `SomeFunction` gibi parametresi olmayan bir işlevden.

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  Aşağıdaki kodda `anon2` değişkeni, `First`adlı bir karakter olan bir özelliğine sahip anonim bir türdür. Bu kod, işlev <xref:System.Linq.Enumerable.First%2A>tarafından döndürülen harfi "E" olarak görüntüler.

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a>Çıkarım arızaları

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Ad çıkarımı, aşağıdakiler dahil olmak üzere birçok durumda başarısız olur:

- Çıkarımı, bir yöntem, Oluşturucu veya bağımsız değişken gerektiren parametreli bir özellik çağrısından türetilir. `someFunction` bir veya daha fazla bağımsız değişken varsa `anon1` önceki bildirimi başarısız olur.

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  Yeni bir özellik adına atama sorunu çözer.

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- Çıkarımı karmaşık bir ifadeden türetilir.

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  Hata, ifadenin sonucu bir özellik adına atanarak çözülebilir.

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- Birden çok özellik için çıkarım aynı ada sahip iki veya daha fazla özellik oluşturur. Önceki örneklerde bildirimlere geri döndüğünüzde, hem `product.Name` hem de `car1.Name` aynı anonim türdeki özellikler olarak listelenemez. Bunun nedeni, bunların her biri için çıkarılan tanımlayıcının `Name`olacaktır.

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  Bu sorun, değerler ayrı özellik adlarına atanarak çözülebilir.

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  Büyük/küçük harf ve küçük harfler arasındaki değişiklikler iki adı farklı hale getirir.

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- Bir özelliğin başlangıç türü ve değeri henüz kurulu olmayan başka bir özelliğe bağlıdır. Örneğin, `.LastName` zaten başlatılmadığı müddetçe `.IDName = .LastName` anonim tür bildiriminde geçerli değildir.

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  Bu örnekte, özelliklerinin bildirildiği sırayı tersine çevirerek sorunu çözebilirsiniz.

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- Anonim türün Özellik adı bir <xref:System.Object>üyesinin adı ile aynıdır. Örneğin, `Equals` bir <xref:System.Object>yöntemi olduğu için aşağıdaki bildirim başarısız olur.

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  Özellik adını değiştirerek sorunu çözebilirsiniz:

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)

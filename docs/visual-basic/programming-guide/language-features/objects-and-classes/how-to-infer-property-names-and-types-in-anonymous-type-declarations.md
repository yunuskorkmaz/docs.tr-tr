---
title: 'Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 9ebbbe9d2e6d36f5ab2bc7f7c916d18c9240a06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404894"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma (Visual Basic)

Anonim türler, özelliklerin veri türlerini doğrudan belirtmek için bir mekanizma sağlar. Tüm özelliklerin türleri algılanır. Aşağıdaki örnekte, türleri `Name` ve, `Price` bunları başlatmak için kullanılan değerlerden doğrudan algılanır.

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

Anonim türler Ayrıca diğer kaynaklardan özellik adlarını ve türlerini de çıkarabilir. Aşağıdaki bölümler, çıkarım mümkün olduğu durumların bir listesini ve olmadığı durumlara örnekler sağlar.

## <a name="successful-inference"></a>Başarılı çıkarım

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Anonim türler, aşağıdaki kaynaklardan özellik adlarını ve türlerini çıkarabilir:

- Değişken adlarından. Anonim türün `anonProduct` iki özelliği `productName` ve olur `productPrice` . Veri türleri, sırasıyla özgün değişkenlerle `String` ve `Double` , ve sırasıyla olur.

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- Diğer nesnelerin özelliğinden veya alan adlarından. Örneğin, `car` ve özelliklerini içeren bir türün nesnesini düşünün `CarClass` `Name` `ID` . Yeni bir anonim tür örneği oluşturmak için, `car1` ve ile `Name` `ID` nesnesinden değerleri ile başlatılan özellikleri `car` , aşağıdakileri yazabilirsiniz:

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  Önceki bildirim, anonim türü tanımlayan daha uzun kod satırıyla eşdeğerdir `car2` .

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- XML üye adlarından.

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  İçin sonuç türünün, `anon` `Book` türünde <xref:System.Collections.IEnumerable> (XElement) bir özelliği olacaktır.

- Aşağıdaki örnekte olduğu gibi parametresi olmayan bir işlevden `SomeFunction` .

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  `anon2`Aşağıdaki kodda bulunan değişkeni, adlı bir karakter olan bir özelliğine sahip anonim bir türdür `First` . Bu kod, işlevi tarafından döndürülen harfi "E" olarak görüntüler <xref:System.Linq.Enumerable.First%2A> .

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a>Çıkarım arızaları

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Ad çıkarımı, aşağıdakiler dahil olmak üzere birçok durumda başarısız olur:

- Çıkarımı, bir yöntem, Oluşturucu veya bağımsız değişken gerektiren parametreli bir özellik çağrısından türetilir. `anon1` `someFunction` Bir veya daha fazla bağımsız değişken varsa, önceki bir bildirimi başarısız olur.

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

- Birden çok özellik için çıkarım aynı ada sahip iki veya daha fazla özellik oluşturur. Önceki örneklerde bildirimlere geri döndüğünüzde, hem hem de `product.Name` `car1.Name` aynı anonim türdeki özellikleri listelenemez. Bunun nedeni, bunların her biri için gösterilen tanıtıcıdır `Name` .

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

- Bir özelliğin başlangıç türü ve değeri henüz kurulu olmayan başka bir özelliğe bağlıdır. Örneğin, `.IDName = .LastName` zaten başlatılmamış olduğu müddetçe anonim tür bildiriminde geçerli değildir `.LastName` .

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  Bu örnekte, özelliklerinin bildirildiği sırayı tersine çevirerek sorunu çözebilirsiniz.

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- Anonim türün Özellik adı bir üyesinin adı ile aynıdır <xref:System.Object> . Örneğin, bir yöntemi olduğu için aşağıdaki bildirim başarısız olur `Equals` <xref:System.Object> .

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  Özellik adını değiştirerek sorunu çözebilirsiniz:

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](object-initializers-named-and-anonymous-types.md)
- [Yerel Tür Arabirimi](../variables/local-type-inference.md)
- [Anonim Türler](anonymous-types.md)
- [Anahtar](../../../language-reference/modifiers/key.md)

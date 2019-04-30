---
title: 'Nasıl yapılır: Özellik adları ve türleri (Visual Basic) anonim türde bildirimlerden çıkarma'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: be3c74e8f8c69eb9f0a1d0dda4d6c90dfd7e567a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760746"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Nasıl yapılır: Özellik adları ve türleri (Visual Basic) anonim türde bildirimlerden çıkarma
Anonim türler, doğrudan özellikleri veri türlerini belirtmek için bir mekanizma sağlar. Tüm özelliklerin türleri algılanır. Aşağıdaki örnekte, türlerini `Name` ve `Price` doğrudan bunları başlatmak için kullanılan değerlerden algılanır.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 Anonim türler, özellik adları ve türlerini diğer kaynaklardan da çıkarabilir. Aşağıdaki bölümlerde, çıkarım mümkün olduğu durumlarda ve nerede durumlara örnek olarak listesini sağlar.  
  
## <a name="successful-inference"></a>Başarılı çıkarımı  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Anonim türler, özellik adları ve türlerini aşağıdaki kaynaklardan çıkarabilir:  
  
- Değişken adları. Anonim tür `anonProduct` iki özelliği vardır `productName` ve `productPrice`. Bu özgün değişkenlerin veri türlerini olacaktır `String` ve `Double`sırasıyla.  
  
     [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]  
  
- Özellik veya alan adlarından diğer nesne. Örneğin, bir `car` nesnesinin bir `CarClass` içeren tür `Name` ve `ID` özellikleri. Yeni bir anonim tür örneği oluşturmak için `car1`, ile `Name` ve `ID` değerlerle başlatılan özellikleri `car` nesnesi, aşağıdakileri yazın:  
  
     [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]  
  
     Uzun anonim türü tanımlayan bir kod satırına önceki bildirime eşdeğerdir `car2`.  
  
     [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]  
  
- XML üye adları.  
  
     [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]  
  
     Sonuç türü `anon` bir özelliğe sahip `Book`, türü <xref:System.Collections.IEnumerable>, (XElement).  
  
- Hiçbir parametre gibi olan bir işlevden `SomeFunction` aşağıdaki örnekte.  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     Değişken `anon2` aşağıdaki kodda bir özellik, adlandırılmış bir karakter içeren bir anonim türdür `First`. Bu kodu bir harf "E", işlev tarafından döndürülen harf görüntüler <xref:System.Linq.Enumerable.First%2A>.  
  
     [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]  
  
## <a name="inference-failures"></a>Çıkarım hataları  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Aşağıdakiler dahil olmak üzere çoğu durumda, adı anlam çıkarma başarısız olur:  
  
- Çıkarım bir yöntemi, bir oluşturucu veya bağımsız değişken gerektirir parametreli bir özellik çağrısından türetilir. Önceki bildirimi `anon1` başarısız olur `someFunction` bir veya daha fazla bağımsız değişkenlere sahiptir.  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     Yeni bir özellik adı atama sorunu çözer.  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
- Çıkarım karmaşık bir ifadeden türetilir.  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     Hata, ifadenin sonucu bir özellik adına atayarak çözülebilir.  
  
     [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]  
  
- Birden çok özellik için çıkarım aynı ada sahip iki veya daha fazla özellik oluşturur. Geri bildirimleri önceki örneklerde başvuran, her ikisi de listelenemiyor `product.Name` ve `car1.Name` aynı anonim tür özellikleri. Bunların her biri için çıkarsanan tanımlayıcı olacağından budur `Name`.  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     Değerlerin benzersiz özellik adlarını atayarak sorun çözülebilir.  
  
     [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]  
  
     (Büyük ve küçük harfler arasında değişiklik) iki ad ayrı yapmayın durumunda değişiklikleri unutmayın.  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
- Bir özelliğin değerini ve başlangıç türü henüz kurulmasa başka bir özellikte bağlıdır. Örneğin, `.IDName = .LastName` bir anonim tür bildiriminde geçerli değil sürece `.LastName` zaten başlatıldı.  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     Bu örnekte, özelliklerini bildirilen sırasını ters çevirerek sorunu düzeltebilirsiniz.  
  
     [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]  
  
- Anonim türün bir özellik adı bir üyesinin adıyla aynı olduğu <xref:System.Object>. Örneğin, aşağıdaki bildirimi nedeniyle başarısız `Equals` bir yöntemidir <xref:System.Object>.  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     Özellik adını değiştirerek sorunu düzeltebilirsiniz:  
  
     [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)

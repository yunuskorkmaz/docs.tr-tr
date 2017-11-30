---
title: "Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 66b9f8c0346f74ff631969bda122de7913a551c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Nasıl yapılır: Anonim Türde Bildirimlerden Özellik Adları ve Türlerini Çıkarma (Visual Basic)
Anonim türler doğrudan özellikleri veri türlerini belirtmek için bir mekanizma sağlar. Tüm özelliklerin türleri algılanır. Aşağıdaki örnekte, türlerini `Name` ve `Price` doğrudan bunları başlatmak için kullanılan değerlerinden algılanır.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 Anonim türler de özellik adları ve diğer kaynaklardan türlerinin çıkarımını. Aşağıdaki bölümlerde çıkarım mümkün olduğu durumlarda ve değil olduğu durumlar örnekleri listesini sağlar.  
  
## <a name="successful-inference"></a>Başarılı çıkarımı  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Anonim türleri, özellik adları ve türlerini aşağıdaki kaynaklardan çıkarımını:  
  
-   Değişken adları. Anonim tür `anonProduct` iki özelliği vardır `productName` ve `productPrice`. Veri türlerini olanlar özgün değişkenlerin olacaktır `String` ve `Double`sırasıyla.  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   Özellik veya alan adlarından diğer nesnelerin. Örneğin, göz önünde bulundurun bir `car` nesnesinin bir `CarClass` içeren türü `Name` ve `ID` özellikleri. Yeni bir anonim tür örneği oluşturmak için `car1`, ile `Name` ve `ID` değerlerle başlatılan özellikleri `car` nesnesi, aşağıdakileri yazın:  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     Uzun kod satırı ile anonim tür tanımlayan için yukarıdaki bildirimi eşdeğerdir `car2`.  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   XML üye adları.  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     Sonuç türü için `anon` bir özellik olması gereken `Book`, türü <xref:System.Collections.IEnumerable>, (XElement).  
  
-   Hiçbir parametre gibi sahip bir işlevden `SomeFunction` aşağıdaki örnekte.  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     Değişkeni `anon2` aşağıdaki kodda bir özellik, adlandırılmış bir karakter içeren bir anonim türüdür `First`. Bu kodu bir harf "E", işlev tarafından döndürülen harf görüntüler <xref:System.Linq.Enumerable.First%2A>.  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a>Çıkarım hataları  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Ad çıkarım, aşağıdakiler de dahil olmak üzere çoğu durumda, başarısız olur:  
  
-   Çıkarım bir yöntemi, bir oluşturucu ya da bağımsız değişkenler gerektirir parametreli bir özelliğin çağrısından türer. Önceki bildirimi `anon1` başarısız olur `someFunction` bir veya daha fazla bağımsız değişkenlere sahiptir.  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     Yeni bir özellik adı atamayı sorununu çözer.  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   Çıkarım karmaşık bir ifade türer.  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     Hata, bir özellik adı ifadenin sonucu atayarak çözülebilir.  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   Çıkarım birden çok özellikler için aynı ada sahip iki veya daha fazla özellik üretir. Önceki örneklerde bildirimleri geri başvurma, her ikisi de listelenemiyor `product.Name` ve `car1.Name` özellikleri aynı anonim tür olarak. Bunların her biri için oluşturulursa tanımlayıcı olacağından budur `Name`.  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     Farklı özellik adları için değerler atayarak sorun çözülebilir.  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     (Büyük ve küçük harfler arasında) iki ad ayrı değişiklik yapmayın durumunda değişiklikler unutmayın.  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   Bir özelliğin değerini ve başlangıç türünü henüz kurulmadığı başka bir özellikte bağlıdır. Örneğin, `.IDName = .LastName` anonim tür bildiriminde geçersiz sürece `.LastName` zaten başlatılmış.  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     Bu örnekte, Özellikler bildirilen sıraya döndürerek sorunu düzeltebilirsiniz.  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   Anonim türün bir özellik adı adı bir üyesi olarak aynıdır <xref:System.Object>. Örneğin, çünkü aşağıdaki bildirimi başarısız `Equals` bir yöntemi <xref:System.Object>.  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     Özellik adı değiştirerek sorunu düzeltebilir:  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Anahtarı](../../../../visual-basic/language-reference/modifiers/key.md)

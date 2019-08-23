---
title: Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: 0683047865f520a09b2d2fe196096286b7d78714
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965390"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma (Visual Basic)
Çoğu durumda, tasarım zamanında bir nesnenin özelliklerini ve yöntemlerini bulabilir ve bunları işlemek için kod yazabilirsiniz. Ancak, bazı durumlarda bir nesnenin özellikleri ve yöntemleri önceden bilmiyor olabilir ya da bir son kullanıcının çalışma zamanında Özellikler belirtmesini veya yöntem yürütmesini sağlama esnekliğini isteyebilirsiniz.  
  
## <a name="callbyname-function"></a>CallByName Işlevi  
 Örneğin, bir COM bileşenine işleç geçirerek Kullanıcı tarafından girilen ifadeleri değerlendiren bir istemci uygulaması gibi düşünün. Yeni işleçler gerektiren bileşene sürekli olarak yeni işlevler eklediğinizi varsayalım. Standart nesne erişim tekniklerini kullandığınızda, istemci uygulamasını yeni işleçleri kullanabilmesi için yeniden derlemeniz ve yeniden dağıtmanız gerekir. Bunu önlemek için, uygulamayı değiştirmeden yeni işleçleri `CallByName` dizeler olarak geçirmek için işlevini kullanabilirsiniz.  
  
 İşlevi `CallByName` , çalışma zamanında bir özelliği veya yöntemi belirtmek için bir dize kullanmanıza olanak sağlar. `CallByName` İşlevin imzası şöyle görünür:  
  
 Sonuç = (nesne, procedurename, çağrı türü, bağımsız değişkenler ())`CallByName`  
  
 İlk bağımsız değişken, *nesne*, üzerinde işlem yapmak istediğiniz nesnenin adını alır. *Procedurename* bağımsız değişkeni çağrılacak yöntemin veya özellik yordamının adını içeren bir dize alır. *CallType* bağımsız değişkeni, çağrılacak yordamın türünü temsil eden bir sabit alır: bir Yöntem (`Microsoft.VisualBasic.CallType.Method`), bir özellik okuma (`Microsoft.VisualBasic.CallType.Get`) veya özellik kümesi (`Microsoft.VisualBasic.CallType.Set`). İsteğe bağlı bağımsız değişken bağımsız değişkeni, yordamda herhangi bir bağımsız değişken içeren `Object` türünde bir dizi alır.  
  
 Geçerli çözümünüzdeki sınıflarla `CallByName` kullanabilirsiniz, ancak genellikle .NET Framework derlemelerden com nesnelerine veya nesnelere erişmek için kullanılır.  
  
 Aşağıdaki kodda gösterildiği gibi adlı `MathClass` `SquareRoot`yeni bir işleve sahip adlı bir sınıfı içeren bir derlemeye başvuru eklediğinizi varsayalım:  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 Uygulamanız, hangi yöntemin çağrdığını ve bağımsız değişkenlerini denetlemek için metin kutusu denetimlerini kullanabilir. Örneğin, `TextBox1` değerlendirilecek ifadeyi içeriyorsa ve `TextBox2` işlevin adını girmek için kullanılırsa, içindeki `TextBox1`ifadesinde `SquareRoot` işlevini çağırmak için aşağıdaki kodu kullanabilirsiniz:  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 `TextBox1`İçinde "64", "SquareRoot `TextBox2`" yazın ve sonra `CallMath` yordamı çağırın, içindeki `TextBox1` sayının kare kökü değerlendirilir. Örnekteki kod, `SquareRoot` işlevini çağırır (gerekli bağımsız değişken olarak değerlendirilecek ifadeyi içeren bir dize alır) ve içinde `TextBox1` "8" döndürür (64 kare kökü). Kuşkusuz, Kullanıcı içinde `TextBox2`geçersiz bir dize girerse, dize bir yöntem yerine bir özelliğin adını içeriyorsa veya metotta gerekli ek bir bağımsız değişken varsa, bir çalışma zamanı hatası oluşur. Bunları veya diğer hataları tahmin etmek için kullandığınızda `CallByName` sağlam hata işleme kodu eklemeniz gerekir.  
  
> [!NOTE]
> İşlev bazı durumlarda faydalı olabilir, ancak bir yordamı çağırmak için kullanmak `CallByName` , geç bağlantılı çağrıdan biraz daha yavaştır. `CallByName` Döngü içinde olduğu gibi, tekrar tekrar çağrılan bir işlevi çağırdıysanız, `CallByName` performansı önemli bir etkiye sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [Nesne Türünü Belirleme](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)

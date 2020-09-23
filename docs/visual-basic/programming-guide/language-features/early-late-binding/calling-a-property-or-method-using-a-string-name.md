---
title: Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma
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
ms.openlocfilehash: 9f28548c27545d94dde38cef3e9c56f98a69b259
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086094"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma (Visual Basic)

Çoğu durumda, tasarım zamanında bir nesnenin özelliklerini ve yöntemlerini bulabilir ve bunları işlemek için kod yazabilirsiniz. Ancak, bazı durumlarda bir nesnenin özellikleri ve yöntemleri önceden bilmiyor olabilir ya da bir son kullanıcının çalışma zamanında Özellikler belirtmesini veya yöntem yürütmesini sağlama esnekliğini isteyebilirsiniz.  
  
## <a name="callbyname-function"></a>CallByName Işlevi  

 Örneğin, bir COM bileşenine işleç geçirerek Kullanıcı tarafından girilen ifadeleri değerlendiren bir istemci uygulaması gibi düşünün. Yeni işleçler gerektiren bileşene sürekli olarak yeni işlevler eklediğinizi varsayalım. Standart nesne erişim tekniklerini kullandığınızda, istemci uygulamasını yeni işleçleri kullanabilmesi için yeniden derlemeniz ve yeniden dağıtmanız gerekir. Bunu önlemek için, `CallByName` uygulamayı değiştirmeden yeni işleçleri dizeler olarak geçirmek için işlevini kullanabilirsiniz.  
  
 `CallByName`İşlevi, çalışma zamanında bir özelliği veya yöntemi belirtmek için bir dize kullanmanıza olanak sağlar. İşlevin imzası şöyle `CallByName` görünür:  
  
 *Result*  =  Sonuç `CallByName` (*Object*, *procedurename*, *CallType*, *arguments*())  
  
 İlk bağımsız değişken, *nesne*, üzerinde işlem yapmak istediğiniz nesnenin adını alır. *Procedurename* bağımsız değişkeni çağrılacak yöntemin veya özellik yordamının adını içeren bir dize alır. *CallType* bağımsız değişkeni, çağrılacak yordamın türünü temsil eden bir sabit alır: bir Yöntem ( `Microsoft.VisualBasic.CallType.Method` ), bir özellik okuma ( `Microsoft.VisualBasic.CallType.Get` ) veya özellik kümesi ( `Microsoft.VisualBasic.CallType.Set` ). İsteğe *bağlı bağımsız değişken bağımsız değişkeni,* `Object` yordamda herhangi bir bağımsız değişken içeren türünde bir dizi alır.  
  
 `CallByName`Geçerli çözümünüzdeki sınıflarla kullanabilirsiniz, ancak genellikle .NET Framework DERLEMELERDEN com nesnelerine veya nesnelere erişmek için kullanılır.  
  
 `MathClass`Aşağıdaki kodda gösterildiği gibi adlı yeni bir işleve sahip adlı bir sınıfı içeren bir derlemeye başvuru eklediğinizi varsayalım `SquareRoot` :  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 Uygulamanız, hangi yöntemin çağrdığını ve bağımsız değişkenlerini denetlemek için metin kutusu denetimlerini kullanabilir. Örneğin, `TextBox1` değerlendirilecek ifadeyi içeriyorsa ve `TextBox2` işlevin adını girmek için kullanılırsa, `SquareRoot` içindeki ifadesinde işlevini çağırmak için aşağıdaki kodu kullanabilirsiniz `TextBox1` :  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 İçinde "64" `TextBox1` , "SquareRoot" yazın `TextBox2` ve sonra `CallMath` yordamı çağırın, içindeki sayının kare kökü `TextBox1` değerlendirilir. Örnekteki kod, `SquareRoot` işlevini çağırır (gerekli bağımsız değişken olarak değerlendirilecek ifadeyi içeren bir dize alır) ve içinde "8" döndürür `TextBox1` (64 kare kökü). Kuşkusuz, Kullanıcı içinde geçersiz bir dize girerse, `TextBox2` dize bir yöntem yerine bir özelliğin adını içeriyorsa veya metotta gerekli ek bir bağımsız değişken varsa, bir çalışma zamanı hatası oluşur. `CallByName`Bunları veya diğer hataları tahmin etmek için kullandığınızda sağlam hata işleme kodu eklemeniz gerekir.  
  
> [!NOTE]
> `CallByName`İşlev bazı durumlarda faydalı olabilir, ancak `CallByName` bir yordamı çağırmak için kullanmak, geç bağlantılı çağrıdan biraz daha yavaştır. Döngü içinde olduğu gibi, tekrar tekrar çağrılan bir işlevi çağırdıysanız, `CallByName` performansı önemli bir etkiye sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [Nesne Türünü Belirleme](determining-object-type.md)

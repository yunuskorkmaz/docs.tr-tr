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
ms.openlocfilehash: cb584f0dfbd905ca071f9a86b1eab231f3017538
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345204"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma (Visual Basic)
Çoğu durumda, tasarım zamanında bir nesnenin özelliklerini ve yöntemlerini bulabilir ve bunları işlemek için kod yazabilirsiniz. Ancak, bazı durumlarda bir nesnenin özellikleri ve yöntemleri önceden bilmiyor olabilir ya da bir son kullanıcının çalışma zamanında Özellikler belirtmesini veya yöntem yürütmesini sağlama esnekliğini isteyebilirsiniz.  
  
## <a name="callbyname-function"></a>CallByName Işlevi  
 Örneğin, bir COM bileşenine işleç geçirerek Kullanıcı tarafından girilen ifadeleri değerlendiren bir istemci uygulaması gibi düşünün. Yeni işleçler gerektiren bileşene sürekli olarak yeni işlevler eklediğinizi varsayalım. Standart nesne erişim tekniklerini kullandığınızda, istemci uygulamasını yeni işleçleri kullanabilmesi için yeniden derlemeniz ve yeniden dağıtmanız gerekir. Bunu önlemek için `CallByName` işlevini kullanarak, uygulamayı değiştirmeden yeni işleçleri dizeler olarak geçirebilirsiniz.  
  
 `CallByName` işlevi, çalışma zamanında bir özelliği veya yöntemi belirtmek için bir dize kullanmanıza olanak sağlar. `CallByName` işlevi için imza şöyle görünür:  
  
 *Sonuç* = `CallByName`(*nesne*, *procedurename*, *çağrı türü*, *bağımsız değişkenler*())  
  
 İlk bağımsız değişken, *nesne*, üzerinde işlem yapmak istediğiniz nesnenin adını alır. *Procedurename* bağımsız değişkeni çağrılacak yöntemin veya özellik yordamının adını içeren bir dize alır. *CallType* bağımsız değişkeni, çağrılacak yordamın türünü temsil eden bir sabit alır: bir yöntem (`Microsoft.VisualBasic.CallType.Method`), bir özellik okuma (`Microsoft.VisualBasic.CallType.Get`) veya özellik kümesi (`Microsoft.VisualBasic.CallType.Set`). İsteğe *bağlı bağımsız değişken bağımsız değişkeni,* yordamda herhangi bir bağımsız değişken içeren `Object` türünde bir dizi alır.  
  
 `CallByName`, geçerli çözümünüzdeki sınıflarla kullanabilirsiniz, ancak genellikle COM nesnelerine veya .NET Framework derlemelerinden nesnelere erişmek için kullanılır.  
  
 Aşağıdaki kodda gösterildiği gibi, `SquareRoot`adlı yeni bir işleve sahip `MathClass`adlı bir sınıf içeren bir derlemeye başvuru eklediğinizi varsayalım:  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 Uygulamanız, hangi yöntemin çağrdığını ve bağımsız değişkenlerini denetlemek için metin kutusu denetimlerini kullanabilir. Örneğin, `TextBox1` değerlendirilecek ifadeyi içeriyorsa ve işlevin adını girmek için `TextBox2` kullanılırsa, `TextBox1`ifadesinde `SquareRoot` işlevini çağırmak için aşağıdaki kodu kullanabilirsiniz:  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 `TextBox1`"64", `TextBox2`' de "SquareRoot" girin ve ardından `CallMath` yordamını çağırırsanız, `TextBox1` içindeki sayının kare kökü değerlendirilir. Örnekteki kod, `SquareRoot` işlevini çağırır (gerekli bağımsız değişken olarak değerlendirilecek ifadeyi içeren bir dize alır) ve `TextBox1` içinde "8" döndürür (64 kare kökü). Kuşkusuz, Kullanıcı `TextBox2`' de geçersiz bir dize girerse, dize bir yöntem yerine bir özelliğin adını içeriyorsa veya metotta gerekli ek bir bağımsız değişken varsa, bir çalışma zamanı hatası oluşur. Bunu veya diğer hataları tahmin etmek için `CallByName` kullandığınızda sağlam hata işleme kodu eklemeniz gerekir.  
  
> [!NOTE]
> `CallByName` işlevi bazı durumlarda faydalı olabilirken, bir yordamı çağırmak için `CallByName` kullanarak bir yordamı geç bağlantılı çağrıdan biraz daha yavaştır. Döngü içinde olduğu gibi sürekli olarak çağrılan bir işlevi çağırdıysanız `CallByName` performans üzerinde ciddi bir etkiye sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [Nesne Türünü Belirleme](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)

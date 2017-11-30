---
title: "Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5974257fb82fe83c66a480225da200c14338898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma (Visual Basic)
Çoğu durumda, özellikleri ve yöntemleri bir nesnenin tasarım zamanında bulun ve bunları işlemek için kod yazın. Ancak, bazı durumlarda, nesnenin özellikleri ve yöntemleri hakkında önceden bilemeyebilirsiniz veya yalnızca bir son kullanıcının özelliklerini belirtin veya çalışma zamanında bir yöntem yürütülemez etkinleştirme esnekliğini isteyebilirsiniz.  
  
## <a name="callbyname-function"></a>CallByName işlevi  
 , Örneğin, bir COM bileşeni için bir işleç geçirerek kullanıcı tarafından girilen ifadeleri değerlendiren bir istemci uygulaması göz önünde bulundurun. Yeni işlevleri yeni işleçleri gerektiren bileşenine sürekli ekleme varsayalım. Standart nesne erişim tekniklerini kullandığınızda, yeniden derleyin ve yeni işleçleri kullanabilirsiniz önce istemci uygulaması yeniden dağıtın. Bu durumu önlemek için kullanabileceğiniz `CallByName` uygulamayı değiştirmeden yeni işleçler dize olarak geçirmek için işlevi.  
  
 `CallByName` İşlevi çalışma zamanında bir özelliği veya yöntemi belirtmek için bir dize kullanmanıza imkan tanır. İmza için `CallByName` işlevi şu şekilde görünür:  
  
 *Sonuç* = `CallByName`(*nesne*, *ProcedureName*, *CallType*, *bağımsız değişkenleri*())  
  
 İlk bağımsız değişken *nesne*, görev istediğiniz nesne adını alır. *ProcedureName* bağımsız değişkeni çağrılacak yöntemi veya özelliği yordamın adını içeren bir dize alır. *CallType* çağırmak için yordamı türünü temsil eden sabit bağımsız değişkeni alır: bir yöntem (`Microsoft.VisualBasic.CallType.Method`), bir özelliğin okuma (`Microsoft.VisualBasic.CallType.Get`), veya bir özellik kümesi (`Microsoft.VisualBasic.CallType.Set`). *Bağımsız değişkenleri* isteğe bağlıdır, bağımsız değişkeni alır türünde bir dizi `Object` yordamı için herhangi bir bağımsız değişken içeriyor.  
  
 Kullanabileceğiniz `CallByName` sınıflarıyla geçerli çözümünüzün, ancak çoğunlukla COM nesneleri erişmek için kullanılan veya nesnelerin [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler.  
  
 Adlı bir sınıf içeren bir derleme başvurusu Ekle varsayalım `MathClass`, adında yeni bir işlevi olan `SquareRoot`aşağıdaki kodda gösterildiği gibi:  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 Uygulamanızın hangi yöntemi adlı Denetim ve bağımsız değişkenleri için metin kutusu denetimleri kullanabilirsiniz. Örneğin, varsa `TextBox1` değerlendirilecek ifade içerir ve `TextBox2` olan işlevin adını girmek için kullanılan, çağırmak için aşağıdaki kodu kullanabilirsiniz `SquareRoot` ifade işlevini `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 İçindeki "64" girerseniz `TextBox1`, "SquareRoot" `TextBox2`ve ardından arama `CallMath` yordamı, sayısının kare kökünü `TextBox1` değerlendirilir. Örnek kodda çağırır `SquareRoot` (gerekli bir bağımsız değişken olarak değerlendirilecek ifade içeren bir dize aldığı) işlev ve "8" döndürür `TextBox1` (64 kare kökünü). Kuşkusuz kullanıcı geçersiz bir dize girerse `TextBox2`, bir yöntem yerine bir özellik adı dize içeriyor ya da yöntemi ek gerekli bağımsız değişken varsa, bir çalışma zamanı hatası oluşur. Kullandığınızda sağlam hata işleme kodu eklemek zorunda `CallByName` bu veya başka bir hatalar tahmin için.  
  
> [!NOTE]
>  Sırada `CallByName` işlevi bazı durumlarda yararlı olabilir, kendi yararlılığını performans etkileri karşı tartmanız gerekir — kullanarak `CallByName` bir yordam çağırma için geç bağlama çağrı kısmen daha yavaştır. Gibi bir döngü olduğu gibi içinde tekrar tekrar çağrılan işlev çağırma varsa `CallByName` performans üzerinde ciddi bir etkisi olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [Nesne türünü belirleme](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)

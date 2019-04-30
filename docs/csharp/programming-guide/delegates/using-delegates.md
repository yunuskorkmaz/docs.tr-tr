---
title: -Kullanma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: eb5721d1c04ad761821bcdae03159f290a802ec0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711167"
---
# <a name="using-delegates-c-programming-guide"></a>Temsilcileri Kullanma (C# Programlama Kılavuzu)
A [temsilci](../../../csharp/language-reference/keywords/delegate.md) güvenli bir şekilde C ve C++ içindeki işlev işaretçisine benzer bir yöntem kapsülleyen bir türdür. C işlev işaretçilerinden farklı nesne yönelimli Temsilciler, korunmasına ve güvende yazın. Bir temsilci türü, temsilcinin adına göre tanımlanır. Aşağıdaki örnek bildirir adlandırılmış bir temsilci `Del` alan bir metodu kapsüllemek bir [dize](../../../csharp/language-reference/keywords/string.md) bağımsız değişken ve döndürür olarak [void](../../../csharp/language-reference/keywords/void.md):  
  
 [!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]  
  
 Bir temsilci nesnesinin normalde tarafından yöntemin adını temsilci kaydırılır sağlanması veya ile oluşturulan bir [anonim yöntem](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md). Bir temsilci oluşturulduktan sonra yöntem için temsilci atamak için yapılan bir yöntem çağrısının, temsilci tarafından geçirilir. Temsilciye çağıran tarafından geçirilen parametreler yöntemine geçirilir ve dönüş değeri varsa, yöntemini çağırana temsilci tarafından döndürülür. Bu temsilci çağırma olarak bilinir. Örneklenmiş bir temsilci Sarmalanan yöntem gibi çağrılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  
  
 [!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]  
  
 Temsilci türleri türetilir <xref:System.Delegate> .NET Framework sınıfı. Temsilci türleri [korumalı](../../../csharp/language-reference/keywords/sealed.md)— bunlar türetilemeyeceğini — ve özel sınıflarından mümkün değildir <xref:System.Delegate>. Örneklenen temsilci bir nesne olduğundan, bir parametre olarak geçirilen veya yükleyebilir bir özelliğine atanır. Bu temsilci bir parametre olarak kabul edin ve daha sonra temsilci çağrısı için bir yöntem sağlar. Bu durum, zaman uyumsuz bir geri arama olarak bilinir ve uzun bir işlem tamamlandığında, çağıran bildiren yaygın bir yöntemdir. Bir temsilci bu şekilde kullanıldığında temsilci kullanarak kodu bilgisine kullanılan yöntemin uygulanmasını sahip olması gerekmez. İşlevi, kapsülleme arabirimleri sağlamak için benzer.  
  
 Geri çağırmaları başka bir yaygın kullanımı özel karşılaştırma yöntemi tanımlayan ve bu temsilciyi bir sıralama yöntemine geçirerek. Arayanın kod Sıralama algoritması bir parçası haline sağlar. Aşağıdaki örnek yöntemini kullanan `Del` türü bir parametre olarak:  
  
 [!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]  
  
 Ardından, yöntem için yukarıda oluşturulan temsilci geçirebilirsiniz:  
  
 [!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]  
  
 ve aşağıdaki konsola çıktı alırsınız:  
  
 `The number is: 3`  
  
 Bir Özet, temsilci kullanarak `MethodWithCallback` konsol doğrudan çağırmanız gerekmez; aklınızda bir konsolu ile tasarlanmış olması gerekmez. Hangi `MethodWithCallback` mu yalnızca bir dize hazırlamak ve dize başka yönteme geçirin. Temsil edilen bir yöntem parametreleri herhangi bir sayıda kullanabildiğinden özellikle güçlüdür.  
  
 Bir örnek yöntemi sarmak için bir temsilci oluşturulduğunda, temsilci örneği hem yöntemi başvuruyor. Bir temsilci sarmaladığı, yöntemin yanı sıra örnek türü olanağıyla olduğundan var olduğu sürece bir yöntemi temsilci imzayla eşleşen söz konusu nesne üzerinde bir temsilci herhangi bir nesne türüne başvuruda bulunabilir. Statik bir yöntem sarmak için bir temsilci oluşturulduğunda yöntemi yalnızca başvuruyor. Aşağıdaki bildirimleri dikkate alın:  
  
 [!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]  
  
 Statik birlikte `DelegateMethod` daha önce gösterilen, şimdi tarafından Sarmalanan üç yöntem vardır bir `Del` örneği.  
  
 Temsilci çağrıldığında birden fazla yöntem çağırabilirsiniz. Bu, çok noktaya yayın adlandırılır. Ek bir yöntem temsilcinin yöntemleri listesine eklemek için — çağırma listesi — yalnızca eklenmesi veya toplama atama işleçleri kullanarak iki temsilcileri ekleme gerektirir ('+' veya '+='). Örneğin:  
  
 [!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]  
  
 Bu noktada `allMethodsDelegate` çağırma listesinde üç yöntem içerir —`Method1`, `Method2`, ve `DelegateMethod`. Özgün üç Temsilciler `d1`, `d2`, ve `d3`, değişmeden kalır. Zaman `allMethodsDelegate` olan çağrılır, tüm üç yöntem sırayla çağrılır. Temsilci başvuru parametrelerini kullanıyorsa, başvuru sırayla her üç yöntemi sırayla geçirilir ve sonraki yönteme değişiklikleri bir yöntem tarafından görülebilir. Ne zaman yöntemlerden herhangi birini, bir yöntem içinde yakalanmamış bir özel durum oluşturursa temsilci ve çağırma listesi sonraki hiçbir yöntemleri çağıran özel durum geçirilecek denir. Temsilci bir dönüş değeri varsa ve/veya out parametreleri, çağrılan son yönteminin parametreleri ve dönüş değeri döndürür. Bir yöntem çağırma listeden kaldırmak için azaltma kullanın veya azaltma atama işleci ('-' veya '-= '). Örneğin:  
  
 [!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]  
  
 Temsilci türleri türetildiği `System.Delegate`, bu sınıf tarafından tanımlanan özellikler ve yöntemler temsilcisindeki çağrılabilir. Örneğin, bir temsilcinin çağırma listesine bir dizi yöntem bulmak için yazabilirsiniz:  
  
 [!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]  
  
 Temsilciler, çağırma listesinde birden fazla yöntemiyle türetilen <xref:System.MulticastDelegate>, öğesinin olduğu `System.Delegate`. Yukarıdaki kod, her iki durumda da çalışır, hem sınıflarını desteklediğinden `GetInvocationList`.  
  
 Çok noktaya yayın temsilcileri olay işlemede, yaygın olarak kullanılır. Olay kaynağı nesneleri olay almak için kayıtlı alıcı nesnelere olay bildirimleri gönderin. Bir etkinliğe kaydolmak için alıcının olayı işlemek için tasarlanmış bir metot oluşturur sonra bu yöntem için bir temsilci oluşturur ve temsilci olay kaynağına geçirir. Olay gerçekleştiğinde kaynak temsilcisini çağırır. Temsilci daha sonra olay işleme alıcı olay verilerini teslim yöntemini çağırır. Belirli bir olayın temsilci türü olay kaynağına göre tanımlanır. Daha fazla bilgi için bkz: [olayları](../../../csharp/programming-guide/events/index.md).  
  
 Derleme zamanında atanan iki farklı türden temsilciler karşılaştıran bir derleme hatasına neden olur. Temsilci örneklerini statik türde ise `System.Delegate`, ardından karşılaştırma izin verilir, ancak, dönüş false çalışır süresi. Örneğin:  
  
 [!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
- [Temsilcilerde Varyans Kullanma](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Temsilcilerde Varyans](../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [İşlev ve Eylem Genel Temsilcileri için Varyans Kullanma](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Olaylar](../../../csharp/programming-guide/events/index.md)

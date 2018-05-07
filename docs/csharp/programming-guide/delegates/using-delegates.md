---
title: Temsilcileri Kullanma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: b27c94570fdf76808e8a7df67b34466bde20de7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-delegates-c-programming-guide"></a>Temsilcileri Kullanma (C# Programlama Kılavuzu)
A [temsilci](../../../csharp/language-reference/keywords/delegate.md) güvenli bir yöntem, benzer bir işlev işaretçisi C ve C++ için yalıtır türüdür. Aksine C işlev işaretçileri, nesne yönelimli Temsilciler, güvenli ve güvenli yazın. Bir temsilci türü temsilci adına göre tanımlanır. Aşağıdaki örnek, adlandırılmış bir temsilci bildirir `Del` geçen bir yöntem kapsülleyen bir [dize](../../../csharp/language-reference/keywords/string.md) bağımsız değişken ve döndürür [void](../../../csharp/language-reference/keywords/void.md):  
  
 [!code-csharp[csProgGuideDelegates#21](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_1.cs)]  
  
 Temsilci nesnesini normalde tarafından yöntemin adını temsilci kaydırılır sağlanması veya ile oluşturulan bir [anonim yöntemi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md). Bir temsilci oluşturulduktan sonra temsilciye yapılan bir yöntem çağrısı için bu yöntem temsilci tarafından geçirilir. Temsilciye çağıran tarafından geçirilen parametreler yönteme geçirilen ve dönüş değeri varsa, yönteminden çağırana temsilci tarafından döndürülür. Bu temsilci çağırma olarak bilinir. Sarmalanan yöntemi değilmiş gibi başlatılan bir temsilci çağrılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideDelegates#22](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_2.cs)]  
  
 [!code-csharp[csProgGuideDelegates#23](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_3.cs)]  
  
 Temsilci türleri türetilir <xref:System.Delegate> .NET Framework sınıf. Temsilci türleri [korumalı](../../../csharp/language-reference/keywords/sealed.md)— bunlar türetilemez — ve özel sınıflarından mümkün değildir <xref:System.Delegate>. Örneklenen temsilci bir nesne olduğundan, parametre olarak geçirilen veya yükleyebilir bir özelliğine atanır. Bu temsilci bir parametre olarak kabul edin ve daha sonraki bir zamanda temsilci çağırmak bir yöntem sağlar. Bu zaman uyumsuz bir geri çağırma bilinir ve uzun bir işlem tamamlandığında, çağıran bildiren yaygın bir yöntemdir. Bu biçimde bir temsilci kullanıldığında, temsilci kullanarak kod kullanılan yöntemin kullanımı bilgisi gerekmez. Arabirimleri sağlamak kapsülleme benzer bir işlevdir.  
  
 Geri aramalar başka bir yaygın kullanımı bir özel karşılaştırma yöntemi tanımlama ve bu temsilciyi bir sıralama yöntemi geçirme. Arayanın kod Sıralama algoritması parçası olmasını sağlar. Aşağıdaki örnek yöntemi kullanan `Del` türünü bir parametre olarak:  
  
 [!code-csharp[csProgGuideDelegates#24](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_4.cs)]  
  
 Ardından, bu yönteme yukarıda oluşturduğunuz temsilci geçirebilirsiniz:  
  
 [!code-csharp[csProgGuideDelegates#25](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_5.cs)]  
  
 ve konsola çıktı aşağıdaki alırsınız:  
  
 `The number is: 3`  
  
 Bir Özet, temsilci kullanarak `MethodWithCallback` konsol doğrudan çağırmanız gerekmez — bir konsol aklınızda tasarlanmalıdır yok. Ne `MethodWithCallback` değil yalnızca bir dize hazırlamak ve dize başka bir yönteme geçirin. Temsil edilen bir yöntem parametreleri herhangi bir sayıda kullanabildiğiniz özellikle güçlüdür.  
  
 Örnek yöntemi sarmalamak için bir temsilci oluşturulduğunda temsilci hem örneği hem de yöntemi başvurur. Bir temsilci sarmaladığı, yöntemi yanı sıra örnek türü olanağıyla sahiptir, bu nedenle var olduğu sürece bir yöntem temsilci imza eşleşen nesnede bir temsilci nesne türüne başvuruda bulunabilir. Bir statik yöntem sarmalamak için bir temsilci oluşturulduğunda, yalnızca yöntemi başvurur. Aşağıdaki bildirimleri dikkate alın:  
  
 [!code-csharp[csProgGuideDelegates#26](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_6.cs)]  
  
 Statik birlikte `DelegateMethod` daha önce gösterilen şimdi tarafından Sarmalanan üç yöntem sahip olduğumuz bir `Del` örneği.  
  
 Bir temsilci çağrıldığında birden fazla yöntemini çağırabilirsiniz. Bu, çok noktaya yayın adlandırılır. Ek bir yöntem temsilcinin yöntemleri listesine eklemek için — çağırma listesi — yalnızca eklenmesi veya toplama atama işleçleri kullanarak iki temsilcileri ekleme gerektirir ('+' veya '+='). Örneğin:  
  
 [!code-csharp[csProgGuideDelegates#27](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_7.cs)]  
  
 Bu noktada `allMethodsDelegate` çağırma listesinde üç yöntem içerir —`Method1`, `Method2`, ve `DelegateMethod`. Özgün üç temsilcileri `d1`, `d2`, ve `d3`, değişmeden kalır. Zaman `allMethodsDelegate` olan çağrılır, tüm üç yöntem sırada çağrılır. Temsilci başvuru parametreleri kullanıyorsa, başvuru sırayla her üç yöntem sırayla geçirilir ve sonraki yönteme değişiklikleri bir yöntem tarafından görülebilir. Ne zaman yöntemlerinden herhangi birini yöntemi içinde yakalandı bir özel durumları oluşturur temsilci ve hiçbir sonraki yöntemi çağırma listesinde çağıran özel durum geçirilecek çağrılır. Temsilci dönüş değeri varsa ve/veya out parametreleri, çağrılan son yönteminin parametrelerini ve dönüş değeri döndürür. Bir yöntemi çağırma listesinden kaldırmak için azaltma kullanın veya azaltma atama işleci ('-' veya ' '-=''). Örneğin:  
  
 [!code-csharp[csProgGuideDelegates#28](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_8.cs)]  
  
 Temsilci türleri türetilmiş çünkü `System.Delegate`, bu sınıf tarafından tanımlanan özellikler ve yöntemler temsilci üzerinde çağrılabilir. Örneğin, bir temsilcinin çağırma listesinde yöntemleri sayısını bulmak için yazabilirsiniz:  
  
 [!code-csharp[csProgGuideDelegates#29](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_9.cs)]  
  
 Temsilcileri kendi çağırma listesinde birden fazla yöntemiyle türetilen <xref:System.MulticastDelegate>, öğesinin bir alt kümesi olan `System.Delegate`. Yukarıdaki kod her iki durumda da çalışır ve her iki sınıflarını destekleyen çünkü `GetInvocationList`.  
  
 Çok noktaya yayın temsilcileri olay işlemede yaygın olarak kullanılır. Olay kaynağı nesneleri olay almak için kayıtlı alıcı nesnelere olay bildirimleri gönderin. İçin bir olay kaydetmek için alıcı olayını işlemek için tasarlanmış bir yöntem oluşturur sonra bu yöntem için bir temsilci oluşturur ve olay kaynağı temsilci geçirir. Olay gerçekleştiğinde kaynak temsilcisini çağırır. Temsilci daha sonra olay işleme alıcı olay verileri teslim yöntemini çağırır. Temsilci türü için belirli bir olayın olay kaynağına göre tanımlanır. Daha fazla bilgi için bkz: [olayları](../../../csharp/programming-guide/events/index.md).  
  
 Derleme zamanında atanan iki farklı türlerde temsilciler karşılaştırma bir derleme hataya neden olur. Temsilci örnekleri statik olarak türdeyse `System.Delegate`sonra karşılaştırma izin verilir, ancak en false döndürür çalışır zaman. Örneğin:  
  
 [!code-csharp[csProgGuideDelegates#30](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_10.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [Temsilcilerde Varyans Kullanma](http://msdn.microsoft.com/library/e6acad03-93e0-4efb-a158-8696d5eb4ecf)  
 [Temsilcilerde Varyans](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)  
 [İşlev ve Eylem Genel Temsilcileri için Varyans Kullanma](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290)  
 [Olaylar](../../../csharp/programming-guide/events/index.md)

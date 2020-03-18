---
title: Temsilci Kullanma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: dcc73aba738d6296a44c48aad8b66cd6fc7f4a7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77448445"
---
# <a name="using-delegates-c-programming-guide"></a>Temsilcileri Kullanma (C# Programlama Kılavuzu)

[Temsilci,](../../language-reference/builtin-types/reference-types.md) C ve C++'daki işlev işaretçisine benzer bir yöntemi güvenli bir şekilde kapsülleyen bir türdür. C işlev işaretçilerinin aksine, temsilciler nesne yönelimli, yazı güvenli ve güvenlidir. Temsilcinin türü, temsilcinin adıyla tanımlanır. Aşağıdaki örnek, bir `Del` [dizeyi](../../language-reference/builtin-types/reference-types.md) bağımsız değişken olarak alan ve [geçersiz](../../language-reference/builtin-types/void.md)döndüren bir yöntemi kapsülleyebilen adlandırılmış bir temsilci bildirir:

[!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]

Bir temsilci nesnesi normalde temsilcinin sarılacağı yöntemin adını sağlayarak veya anonim bir [işlevle](../statements-expressions-operators/anonymous-functions.md)oluşturulur. Bir temsilci anında alındıktan sonra, temsilciye yapılan bir yöntem çağrısı bu yönteme temsilci tarafından geçirilir. Arayan tarafından temsilciye geçirilen parametreler yönteme aktarılır ve yöntemden gelen iade değeri temsilci tarafından arayanın döndürülür. Bu, temsilciyi çağırmak olarak bilinir. Anlık bir temsilci, sarılmış yöntemin kendisiymiş gibi çağrılabilir. Örnek:

[!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  

[!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]

.NET Framework'deki <xref:System.Delegate> sınıftan temsilci türleri türetilmiştir. Temsilci türleri [mühürlenir](../../language-reference/keywords/sealed.md)—türetilemezler- ve özel sınıflardan türemesi mümkün <xref:System.Delegate>değildir. Anlık temsilci bir nesne olduğundan, parametre olarak geçirilebilir veya bir özelliğe atanabilir. Bu, bir yöntemin bir temsilciyi parametre olarak kabul etmesine ve daha sonra temsilciyi aramasına olanak tanır. Bu, eşzamanlı geri arama olarak bilinir ve uzun bir işlem tamamlandığında arayanın bildirilmesi için yaygın bir yöntemdir. Bu şekilde bir temsilci kullanıldığında, temsilciyi kullanan kodun kullanılan yöntemin uygulanması hakkında herhangi bir bilgiye ihtiyacı yoktur. İşlevsellik kapsülleme arabirimleri sağlamak benzer.

Geri aramaların başka bir yaygın kullanımı, özel bir karşılaştırma yöntemi tanımlamak ve bu temsilciyi bir sıralama yöntemine geçirmektir. Arayanın kodunun sıralama algoritmasının bir parçası olmasını sağlar. Aşağıdaki örnek yöntem `Del` parametre olarak türü kullanır:

[!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]

Daha sonra yukarıda oluşturulan temsilciyi bu yönteme geçirebilirsiniz:

[!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]

ve konsola aşağıdaki çıktıyı alın:

```console
The number is: 3
```

Temsilciyi soyutlama olarak kullanmak, `MethodWithCallback` konsolu doğrudan aramanız gerekmez-konsol göz önünde bulundurularak tasarlanmamalıdır. Ne `MethodWithCallback` yapar sadece bir dize hazırlamak ve başka bir yöntem için dize geçmektir. Bu, özellikle devralınan bir yöntem herhangi bir sayıda parametre kullanabildiği için güçlüdür.

Bir örnek yöntemini sarmak için bir temsilci oluşturulduğunda, temsilci hem örnek hem de yönteme başvurur. Bir temsilcinin, saran yöntemdışında örnek türü hakkında hiçbir bilgisi yoktur, bu nedenle temsilci, bu nesnede temsilci imzasıyla eşleşen bir yöntem olduğu sürece herhangi bir nesne türüne başvurabilir. Statik bir yöntemi sarmak için bir temsilci oluşturulduğunda, yalnızca yönteme başvurur. Aşağıdaki bildirimleri dikkate alın:

[!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]

Daha önce `DelegateMethod` gösterilen statik ile birlikte, şimdi bir `Del` örnek tarafından sarılmış olabilir üç yöntem var.

Bir temsilci çağrıldığınızda birden fazla yöntemi çağırabilir. Buna çok döküm denir. Temsilcinin yöntem listesine ek bir yöntem eklemek için çağırma listesi, ek veya ek atama işleçlerini ('+' veya '+=') kullanarak iki temsilci eklemeyi gerektirir. Örnek:

[!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]

`allMethodsDelegate` Bu noktada, çağrı listesinde üç yöntem`Method1` `Method2`içerir— `DelegateMethod`, , ve . Orijinal üç delege, `d1` `d2`, `d3`, ve , değişmeden kalır. Çağrıldığında, `allMethodsDelegate` üç yöntem sırayla çağrılır. Temsilci başvuru parametrelerini kullanırsa, başvuru sırayla üç yöntemin her birine sırayla geçirilir ve bir yöntemle yapılan değişiklikler sonraki yöntemtarafından görülebilir. Yöntemlerden herhangi biri yöntem içinde yakalanmayan bir özel durum attığında, bu özel durum temsilcinin arayanına geçirilir ve çağırma listesinde sonraki yöntemler çağrılmez. Temsilcinin bir iade değeri ve/veya çıkış parametreleri varsa, çağrılan son yöntemin iade değerini ve parametrelerini döndürür. Bir yöntemi çağırma listesinden kaldırmak [için, çıkarma veya çıkarma atama işleçlerini](../../language-reference/operators/subtraction-operator.md) (veya)`-` `-=`kullanın. Örnek:

[!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]

Temsilci türleri türetildiği `System.Delegate`için, bu sınıf tarafından tanımlanan yöntemler ve özellikler temsilciye çağrılabilir. Örneğin, bir temsilcinin çağrı listesindeki yöntem sayısını bulmak için şunları yazabilirsiniz:

[!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]

Çağrı listelerinde birden fazla yöntemi olan temsilciler <xref:System.MulticastDelegate>, `System.Delegate`'nin bir alt sınıfıdır. Her iki sınıf desteği, `GetInvocationList`çünkü yukarıdaki kod her iki durumda da çalışır.

Çok noktaya yayın delegeleri olay işlemede yaygın olarak kullanılır. Olay kaynağı nesneler, olay bildirimini bu olayı almak için kaydolan alıcı nesnelere gönderir. Bir olay için kaydolmak için, alıcı olayı işlemek için tasarlanmış bir yöntem oluşturur, sonra bu yöntem için bir temsilci oluşturur ve temsilciyi olay kaynağına geçirir. Olay gerçekleştiğinde kaynak temsilciyi çağırır. Temsilci daha sonra olay verilerini teslim ederek alıcıüzerinde olay işleme yöntemini çağırır. Belirli bir olayın temsilci türü olay kaynağı tarafından tanımlanır. Daha fazla için [Etkinlikler'e](../events/index.md)bakın.

Derleme zamanında atanan iki farklı türdeki temsilcilerin karşılaştırılması bir derleme hatasına neden olur. Temsilci örnekleri statik olarak türün `System.Delegate`durumunda, karşılaştırmaya izin verilir, ancak çalışma zamanında yanlış döndürülecektir. Örnek:

[!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Temsilciler](./index.md)
- [Temsilcilerde Varyans Kullanma](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Temsilcilerde Varyans](../concepts/covariance-contravariance/variance-in-delegates.md)
- [İşlev ve Eylem Genel Temsilcileri için Varyans Kullanma](../concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Olaylar](../events/index.md)

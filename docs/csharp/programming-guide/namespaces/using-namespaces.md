---
title: "Ad Alanlarını Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f485992f5d4b7bc16aaefeec8c7c76ce39f48ef0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-namespaces-c-programming-guide"></a>Ad Alanlarını Kullanma (C# Programlama Kılavuzu)
Ad alanları, C# programları iki yolla içinde yoğun olarak kullanılır. İlk olarak, .NET Framework sınıfları birçok sınıflarından düzenlemek için ad alanları kullanın. İkincisi, kendi ad alanlarını bildirme sınıfı ve yöntemi kapsamını büyük programlama projelerinde adları denetimi yardımcı olabilir.  
  
## <a name="accessing-namespaces"></a>Ad alanları erişme  
 Çoğu C# uygulamalarının bir bölümünü ile başlayan `using` yönergeleri. Bu bölümde, uygulama sık kullanıyor olmanız ve kullanılan kapsamında yer alan bir yöntem her zaman tam adını belirterek Programcı kaydeder ad alanları listelenir.  
  
 Örneğin, satır dahil ederek:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 Bir program başlangıcında programcı kodu kullanabilirsiniz:  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 Onun yerine:  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a>Namespace diğer adlar  
 [Using yönergesi](../../../csharp/language-reference/keywords/using-directive.md) için diğer ad oluşturmak için de kullanılabilir bir [ad alanı](../../../csharp/language-reference/keywords/namespace.md). Örneğin, iç içe geçmiş ad alanları içeren önceden yazılmış bir ad alanı kullanıyorsanız, bir özel olarak, aşağıdaki örnekte olduğu gibi başvuran bir kestirme yol sağlamak için bir diğer ad bildirmek isteyebilirsiniz:  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a>Denetim kapsamına ad alanlarını kullanma  
 `namespace` Anahtar sözcüğü bir kapsam bildirmek için kullanılır. Projenizi kapsamlarında oluşturma olanağı kod düzenlemenize yardımcı olur ve genel benzersiz türleri oluşturmanızı sağlar. Aşağıdaki örnekte, bir sınıf başlıklı `SampleClass` iki ad alanı, bir diğer içe geçmiş tanımlanır. [. İşleç](../../../csharp/language-reference/operators/member-access-operator.md) hangi yöntemi çağrılır ayırt etmek için kullanılır.  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a>Tam olarak nitelenmiş adlar  
 Ad alanları ve türler mantıksal bir hiyerarşi belirtmek tam olarak nitelenmiş adlar tarafından tanımlanan benzersiz başlıklar sahiptir. Örneğin, deyim `A.B` , gelir `A` ad alanı veya türü adıdır ve `B` içinde iç içe geçmiş.  
  
 Aşağıdaki örnekte, iç içe geçmiş sınıflar ve ad alanları vardır. Tam adı, her bir varlık aşağıdaki yorum olarak belirtilir.  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 Önceki kod kesimi:  
  
-   Ad alanı `N1` genel ad alanı bir üyesidir. Tam ad `N1`.  
  
-   Ad alanı `N2` üyesi `N1`. Tam ad `N1.N2`.  
  
-   Sınıf `C1` üyesi `N1`. Tam ad `N1.C1`.  
  
-   Sınıf adı `C2` iki kez bu kodda kullanılır. Ancak, tam olarak nitelenmiş adlar benzersizdir. İlk örneğini `C2` içinde bildirilen `C1`; bu nedenle, tam ad: `N1.C1.C2`. İkinci bir örneğini `C2` bir ad alanı içinde bildirilen `N2`; bu nedenle, tam ad `N1.N2.C2`.  
  
 Önceki kod kesimi kullanarak, yeni bir sınıf üyesi ekleyebilirsiniz `C3`, ad alanına `N1.N2` gibi:  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 Genel olarak, kullanın `::` ad alanı diğer adı başvurmak için veya `global::` genel ad alanı başvurmak için ve `.` türler veya üyeler nitelemek için.  
  
 Kullanmak için bir hata olduğunu `::` türü bir ad alanı yerine başvuran diğer ad ile. Örneğin:  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 Unutmayın word `global` önceden tanımlanmış bir diğer ad; değil Bu nedenle, `global.X` özel bir anlamı yok. Yalnızca ile kullanıldığında, özel bir anlamı edinir `::`.  
  
 Bir diğer ad tanımlarsanız CS0440 oluşturulan uyarı derleyici adlı genel çünkü `global::` her zaman genel ad alanı ve bir diğer başvuruyor. Örneğin, aşağıdaki satırı uyarı üretir:  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 Kullanarak `::` diğer adları ile iyi bir fikirdir ve ek türleri beklenmeyen giriş karşı korur. Örneğin, bu örneği göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 Bir tür adlı, ancak bu, çalışır `Alias` sonradan sunulması için olan `Alias.` bunun yerine o türüne bağlayın. Kullanarak `Alias::Exception` , yöntem başlanmasını sağlar `Alias` ad alanı diğer adı kabul edilir ve mistaken için bir tür değil.  
  
 Konusuna [nasıl yapılır: Genel Namespace diğer adlarını kullanma](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) daha fazla bilgi için ilgili `global` diğer adı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Ad alanları](../../../csharp/programming-guide/namespaces/index.md)  
 [Namespace anahtar sözcükler](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [. İşleci](../../../csharp/language-reference/operators/member-access-operator.md)  
 [:: İşleci](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [extern](../../../csharp/language-reference/keywords/extern.md)

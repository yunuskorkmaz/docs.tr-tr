---
title: Ad alanlarını kullanma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 32e36a3ebc0de3e5f4a850e0af0261c1e7fd5a07
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039467"
---
# <a name="using-namespaces-c-programming-guide"></a>Ad alanlarını kullanmaC# (Programlama Kılavuzu)

Ad alanları programlar içinde C# yoğun olarak iki şekilde kullanılır. İlk olarak, .NET Framework sınıfları, birçok sınıfını düzenlemek için ad alanlarını kullanır. İkinci olarak, kendi ad alanlarınızı bildirmek, sınıf ve yöntem adlarının kapsamını daha büyük programlama projelerinde denetlemenize yardımcı olabilir.  
  
## <a name="accessing-namespaces"></a>Ad alanlarına erişme

 Çoğu C# uygulama, `using` yönergelerin bir bölümüyle başlar. Bu bölüm, uygulamanın sıklıkla kullanacağı ad alanlarını listeler ve içinde yer alan bir yöntemin kullanıldığı her seferinde her defasında tam nitelikli bir ad belirtmekten tasarruf eder.  
  
 Örneğin, satırını dahil ederek:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 Program başlangıcında, Programcı kodu kullanabilir:  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 Onun yerine:  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>Ad uzayı diğer adları

 Bir ad alanı için bir diğer ad oluşturmak için [ `using` yönergesini](../../language-reference/keywords/using-directive.md) de kullanabilirsiniz. Diğer ad alanının üyelerine erişmek için [ad alanı diğer `::` adı niteleyicisi](../../language-reference/operators/namespace-alias-qualifier.md) kullanın. Aşağıdaki örnek, bir ad alanı diğer adının nasıl oluşturulduğunu ve kullanılacağını gösterir:
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a>Kapsamı denetlemek için ad alanlarını kullanma

 `namespace` Anahtar sözcüğü bir kapsamı bildirmek için kullanılır. Projenizin içinde kapsam oluşturma özelliği, kodun düzenlenmesine yardımcı olur ve küresel olarak benzersiz türler oluşturmanıza olanak sağlar. Aşağıdaki örnekte, başlıklı `SampleClass` bir sınıf, diğeri içinde iç içe iki ad alanında tanımlanır. [ `.` Üye erişim işleci](../../language-reference/operators/member-access-operators.md#member-access-operator-) , hangi yöntemin çağracağını ayırt etmek için kullanılır.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>Tam nitelikli adlar

 Ad alanları ve türler, bir mantıksal hiyerarşiyi gösteren tam nitelikli adlarla tanımlanan benzersiz başlıklara sahiptir. Örneğin, ifade `A.B` , ad alanının veya `A` türün adı olduğunu ve `B` içinde iç içe geçmiş olduğunu gösterir.  
  
 Aşağıdaki örnekte, iç içe geçmiş sınıflar ve ad alanları vardır. Tam nitelikli ad her bir varlıktan sonra bir yorum olarak belirtilir.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 Önceki kod segmentinde:  
  
- Ad alanı `N1` , genel ad alanının bir üyesidir. Tam nitelikli adı `N1`.  
  
- Ad alanı `N2` bir `N1`üyesidir. Tam nitelikli adı `N1.N2`.  
  
- Sınıfı `C1` öğesinin`N1`üyesidir. Tam nitelikli adı `N1.C1`.  
  
- Sınıf adı `C2` Bu kodda iki kez kullanılır. Ancak, tam nitelikli adlar benzersizdir. İlk örneği `C2` içinde `C1`, bu nedenle tam adı: `N1.C1.C2`. İkinci örneği `C2` bir ad alanı `N2`içinde bildirilmiştir; bu nedenle tam adı ' dir `N1.N2.C2`.  
  
 Önceki kod segmentini kullanarak, ad alanına `C3` `N1.N2` yeni bir sınıf üyesini aşağıdaki şekilde ekleyebilirsiniz:  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 Genel olarak, ad alanı diğer adına başvurmak için ad [alanı diğer `::` ](../../language-reference/operators/namespace-alias-qualifier.md) adı niteleyicisi `global::` kullanın veya genel ad alanına başvurmak `.` ve türleri veya üyeleri nitelemek için kullanın.  
  
 Ad alanı yerine bir türe başvuran `::` diğer adla birlikte kullanılması hatadır. Örneğin:  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Sözcüğün `global` önceden tanımlanmış bir diğer ad olmadığını unutmayın; bu nedenle, `global.X` özel bir anlamı yoktur. Yalnızca ile `::`kullanıldığında özel bir anlam elde edin.  
  
 Bir diğer ad değil genel ad alanına başvurduğu için, genel `global::` adlı bir diğer ad tanımlarsanız derleyici uyarısı CS0440 oluşturulur. Örneğin, aşağıdaki satır uyarı oluşturur:  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Diğer `::` adlarla kullanmak iyi bir fikirdir ve ek türlerin beklenmedik şekilde tanıtılmasıyla karşı koruma sağlar. Örneğin, şu örneği göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 Bu işe yarar, ancak adlandırılmış `Alias` bir tür daha sonra tanıtılmışsa, `Alias.` bunun yerine bu türe bağlanır. Kullanmak `Alias::Exception` `Alias` , bir ad alanı diğer adı olarak değerlendirilip bir tür için hatalı alınmamasını sağlar.  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)
- [. işlecinde](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [:: işleci](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [extern diğer adı](../../../csharp/language-reference/keywords/extern-alias.md)

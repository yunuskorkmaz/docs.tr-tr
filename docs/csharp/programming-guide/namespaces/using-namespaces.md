---
title: Ad Boşluklarını Kullanma - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: b4326be8c9e299a96477096ec21864ec69037abe
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738238"
---
# <a name="using-namespaces-c-programming-guide"></a>Ad alanlarını kullanma (C# Programlama Kılavuzu)

Ad boşlukları C# programlarında iki şekilde yoğun olarak kullanılır. İlk olarak, .NET Framework sınıfları birçok sınıflarını düzenlemek için ad boşluklarını kullanır. İkinci olarak, kendi ad alanlarınızı bildirmek, daha büyük programlama projelerinde sınıf ve yöntem adlarının kapsamını denetlemenize yardımcı olabilir.  
  
## <a name="accessing-namespaces"></a>Ad alanlarına erişim

 Çoğu C# uygulaması yönergelerin `using` bir bölümüyle başlar. Bu bölümde, uygulamanın sık sık kullanılacağı ad alanları listelenir ve programcının içinde bulunan bir yöntemin her kullanıldığında tam nitelikli bir ad belirtilmesinden kurtarılır.  
  
 Örneğin, satırı ekleyerek:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 Programın başlangıcında, programcı kodu kullanabilir:  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 Onun yerine:  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>Ad alanı takma adları

 Ad alanı için takma ad oluşturmak için yönergeyi de kullanabilirsiniz. [ `using` ](../../language-reference/keywords/using-directive.md) Diğer ad alanının üyelerine erişmek için [ad alanı diğer ad niteleyicisini `::` ](../../language-reference/operators/namespace-alias-qualifier.md) kullanın. Aşağıdaki örnek, ad alanı diğer adının nasıl oluşturulup kullanılacağını gösterir:
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a>Kapsamı denetlemek için ad alanlarını kullanma

 Anahtar `namespace` kelime bir kapsamı bildirmek için kullanılır. Projenizde kapsam oluşturma olanağı, kodun düzenlenmesine yardımcı olur ve genel olarak benzersiz türler oluşturmanıza yardımcı olur. Aşağıdaki örnekte, başlıklı `SampleClass` bir sınıf, biri diğerinin iç içe olduğu iki ad alanında tanımlanır. [ `.` Belirteç,](../../language-reference/operators/member-access-operators.md#member-access-expression-) hangi yöntemin çağrıldığını ayırt etmek için kullanılır.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>Tam nitelikli isimler

 Ad alanları ve türleri, mantıksal bir hiyerarşiyi gösteren tam nitelikli adlarla açıklanan benzersiz başlıklara sahiptir. Örneğin, deyim, `A.B` ad `A` alanının veya türün adı `B` olduğunu ve içinde iç içe olduğunu ima eder.  
  
 Aşağıdaki örnekte, iç içe ayrılmış sınıflar ve ad alanları vardır. Tam nitelikli ad, her varlığı izleyen bir yorum olarak gösterilir.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 Önceki kod segmentinde:  
  
- Ad alanı, `N1` genel ad alanının bir üyesidir. Onun tam nitelikli `N1`adıdır .  
  
- Ad alanı. `N2` `N1` Onun tam nitelikli `N1.N2`adıdır .  
  
- `C1` Sınıf bir `N1`üyesidir. Onun tam nitelikli `N1.C1`adıdır .  
  
- Sınıf adı `C2` bu kodda iki kez kullanılır. Ancak, tam nitelikli adlar benzersizdir. İlk örneği `C2` içinde `C1`ilan edilir; bu nedenle, tam nitelikli `N1.C1.C2`adı: . İkinci örnek `C2` bir ad alanı `N2`içinde bildirilir; bu nedenle, tam `N1.N2.C2`nitelikli adıdır .  
  
 Önceki kod kesimini kullanarak, `C3`ad alanına `N1.N2` aşağıdaki gibi yeni bir sınıf üyesi ekleyebilirsiniz:  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 Genel olarak, ad alanı diğer adını başvurmak veya `global::` genel ad alanına başvurmak `.` ve türleri veya üyeleri nitelemek için [ad alanı diğer adını `::` ](../../language-reference/operators/namespace-alias-qualifier.md) kullanın.  
  
 Ad alanı yerine `::` bir türe başvuruyapan bir takma adla kullanmak bir hatadır. Örneğin:  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Sözcüğün `global` önceden tanımlanmış bir takma ad olmadığını unutmayın; bu `global.X` nedenle, herhangi bir özel anlamı yoktur. Sadece . `::`  
  
 Derleyici uyarısı CS0440, her zaman bir takma `global::` ad değil, genel ad alanına başvurulduğundan, global adlı bir takma ad tanımlarsanız oluşturulur. Örneğin, aşağıdaki satır uyarı oluşturur:  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Takma `::` adlarla kullanmak iyi bir fikirdir ve ek türlerin beklenmeyen girişine karşı koruma dır. Örneğin, şu örneği göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 Bu çalışır, ancak adlandırılmış `Alias` bir tür daha `Alias.` sonra tanıtılacak olsaydı, bunun yerine bu türe bağlanır. Bir `Alias::Exception` ad `Alias` alanı diğer adı olarak kabul edilen ve bir türle karıştırılmayan bir sözcük kullanmak,  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ad Alanları](./index.md)
- [Üye erişim ifadesi](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [:: işleci](../../language-reference/operators/namespace-alias-qualifier.md)
- [extern alias](../../language-reference/keywords/extern-alias.md)

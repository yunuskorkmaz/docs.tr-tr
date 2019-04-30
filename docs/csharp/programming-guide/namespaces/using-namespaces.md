---
title: Ad alanlarını - kullanma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 510a8dd2721e9c709444c065a8df25b0e5526c08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678406"
---
# <a name="using-namespaces-c-programming-guide"></a>Ad Alanlarını Kullanma (C# Programlama Kılavuzu)
Ad alanlarında, C# programları iki yolla içinde yoğun olarak kullanılır. İlk olarak, .NET Framework sınıfları ad alanları, çok sayıda sınıfa düzenlemek için kullanın. İkincisi, kendi ad alanlarını bildirme denetimi sınıf ve metod kapsamını daha büyük programlama projelerinde adları yardımcı olabilir.  
  
## <a name="accessing-namespaces"></a>Ad alanları erişme  
 Çoğu C# uygulama bölümü ile başlayan `using` yönergeleri. Bu bölümde, uygulama sık sık kullanacağınız ve içinde yer alan bir yöntem kullanılır her zaman tamamen nitelikli ada belirtmelerini Programcı kaydeder ad alanlarını listeler.  
  
 Örneğin, satır dahil ederek:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 Bir program başlangıcında, programcılar kodu kullanabilirsiniz:  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 Onun yerine:  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>Namespace diğer adları  
 [Using yönergesi](../../../csharp/language-reference/keywords/using-directive.md) için bir diğer ad oluşturmak için de kullanılabilir bir [ad alanı](../../../csharp/language-reference/keywords/namespace.md). Örneğin, iç içe ad alanlarını içeren önceden yazılmış bir ad alanı kullanıyorsanız, aşağıdaki örnekte olduğu gibi bir özellikle, başvuru toplu bir yol sağlamak üzere bir diğer ad bildirmek isteyebilirsiniz:  
  
 [!code-csharp[csProgGuideNamespaces#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#7)]  
  
## <a name="using-namespaces-to-control-scope"></a>Denetim kapsamı ad alanlarını kullanma  
 `namespace` Anahtar sözcüğü bir kapsamı bildirmek için kullanılır. Projenizi kapsamlarda oluşturma olanağı kodunu düzenlemenize yardımcı olur ve genel olarak benzersiz türleri oluşturmanıza olanak sağlar. Aşağıdaki örnekte, bir sınıf başlıklı `SampleClass` bir diğer içinde iç içe iki ad alanında tanımlanır. [. İşleç](../../../csharp/language-reference/operators/member-access-operator.md) hangi yöntemi çağrıldığında ayırt etmek için kullanılır.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>Tam olarak nitelenmiş adlar  
 Ad alanları ve türler, mantıksal bir hiyerarşi gösteren tam olarak nitelenmiş adlar tarafından açıklanan benzersiz başlıkları sahip. Örneğin, deyim `A.B` , gelir `A` ad alanı veya tür, adıdır ve `B` içinde iç içe geçmiş.  
  
 Aşağıdaki örnekte, iç içe geçmiş sınıflar ve ad alanları vardır. Tam adı, her varlık aşağıdaki açıklama olarak belirtilir.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 Önceki kod kesimi içinde:  
  
- Ad alanı `N1` genel ad alanının bir üyesidir. Tam olarak nitelenmiş adını `N1`.  
  
- Ad alanı `N2` üyesi `N1`. Tam olarak nitelenmiş adını `N1.N2`.  
  
- Sınıf `C1` üyesi `N1`. Tam olarak nitelenmiş adını `N1.C1`.  
  
- Sınıf adı `C2` iki kez bu kodda kullanılır. Ancak, tam nitelikli adları benzersizdir. İlk örneğinin `C2` içinde bildirilen `C1`; bu nedenle, tam ad: `N1.C1.C2`. İkinci bir örneğini `C2` bir ad alanı içinde bildirilen `N2`; bu nedenle, tam olarak nitelenmiş adını `N1.N2.C2`.  
  
 Önceki kod kesimi kullanarak yeni bir sınıf üyesi ekleyebilirsiniz `C3`, ad alanına `N1.N2` gibi:  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 Genel olarak, kullanın `::` ad alanı diğer ada başvuru yapmak veya `global::` genel ad başvurmak için ve `.` türleri veya üyeleri nitelemek için.  
  
 Kullanılacak bir hata olduğunu `::` bir ad alanı yerine bir türe başvuran bir takma ad ile. Örneğin:  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Unutmayın word `global` önceden tanımlanmış bir değil diğer adı; bu nedenle `global.X` özel bir anlamı yok. Yalnızca ile kullanıldığında, özel bir anlamı edinme `::`.  
  
 Bir diğer ad tanımlarsanız CS0440 oluşturulan uyarı derleyici adlı genel çünkü `global::` her zaman genel ad ve bir diğer başvuruyor. Örneğin, aşağıdaki satırı uyarıyı üretir:  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Kullanarak `::` diğer adları ile iyi bir uygulamadır ve ek türleri beklenmeyen giriş karşı korur. Örneğin, bu örneği göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 Adlı bir tür, ancak bu, çalışan `Alias` sonradan tanıtılmak üzere olduğunuz `Alias.` bunun yerine o türüne bağlayın. Kullanarak `Alias::Exception` , oluşturmasını sağlar `Alias` bir ad alanı diğer ad olarak kabul edilir ve mistaken için bir tür değil.  
  
 Konusuna [nasıl yapılır: Genel Namespace diğer adlarını kullanma](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) daha fazla bilgi için ilgili `global` diğer adı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)
- [Ad Alanı Anahtar Sözcükleri](../../../csharp/language-reference/keywords/namespace-keywords.md)
- [. İşleç](../../../csharp/language-reference/operators/member-access-operator.md)
- [:: İşleç](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [extern](../../../csharp/language-reference/keywords/extern.md)

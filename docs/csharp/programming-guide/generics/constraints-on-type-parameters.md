---
title: "Tür Parametrelerindeki Kısıtlamalar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: "41"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f7c80acdb3815af4b5d545297894778029a9104
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Tür Parametrelerindeki Kısıtlamalar (C# Programlama Kılavuzu)
Genel bir sınıf tanımladığınızda, sınıfını başlattığında, istemci kodu tür bağımsız değişkenleri için kullanabileceğiniz türü tür kısıtlamaları uygulayabilirsiniz. İstemci kodu kısıtlaması tarafından izin verilmeyen bir türünü kullanarak, sınıfının örneği çalışırsa, bir derleme zamanı hatası sonucudur. Bu kısıtlamalar kısıtlamaları denir. Kısıtlamaları belirtilen kullanarak `where` bağlamsal anahtar sözcüğü. Aşağıdaki tabloda kısıtlamaları altı türlerini listeler:  
  
|Kısıtlama|Açıklama|  
|----------------|-----------------|  
|`where T: struct`|Tür bağımsız değişkeni bir değer türü olmalıdır. Herhangi bir değer türü dışında <xref:System.Nullable> belirtilebilir. Bkz: [kullanarak boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/using-nullable-types.md) daha fazla bilgi için.|  
|`where T : class`|Tür bağımsız değişkeni bir başvuru türü olmalıdır; Bu aynı zamanda herhangi sınıfı, arabirim, temsilci veya dizi türü için geçerlidir.|  
|`where T : new()`|Tür bağımsız değişkeni genel bir parametresiz oluşturucuya sahip olmalıdır. Diğer kısıtlamalar ile birlikte kullanıldığında `new()` kısıtlaması son belirtilmelidir.|  
|`where T : `*\<taban sınıf adı >*|Tür bağımsız değişkeni, olabilir veya belirtilen temel sınıfından türetilir.|  
|`where T : `*\<Arabirim adı >*|Tür bağımsız değişkeni olabilir veya belirtilen arabirimini uygulaması gerekir. Birden çok arabirim kısıtlamaları belirtilebilir. Kısıtlayan arabirimi genel olabilir.|  
|`where T : U`|T olması veya u için sağlanan bağımsız değişken öğesinden türetilen için sağlanan tür bağımsız değişkeni|  
  
## <a name="why-use-constraints"></a>Kısıtlamaları neden kullanılır?  
 Geçerli olup olmadığını belirlemek için veya başka bir öğe karşılaştırmak için genel bir listedeki bir öğe incelemek isterseniz, derleyicinin bazı istemci ortak tarafından belirtilen tür bağımsız değişkeni tarafından işleci veya yöntem çağrılacak olan desteklenecek garanti olmalıdır de. Bu garantisi, genel bir sınıf tanımı için bir veya daha fazla kısıtlamaları uygulayarak elde edilir. Örneğin, taban sınıf kısıtlaması bu tür nesneler yalnızca derleyici söyler veya öğesinden türetilmiş türü tür bağımsız değişkenleri kullanılır. Derleyici bu garantisi sonra genel sınıfında çağrılacak türü yöntemleri izin verebilirsiniz. Bağlamsal anahtar sözcüğünü kullanarak kısıtlamalar uygulanır `where`. Aşağıdaki kod örneği için ekleyebilirsiniz biz işlevini gösterir `GenericList<T>` sınıfı (içinde [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)) bir taban sınıf kısıtlaması uygulayarak.  
  
 [!code-csharp[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 Kullanmak genel bir sınıf kısıtlaması etkinleştirir `Employee.Name` özelliği tüm öğeleri T türü ya da olması garanti çünkü bir `Employee` veya öğesinden devralınan bir nesneyi `Employee`.  
  
 Aynı tür parametresi birden çok kısıtlama uygulanabilir ve kısıtlamaları kendilerini genel türleri, aşağıdaki gibi olabilir:  
  
 [!code-csharp[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 Tür parametresi kısıtlayarak, izin verilen işlemler ve kısıtlama türü ve devralma hiyerarşisi içindeki tüm türler tarafından desteklenen yöntem çağrılarını sayısını artırın. Bu nedenle, tasarlarken genel sınıfları veya yöntemleri, basit atama ötesinde Genel üyeler üzerinde herhangi bir işlemi gerçekleştirme veya kaldırılacak tarafından desteklenmeyen herhangi bir yöntem çağırma varsa `System.Object`, tür parametresi kısıtlamaları uygulamak gerekir.  
  
 Uygularken `where T : class` kısıtlaması, kaçının `==` ve `!=` tür parametresi işleçlerini çünkü bu işleçlere yalnızca başvuru kimliği olmayan değer eşitlik için test. Bağımsız değişken olarak kullanılan bir türdeki Bu işleçleri aşırı yüklenmiş olsa bile bu geçerlidir. Aşağıdaki kod bu noktayı gösterir; Çıktı halde false şeklindedir <xref:System.String> sınıf aşırı `==` işleci.  
  
 [!code-csharp[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 Bu davranış derleme zamanında Derleyici yalnızca T bir başvuru türü ve dolayısıyla tüm başvuru türleri için geçerli varsayılan işleçleri kullanması gerekir bilir, nedeni. Değer eşitlik için test etmeniz gerekir, önerilen yöntem de uygulamak için ise `where T : IComparable<T>` kısıtlaması ve genel bir sınıf oluşturmak için kullanılan herhangi bir sınıf arabirimi uygulayın.  
  
## <a name="constraining-multiple-parameters"></a>Birden çok parametre sınırlama  
 Aşağıdaki örnekte gösterildiği gibi birden çok parametre ve tek bir parametre için birden çok kısıtlama kısıtlamaları uygulayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## <a name="unbounded-type-parameters"></a>Sınırsız tür parametreleri  
 Tür ortak sınıfı T gibi herhangi bir kısıtlama söz konusu parametrelerindeki `SampleClass<T>{}`, sınırsız tür parametreleri olarak adlandırılır. Sınırsız tür parametreleri aşağıdaki kurallar vardır:  
  
-   `!=` Ve `==` somut tür bağımsız değişkeni bu işleçlere destekleyecek garanti olduğundan işleçleri kullanılamaz.  
  
-   Ve ondan dönüştürülebilir `System.Object` veya herhangi bir arabirim türü açıkça dönüştürülebilir.  
  
-   ' Karşılaştırabilirsiniz [null](../../../csharp/language-reference/keywords/null.md). Sınırsız bir parametre karşılaştırılır varsa `null`, karşılaştırma her zaman tür bağımsız değişkeni bir değer türü ise false döndürür.  
  
## <a name="type-parameters-as-constraints"></a>Tür parametreleri kısıtlamaları olarak  
 Bir kısıtlama yararlı üye işlevi kendi tür parametresi ile olduğu gibi aşağıdaki örnekte gösterildiği gibi kapsayan tür tür parametresi bu parametreye sınırlamak bir genel tür parametresi kullanımını sahiptir:  
  
 [!code-csharp[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 Önceki örnekte, `T` türü kısıtlaması bağlamında `Add` yöntemi ve sınırsız tür parametresi bağlamında `List` sınıfı.  
  
 Tür parametreleri, genel bir sınıf tanımları kısıtlamalar olarak da kullanılabilir. Tür parametresi herhangi bir tür parametre birlikte köşeli ayraç içinde bildirilmelidir dikkat edin:  
  
 [!code-csharp[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 Tür parametreleri yararlılığını Genel sınıflar kısıtlamalarıyla olarak den türemesi dışında derleyici tür parametresi hakkında hiçbir şey kabul edilebilir olduğundan çok sınırlı `System.Object`. Genel sınıflar, iki tür parametreleri arasında bir devralma ilişkisi uygulamak istediğiniz senaryolarda kısıtlamalar olarak tür parametreleri kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Genel Sınıflar](../../../csharp/programming-guide/generics/generic-classes.md)  
 [new Kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md)

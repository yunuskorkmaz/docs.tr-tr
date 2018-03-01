---
title: "new İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3c2b484b9872a54ce42520de77a723b9edb441a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-c-reference"></a>new İşleci (C# Başvurusu)
Nesneleri oluşturmak ve oluşturucular çağırmak için kullanılır. Örneğin:  
  
```  
Class1 obj  = new Class1();  
```  
  
 Anonim türler örneklerini oluşturmak için de kullanılır:  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 `new` İşleci değer türleri için varsayılan oluşturucu çağırmak için de kullanılır. Örneğin:  
  
```  
int i = new int();  
```  
  
 Önceki deyiminde `i` için başlatılan `0`, türü için varsayılan değeri olduğu `int`. Deyim şu aynı etkiye sahiptir:  
  
```  
int i = 0;  
```  
  
 Varsayılan değerlerin tam listesi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 İçin varsayılan bir oluşturucu bildirmek için bir hata olduğunu unutmayın bir [yapısı](../../../csharp/language-reference/keywords/struct.md) her değer türü örtük olarak ortak varsayılan bir oluşturucu olduğundan. Parametreli oluşturucular ilk değerlerini ayarlamak için bir yapı türüne bildirmeniz mümkündür, ancak bu yalnızca varsayılan dışındaki değerler gerekli ise gereklidir.  
  
 Başvuru türü gibi sınıfları öbek üzerinde oluşturulan nesneleri sırada yapılar gibi değer türü nesneleri yığında oluşturulur. Her iki türdeki nesneler otomatik olarak yok ancak kapsamının dışına gittiğinizde değer türleri üzerinde bağlı nesneleri yok, nesneleri temel ancak başvuru türleri bunları son referansı kaldırıldıktan sonra belirtilmeyen bir zamanda yok olur. Büyük miktarlarda bellek, dosya tanıtıcısı veya ağ bağlantıları gibi sabit kaynaklarını tüketebilir başvuru türleri için bazen nesnesi mümkün olan en kısa sürede yok emin olmak için sonlandırma kullanmayı tercih edilir. Daha fazla bilgi için bkz: [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md).  
  
 `new` İşleci olamaz aşırı yüklenebilir.  
  
 Varsa `new` işleci başarısız bellek ayıramadı, özel durum oluşturur <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir `struct` nesnesi ve bir sınıf nesnesi oluşturulur ve kullanarak başlatılmış `new` işleci ve değerler atanır. Varsayılan ve atanmış değerler görüntülenir.  
  
 [!code-csharp[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 Varsayılan değer bir dize örneği bildiriminde `null`. Bu nedenle, görüntülenmez.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç anahtar sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Yeni](../../../csharp/language-reference/keywords/new.md)  
 [Anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

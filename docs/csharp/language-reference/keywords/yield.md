---
title: yield (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: b22822656860b58a2f225fadcb3c68802899a505
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="yield-c-reference"></a>yield (C# Başvurusu)
Kullandığınızda `yield` anahtar sözcüğü bir deyimde size bildiren işleci, yöntemi veya `get` görünür olan yineleyici erişimcisi. Kullanarak `yield` yineleyici tanımlamak için bir açık ek sınıf gereksinimini ortadan kaldırır (bkz: bir numaralandırma durumu tutan sınıfı <xref:System.Collections.Generic.IEnumerator%601> bir örnek) ne zaman uygulamak <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> özel bir koleksiyon için deseni yazın.  
  
 Aşağıdaki örnek, iki tür gösterir `yield` deyimi.  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Kullandığınız bir `yield return` her öğeye aynı anda geri dönmek için deyimi.  
  
 İterator yöntemi ile kullanmasını bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi veya LINQ sorgusu. Her yinelemesinden `foreach` döngü yineleyici yöntemini çağırır. Zaman bir `yield return` deyimi yineleyici yönteminde ulaşıldığında `expression` döndürülür ve kod geçerli konumda korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.  
  
 Kullanabileceğiniz bir `yield break` yinelemeyi sonlandırmak için deyimi.  
  
 Yineleyiciler hakkında daha fazla bilgi için bkz: [yineleyiciler](../../iterators.md).  
  
## <a name="iterator-methods-and-get-accessors"></a>Yineleyici Yöntemleri ve get Erişimcileri  
 Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:  
  
-   Dönüş türü olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Bildirimi içeremez [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri.  
  
 `yield` Döndürür yineleyici türünü <xref:System.Collections.IEnumerable> veya <xref:System.Collections.IEnumerator> olan `object`.  Yineleyici döndürürse <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.Generic.IEnumerator%601>, ifadesinde türü örtük bir dönüştürme olmalıdır `yield return` genel tür parametresi ifadesine.  
  
 Dahil edilemiyor bir `yield return` veya `yield break` aşağıdaki özelliklere sahip yöntemleri deyiminde:  
  
-   Anonim yöntemler. Daha fazla bilgi için bkz: [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
-   Güvenli olmayan bloklar içeren yöntemler. Daha fazla bilgi için bkz: [güvensiz](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 A `yield return` deyimi bir try-catch bloğu içinde bulunamıyor. A `yield return` deyimi, bir try-finally deyimi try bloğunda yer alması.  
  
 A `yield break` deyimi yer alması try blok veya bir catch bloğunun dışında bir finally bloğunda.  
  
 Varsa `foreach` gövdesi (dışında yineleyici yöntemi) bir özel durum oluşturur bir `finally` yineleyici yöntemi bloğunda gerçekleştirilir.  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Aşağıdaki kod döndürür bir `IEnumerable<string>` yineleyici yönteminden ve öğeleri arasında yineler.  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 Çağrı `MyIteratorMethod` yönteminin gövdesi yürütmez. Bunun yerine çağrı döndürür bir `IEnumerable<string>` içine `elements` değişkeni.  
  
 Bir yineleme `foreach` döngü, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements`. Bu çağrı gövdesini yürütür `MyIteratorMethod` sonraki kadar `yield return` deyimi ulaşıldığında. İfadesi tarafından döndürülen `yield return` ifadesi belirler değeri yalnızca `element` döngü gövdesine tüketimi için değişken aynı zamanda <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özelliği `elements`, olduğu bir `IEnumerable<string>`.  
  
 Sonraki her yinelemesinden üzerinde `foreach` nereden yürütülmeye yineleyici gövdesinin döngü ulaştığında yeniden durdurma kapalı, solda bir `yield return` deyimi. `foreach` Döngüsü tamamlandıktan yineleyici yönteminin sonuna veya `yield break` deyimi ulaşıldığında.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sahip bir `yield return` içinde deyimi bir `for` döngü. Her yinelemesinden `foreach` deyiminin gövdesinde `Main` yöntem çağrısı oluşturur `Power` yineleyici işlevi. Yineleyici işlevi her çağrısı devam eder, sonraki yürütülmesi `yield return` sonraki yinelemesini sırasında oluşur deyimi `for` döngü.  
  
 Yineleyici yöntemin dönüş türü <xref:System.Collections.IEnumerable>, bir yineleyici arabirimi türü değil. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterilmiştir bir `get` yineleyici olduğu erişimcisi. Örnekte, her `yield return` deyimi bir kullanıcı tarafından tanımlanan sınıfının bir örneğini döndürür.  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Yineleyiciler](../../iterators.md)

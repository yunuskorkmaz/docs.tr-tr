---
title: 'Nasıl yapılır: Başvuru Eşitliği Testi (Kimlik) (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 78a6bf1f5d4a93bd561faada91b4a11f52692dbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322347"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Nasıl yapılır: Başvuru Eşitliği Testi (Kimlik) (C# Programlama Kılavuzu)
Referans eşitlik karşılaştırmaları, türlerinizi desteklemek için hiçbir özel mantığı uygulamanız gerekmez. Bu işlev tarafından statik tüm türleri için sağlanan <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki örnekte, iki değişken sahip olup olmadığınızı belirlemek gösterilmiştir *başvuru eşitliği*, bellekte aynı nesnesi başvuruda bulunulan anlamına gelir.  
  
 Bu örnek ayrıca neden gösterir <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her zaman döndürür `false` değer türleri ve neden kullanılamaz <xref:System.Object.ReferenceEquals%2A> dize eşitlik belirlemek için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 Uygulaması `Equals` içinde <xref:System.Object?displayProperty=nameWithType> Evrensel taban sınıfı ayrıca bir referans eşitlik denetimi gerçekleştirir, ancak beklediğiniz sonuçları yöntemi geçersiz kılmak için bir sınıf meydana gelirse olmayabileceğinden, bu kullanmamanız önerilir. Aynı için doğrudur `==` ve `!=` işleçler. Referans olarak ne zaman işletim türleri, == varsayılan davranışını ve `!=` referans eşitlik kontrolüne gerçekleştirmektir. Ancak, türetilen sınıflar değeri eşitlik denetimi gerçekleştirmek için işleç aşırı yüklenebilir. Hata olasılığını en aza indirmek için her zaman kullanmak en iyisidir <xref:System.Object.ReferenceEquals%2A> iki nesne başvuru eşitliği sahip olup olmadığınızı belirlemek olduğunda.  
  
 Sabit Dizeler aynı bütünleştirilmiş kod içinde her zaman çalışma zamanı tarafından interned. Diğer bir deyişle, her benzersiz bir değişmez dize yalnızca bir örneği korunur. Ancak, çalışma zamanı dizeleri çalışma zamanında oluşturulan interned veya farklı derlemelerde iki eşit sabit dizeler interned garanti etmez garanti etmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşitlik Karşılaştırmaları](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)

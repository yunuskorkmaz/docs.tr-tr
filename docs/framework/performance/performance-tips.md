---
title: .NET Performans İpuçları
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d5d91db9256cdfb3aa0062d66333f13797ee1bb
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48025259"
---
# <a name="net-performance-tips"></a>.NET Performans İpuçları
Terim *performans* genellikle bir programı yürütme hızını gösterir. Ayrıca, bazı temel kurallara kaynak kodunuza uygulayarak bazen yürütme hızını artırabilirsiniz. Bazı programlarda, kodu yakından incelemek ve mümkün olduğunca hızlı çalıştığından emin olmak için profil oluşturucuları kullanmak önemlidir. Diğer programlarda, hızlı yazıldığı gibi kod yazıldıkça yeterince çalıştığından böyle bir iyileştirme gerçekleştirmek zorunda değildir. Bu makalede, bazı ortak alanlar burada performans olumsuz etkilenebilir ve bunun yanı sıra ek performans konularının bağlantılarını geliştirme ipuçları listelenmektedir. Planlama ve performans ölçümü hakkında daha fazla bilgi için bkz. [performans](../../../docs/framework/performance/index.md)  
  
## <a name="boxing-and-unboxing"></a>Kutulama ve Kutudan Çıkarma  
 En iyi değer kullanmaktan kaçınmak için türleri olduğu durumlarda çok sayıda zaman, örneğin genel olmayan koleksiyon sınıflarında gibi Kutulu <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Genel koleksiyonları kullanarak değer türlerini kutulama kaçınabilirsiniz <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Kutulama ve kutudan çıkarma hesaplama açısından pahalı işlemlerdir. Bir değer türü kutulandığında tamamen yeni bir nesnenin oluşturulması gerekir. Bu basit başvuru atamasından en çok 20 kat daha uzun sürebilir. Kutudan çıkarma sırasında dağılımı süreci atamadan dört kat daha uzun sürebilir. Daha fazla bilgi için [kutulama ve kutudan çıkarma](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Dizeler  
 Çok sayıda dize değişkenleri art arda eklerken, örneğin sıkı bir döngüde kullanın <xref:System.Text.StringBuilder?displayProperty=nameWithType> yerine C# [+ işleci](~/docs/csharp/language-reference/operators/addition-operator.md) veya Visual Basic [birleştirme işleçleri](~/docs/visual-basic/language-reference/operators/concatenation-operators.md). Daha fazla bilgi için [nasıl yapılır: birden çok dizeyi birleştirme](../../csharp/how-to/concatenate-multiple-strings.md) ve [Visual Basic'de birleştirme işleçleri](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Yıkıcılar  
 Boş yok ediciler kullanılmamalıdır. Bir sınıf bir yıkıcı olduğunda bitirme kuyruğunda bir girdi oluşturulur. Yıkıcı çağrıldığında çöp toplayıcı kuyruğu işlemek için çağrılır. Yıkıcı boş ise, bu yalnızca bir performans kaybı ile sonuçlanır. Daha fazla bilgi için [yok ediciler](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) ve [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Diğer Kaynaklar  
  
-   [Yönetilen kodu daha hızlı yazma: Maliyetleri anlama](https://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [Yazma yüksek performanslı yönetilen uygulamalar: Öncü](https://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [Çöp toplayıcı temelleri ve performans ipuçları](https://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [Performans İpuçları ve püf noktaları .NET uygulamalarında](https://go.microsoft.com/fwlink/?LinkId=99297)  

-   [Rico Mariani'nın performans ipuçları](https://go.microsoft.com/fwlink/?LinkId=115679)  

-   [Vance Morrison'ın blogu](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans](../../../docs/framework/performance/index.md)  
 [Programlama Kavramları](https://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6)  
 [Visual Basic programlama kılavuzu](../../visual-basic/programming-guide/index.md)  
 [C# Programlama Kılavuzu](https://msdn.microsoft.com/library/ac0f23a2-6bf3-4077-be99-538ae5fd3bc5)

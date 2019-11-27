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
ms.openlocfilehash: 48b62990abf85eac4d4ab30c9a4b891de0875cd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444538"
---
# <a name="net-performance-tips"></a>.NET Performans İpuçları
*Performans* terimi genellikle programın yürütme hızına başvurur. Kaynak kodunuzda belirli temel kuralları izleyerek, bazen yürütme hızını artırabilirsiniz. Bazı programlarda, kodu yakından incelemek ve profil oluşturucular kullanarak olabildiğince hızlı çalıştığından emin olmak önemlidir. Diğer programlarda, bu tür iyileştirme gerçekleştirmek zorunda değilsiniz çünkü kod yazıldığı kadar hızlı şekilde çalışıyor. Bu makalede, performansın önyüklenebileceği bazı yaygın bölgeler ve ek performans konularına yönelik bağlantılar yer almaktadır. Performansı planlama ve ölçme hakkında daha fazla bilgi için bkz. [performans](index.md)  
  
## <a name="boxing-and-unboxing"></a>Kutulama ve Kutudan Çıkarma  
 Örneğin, <xref:System.Collections.ArrayList?displayProperty=nameWithType>gibi genel olmayan koleksiyonlar sınıflarında çok sayıda kutulanmış olmaları gereken durumlarda değer türlerini kullanmaktan kaçınmak en iyisidir. <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>gibi genel Koleksiyonlar kullanarak değer türlerinin kutulamayı önleyebilirsiniz. Kutulama ve kutudan çıkarma, hesaplama açısından pahalı işlemlerdir. Bir değer türü paketlenme olduğunda, tamamen yeni bir nesne oluşturulması gerekir. Bu, basit bir başvuru atamasından 20 kat daha uzun sürebilir. Kutudan çıkarma sırasında, atama işlemi atamanın dört katı zaman alabilir. Daha fazla bilgi için bkz. [kutulama ve kutudan](../../csharp/programming-guide/types/boxing-and-unboxing.md)çıkarma.  
  
## <a name="strings"></a>Dizeler  
 Çok sayıda dize değişkenini birleştirme sırasında, örneğin sıkı bir döngüde, C# [+ işleci](../../csharp/language-reference/operators/addition-operator.md) veya Visual Basic [birleştirme işleçleri](../../visual-basic/language-reference/operators/concatenation-operators.md)yerine <xref:System.Text.StringBuilder?displayProperty=nameWithType> kullanın. Daha fazla bilgi için bkz. Visual Basic [Çoklu dizeleri](../../csharp/how-to/concatenate-multiple-strings.md) birleştirme ve [birleştirme işleçleri](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Yıkıcılar  
 Boş Yıkıcılar kullanılmamalıdır. Bir sınıf bir yıkıcı içerdiğinde, sonlandırma kuyruğunda bir giriş oluşturulur. Yıkıcı çağrıldığında, atık toplayıcı kuyruğu işlemek için çağrılır. Yok edicisi boşsa, bu yalnızca performans kaybı ile sonuçlanır. Daha fazla bilgi için bkz. [Yıkıcılar](../../csharp/programming-guide/classes-and-structs/destructors.md) ve [nesne ömrü: nesneler nasıl oluşturulur ve yok edilir](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Diğer Kaynaklar  
  
- [Daha hızlı yönetilen kod yazma: Işlerin maliyetini öğrenin](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973852(v=msdn.10))  
  
- [Yüksek performanslı yönetilen uygulamalar yazma: bir öncü](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973858(v=msdn.10))  
  
- [Çöp toplayıcı temelleri ve performans Ipuçları](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973837(v=msdn.10))  
  
- [.NET uygulamalarındaki performans Ipuçları ve püf noktaları](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v=msdn.10))  

- [Riko Mariani performansı tidbits](https://blogs.msdn.microsoft.com/ricom/)  

- [Vance Morrison blogu](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans](index.md)
- [Visual Basic programlama kılavuzu](../../visual-basic/programming-guide/index.md)
- [C# Programlama Kılavuzu](../../csharp/programming-guide/index.md)

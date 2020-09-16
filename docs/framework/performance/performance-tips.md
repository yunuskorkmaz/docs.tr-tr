---
title: .NET Performans İpuçları
description: .NET 'teki bir programın yürütme hızını artırmak için performans ipuçlarını keşfet. Kutulama ve kutudan çıkarma, dizeler ve Yıkıcılar için ipuçlarına bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c5e3f692c2bf754ccd35324019246ee905e8c591
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554651"
---
# <a name="net-performance-tips"></a>.NET Performans İpuçları
*Performans* terimi genellikle programın yürütme hızına başvurur. Kaynak kodunuzda belirli temel kuralları izleyerek, bazen yürütme hızını artırabilirsiniz. Bazı programlarda, kodu yakından incelemek ve profil oluşturucular kullanarak olabildiğince hızlı çalıştığından emin olmak önemlidir. Diğer programlarda, bu tür iyileştirme gerçekleştirmek zorunda değilsiniz çünkü kod yazıldığı kadar hızlı şekilde çalışıyor. Bu makalede, performansın önyüklenebileceği bazı yaygın bölgeler ve ek performans konularına yönelik bağlantılar yer almaktadır. Performansı planlama ve ölçme hakkında daha fazla bilgi için bkz. [performans](index.md)  
  
## <a name="boxing-and-unboxing"></a>Kutulama ve Kutudan Çıkarma  
 Değer türlerinin, örneğin gibi genel olmayan koleksiyonlar sınıflarında çok sayıda kez paketlenmeleri gerektiği durumlarda kullanmaktan kaçınmak en iyisidir <xref:System.Collections.ArrayList?displayProperty=nameWithType> . Gibi genel Koleksiyonlar kullanarak değer türlerinin kutulamaktan kaçınabilirsiniz <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> . Kutulama ve kutudan çıkarma, hesaplama açısından pahalı işlemlerdir. Bir değer türü paketlenme olduğunda, tamamen yeni bir nesne oluşturulması gerekir. Bu, basit bir başvuru atamasından 20 kat daha uzun sürebilir. Kutudan çıkarma sırasında, atama işlemi atamanın dört katı zaman alabilir. Daha fazla bilgi için bkz. [kutulama ve kutudan](../../csharp/programming-guide/types/boxing-and-unboxing.md)çıkarma.  
  
## <a name="strings"></a>Dizeler  
 Örneğin, çok sayıda dize değişkenini birleştirme sırasında, örneğin sıkı bir döngüde, <xref:System.Text.StringBuilder?displayProperty=nameWithType> C# [+ işleci](../../csharp/language-reference/operators/addition-operator.md) veya Visual Basic [birleştirme işleçleri](../../visual-basic/language-reference/operators/concatenation-operators.md)yerine kullanın. Daha fazla bilgi için bkz. Visual Basic [Çoklu dizeleri](../../csharp/how-to/concatenate-multiple-strings.md) birleştirme ve [birleştirme işleçleri](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Yıkıcılar  
 Boş Yıkıcılar kullanılmamalıdır. Bir sınıf bir yıkıcı içerdiğinde, sonlandırma kuyruğunda bir giriş oluşturulur. Yıkıcı çağrıldığında, atık toplayıcı kuyruğu işlemek için çağrılır. Yok edicisi boşsa, bu yalnızca performans kaybı ile sonuçlanır. Daha fazla bilgi için bkz. [Yıkıcılar](../../csharp/programming-guide/classes-and-structs/destructors.md) ve [nesne ömrü: nesneler nasıl oluşturulur ve yok edilir](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Diğer Kaynaklar  
  
- [Daha hızlı yönetilen kod yazma: Işlerin maliyetini öğrenin](/previous-versions/dotnet/articles/ms973852(v=msdn.10))  
  
- [Yüksek performanslı yönetilen uygulamalar yazma: bir öncü](/previous-versions/dotnet/articles/ms973858(v=msdn.10))  
  
- [Çöp toplayıcı temelleri ve performans Ipuçları](/previous-versions/dotnet/articles/ms973837(v=msdn.10))  
  
- [.NET uygulamalarındaki performans Ipuçları ve püf noktaları](/previous-versions/dotnet/articles/ms973839(v=msdn.10))  

- [Riko Mariani performansı tidbits](/archive/blogs/ricom/)  

- [Vance Morrison blogu](/archive/blogs/vancem/)
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans](index.md)
- [Visual Basic Programlama Kılavuzu](../../visual-basic/programming-guide/index.md)
- [C# Programlama Kılavuzu](../../csharp/programming-guide/index.md)

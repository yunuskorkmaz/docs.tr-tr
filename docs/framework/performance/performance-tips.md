---
title: .NET Performans İpuçları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
manager: wpickett
ms.workload:
- wiwagn
ms.openlocfilehash: ac1f5b9e0897650751320a7f5a9290c378d428b6
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="net-performance-tips"></a>.NET Performans İpuçları
Terim *performans* genellikle bir program yürütme hızını gösterir. Kaynak kodunuz temel belirli kurallarında izleyerek bazen yürütme hızını artırabilir. Bazı programlarda kodu yakından inceleyin ve mümkün olduğunca hızlı çalıştığından emin olmak için profil oluşturucular kullanmak önemlidir. Diğer programlarda hızlı yazılan kod çalışarak çalıştığından gibi en iyi duruma getirme gerçekleştirmek zorunda değildir. Bu makalede, bazı ortak burada performans olumsuz etkilenebilir alanları ve bunun yanı sıra ek performans konulara bağlantılar geliştirme ipuçları listelenmektedir. Planlama ve performans için ölçme hakkında daha fazla bilgi için bkz: [performans](../../../docs/framework/performance/index.md)  
  
## <a name="boxing-and-unboxing"></a>Kutulama ve Kutudan Çıkarma  
 En iyi değer kullanmaktan kaçınmak için bunlar burada olmalıdır durumlarda türleri çok sayıda kez, örneğin genel olmayan koleksiyon sınıfları gibi Kutulu <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Genel koleksiyonlar gibi kullanarak değer türleri kutulama önleyebilirsiniz <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Kutulama ve kutudan çıkarma pkı'ya pahalı işlemlerdir. Değer türü Kutulu, tamamen yeni bir nesne oluşturulması gerekir. Basit başvuru atama en çok 20 kez daha uzun sürer. Kutudan çıkarma, atama işleminin atama dört kez daha uzun sürebilir. Daha fazla bilgi için bkz: [kutulama ve kutudan çıkarma](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Dizeler  
 Çok sayıda dize değişkenleri birleştirmek, örneğin sıkı bir döngüde kullanın <xref:System.Text.StringBuilder?displayProperty=nameWithType> yerine C# [+ işleci](~/docs/csharp/language-reference/operators/addition-operator.md) veya Visual Basic [birleştirme işleçleri](~/docs/visual-basic/language-reference/operators/concatenation-operators.md). Daha fazla bilgi için bkz: [nasıl yapılır: birden çok dizeyi birleştirme](../../csharp/how-to/concatenate-multiple-strings.md) ve [Visual Basic'de birleştirme işleçleri](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Yıkıcılar  
 Boş Yıkıcılar kullanılmamalıdır. Bir sınıf bir yıkıcı içeriyorsa, bir giriş Finalize sıraya oluşturulur. Yok Edicisi çağrıldığında atık toplayıcı sırasını işlemek üzere çağrılır. Yıkıcı boşsa, bu yalnızca bir performans kaybı ile sonuçlanır. Daha fazla bilgi için bkz: [Yıkıcılar](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) ve [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Diğer Kaynaklar  
  
-   [Yönetilen kodu daha hızlı yazma: Ne şeyler maliyet bildirin](http://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [Yazma yüksek performanslı uygulamalar yönetilen: Öncü](http://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [Çöp toplayıcı temel kavramları ve performans ipuçları](http://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [Performans İpuçları ve püf noktaları .NET uygulamalarında](http://go.microsoft.com/fwlink/?LinkId=99297)  

-   [Riko Mariani'nın performans ipuçları](http://go.microsoft.com/fwlink/?LinkId=115679)  

-   [Vance Morrison'ın blogu](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans](../../../docs/framework/performance/index.md)  
 [Programlama Kavramları](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6)  
 [Visual Basic programlama kılavuzu](../../visual-basic/programming-guide/index.md)  
 [C# Programlama Kılavuzu](http://msdn.microsoft.com/library/ac0f23a2-6bf3-4077-be99-538ae5fd3bc5)

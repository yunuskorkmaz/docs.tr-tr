---
title: Genel Yöntemler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 04bc59d41eb7883e08138382b396bc737c7f11bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329874"
---
# <a name="generic-methods-c-programming-guide"></a>Genel Yöntemler (C# Programlama Kılavuzu)
Genel yöntem tür parametreleri ile aşağıdaki gibi bildirilmiş bir yöntemdir:  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 Aşağıdaki kod örneği kullanarak yöntemini çağırmak için bir yolunu gösterir `int` tür bağımsız değişkeni için:  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 Tür bağımsız değişkeni de atlayabilirsiniz ve derleyici Infer. Aşağıdaki çağrı `Swap` önceki çağrısına eşdeğerdir:  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 Tür çıkarımı için aynı kuralları statik yöntemler ve örnek yöntemleri için geçerlidir. Derleyici, geçirdiğiniz yöntem bağımsız değişkenleri temel tür parametreleri çıkarımını; Tür parametreleri yalnızca bir kısıtlama gelen Infer veya dönüş değeri. Bu nedenle tür çıkarımı parametresi olmayan yöntemleriyle çalışmaz. Tür çıkarımı derleyici aşırı yüklenmiş yöntemin imzaları çözümlemeye önce derleme zamanında oluşur. Derleyici aynı adı paylaşan tüm genel yöntemler tür çıkarımı mantığı uygular. Aşırı yükleme çözümü adımda Derleyici yalnızca üzerinde tür çıkarımı başarılı genel yöntemler içerir.  
  
 Genel bir sınıf içinde genel olmayan yöntemleri sınıf düzeyi tür parametreleri aşağıdaki gibi erişebilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 Aynı tür parametreleri içeren sınıf gereken genel bir yöntem tanımlarsanız yöntemi kapsamında bağımsız değişkeni için iç sağladığından derleyici uyarı CS0693 oluşturur `T` dış içinsağlananbağımsızdeğişkengizler`T`. Tür bağımsız değişkenleri sınıfı örneğinin başlatılmasından çalıştırılırken sağlanan dışındaki genel sınıfı yöntemiyle çağırma esnekliğini gerektiriyorsa, başka bir tanımlayıcı yöntemi tür parametresi için sağlamayı gösterildiği gibi düşünün `GenericList2<T>` aşağıdaki örnek.  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 Tür parametrelerindeki yöntemler daha özelleştirilmiş işlemlerini etkinleştirmek için kısıtlamaları kullanın. Bu sürümü `Swap<T>`, şimdi adlandırılmış `SwapIfGreater<T>`, yalnızca uygulama tür bağımsız değişkenleri ile kullanılabilir <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 Genel yöntemler birkaç türü parametrelerine aşırı yüklenmiş. Örneğin, aşağıdaki yöntemlerden tümü aynı sınıfta bulunabilir:  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)

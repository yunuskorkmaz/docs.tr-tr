---
title: Genel yöntemler-C# Programlama Kılavuzu
description: Genel yöntemler olarak bilinen tür parametreleriyle belirtilen yöntemler hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 195e3f11c73a17931fa6331750e2ae4ee8fd6f10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151473"
---
# <a name="generic-methods-c-programming-guide"></a>Genel Yöntemler (C# Programlama Kılavuzu)

Genel bir yöntem, tür parametreleriyle belirtilen ve aşağıdaki gibi bir yöntemdir:  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 Aşağıdaki kod örneği, `int` tür bağımsız değişkeni için kullanarak yöntemini çağırmak için bir yol gösterir:  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 Ayrıca tür bağımsız değişkenini de atlayabilirsiniz, derleyici onu çıkaracaktır. Aşağıdaki çağrısı, `Swap` önceki çağrıya eşdeğerdir:  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 Tür çıkarımı için aynı kurallar statik yöntemler ve örnek yöntemler için geçerlidir. Derleyici, tür parametrelerini geçirdiğiniz Yöntem bağımsız değişkenlerine göre çıkarabilir; tür parametreleri yalnızca bir kısıtlamadan veya dönüş değerinden çıkarılamaz. Bu nedenle tür çıkarımı parametresi olmayan yöntemlerle çalışmaz. Derleyici aşırı yüklenmiş yöntem imzalarını çözmeyi denemeden önce derleme zamanında tür çıkarımı oluşur. Derleyici, aynı adı paylaşan tüm genel metotlara tür çıkarımı mantığını uygular. Aşırı yükleme çözümleme adımında, derleyici yalnızca tür çıkarımı başarılı olan genel yöntemleri içerir.  
  
 Genel bir sınıf içinde genel olmayan yöntemler, sınıf düzeyi tür parametrelerine aşağıdaki gibi erişebilir:  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 İçerilen sınıfla aynı tür parametrelerini alan genel bir yöntem tanımlarsanız, derleyici yöntem kapsamı içinde uyarı [CS0693](../../misc/cs0693.md) oluşturur, iç için sağlanan bağımsız değişken `T` dıştaki için sağlanan bağımsız değişkeni gizler `T` . Sınıf örneği oluşturulurken sağlandıklardan farklı tür bağımsız değişkenleriyle bir genel sınıf yöntemi çağırma esnekliğine ihtiyaç duyuyorsanız, aşağıdaki örnekte gösterildiği gibi yönteminin tür parametresi için başka bir tanımlayıcı sağlamayı düşünün `GenericList2<T>` .  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 Yöntemlerde tür parametrelerinde daha özelleştirilmiş işlemleri sağlamak için kısıtlamaları kullanın. `Swap<T>`Artık adlandırılan bu sürümü `SwapIfGreater<T>` Yalnızca uygulayan tür bağımsız değişkenleriyle kullanılabilir <xref:System.IComparable%601> .  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 Genel metotlar çeşitli tür parametrelerinde aşırı yüklenebilir. Örneğin, aşağıdaki yöntemler aynı sınıfta bulunabilir:  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

 Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Yöntemler](../classes-and-structs/methods.md)

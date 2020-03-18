---
title: Genel Yöntemler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 5f066ca39c97b70554886e423c37c4ee47d49158
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712201"
---
# <a name="generic-methods-c-programming-guide"></a>Genel Yöntemler (C# Programlama Kılavuzu)
Genel bir yöntem, tür parametreleri ile bildirilen bir yöntemdir:  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 Aşağıdaki kod örneği, tür bağımsız değişkeni `int` için kullanarak yöntemi çağırmanın bir yolunu gösterir:  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 Ayrıca tür bağımsız değişkenini atlayabilirsiniz ve derleyici bunu çıkaracaktır. Aşağıdaki arama `Swap` önceki çağrıya eşdeğerdir:  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 Tür çıkarım için aynı kurallar statik yöntemler ve örnek yöntemleri için de geçerlidir. Derleyici, geçiş yaptığınız yöntem bağımsız değişkenlerine göre tür parametrelerini çıkartabilir; tür parametrelerini yalnızca bir kısıtlama veya geri dönüş değerinden çıkaramaz. Bu nedenle tür çıkarım hiçbir parametre si olmayan yöntemlerle çalışmıyor. Tür çıkarımı, derleyici aşırı yüklenen yöntem imzalarını çözmeye çalışmadan önce derleme zamanında gerçekleşir. Derleyici, aynı adı paylaşan tüm genel yöntemlere tür çıkarım mantığı uygular. Aşırı yük çözümlemesi adımında derleyici yalnızca tür çıkarımlarında başarılı olan genel yöntemleri içerir.  
  
 Genel bir sınıf içinde, genel olmayan yöntemler sınıf düzeyi türü parametrelerine aşağıdaki gibi erişebilir:  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 İçerdiği sınıfla aynı tür parametrelerini alan genel bir yöntem tanımlarsanız, derleyici [cs0693](../../misc/cs0693.md) uyarısı üretir, `T` çünkü yöntem kapsamı içinde, `T`iç için sağlanan bağımsız değişken dış için sağlanan bağımsız değişkeni gizler. Sınıf anında yapıldığında sağlananlar dışındaki tür bağımsız değişkenleri ile genel bir sınıf yöntemini çağırma esnekliğine ihtiyaç duyuyorsanız, aşağıdaki örnekte `GenericList2<T>` gösterildiği gibi yöntemin tür parametresi için başka bir tanımlayıcı sağlamayı düşünün.  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 Yöntemlerdeki tür parametreleri üzerinde daha özel işlemler etkinleştirmek için kısıtlamaları kullanın. Şimdi adlandırılmış `Swap<T>` `SwapIfGreater<T>`olan bu sürüm yalnızca uygulayan <xref:System.IComparable%601>tür bağımsız değişkenleri ile kullanılabilir.  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 Genel yöntemler çeşitli tür parametreleri üzerinde aşırı yüklenebilir. Örneğin, aşağıdaki yöntemlerin tümü aynı sınıfta bulunabilir:  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Yöntemler](../classes-and-structs/methods.md)

---
title: Temsilciler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 96de5601c60dd309fe5467414affd20b8bc93d87
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006177"
---
# <a name="delegates-c-programming-guide"></a>Temsilciler (C# Programlama Kılavuzu)
A [temsilci](../../../csharp/language-reference/keywords/delegate.md) belirli bir parametre listesi olan yöntemlere başvuruları temsil eden bir tür ve dönüş türü. Bir temsilci oluşturduğunuzda, örneğini uyumlu bir imza ve dönüş türü içeren herhangi bir yöntemle ilişkilendirebilirsiniz. Yöntemi, temsilci örneği aracılığıyla çağırabilirsiniz.  
  
 Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır. Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Özel bir yöntem oluşturabilirsiniz ve bir pencere denetimi gibi bir sınıf, belirli bir olay olduğunda yönteminizi çağırabilir. Aşağıdaki örnek, bir temsilci bildirimini gösterir:  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 Temsilci türüyle eşleşen herhangi bir erişilebilir sınıf veya yapıdan alınan herhangi bir yöntem temsilciye atanabilir. Yöntem, statik veya örnek bir yöntem olabilir. Bu, yöntem çağrılarını programatik olarak değiştirmeyi ve varolan sınıflara yeni kod eklemeyi olanaklı kılar.  
  
> [!NOTE]
>  Yöntem aşırı yükü bağlamında, yöntemin imzası dönüş değeri içermez. Ancak, temsilciler bağlamında, imza dönüş değerini içermez. Başka bir deyişle, bir yöntemin dönüş türü temsilciyle aynı olmalıdır.  
  
 Bir yönteme bir parametre olarak başvurma yeteneği, temsilciyi geri çağırma yöntemleri için ideal hale getirir. Örneğin, iki nesneyi karşılaştıran bir yönteme yapılan bir başvuru, bir sıralama algoritmasına bir bağımsız değişken olarak geçirilebilir. Karşılaştırma kodu ayrı bir yordamda olduğundan, sıralama algoritması daha genel bir şekilde yazılabilir.  
  
## <a name="delegates-overview"></a>Temsilcilere Genel Bakış  
 Temsilciler aşağıdaki özelliklere sahiptir:  
  
-   Temsilciler C++ işlev işaretçilerine benzer ancak temsilcileri, bir tam nesne yönelimli ve hem nesne örneği hem de bir yöntem üye işlevlerinin C++ işaretçileri, temsilciler yalıtma.
  
-   Temsilciler, yöntemlerin parametre olarak geçirilmesine olanak tanır.  
  
-   Temsilciler, geri çağırma yöntemlerini tanımlamak için kullanılabilir.  
  
-   Temsilciler birlikte zincirleme yapılabilir; Örneğin, tek bir olay üzerine birden çok yöntem çağrılabilir.  
  
-   Yöntemlerin temsilci türüyle tam olarak eşleşmesi gerekmez. Daha fazla bilgi için [kullanarak Temsilcilerde varyans](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
-   C# sürüm 2.0 kavramını kullanıma sundu [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), kod bloklarının ayrı olarak tanımlanan bir yöntem yerine parametre olarak geçirilmesine izin verin. C# 3.0, satır içi kod blokları yazmak için daha kısa bir yol olarak lambda ifadelerini kullanmaya başladı. Hem anonim yöntemler hem de lambda ifadeleri (belirli bağlamlarda) temsilci türleri olarak derlenir. Birlikte, bu özellikler artık anonim işlevler olarak bilinir. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [Temsilcileri Kullanma](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [Arabirimler (C# programlama Kılavuzu) yerine temsilciler ne zaman kullanılır?](https://msdn.microsoft.com/library/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [Anonim Metotlar](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [Temsilcilerde Varyans Kullanma](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [Nasıl yapılır: temsilcileri (çok noktaya yayın temsilcileri) birleştirme](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 [Temsilciler, olayları ve Lambda ifadeleri](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) içinde [C# 3.0 Cookbook, Third Edition: C# 3.0 programcıları için 250'den fazla çözüm](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Temsilciler ve olaylar](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) içinde [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Delegate>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Olaylar](../../../csharp/programming-guide/events/index.md)

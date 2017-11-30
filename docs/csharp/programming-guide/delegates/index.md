---
title: "Temsilciler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a6649537238af38e073eeb8747487822d058b7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="delegates-c-programming-guide"></a>Temsilciler (C# Programlama Kılavuzu)
A [temsilci](../../../csharp/language-reference/keywords/delegate.md) belirli parametre listesi yöntemleriyle başvurular temsil eden bir tür ve dönüş türü. Bir temsilci oluşturduğunuzda, örneğini uyumlu bir imza ve dönüş türü içeren herhangi bir yöntemle ilişkilendirebilirsiniz. Yöntemi, temsilci örneği aracılığıyla çağırabilirsiniz.  
  
 Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır. Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Özel bir yöntem oluşturabilirsiniz ve bir pencere denetimi gibi bir sınıf, belirli bir olay olduğunda yönteminizi çağırabilir. Aşağıdaki örnek, bir temsilci bildirimini gösterir:  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 Temsilci türüyle eşleşen herhangi bir erişilebilir sınıf veya yapıdan alınan herhangi bir yöntem temsilciye atanabilir. Yöntem, statik veya örnek bir yöntem olabilir. Bu, yöntem çağrılarını programatik olarak değiştirmeyi ve varolan sınıflara yeni kod eklemeyi olanaklı kılar.  
  
> [!NOTE]
>  Yöntem aşırı yükü bağlamında, yöntemin imzası dönüş değeri içermez. Ancak, temsilciler bağlamında, imza dönüş değerini içermez. Başka bir deyişle, bir yöntemin dönüş türü temsilciyle aynı olmalıdır.  
  
 Bir yönteme bir parametre olarak başvurma yeteneği, temsilciyi geri çağırma yöntemleri için ideal hale getirir. Örneğin, iki nesneyi karşılaştıran bir yönteme yapılan bir başvuru, bir sıralama algoritmasına bir bağımsız değişken olarak geçirilebilir. Karşılaştırma kodu ayrı bir yordamda olduğundan, sıralama algoritması daha genel bir şekilde yazılabilir.  
  
## <a name="delegates-overview"></a>Temsilcilere Genel Bakış  
 Temsilciler aşağıdaki özelliklere sahiptir:  
  
-   Temsilciler C++ işlev işaretçileri gibidir, fakat tür bakımından güvenlidir.  
  
-   Temsilciler, yöntemlerin parametre olarak geçirilmesine olanak tanır.  
  
-   Temsilciler, geri çağırma yöntemlerini tanımlamak için kullanılabilir.  
  
-   Temsilciler birlikte zincirleme yapılabilir; Örneğin, tek bir olay üzerine birden çok yöntem çağrılabilir.  
  
-   Yöntemlerin temsilci türüyle tam olarak eşleşmesi gerekmez. Daha fazla bilgi için bkz: [kullanarak Temsilcilerde varyans](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
-   C# 2.0 sürümünde sunulan kavramı [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), kod blokları ayrı olarak tanımlanan bir yöntem yerine parametre olarak geçirilen izin verin. C# 3.0, satır içi kod blokları yazmak için daha kısa bir yol olarak lambda ifadelerini kullanmaya başladı. Hem anonim yöntemler hem de lambda ifadeleri (belirli bağlamlarda) temsilci türleri olarak derlenir. Birlikte, bu özellikler artık anonim işlevler olarak bilinir. Lambda ifadeleri hakkında daha fazla bilgi için bkz: [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [Temsilcileri kullanma](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [Arabirimler (C# programlama Kılavuzu) yerine ne zaman kullanılacağı temsilciler](http://msdn.microsoft.com/en-us/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [Temsilciler adlandırılmış vs ile. Anonim yöntemler](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [Anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [Temsilcilerde varyans kullanma](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [Nasıl yapılır: temsilcileri (çok noktaya yayın temsilcileri) birleştirme](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [Nasıl yapılır: bildirme, oluşturma ve bir temsilci kullanın](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 [Temsilciler ve olaylar Lambda ifadeleri](http://go.microsoft.com/fwlink/?LinkId=195395) içinde [C# 3.0 Kılavuzu, üçüncü baskı: C# 3.0 programcıları için 250'den fazla çözüm](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
 [Temsilciler ve olaylar](http://go.microsoft.com/fwlink/?LinkId=195418) içinde [öğrenme C# 3.0: C# 3.0 ile ilgili temel bilgileri Yöneticisi](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Delegate>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Olayları](../../../csharp/programming-guide/events/index.md)

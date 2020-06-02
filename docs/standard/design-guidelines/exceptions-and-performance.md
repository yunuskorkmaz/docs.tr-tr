---
title: Özel Durumlar ve Performans
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: a558547f0e6770e7e76ca31f760d6e2f55c712db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289791"
---
# <a name="exceptions-and-performance"></a>Özel Durumlar ve Performans
Özel durumlarla ilgili yaygın bir sorun, düzenli olarak başarısız olan kod için özel durumlar kullanılıyorsa, uygulamanın performansının kabul edilemez olacağı bir konudur. Bu, geçerli bir konudur. Bir üye özel durum oluşturduğunda, performansı daha yavaş olabilir. Ancak, hata kodlarının kullanılmasına izin vermeyen özel durum yönergelerine tam olarak uyurken iyi bir performans elde etmek mümkündür. Bu bölümde açıklanan iki desen bunu yapmak için yollar önerir.

 ❌Özel durumların performansı olumsuz etkileyebilecek sorunlar nedeniyle hata kodlarını kullanmayın.

 Performansı artırmak için, sonraki iki bölümde açıklanan sınayıcı-doer deseninin veya TRY-Parse deseninin kullanılması mümkündür.

## <a name="tester-doer-pattern"></a>Sınayıcı-doer stili
 Bazen özel durum atma üyesinin performansı, üyenin iki içine bölünerek artırılabilir. <xref:System.Collections.Generic.ICollection%601.Add%2A>Arabirimin yöntemine bakalım <xref:System.Collections.Generic.ICollection%601> .

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 `Add`Koleksiyon salt okunurdur, yöntemi atar. Bu, yöntem çağrısının genellikle başarısız olması beklenen senaryolarda bir performans sorunu olabilir. Sorunu hafifletmenin yöntemlerinden biri, bir değer eklemeye çalışmadan önce koleksiyonun yazılabilir olup olmadığını test eteklemektir.

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 Örneğimizde bir koşulu test etmek için kullanılan üye, `IsReadOnly` sınayıcı olarak adlandırılır. Olası bir atma işlemini gerçekleştirmek için kullanılan üye, `Add` örneğimizdeki yöntemi, doer olarak adlandırılır.

 ✔️ özel durumlarla ilgili performans sorunlarından kaçınmak için ortak senaryolarda özel durumlar oluşturabilecek Üyeler için sınayıcı-doer modelini göz önünde bulundurun.

## <a name="try-parse-pattern"></a>TRY-Parse kriteri
 Son derece performansa duyarlı API 'Ler için, önceki bölümde açıklanan sınayıcı-doer deseninin daha da hızlı bir şekilde kullanılması gerekir. Model, üye semantiğinin bir parçası olarak iyi tanımlanmış bir test çalışması yapmak için üye adını ayarlamayı çağırır. Örneğin, <xref:System.DateTime> <xref:System.DateTime.Parse%2A> bir dizeyi ayrıştırma başarısız olursa özel durum oluşturan bir yöntemi tanımlar. Ayrıca <xref:System.DateTime.TryParse%2A> , ayrıştırmaya deneyen karşılık gelen bir yöntemi tanımlar, ancak ayrıştırma başarısız olursa false döndürür ve bir parametre kullanarak başarılı bir ayrıştırma sonucunu döndürür `out` .

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 Bu model kullanılırken, TRY işlevlerini katı koşullarda tanımlamak önemlidir. Üye, iyi tanımlanmış deneme dışında herhangi bir nedenle başarısız olursa, üye yine de karşılık gelen bir özel durum oluşturması gerekir.

 ✔️ özel durumlarla ilgili performans sorunlarından kaçınmak için ortak senaryolarda özel durumlar oluşturabilecek Üyeler için TRY-Parse modelini göz önünde bulundurun.

 ✔️, bu kalıbı uygulayan yöntemler için "TRY" önekini ve Boole dönüş türünü kullanır.

 ✔️, TRY-Parse modelini kullanarak her üye için bir özel durum atma üyesi sağlar.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Özel Durumlar için Tasarım Yönergeleri](exceptions.md)

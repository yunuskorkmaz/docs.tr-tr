---
description: 'Daha fazla bilgi edinin: özel durumlar ve performans'
title: Özel Durumlar ve Performans
ms.date: 10/22/2008
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: 72b35ccca5514e56dcc04fc0a07d1f9887c4a2f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642129"
---
# <a name="exceptions-and-performance"></a>Özel Durumlar ve Performans

Özel durumlarla ilgili yaygın bir sorun, düzenli olarak başarısız olan kod için özel durumlar kullanılıyorsa, uygulamanın performansının kabul edilemez olacağı bir konudur. Bu, geçerli bir endişedir. Bir üye özel durum oluşturduğunda, performansı daha yavaş olabilir. Ancak, hata kodlarının kullanılmasına izin vermeyen özel durum yönergelerine tam olarak uyurken iyi bir performans elde etmek mümkündür. Bu bölümde açıklanan iki desen bunu yapmak için yollar önerir.

 ❌ Özel durumların performansı olumsuz etkileyebilecek sorunlar nedeniyle hata kodlarını kullanmayın.

 Performansı artırmak için, sonraki iki bölümde açıklanan Tester-Doer deseninin veya Try-Parse deseninin kullanılması mümkündür.

## <a name="tester-doer-pattern"></a>Tester-Doer deseninin

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

 ✔️ özel durumlarla ilgili performans sorunlarından kaçınmak için ortak senaryolarda özel durumlar oluşturabilecek Üyeler için Tester-Doer modelini göz önünde bulundurun.

## <a name="try-parse-pattern"></a>Try-Parse deseninin

 Son derece performans duyarlı API 'Ler için, önceki bölümde açıklanan Tester-Doer deseninin daha hızlı bir düzende kullanılması gerekir. Model, üye semantiğinin bir parçası olarak iyi tanımlanmış bir test çalışması yapmak için üye adını ayarlamayı çağırır. Örneğin, <xref:System.DateTime> <xref:System.DateTime.Parse%2A> bir dizeyi ayrıştırma başarısız olursa özel durum oluşturan bir yöntemi tanımlar. Ayrıca <xref:System.DateTime.TryParse%2A> , ayrıştırmaya deneyen karşılık gelen bir yöntemi tanımlar, ancak ayrıştırma başarısız olursa false döndürür ve bir parametre kullanarak başarılı bir ayrıştırma sonucunu döndürür `out` .

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

 ✔️ özel durumlarla ilgili performans sorunlarından kaçınmak için ortak senaryolarda özel durumlar oluşturabilecek Üyeler için Try-Parse modelini göz önünde bulundurun.

 ✔️, bu kalıbı uygulayan yöntemler için "TRY" önekini ve Boole dönüş türünü kullanır.

 ✔️, Try-Parse modelini kullanarak her üye için bir özel durum atma üyesi sağlar.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Özel Durumlar için Tasarım Yönergeleri](exceptions.md)

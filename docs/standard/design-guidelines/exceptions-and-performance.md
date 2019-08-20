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
author: KrzysztofCwalina
ms.openlocfilehash: 967692092186b81802a7ab635ea8fe4dbacd49ed
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611509"
---
# <a name="exceptions-and-performance"></a>Özel Durumlar ve Performans
Özel durumlarla ilgili yaygın bir sorun, düzenli olarak başarısız olan kod için özel durumlar kullanılıyorsa, uygulamanın performansının kabul edilemez olacağı bir konudur. Bu, geçerli bir konudur. Bir üye özel durum oluşturduğunda, performansı daha yavaş olabilir. Ancak, hata kodlarının kullanılmasına izin vermeyen özel durum yönergelerine tam olarak uyurken iyi bir performans elde etmek mümkündür. Bu bölümde açıklanan iki desen bunu yapmak için yollar önerir.

 **X DO NOT** özel durumlar performansı olumsuz etkileyebilir sorunları nedeniyle hata kodları kullanın.

 Performansı artırmak için, sonraki iki bölümde açıklanan sınayıcı-doer deseninin veya TRY-Parse deseninin kullanılması mümkündür.

## <a name="tester-doer-pattern"></a>Sınayıcı-doer stili
 Bazen özel durum atma üyesinin performansı, üyenin iki içine bölünerek artırılabilir. <xref:System.Collections.Generic.ICollection%601> Arabirimin <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemine bakalım.

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 Koleksiyon salt `Add` okunurdur, yöntemi atar. Bu, yöntem çağrısının genellikle başarısız olması beklenen senaryolarda bir performans sorunu olabilir. Sorunu hafifletmenin yöntemlerinden biri, bir değer eklemeye çalışmadan önce koleksiyonun yazılabilir olup olmadığını test eteklemektir.

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 Örneğimizde `IsReadOnly`bir koşulu test etmek için kullanılan üye, sınayıcı olarak adlandırılır. Olası bir atma işlemini `Add` gerçekleştirmek için kullanılan üye, örneğimizdeki yöntemi, doer olarak adlandırılır.

 **✓ CONSIDER** Tester Doer düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.

## <a name="try-parse-pattern"></a>TRY-Parse kriteri
 Son derece performansa duyarlı API 'Ler için, önceki bölümde açıklanan sınayıcı-doer deseninin daha da hızlı bir şekilde kullanılması gerekir. Model, üye semantiğinin bir parçası olarak iyi tanımlanmış bir test çalışması yapmak için üye adını ayarlamayı çağırır. Örneğin, <xref:System.DateTime> bir dizeyi ayrıştırma <xref:System.DateTime.Parse%2A> başarısız olursa özel durum oluşturan bir yöntemi tanımlar. Ayrıca, ayrıştırmaya deneyen <xref:System.DateTime.TryParse%2A> karşılık gelen bir yöntemi tanımlar, ancak ayrıştırma başarısız olursa false döndürür ve bir `out` parametre kullanarak başarılı bir ayrıştırma sonucunu döndürür.

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

 **✓ CONSIDER** deneyin ayrıştırma düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.

 **✓ DO** bu düzeni uygulama yöntemleri için "Deneme" ve Boolean dönüş türü önekini kullanın.

 **✓ DO** deneyin ayrıştırma desenini kullanarak her üyesi için bir özel durum atma üye sağlayın.

 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Framework tasarım yönergelerinden [Pearson Eğitim, Inc. izni ile yeniden yazdırılıyor: Microsoft Windows geliştirme serisi 'nin bir parçası olarak, bezysztof](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Cwalina ve atacan abkms, Ekim 22, 2008 ile Addison-Wesley Professional ile yeniden kullanılabilir .NET kitaplıkları için kurallar, ıoms ve desenler.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)

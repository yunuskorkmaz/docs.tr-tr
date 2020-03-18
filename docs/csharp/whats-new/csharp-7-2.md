---
title: C# 7.2 Yenilikleri
description: C# 7.2'deki yeni özelliklere genel bakış.
ms.date: 08/16/2017
ms.openlocfilehash: 7febefb81bbea6f24690adb05488ad6a18bbf552
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75694601"
---
# <a name="whats-new-in-c-72"></a>C# 7.2 Yenilikleri

C# 7.2, bir dizi kullanışlı özellik ekleyen başka bir nokta sürümedir.
Bu sürüm için bir tema gereksiz kopyaları veya ayırmaları kaçınarak değer türleri ile daha verimli çalışıyor.

Geri kalan özellikler küçük, sahip olmak için güzel özelliklerdir.

C# 7.2 derleyici dil sürümünü seçmek için [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesini kullanır.

Bu sürümdeki yeni dil özellikleri şunlardır:

- [Güvenli verimli kod yazma teknikleri](#safe-efficient-code-enhancements)
  - Referans semantikkullanarak değer türleri ile çalışmayı sağlayan sözdizimi geliştirmelerinin birleşimi.
- [Girintili olmayan adlandırılmış bağımsız değişkenler](#non-trailing-named-arguments)
  - Adlandırılmış bağımsız değişkenler konumsal bağımsız değişkenler tarafından izlenebilir.
- [Sayısal edebi alanlarda önde gelen alt](#leading-underscores-in-numeric-literals)
  - Sayısal literals artık herhangi bir yazdırılan basamak önce önde gelen alt çizerolabilir.
- [`private protected`erişim değiştirici](#private-protected-access-modifier)
  - Erişim `private protected` değiştiricisi, aynı derlemede türetilmiş sınıflar için erişim sağlar.
- [Koşullu `ref` ifadeler](#conditional-ref-expressions)
  - Koşullu ifadenin sonucu`?:`( ) artık bir başvuru olabilir.

Bu makalenin geri kalanı her özelliğin genel bir özetini sağlar. Her özellik için, bunun arkasındaki mantığı öğreneceksiniz. Sözdizimini öğreneceksin. `dotnet try` Bu özellikleri ortamınızda genel aracı kullanarak keşfedebilirsiniz:

1. [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global aracını yükleyin.
1. [Dotnet/try-samples](https://github.com/dotnet/try-samples) deposunu klonla.
1. *Deneme örnekleri* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="safe-efficient-code-enhancements"></a>Güvenli verimli kod geliştirmeleri

7.2'de tanıtılan dil özellikleri, referans semantikini kullanırken değer türleri ile çalışmanıza izin verirken. Bunlar, başvuru türlerini kullanmayla ilişkili bellek ayırmalarına maruz kalmadan kopyalama değer türlerini en aza indirerek performansı artırmak üzere tasarlanmıştır. Özellikler şunlardır:

- Bir `in` bağımsız değişkenin başvuru yla geçirildiğini, ancak çağrılan yöntem tarafından değiştirilmediğini belirtmek için parametreler üzerinde değiştirici. `in` Bir bağımsız değişkene değiştirici eklemek kaynak uyumlu bir [değişikliktir.](version-update-considerations.md#source-compatible-changes)
- Yöntemüzerindeki `ref readonly` değiştirici, bir yöntemin değerini başvuruyla döndürür, ancak bu nesneye yazmaya izin vermez belirtmek için döndürür. Değiştirici `ref readonly` ekleme, bir değere atanmışsa kaynak uyumlu bir [değişikliktir.](version-update-considerations.md#source-compatible-changes) `readonly` Varolan `ref` bir iade deyimine değiştirici eklemek uyumsuz bir [değişikliktir.](version-update-considerations.md#incompatible-changes) Arayanların `readonly` değiştiriciyi içerecek `ref` şekilde yerel değişkenlerin bildirimini güncelleştirmelerini gerektirir.
- Bir `readonly struct` yapının değişmez olduğunu ve üye yöntemlerine `in` bir parametre olarak geçirilmesi gerektiğini belirtmek için bildirim. `readonly` Varolan bir yapı bildirimine değiştirici nin eklenmesi ikili uyumlu bir [değişikliktir.](version-update-considerations.md#binary-compatible-changes)
- `ref struct` Bir yapı türünün yönetilen belleğe doğrudan eriştiğini ve her zaman yığın ayrılması gerektiğini belirtmek için bildirim. `ref` Varolan `struct` bir bildirime değiştirici eklemek uyumsuz bir [değişikliktir.](version-update-considerations.md#incompatible-changes) A, `ref struct` bir sınıfın üyesi olamaz veya yığına ayrılabileceği diğer konumlarda kullanılamaz.

Güvenli [verimli kod yaz'da](../write-safe-efficient-code.md)tüm bu değişiklikler hakkında daha fazla bilgi edinebilirsiniz.

## <a name="non-trailing-named-arguments"></a>Girintili olmayan adlandırılmış bağımsız değişkenler

Yöntem çağrıları artık, adlandırılmış bağımsız değişkenler doğru konumlardayken konumsal bağımsız değişkenlerden önce gelen adlandırılmış bağımsız değişkenleri kullanabilir. Daha fazla bilgi için [bkz.](../programming-guide/classes-and-structs/named-and-optional-arguments.md)

## <a name="leading-underscores-in-numeric-literals"></a>Sayısal edebi alanlarda önde gelen alt

C# 7.0'da basamak ayırıcıları için destek uygulanması, gerçek değerin ilk karakteri olmasını izin `_` vermedi. Hex ve ikili sayısal literals şimdi `_`bir ile başlayabilir .

Örnek:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>*özel korumalı* erişim değiştirici

Yeni bir bileşik erişim `private protected` değiştirici: bir üyeye aynı derlemede bildirilen sınıf veya türetilmiş sınıflar içeren erişilebilir olabileceğini gösterir. Türetilmiş sınıfların veya aynı derlemede bulunan `private protected` sınıfların erişimine izin vermekle birlikte, `protected internal` aynı derlemede bildirilen türemiş türlere erişimi sınırlar.

Daha fazla bilgi için dil [başvurusundaki erişim değiştiricilere](../language-reference/keywords/access-modifiers.md) bakın.

## <a name="conditional-ref-expressions"></a>Koşullu `ref` ifadeler

Son olarak, koşullu ifade bir değer sonucu yerine bir ref sonucu üretebilir. Örneğin, iki diziden birinde ilk öğeye bir başvuru almak için aşağıdakileri yazarsınız:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

Değişken, `r` ilk `arr` değere yapılan bir `otherArr`başvurudur ya da .

Daha fazla bilgi için [koşullu işleç (?:)](../language-reference/operators/conditional-operator.md) dil başvurusunda.

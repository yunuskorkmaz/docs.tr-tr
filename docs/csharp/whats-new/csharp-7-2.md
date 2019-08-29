---
title: C# 7,2 sürümündeki yenilikler
description: C# 7,2 sürümündeki yeni özelliklere genel bakış.
ms.date: 08/16/2017
ms.openlocfilehash: a2010b2bda769a625deb545964a2cc127aaf2e06
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105739"
---
# <a name="whats-new-in-c-72"></a>C# 7,2 sürümündeki yenilikler

C#7,2, çok sayıda yararlı özellik ekleyen başka bir nokta sürümüdür.
Bu yayın için bir tema gereksiz kopyaları veya ayırmaları önleyerek değer türleriyle daha verimli çalışıyor.

Kalan özellikler küçük, tam özellikli özelliklerdir.

C#7,2, derleyici dili sürümünü seçmek için [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesini kullanır.

Bu sürümdeki yeni dil özellikleri şunlardır:

- [Güvenli verimli kod yazma teknikleri](#safe-efficient-code-enhancements)
  - Başvuru semantiğinin kullanıldığı değer türleriyle çalışmayı sağlayan sözdizimi geliştirmelerinden oluşan bir bileşim.
- [Girintili olmayan adlandırılmış bağımsız değişkenler](#non-trailing-named-arguments)
  - Adlandırılmış bağımsız değişkenlerin ardından konumsal bağımsız değişkenler gelebilir.
- [Sayısal sabit değerlerde önde gelen alt çizgiler](#leading-underscores-in-numeric-literals)
  - Sayısal değişmez değerler artık, yazdırılan rakamlardan önce önde gelen alt çizgileri olabilir.
- [`private protected`erişim değiştiricisi](#private-protected-access-modifier)
  - `private protected` Erişim değiştiricisi aynı derlemede türetilmiş sınıflar için erişim imkanı sunar.
- [Koşullu `ref` ifadeler](#conditional-ref-expressions)
  - Koşullu ifadenin (`?:`) sonucu artık bir başvuru olabilir.

Bu makalenin geri kalanında her özelliğe bir genel bakış sunulmaktadır. Her bir özellik için, arkasında yatan bir düşünme olduğunu öğrenirsiniz. Söz dizimini öğrenirsiniz. `dotnet try` Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz:

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try`'i çalıştırın.

## <a name="safe-efficient-code-enhancements"></a>Güvenli verimli kod geliştirmeleri

7,2 ' de tanıtılan dil özellikleri, başvuru semantiğinin kullanıldığı sırada değer türleriyle çalışmanıza olanak sağlar. Başvuru türleri kullanılarak ilişkili bellek ayırmalarını oluşturmadan değer türlerini kopyalamayı en aza indirerek performansı artırmak için tasarlanmıştır. Özellikler şunlardır:

- Bir bağımsız değişkenin başvuruya göre geçirilmesini, ancak çağrılan yöntem tarafından değiştirilmediğinden emin olmak için parametrelerde değiştirici.`in` Bir bağımsız değişkene [](version-update-considerations.md#source-compatible-changes) değiştiricieklemek,kaynakileuyumlubirdeğişiklik`in` olur.
- Yöntem `ref readonly` üzerinde değiştirici, bir yöntemin değerini başvuruya göre döndürdüğünü ancak bu nesneye yazma izni olmadığını belirtmek için döndürür. Değiştirici eklemek, döndürme bir değere atanmışsa, [kaynak ile uyumlu bir değişiklik](version-update-considerations.md#source-compatible-changes)olur. `ref readonly` Değiştirici varolan `ref` bir return ifadesine eklendiğinde uyumsuz bir değişiklik vardır. [](version-update-considerations.md#incompatible-changes) `readonly` Çağrıcıların `ref` , `readonly` değiştiricisini içermesi için yerel değişkenlerin bildirimini güncelleştirmesi gerekir.
- Bir yapının sabit olduğunu ve onun üye yöntemlerine bir `in` parametre olarak geçirilmesi gerektiğini göstermek için bildirimi.`readonly struct` Değiştirici, `readonly` var olan bir struct bildirimine eklendiğinde, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)bulunur.
- Bir yapı türünün doğrudan yönetilen belleğe eriştiğini ve her zaman yığın ayrılması gerektiğini göstermek için bildirimi.`ref struct` Değiştirici varolan `struct` bir bildirime eklendiğinde uyumsuz bir değişiklik vardır. [](version-update-considerations.md#incompatible-changes) `ref` Bir `ref struct` sınıfın üyesi olamaz veya yığın üzerinde ayrılabileceği diğer konumlarda kullanılabilir.

Bu değişiklikler hakkında daha fazla bilgi için [yazma güvenli verimli kod](../write-safe-efficient-code.md)' a erişebilirsiniz.

## <a name="non-trailing-named-arguments"></a>Girintili olmayan adlandırılmış bağımsız değişkenler

Yöntem çağrıları artık, adlandırılmış bağımsız değişkenler doğru konumlarda olduğunda Konumsal bağımsız değişkenlerden önce gelen adlandırılmış bağımsız değişkenleri kullanabilir. Daha fazla bilgi için bkz. [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Sayısal sabit değerlerde önde gelen alt çizgiler

7,0 ' de C# basamak ayırıcıları için destek uygulanması, `_` öğesinin sabit değerin ilk karakteri olmasını izin vermedi. Onaltılık ve ikili sayısal değişmez değerler artık ile `_`başlayabilir.

Örneğin:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="_private-protected_-access-modifier"></a>_özel korumalı_ erişim değiştiricisi

Yeni bir bileşik erişim değiştiricisi: `private protected` bir üyeye, aynı derlemede belirtilen sınıf veya türetilmiş sınıfları içeren bir üyeye erişilebildiğini gösterir. Aynı derlemede bulunan türetilmiş sınıfların veya sınıfların erişimine `private protected` izinverdiğinden,aynıderlemedebelirtilentüretilmiştürlereerişimikısıtlar.`protected internal`

Daha fazla bilgi için bkz. dil başvurusunda [erişim değiştiriciler](../language-reference/keywords/access-modifiers.md) .

## <a name="conditional-ref-expressions"></a>Koşullu `ref` ifadeler

Son olarak, koşullu ifade bir değer sonucu yerine bir başvuru sonucu üretebilir. Örneğin, iki diziden birindeki ilk öğeye başvuru almak için aşağıdakini yazın:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

Değişken `r` , `arr` veya içindekiilkdeğerebirbaşvurudur.`otherArr`

Daha fazla bilgi için bkz. dil başvurusunda [koşullu işleç (?:)](../language-reference/operators/conditional-operator.md) .

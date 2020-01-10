---
title: C# 7,2 sürümündeki yenilikler
description: C# 7,2 sürümündeki yeni özelliklere genel bakış.
ms.date: 08/16/2017
ms.openlocfilehash: 7febefb81bbea6f24690adb05488ad6a18bbf552
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694601"
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
- [`private protected` erişim değiştiricisi](#private-protected-access-modifier)
  - `private protected` erişim değiştiricisi aynı derlemede türetilmiş sınıfların erişimine izin vermez.
- [Koşullu `ref` ifadeleri](#conditional-ref-expressions)
  - Koşullu ifadenin sonucu (`?:`) artık bir başvuru olabilir.

Bu makalenin geri kalanında her özelliğe bir genel bakış sunulmaktadır. Her bir özellik için, arkasında yatan bir düşünme olduğunu öğrenirsiniz. Söz dizimini öğrenirsiniz. Ortamınızdaki bu özellikleri, `dotnet try` genel aracını kullanarak inceleyebilirsiniz:

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try`'i çalıştırın.

## <a name="safe-efficient-code-enhancements"></a>Güvenli verimli kod geliştirmeleri

7,2 ' de tanıtılan dil özellikleri, başvuru semantiğinin kullanıldığı sırada değer türleriyle çalışmanıza olanak sağlar. Başvuru türleri kullanılarak ilişkili bellek ayırmalarını oluşturmadan değer türlerini kopyalamayı en aza indirerek performansı artırmak için tasarlanmıştır. Özellikler şunlardır:

- Bir bağımsız değişkenin başvuruya göre geçirilmesini, ancak çağrılan yöntem tarafından değiştirilmediğini belirtmek için parametrelerde `in` değiştirici. `in` değiştiricisini bir bağımsız değişkene eklemek, kaynak ile [uyumlu bir değişikdir](version-update-considerations.md#source-compatible-changes).
- Yöntem üzerinde `ref readonly` değiştirici, bir yöntemin değerini başvuruya göre döndürdüğünü ancak bu nesneye yazma izni olmadığını belirtmek için döndürür. `ref readonly` değiştiricisini eklemek, return değeri bir değere atanmışsa, [kaynak ile uyumlu bir değişiklik](version-update-considerations.md#source-compatible-changes)olur. `readonly` değiştiricisini var olan bir `ref` Return ifadesine eklemek [uyumsuz bir değişiklik](version-update-considerations.md#incompatible-changes). Çağıranların `readonly` değiştiricisini içermesi için `ref` yerel değişkenlerin bildirimini güncelleştirmesi gerekir.
- Bir yapının sabit olduğunu ve onun üye yöntemlerine bir `in` parametresi olarak geçirilmesi gerektiğini göstermek için `readonly struct` bildirimi. `readonly` değiştiricisini varolan bir struct bildirimine eklemek, [ikili uyumlu bir değişikdir](version-update-considerations.md#binary-compatible-changes).
- Bir struct türünün doğrudan yönetilen belleğe eriştiğini ve her zaman yığın ayrılması gerektiğini göstermek için `ref struct` bildirimi. `ref` değiştiricisini mevcut bir `struct` bildirimine eklemek [uyumsuz bir değişiklik](version-update-considerations.md#incompatible-changes). `ref struct`, bir sınıfın üyesi olamaz veya yığın üzerinde ayrılabileceği diğer konumlarda kullanılabilir.

Bu değişiklikler hakkında daha fazla bilgi için [yazma güvenli verimli kod](../write-safe-efficient-code.md)' a erişebilirsiniz.

## <a name="non-trailing-named-arguments"></a>Girintili olmayan adlandırılmış bağımsız değişkenler

Yöntem çağrıları artık, adlandırılmış bağımsız değişkenler doğru konumlarda olduğunda Konumsal bağımsız değişkenlerden önce gelen adlandırılmış bağımsız değişkenleri kullanabilir. Daha fazla bilgi için bkz. [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Sayısal sabit değerlerde önde gelen alt çizgiler

7,0 ' de C# basamak ayırıcıları için destek uygulanması, `_` değişmez değerin ilk karakteri olarak izin vermedi. Onaltılık ve ikili sayısal değişmez değerler artık `_`başlayabilir.

Örneğin:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>*özel korumalı* erişim değiştiricisi

Yeni bir bileşik erişim değiştiricisi: `private protected`, bir üyenin aynı derlemede belirtilen sınıf veya türetilmiş sınıflar ile erişilebilir olabileceğini gösterir. `protected internal` aynı derlemede bulunan türetilmiş sınıfların veya sınıfların erişimine izin verdiğinden, `private protected` aynı derlemede belirtilen türetilmiş türlere erişimi kısıtlar.

Daha fazla bilgi için bkz. dil başvurusunda [erişim değiştiriciler](../language-reference/keywords/access-modifiers.md) .

## <a name="conditional-ref-expressions"></a>Koşullu `ref` ifadeleri

Son olarak, koşullu ifade bir değer sonucu yerine bir başvuru sonucu üretebilir. Örneğin, iki diziden birindeki ilk öğeye başvuru almak için aşağıdakini yazın:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

`r` değişkeni, `arr` veya `otherArr`ilk değerine bir başvurudur.

Daha fazla bilgi için bkz. dil başvurusunda [koşullu işleç (?:)](../language-reference/operators/conditional-operator.md) .

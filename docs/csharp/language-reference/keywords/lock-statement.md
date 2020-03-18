---
title: kilit deyimi - C# başvurusu
description: İş parçacığı erişimini paylaşılan bir kaynağa eşitlemek için C# kilit deyimini kullanma
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 467881dd36c97b6b18b7f31d4e4af25152b0d012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713397"
---
# <a name="lock-statement-c-reference"></a>kilit deyimi (C# başvurusu)

Deyim, `lock` belirli bir nesne için karşılıklı dışlama kilidi kazanır, bir deyim bloğunu yürütür ve kilidi serbest bırakır. Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir. Başka bir iş parçacığı kilidi edinme engellenir ve kilit serbest bırakılınyana kadar bekler.

İfade `lock` formu

```csharp
lock (x)
{
    // Your code...
}
```

nerede `x` bir başvuru [türünün](reference-types.md)bir ifadesidir. Tam olarak eşdeğer.

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

Kod bir [deneyin kullandığından... son olarak](try-finally.md) blok, bir özel durum bir `lock` ifadenin gövdesi içinde atılmış olsa bile kilit serbest bırakılır.

[Bir](../operators/await.md) `lock` deyimin gövdesinde bekleyen operatörü kullanamazsınız.

## <a name="remarks"></a>Açıklamalar

İş parçacığı erişimini paylaşılan bir kaynağa eşitlediğinizde, özel bir `private readonly object balanceLock = new object();`nesne örneğini (örneğin,) veya kodun ilgisiz bölümleri tarafından kilit nesnesi olarak kullanılma olasılığı düşük başka bir örneği kilitleyin. Kilitlenme veya kilit çekişmesi neden olabileceğinden, farklı paylaşılan kaynaklar için aynı kilit nesnesi örneğini kullanmaktan kaçının. Özellikle, aşağıdakileri kilit nesneleri olarak kullanmaktan kaçının:

- `this`, arayanlar tarafından kilit olarak kullanılabilir.
- <xref:System.Type>örnekler, bu işleç veya yansıma [türü](../operators/type-testing-and-cast.md#typeof-operator) tarafından elde edilebilir gibi.
- dize örnekleri, dize literals de dahil olmak üzere, bu [interned](/dotnet/api/system.string.intern#remarks)olabilir gibi .

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel `Account` `balanceLock` bir örneği kilitleyerek özel `balance` alanına erişimi eşitleyen bir sınıf tanımlar. Kilitleme için aynı örneğin kullanılması, `balance` alanın aynı anda veya `Debit` `Credit` yöntemleri aynı anda çağırmaya çalışan iki iş parçacığı tarafından güncelleştirilememesini sağlar.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [kilit deyimi](~/_csharplang/spec/statements.md#the-lock-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C# başvurusu](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Eşitleme temellerine genel bakış](../../../standard/threading/overview-of-synchronization-primitives.md)

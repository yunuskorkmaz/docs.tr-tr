---
title: Lock deyimleri-C# başvurusu
description: İş parçacığı erişimini paylaşılan bir kaynağa eşleştirmek için C# lock ifadesini kullanın
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6e9a6975977588ba7692c925d7940cd2ec26671f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406696"
---
# <a name="lock-statement-c-reference"></a>Lock deyimleri (C# Başvurusu)

`lock`İfade, belirli bir nesne için karşılıklı dışlama kilidi alır, bir ekstre bloğunu yürütür ve sonra kilidi serbest bırakır. Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir. Diğer herhangi bir iş parçacığının kilidi almak engellenir ve kilit serbest bırakılana kadar bekler.

`lock`İfade şu biçimdedir

```csharp
lock (x)
{
    // Your code...
}
```

`x`, [başvuru türünün](reference-types.md)bir ifadesidir. Tam olarak eşdeğerdir

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

Kod bir TRY kullandığından... [ finally](try-finally.md) bloğu, bir deyimin gövdesinde özel durum oluşturulursa bile kilit serbest bırakılır `lock` .

Bir deyimin gövdesinde [await işlecini](../operators/await.md) kullanamazsınız `lock` .

## <a name="guidelines"></a>Yönergeler

İş parçacığı erişimini paylaşılan bir kaynağa eşitlediğinizde, ayrılmış bir nesne örneği üzerinde (örneğin, `private readonly object balanceLock = new object();` ) veya kodun ilişkisiz parçaları tarafından kilit nesnesi olarak kullanılması olası bir örnek üzerinde kilit. Farklı paylaşılan kaynaklar için aynı kilit nesnesi örneğini kullanmaktan kaçının, çünkü kilitlenme veya kilitleme çekişmesine yol açabilir. Özellikle, Lock nesneleri olarak aşağıdakileri kullanmaktan kaçının:

- `this`, çünkü çağıranlar bir kilit olarak kullanılıyor olabilir.
- <xref:System.Type>örnekler, [typeof](../operators/type-testing-and-cast.md#typeof-operator) işleci veya Reflection tarafından elde edilebilir.
- dize sabit değerleri de dahil olmak üzere dize örnekleri [birbirine](/dotnet/api/system.string.intern#remarks)bağlı olabilir.

Kilit çekişmesini azaltmak için olabildiğince kısa bir süre bekleyin.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Account` `balance` adanmış bir örnek üzerinde kilitleyerek özel alanına erişimi eşitleyen bir sınıfı tanımlar `balanceLock` . Kilitleme için aynı örneği kullanmak, alanın aynı anda `balance` veya yöntemlerini çağırmaya çalışan iki iş parçacığı tarafından aynı anda güncelleştirilememesini sağlar `Debit` `Credit` .

[!code-csharp[lock-statement-example](snippets/LockStatementExample.cs)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [kilit bildirimi](~/_csharplang/spec/statements.md#the-lock-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# anahtar sözcükleri](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Eşitleme temellerine genel bakış](../../../standard/threading/overview-of-synchronization-primitives.md)

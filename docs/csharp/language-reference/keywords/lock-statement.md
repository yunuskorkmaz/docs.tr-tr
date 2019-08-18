---
title: Lock deyimleri- C# başvuru
ms.custom: seodec18
description: İş parçacığı C# erişimini paylaşılan bir kaynağa eşleştirmek için Lock ifadesini kullanın
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 7ae19e48467bf5feca115c993c2299c1ecbaadc7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566340"
---
# <a name="lock-statement-c-reference"></a>Lock deyimleri (C# başvuru)

`lock` İfade, belirli bir nesne için karşılıklı dışlama kilidi alır, bir ekstre bloğunu yürütür ve sonra kilidi serbest bırakır. Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir. Diğer herhangi bir iş parçacığının kilidi almak engellenir ve kilit serbest bırakılana kadar bekler.

`lock` İfade şu biçimdedir

```csharp
lock (x)
{
    // Your code...
}
```

, başvuru türünün bir ifadesidir. [](reference-types.md) `x` Tam olarak eşdeğerdir

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

Kod bir TRY kullandığından... [ finally](try-finally.md) bloğu, bir `lock` deyimin gövdesinde özel durum oluşturulursa bile kilit serbest bırakılır.

Bir`lock` deyimin gövdesinde [await](await.md) anahtar sözcüğünü kullanamazsınız.

## <a name="remarks"></a>Açıklamalar

İş parçacığı erişimini paylaşılan bir kaynağa eşitlediğinizde, ayrılmış bir nesne örneği üzerinde (örneğin, `private readonly object balanceLock = new object();`) veya kodun ilişkisiz parçaları tarafından kilit nesnesi olarak kullanılması olası bir örnek üzerinde kilit. Farklı paylaşılan kaynaklar için aynı kilit nesnesi örneğini kullanmaktan kaçının, çünkü kilitlenme veya kilitleme çekişmesine yol açabilir. Özellikle, Lock nesneleri olarak aşağıdakileri kullanmaktan kaçının:

- `this`, çünkü çağıranlar bir kilit olarak kullanılıyor olabilir.
- <xref:System.Type>örnekler, [typeof](../operators/type-testing-and-cast.md#typeof-operator) işleci veya Reflection tarafından elde edilebilir.
- dize sabit değerleri de dahil olmak üzere dize örnekleri [birbirine](/dotnet/api/system.string.intern#remarks)bağlı olabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, adanmış `Account` `balanceLock` bir örnek üzerinde kilitleyerek özel `balance` alanına erişimi eşitleyen bir sınıfı tanımlar. Kilitleme için aynı örneği kullanmak, `balance` alanın aynı anda `Debit` veya `Credit` yöntemlerini çağırmaya çalışan iki iş parçacığı tarafından aynı anda güncelleştirilememesini sağlar.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [kilit bildirimi](~/_csharplang/spec/statements.md#the-lock-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C#başvurunun](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Eşitleme temelleri 'ne genel bakış](../../../standard/threading/overview-of-synchronization-primitives.md)

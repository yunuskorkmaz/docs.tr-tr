---
title: Lock deyimleri- C# başvuru
description: İş parçacığı C# erişimini paylaşılan bir kaynağa eşleştirmek için Lock ifadesini kullanın
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 467881dd36c97b6b18b7f31d4e4af25152b0d012
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713397"
---
# <a name="lock-statement-c-reference"></a>Lock deyimleri (C# başvuru)

`lock` ifade, belirli bir nesne için karşılıklı dışlama kilidini alır, bir ekstre bloğunu yürütür ve sonra kilidi serbest bırakır. Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir. Diğer herhangi bir iş parçacığının kilidi almak engellenir ve kilit serbest bırakılana kadar bekler.

`lock` deyimin biçimi

```csharp
lock (x)
{
    // Your code...
}
```

Burada `x`, [başvuru türünün](reference-types.md)bir ifadesidir. Tam olarak eşdeğerdir

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

Kod bir TRY kullandığından... [ finally](try-finally.md) bloğu, bir `lock` deyimin gövdesinde bir özel durum oluşturulursa bile kilit serbest bırakılır.

`lock` deyimin gövdesinde [await işlecini](../operators/await.md) kullanamazsınız.

## <a name="remarks"></a>Açıklamalar

İş parçacığı erişimini paylaşılan bir kaynağa eşitlediğinizde, ayrılmış bir nesne örneği üzerinde (örneğin, `private readonly object balanceLock = new object();`) veya kodun ilişkisiz parçaları tarafından kilit nesnesi olarak kullanılması olası olmayan başka bir örneğe kilit. Farklı paylaşılan kaynaklar için aynı kilit nesnesi örneğini kullanmaktan kaçının, çünkü kilitlenme veya kilitleme çekişmesine yol açabilir. Özellikle, Lock nesneleri olarak aşağıdakileri kullanmaktan kaçının:

- `this`, çağıranlar bir kilit olarak kullanılıyor olabilir.
- <xref:System.Type> örnekler, [typeof](../operators/type-testing-and-cast.md#typeof-operator) işleci veya Reflection tarafından alınanlarla olabilir.
- dize sabit değerleri de dahil olmak üzere dize örnekleri [birbirine](/dotnet/api/system.string.intern#remarks)bağlı olabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel `balance` alanına erişimi, adanmış bir `balanceLock` örneğine kilitleyerek eşitleyen bir `Account` sınıfını tanımlar. Kilitleme için aynı örneği kullanmak, `balance` alanının aynı anda `Debit` veya `Credit` yöntemlerini çağırmaya çalışan iki iş parçacığı tarafından aynı anda güncelleştirilmesini sağlar.

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

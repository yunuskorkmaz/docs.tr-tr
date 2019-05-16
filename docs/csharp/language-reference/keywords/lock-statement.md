---
title: lock deyimi - C# başvurusu
ms.custom: seodec18
description: İş parçacığı paylaşılan bir kaynağa erişimi eşitlemek için C# lock deyiminin kullanın
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6bf53cba73c4d7331b2a1c68bf7187c13281d844
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633446"
---
# <a name="lock-statement-c-reference"></a>lock deyimi (C# Başvurusu)

`lock` Deyimi belirli bir nesne için karşılıklı dışlama kilidini alır, bir deyim bloğunu yürütür ve ardından kilidi serbest bırakır. Kilidi açık tutulduğu sürece kilidi tutan iş parçacığı yeniden almak ve kilidi serbest bırakır. Başka bir iş parçacığı kilit alınırken gelen engellenir ve kilidi serbest bırakılıncaya kadar bekler.

`lock` Deyimdir biçimi

```csharp
lock (x)
{
    // Your code...
}
```

Burada `x` bir ifade olan bir [başvuru türüne](reference-types.md). Tam olarak eşdeğerdir

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

Kod kullandığından bir [try... finally](try-finally.md) bloğu kilidi serbest gövdesi içinde bir özel durum olsa bile bir `lock` deyimi.

Kullanamazsınız [await](await.md) gövdesinde anahtar sözcüğü bir `lock` deyimi.

## <a name="remarks"></a>Açıklamalar

İş parçacığı paylaşılan bir kaynağa erişmeye eşitlediğinizde, adanmış Pro instanci objektu kilitleme (örneğin, `private readonly object balanceLock = new object();`) ya da bir kilit nesnesi olarak kodun ilgisiz parçaları tarafından kullanılmak üzere düşüktür, başka bir örneği. Kilitlenme veya kilit Çekişme neden olabilir, farklı paylaşılan kaynaklar için aynı kilit nesne örneğini kullanarak kaçının. Özellikle, aşağıdaki nesneleri Kilitle kullanmaktan kaçının:

- `this`, gibi bir kilit çağıranlar tarafından kullanılabilir.
- <xref:System.Type> örnekler olanlar tarafından alınabilir olarak [typeof](typeof.md) işleci veya yansıma.
- dize değişmez değerleri, bu durumda olabileceğinden dahil olmak üzere örnekleri, dize [interned](/dotnet/api/system.string.intern#remarks).

## <a name="example"></a>Örnek

Aşağıdaki örnekte tanımlayan bir `Account` özel erişimi eşitler sınıfı `balance` üzerinde adanmış bir kilitleme alanı `balanceLock` örneği. Kilitleme sağlar için aynı örneği kullanarak `balance` alanı güncelleştirilemiyor aynı anda arama girişimi iki iş parçacığı tarafından `Debit` veya `Credit` yöntemleri aynı anda.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C# başvurusu](../index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Deyim Anahtar Sözcükleri](statement-keywords.md)
- [Eşitleme temellerine genel bakış](../../../standard/threading/overview-of-synchronization-primitives.md)

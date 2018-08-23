---
title: lock deyimi (C# Başvurusu)
description: 'Lock anahtar sözcüğü iş parçacığı içinde kullanılır. '
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6ed46837482642dfd7e1a96cd120fc18023c5e9f
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753981"
---
# <a name="lock-statement-c-reference"></a>lock deyimi (C# Başvurusu)

`lock` Anahtar sözcük belirli bir nesne için karşılıklı dışlama kilidini alma, deyimi yürütüp ve sonra kilidi bırakarak bu bir deyim bloğunu kritik bir bölüm olarak işaretler. Aşağıdaki örnek içeren bir `lock` deyimi.

```csharp
class Account
{
    decimal balance;
    private Object thisLock = new Object();

    public void Withdraw(decimal amount)
    {
        lock (thisLock)
        {
            if (amount > balance)
            {
                throw new Exception("Insufficient funds");
            }
            balance -= amount;
        }
    }
}
```

Daha fazla bilgi için [iş parçacığı eşitleme](../../programming-guide/concepts/threading/thread-synchronization.md).

## <a name="remarks"></a>Açıklamalar

`lock` Anahtar sözcüğü, başka bir iş parçacığı kritik bölümünde olsa da bir iş parçacığı kodun önemli bir bölümünü geçmiyor sağlar. Kilitli bir kodu girmek başka bir iş parçacığı çalışırsa, bekler, nesne yayımlanana kadar engelleyin.

Bölüm [parçacıkları](../../programming-guide/concepts/threading/index.md) iş parçacığı oluşturma açıklanır.

`lock` Anahtar sözcüğü çağrıları <xref:System.Threading.Monitor.Enter%2A> bloğun başlangıcında ve <xref:System.Threading.Monitor.Exit%2A> bloğunun sonunda. A <xref:System.Threading.ThreadInterruptedException> oluşturulur <xref:System.Threading.Thread.Interrupt%2A> girmek için bekleyen bir iş parçacığı kesmeleri bir `lock` deyimi.

Genel olarak, üzerinde kilitleme kaçının bir `public` türü veya kodunuzun kontrolü örnekleri. Ortak Yapılar `lock (this)`, `lock (typeof (MyType))`, ve `lock ("myLock")` bu anlayışın ihlal:

- `lock (this)` Örneğin genel olarak erişilebilen bir sorun ise.

- `lock (typeof (MyType))` bir sorun ise `MyType` genel olarak erişilebilir.

- `lock("myLock")` aynı dize kullanarak işlemindeki herhangi bir kod paylaştığından aynı kilit bir sorundur.

En iyi uygulamadır tanımlamak için bir `private` , kilitlemek için nesne veya `private static` için tüm örnekleri ortak verileri korumak için nesne değişkeni.

Kullanamazsınız [await](await.md) gövdesinde anahtar sözcüğü bir `lock` deyimi.

## <a name="example---threads-without-locking"></a>Örnek - kilitlemeden iş parçacıkları

Aşağıdaki örnek, C# dilinde kilitlemeden basit bir iş parçacığı kullanımı gösterilmektedir:

[!code-csharp[csrefKeywordsFixedLock#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#5)]

## <a name="example---threads-using-locking"></a>Örnek - iş parçacıklarını kilitleme kullanma

Aşağıdaki örnek iş parçacığı kullanır ve `lock`. Sürece `lock` deyimi, deyim bloğunu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı olur:

[!code-csharp[csrefKeywordsFixedLock#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#6)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.MethodImplAttributes>
- <xref:System.Threading.Mutex>
- <xref:System.Threading.Monitor>
- [C# başvurusu](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [İş parçacığı oluşturma](../../programming-guide/concepts/threading/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Deyim Anahtar Sözcükleri](statement-keywords.md)
- [Birbirine Kenetlenmiş İşlemler](../../../standard/threading/interlocked-operations.md)
- [AutoResetEvent](../../../standard/threading/autoresetevent.md)
- [İş Parçacığı Eşitleme](../../programming-guide/concepts/threading/thread-synchronization.md)
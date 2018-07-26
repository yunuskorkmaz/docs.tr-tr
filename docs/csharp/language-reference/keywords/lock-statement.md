---
title: lock Deyimi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2ce870e8caa67d780ce603a6f1dbcc7cd303b842
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960965"
---
# <a name="lock-statement-c-reference"></a>lock Deyimi (C# Başvurusu)
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
  
-   `lock (this)` Örneğin genel olarak erişilebilen bir sorun ise.  
  
-   `lock (typeof (MyType))` bir sorun ise `MyType` genel olarak erişilebilir.  
  
-   `lock("myLock")` aynı dize kullanarak işlemindeki herhangi bir kod paylaştığından aynı kilit bir sorundur.  
  
 En iyi uygulamadır tanımlamak için bir `private` , kilitlemek için nesne veya `private static` için tüm örnekleri ortak verileri korumak için nesne değişkeni.  
  
 Kullanamazsınız [await](../../../csharp/language-reference/keywords/await.md) gövdesinde anahtar sözcüğü bir `lock` deyimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# dilinde kilitlemeden basit bir iş parçacığı kullanımını gösterir.  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iş parçacığı kullanır ve `lock`. Sürece `lock` deyimi, deyim bloğunu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı olur.  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [İş parçacığı oluşturma](../../programming-guide/concepts/threading/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Deyim Anahtar Sözcükleri](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [Birbirine Kenetlenmiş İşlemler](../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../standard/threading/autoresetevent.md)  
 [İş Parçacığı Eşitleme](../../programming-guide/concepts/threading/thread-synchronization.md)

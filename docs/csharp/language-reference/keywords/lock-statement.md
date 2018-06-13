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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274225"
---
# <a name="lock-statement-c-reference"></a>lock Deyimi (C# Başvurusu)
`lock` Anahtar sözcüğü belirli nesne karşılıklı dışlama kilidi alma, bir deyimi yürütme ve kilidin açılması bu deyimi blok önemli bir bölümü işaretler. Aşağıdaki örnek içeren bir `lock` deyimi.  
  
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
  
 Daha fazla bilgi için bkz: [iş parçacığı eşitleme](../../programming-guide/concepts/threading/thread-synchronization.md).  
  
## <a name="remarks"></a>Açıklamalar  
 `lock` Anahtar sözcüğü sağlar başka bir iş parçacığı kritik bölümünde olsa da bir iş parçacığı önemli bir bölümü kodunun geçmiyor. Başka bir iş parçacığı kilitli kodu girmek çalışırsa, bekler, nesne serbest kadar engelleyin.  
  
 Bölüm [parçacıkları](../../programming-guide/concepts/threading/index.md) iş parçacığı oluşturma açıklanır.  
  
 `lock` Anahtar sözcüğü çağrıları <xref:System.Threading.Monitor.Enter%2A> bloğun başlangıcında ve <xref:System.Threading.Monitor.Exit%2A> bloğun sonunda. A <xref:System.Threading.ThreadInterruptedException> erişilirse durum <xref:System.Threading.Thread.Interrupt%2A> girmek için bekleyen bir iş parçacığı keser bir `lock` deyimi.  
  
 Genel olarak, üzerinde kilitleme kaçının bir `public` türü ya da kodunuzu ait denetim ötesinde örnekleri. Ortak yapıları `lock (this)`, `lock (typeof (MyType))`, ve `lock ("myLock")` bu kılavuz ihlal:  
  
-   `lock (this)` örnek genel olarak erişilebiliyorsa bir sorundur.  
  
-   `lock (typeof (MyType))` bir sorun ise `MyType` genel olarak erişilebilir.  
  
-   `lock("myLock")` aynı dize kullanarak işlemdeki başka bir kod paylaşır çünkü aynı kilit bir sorundur.  
  
 En iyi uygulamadır tanımlamak için bir `private` , kilitlemek için nesne veya `private static` için tüm örnekleri ortak verileri korumak için nesne değişkeni.  
  
 Kullanamazsınız [await](../../../csharp/language-reference/keywords/await.md) gövdesinde anahtar sözcüğü bir `lock` deyimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# ' ta kilitlemeden basit bir iş parçacığı kullanımını gösterir.  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iş parçacığı kullanır ve `lock`. Sürece `lock` deyimi varsa, deyimi blok kritik bir bölümdür ve `balance` negatif bir sayı hiçbir zaman olur.  
  
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

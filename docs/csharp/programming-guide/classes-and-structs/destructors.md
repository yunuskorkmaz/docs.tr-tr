---
title: Sonlandırıcılar - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 19c1f754aaef66197b033a68bc215255511cd618
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646533"
---
# <a name="finalizers-c-programming-guide"></a>Sonlandırıcılar (C# programlama Kılavuzu)
Sonlandırıcılar (de denir **yok ediciler**) çöp toplayıcısı tarafından toplanmış bir sınıf örneği, tüm gerekli son temizleme gerçekleştirmek için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
  
- Sonlandırıcılar yapılarda tanımlanamaz. Bunlar, yalnızca sınıf ile kullanılır.  
  
- Bir sınıf, bir sonlandırıcı yalnızca olabilir.  
  
- Sonlandırıcılar devralınmış veya aşırı yüklenmiş.  
  
- Sonlandırıcılar çağrılamaz. Bunlar otomatik olarak çağrılır.  
  
- Bir sonlandırıcı değiştiriciler alın veya parametreleri desteklemez.  
  
 Örneğin, bir sonlandırıcı için bildirimi aşağıdaki gibidir `Car` sınıfı.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Bir Sonlandırıcı, aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı da uygulanabilir.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Sonlandırıcı örtük olarak çağırır <xref:System.Object.Finalize%2A> nesnenin temel sınıfı üzerinde. Bu nedenle, bir sonlandırıcı bir çağrı örtük olarak aşağıdaki kodu çevrilir:  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 Diğer bir deyişle `Finalize` yöntemi çağrılır yinelemeli devralma zincirini tüm örnekler için en çok türetilen en az türetilen için.  
  
> [!NOTE]
>  Boş Sonlandırıcıları kullanılmamalıdır. Bir sınıf, bir sonlandırıcı içeriyorsa, bir giriş oluşturulan `Finalize` kuyruk. Sonlandırıcı çağrıldığında çöp toplayıcı kuyruğu işlemek için çağrılır. Boş Sonlandırıcı yalnızca gereksiz bir performans kaybı neden olur.  
  
 Bu çöp toplayıcı tarafından belirlenir çünkü Sonlandırıcı çağrıldığında Programcı üzerinde denetimi yoktur. Çöp toplayıcı uygulama tarafından artık kullanılmayan nesneleri denetler. Bu nesne sonlandırma için uygun olarak değerlendirir, sonlandırıcı (varsa) çağırır ve nesne depolamak için kullanılan belleği geri kazanır. 
 
 Program çıkış yaptığı andaki .NET Framework uygulamalarında (ancak .NET Core uygulamalarında), bir sonlandırıcı da denir. 
  
 Çağırarak atık toplamayı zorlamak mümkün mü <xref:System.GC.Collect%2A>, ancak performans sorunları oluşturabilir, çünkü çoğu zaman bu kaçınılmalıdır.  
  
## <a name="using-finalizers-to-release-resources"></a>Kaynaklar serbest bırakılacaksa Sonlandırıcı kullanma  
 Genel olarak, C# bir çalışma zamanının atık toplama ile hedeflemiyor bir dil ile geliştirdiğinizde gerektiği kadar bellek yönetimi gerektirmez. .NET Framework atık toplayıcı, örtük olarak sağlanmasını ve ayrılmasını, nesneler için bellek yönetir olmasıdır. Ancak, uygulamanızı windows, dosyaları ve ağ bağlantıları gibi yönetilmeyen kaynakları yalıtan, bu kaynakları serbest bırakacak sonlandırıcılar kullanmanız gerekir. Nesne sonlandırma için uygun olduğunda, Atık toplayıcısının çalışacağı `Finalize` nesnesinin yöntemi.  
  
## <a name="explicit-release-of-resources"></a>Açık kaynak sürümü  
 Uygulamanızı pahalı bir dış kaynağa kullanıyorsanız, çöp toplayıcı nesneyi serbest bırakan önce kaynak açıkça serbest bırakmak için bir yol sağlamak da öneririz. Uygulayarak bunu bir `Dispose` yönteminden <xref:System.IDisposable> nesne için gerekli temizleme gerçekleştirir arabirimi. Bu, uygulamanın performansını önemli ölçüde artırabilir. Bile bu açık denetime ile kaynakları, sonlandırıcı durumunda kaynakları temizlemek için bir önlem haline gelir. çağrı `Dispose` yöntemi başarısız oldu.  
  
 Kaynakları temizleme hakkında daha fazla ayrıntı için aşağıdaki konulara bakın:  
  
- [Yönetilmeyen Kaynakları Temizleme](../../../standard/garbage-collection/unmanaged.md)  
  
- [Dispose Yöntemi Uygulama](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using Deyimi](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir devralma zincirini olun üç sınıf oluşturur. Sınıf `First` temel sınıf `Second` türetilir `First`, ve `Third` türetilir `Second`. Üç sonlandırıcılar vardır. İçinde `Main`, en çok türetilen sınıfın bir örneği oluşturulur. Program çalıştığında sonlandırıcılar üç sınıfları için otomatik olarak ve sırasıyla en çok türetilen en az türetilen için gelen çağrılır, dikkat edin.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için [yok ediciler](~/_csharplang/spec/classes.md#destructors) bölümünü [ C# dil belirtimi](../../language-reference/language-specification/index.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Atık Toplama](../../../standard/garbage-collection/index.md)

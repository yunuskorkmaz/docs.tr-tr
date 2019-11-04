---
title: Sonlandırıcılar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: f7cb9bd05d08a33be53abad58b78b39e36c6dffe
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419355"
---
# <a name="finalizers-c-programming-guide"></a>Sonlandırıcılar (C# Programlama Kılavuzu)
Sonlandırıcılar (yani **Yıkıcılar**olarak da bilinir), bir sınıf örneği çöp toplayıcısı tarafından toplandığında gerekli son temizleme işlemini gerçekleştirmek için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
  
- Sonlandırıcılar yapılar içinde tanımlanamaz. Bunlar yalnızca sınıflarla birlikte kullanılır.  
  
- Bir sınıfın yalnızca bir sonlandırıcısı olabilir.  
  
- Sonlandırıcılar devralınamaz veya aşırı yüklenemez.  
  
- Sonlandırıcılar çağrılamaz. Bunlar otomatik olarak çağırılır.  
  
- Sonlandırıcı değiştirici almaz veya parametrelere sahip değildir.  
  
 Örneğin, `Car` sınıfı için sonlandırıcının bildirimi aşağıda verilmiştir.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Bir Sonlandırıcı, aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı olarak da uygulanabilir.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Sonlandırıcı nesnenin temel sınıfında <xref:System.Object.Finalize%2A> dolaylı olarak çağırır. Bu nedenle, sonlandırıcının çağrısı dolaylı olarak aşağıdaki koda çevrilir:  
  
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
  
 Bu, `Finalize` yönteminin devralma zincirindeki tüm örnekler için özyinelemeli olarak çağrıldığı, en az türetilen ' ın en küçük bir değer olarak çağrıldığı anlamına gelir.  
  
> [!NOTE]
> Boş sonlandırıcılar kullanılmamalıdır. Bir sınıf bir Sonlandırıcı içerdiğinde, `Finalize` kuyrukta bir giriş oluşturulur. Sonlandırıcı çağrıldığında, atık toplayıcı kuyruğu işleyecek şekilde çağrılır. Boş bir Sonlandırıcı yalnızca gereksiz performans kaybına neden olur.  
  
 Bu, çöp toplayıcı tarafından belirlendiği için sonlandırıcının çağrıldığı zaman üzerinde denetime sahip değildir. Çöp toplayıcı, artık uygulama tarafından kullanılmayan nesneleri denetler. Sonlandırma için uygun bir nesne kabul eder, sonlandırıcıyı çağırır (varsa) ve nesneyi depolamak için kullanılan belleği geri kazanır. 
 
 .NET Framework uygulamalarda (.NET Core uygulamalarında değil), program çıkıldığında sonlandırıcılar da çağırılır. 
  
 <xref:System.GC.Collect%2A>çağırarak çöp toplamayı zorlamak mümkündür, ancak çoğu zaman performans sorunları oluşturabileceğinden bu durum kaçınılmalıdır.  
  
## <a name="using-finalizers-to-release-resources"></a>Kaynakları serbest bırakmak için sonlandırıcıları kullanma  
 Genel olarak, C# çöp toplama ile çalışma zamanını hedeflemez bir dille geliştirirken gereken kadar bellek yönetimi gerekmez. Bunun nedeni, .NET Framework atık toplayıcının nesneleriniz için bellek ayırmayı ve serbest bırakma işlemini örtülü olarak yönetmesinden kaynaklanır. Ancak, uygulamanız Windows, dosyalar ve ağ bağlantıları gibi yönetilmeyen kaynakları kapsüller, bu kaynakları serbest bırakmak için sonlandırıcıları kullanmanız gerekir. Nesne sonlandırmaya uygun olduğunda, çöp toplayıcı nesnenin `Finalize` yöntemini çalıştırır.  
  
## <a name="explicit-release-of-resources"></a>Kaynakların açık yayını  
 Uygulamanız pahalı bir dış kaynak kullanıyorsa, atık toplayıcı nesneyi serbest bırakmadan önce kaynağı açıkça serbest bırakmak için bir yol sağlamanızı öneririz. Bu, nesnesi için gerekli temizleme işlemini gerçekleştiren <xref:System.IDisposable> arabiriminden bir `Dispose` yöntemi uygulayarak yapılır. Bu, uygulamanın performansını önemli ölçüde iyileştirebilirler. Kaynak üzerinde bu açık denetimle birlikte, `Dispose` yöntemine yapılan çağrı başarısız olursa Sonlandırıcı, kaynakları temizlemek için bir güvenlik önlemi haline gelir.  
  
 Kaynakları Temizleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Yönetilmeyen Kaynakları Temizleme](../../../standard/garbage-collection/unmanaged.md)  
  
- [Dispose Yöntemi Uygulama](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using Deyimi](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir devralım zinciri oluşturan üç sınıf oluşturur. Sınıf `First` temel sınıftır, `Second` `First`türetilir ve `Third` `Second`türetilir. Tüm üçünün sonlandırıcıları vardır. `Main`, en çok türetilen sınıfın bir örneği oluşturulur. Program çalıştığında, üç sınıfa ait sonlandırıcılara otomatik olarak ve sırasıyla en az türetilmiş ' dan türetilmiş ' a göre çağrıldığını unutmayın.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [Yıkıcılar](~/_csharplang/spec/classes.md#destructors) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [C# Programlama Kılavuzu](../index.md)
- [Oluşturucular](./constructors.md)
- [Atık Toplama](../../../standard/garbage-collection/index.md)

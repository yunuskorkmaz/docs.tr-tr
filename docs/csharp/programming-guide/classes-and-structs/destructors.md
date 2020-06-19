---
title: Sonlandırıcılar-C# Programlama Kılavuzu
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 62fc531a8064a8a5cb144a89aa9975b3199db976
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990110"
---
# <a name="finalizers-c-programming-guide"></a>Sonlandırıcılar (C# Programlama Kılavuzu)
Sonlandırıcılar (yani **Yıkıcılar**olarak da bilinir), bir sınıf örneği çöp toplayıcısı tarafından toplandığında gerekli son temizleme işlemini gerçekleştirmek için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
  
- Sonlandırıcılar yapılar içinde tanımlanamaz. Bunlar yalnızca sınıflarla birlikte kullanılır.  
  
- Bir sınıfın yalnızca bir sonlandırıcısı olabilir.  
  
- Sonlandırıcılar devralınamaz veya aşırı yüklenemez.  
  
- Sonlandırıcılar çağrılamaz. Bunlar otomatik olarak çağırılır.  
  
- Sonlandırıcı değiştirici almaz veya parametrelere sahip değildir.  
  
 Örneğin, aşağıdaki, sınıfı için sonlandırıcının bir bildirimidir `Car` .
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Bir Sonlandırıcı, aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı olarak da uygulanabilir.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Sonlandırıcı nesnenin temel sınıfında örtülü olarak çağrı çağırır <xref:System.Object.Finalize%2A> . Bu nedenle, sonlandırıcının çağrısı dolaylı olarak aşağıdaki koda çevrilir:  
  
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
  
 Bu tasarım, bir `Finalize` metodun devralma zincirindeki tüm örnekler için yinelemeli olarak çağrıldığı, en az türetilen ' ın en az türetiği anlamına gelir.  
  
> [!NOTE]
> Boş sonlandırıcılar kullanılmamalıdır. Bir sınıf bir Sonlandırıcı içerdiğinde, kuyrukta bir giriş oluşturulur `Finalize` . Sonlandırıcı çağrıldığında, atık toplayıcı kuyruğu işleyecek şekilde çağrılır. Boş bir Sonlandırıcı yalnızca gereksiz performans kaybına neden olur.  
  
 Programcının Sonlandırıcı çağrıldığında hiçbir denetimi yoktur; Çöp toplayıcı, ne zaman çağrılacağını belirler. Çöp toplayıcı, artık uygulama tarafından kullanılmayan nesneleri denetler. Sonlandırma için uygun bir nesne kabul eder, sonlandırıcıyı çağırır (varsa) ve nesneyi depolamak için kullanılan belleği geri kazanır.

 .NET Framework uygulamalarda (.NET Core uygulamalarında değil), program çıkıldığında sonlandırıcılar da çağırılır.
  
 Çöp toplamayı çağırarak <xref:System.GC.Collect%2A> , ancak çoğu zaman, performans sorunları oluşturabileceğinden Bu çağrının önlenebilir olması gerekir.  
  
## <a name="using-finalizers-to-release-resources"></a>Kaynakları serbest bırakmak için sonlandırıcıları kullanma  
 Genellikle C#, bir çalışma zamanını çöp koleksiyonuyla hedeflemez diller olarak geliştirici bölümünde çok fazla bellek yönetimi gerektirmez. Bunun nedeni, .NET çöp toplayıcı 'nin nesneleriniz için bellek ayırmayı ve serbest bırakma işlemini örtülü olarak yönetmesinden kaynaklanır. Ancak, uygulamanız Windows, dosyalar ve ağ bağlantıları gibi yönetilmeyen kaynakları kapsüller, bu kaynakları serbest bırakmak için sonlandırıcıları kullanmanız gerekir. Nesne sonlandırmaya uygun olduğunda, çöp toplayıcı `Finalize` nesnenin yöntemini çalıştırır.
  
## <a name="explicit-release-of-resources"></a>Kaynakların açık yayını  
 Uygulamanız pahalı bir dış kaynak kullanıyorsa, atık toplayıcı nesneyi serbest bırakmadan önce kaynağı açıkça serbest bırakmak için bir yol sağlamanızı öneririz. Kaynağı serbest bırakmak için, `Dispose` <xref:System.IDisposable> arabiriminden nesne için gerekli temizleme işlemini gerçekleştiren bir yöntem uygulayın. Bu, uygulamanın performansını önemli ölçüde iyileştirebilirler. Kaynak üzerinde bu açık denetimle birlikte, yöntem çağrısı başarısız olursa Sonlandırıcı, kaynakları temizlemek için bir güvenlik önlemi haline gelir `Dispose` .  
  
 Kaynakları Temizleme hakkında daha fazla bilgi için aşağıdaki makalelere bakın:  
  
- [Yönetilmeyen Kaynakları Temizleme](../../../standard/garbage-collection/unmanaged.md)  
  
- [Dispose Yöntemi Uygulama](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using Deyimi](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir devralım zinciri oluşturan üç sınıf oluşturur. Sınıfı `First` temel sınıftır, `Second` öğesinden türetilir `First` ve `Third` öğesinden türetilir `Second` . Tüm üçünün sonlandırıcıları vardır. `Main`' De, en çok türetilmiş sınıfın bir örneği oluşturulur. Program çalıştığında, üç sınıfa ait sonlandırıcılara otomatik olarak ve sırasıyla en az türetilmiş ' dan türetilmiş ' a göre çağrıldığını unutmayın.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [Yıkıcılar](~/_csharplang/spec/classes.md#destructors) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [C# Programlama Kılavuzu](../index.md)
- [Oluşturucular](./constructors.md)
- [Çöp toplama](../../../standard/garbage-collection/index.md)

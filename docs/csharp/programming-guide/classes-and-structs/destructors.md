---
title: Sonlandırıcılar (C# programlama Kılavuzu)
ms.date: 05/10/2017
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: fc15818883736015419f8599d482185bbab5120a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313972"
---
# <a name="finalizers-c-programming-guide"></a>Sonlandırıcılar (C# programlama Kılavuzu)
Sonlandırıcılar sınıfların örneklerini destruct için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
  
-   Sonlandırıcılar yapılar için tanımlanamaz. Bunlar yalnızca sınıflarıyla kullanılır.  
  
-   Bir sınıf, yalnızca bir Sonlandırıcısı olabilir.  
  
-   Sonlandırıcılar devralınan veya aşırı yüklendi.  
  
-   Sonlandırıcılar çağrılamaz. Bunlar otomatik olarak çağrılır.  
  
-   Bir sonlandırıcı değiştiricileri alın ya da parametrelere sahip.  
  
 Örneğin, aşağıdaki sonlandırıcıyı için bildirimini `Car` sınıfı.
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

Bir Sonlandırıcı, aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı olarak da uygulanabilir.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Sonlandırıcıyı örtük olarak çağırır <xref:System.Object.Finalize%2A> nesnenin temel sınıfı. Bu nedenle, bir sonlandırıcı çağrısına örtük olarak aşağıdaki kodu çevrilir:  
  
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
  
 Bunun anlamı `Finalize` yöntemi çağrılır yinelemeli olarak devralma zincirinde tüm örnekleri için en çok türetilen en az türetilen için.  
  
> [!NOTE]
>  Boş Sonlandırıcıları kullanılmamalıdır. Bir sınıf bir sonlandırıcı içeriyorsa, bir giriş oluşturulan `Finalize` sırası. Sonlandırıcıyı çağrıldığında atık toplayıcı sırasını işlemek üzere çağrılır. Boş bir Sonlandırıcısı yalnızca performans gereksiz kaybına neden olur.  
  
 Bu Atık toplayıcısının belirlediğinden sonlandırıcıyı çağrıldığında Programcı üzerinde denetimi yoktur. Uygulama tarafından artık kullanılmayan nesneler için atık toplayıcı denetler. Bu nesneyi sonlandırma için uygun olarak değerlendirir, (varsa) sonlandırıcıyı çağırır ve nesne depolamak için kullanılan bellek geri kazanır. Program çıktığında sonlandırıcılar da denir.  
  
 Çöp toplama çağırarak zorlamak mümkün mü <xref:System.GC.Collect%2A>, ancak performans sorunları oluşturabilir çünkü çoğu zaman, bu kaçınılmalıdır.  
  
## <a name="using-finalizers-to-release-resources"></a>Yayın kaynaklara sonlandırıcılar kullanma  
 Genel olarak, C# çalışma zamanı çöp toplama ile hedeflemiyor bir dille geliştirirken gerektiği kadar bellek yönetimi gerektirmez. .NET Framework Atık toplayıcısının örtük olarak ayırma ve yayın nesneleriniz için bellek yönetir olmasıdır. Ancak, windows, dosyaları ve ağ bağlantıları gibi yönetilmeyen kaynakları uygulamanızı yalıtır olduğunda, bu kaynakları serbest sonlandırıcılar kullanmanız gerekir. Nesne sonlandırma için uygun olduğunda Atık toplayıcısının çalışacağı `Finalize` nesnesinin yöntemi.  
  
## <a name="explicit-release-of-resources"></a>Açık kaynak sürümü  
 Uygulamanızı pahalı dış kaynak kullanıyorsa, atık toplayıcı nesnesi boşaltır önce kaynak açıkça serbest bırakmak için bir yol sağlamak da öneririz. Uygulayarak bunu bir `Dispose` yönteminden <xref:System.IDisposable> nesne için gerekli temizleme gerçekleştirir arabirimi. Bu uygulamanın performansını önemli ölçüde artırabilir. Bile bu açık denetim ile kaynakları üzerinden sonlandırıcıyı varsa kaynakları temizlemek için koruyucu hale çağrısı `Dispose` yöntemi başarısız oldu.  
  
 Kaynakları temizleme hakkında daha fazla ayrıntı için aşağıdaki konulara bakın:  
  
-   [Yönetilmeyen Kaynakları Temizleme](../../../standard/garbage-collection/unmanaged.md)  
  
-   [Dispose Yöntemi Uygulama](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [using Deyimi](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, devralma zinciri olun üç sınıfları oluşturur. Sınıf `First` taban sınıf `Second` türetildiği `First`, ve `Third` türetildiği `Second`. Üç sonlandırıcılar vardır. İçinde `Main`, çoğu türetilmiş sınıf örneği oluşturdu. Program çalıştırıldığında sonlandırıcılar üç sınıfları için otomatik olarak ve sırasıyla çoğu türetilmiş en az türetilen için gelen olarak adlandırılır, dikkat edin.  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IDisposable>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Atık Toplama](../../../standard/garbage-collection/index.md)

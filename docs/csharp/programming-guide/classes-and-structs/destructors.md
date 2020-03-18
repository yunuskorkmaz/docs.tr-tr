---
title: Finalistler - C# Programlama Kılavuzu
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: c8ad738baa3ff76cf9ae8367f2fd2a1fb44a79d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170305"
---
# <a name="finalizers-c-programming-guide"></a>Finalistler (C# Programlama Kılavuzu)
**Sonlandırıcılar (yıkıcılar**olarak da adlandırılır) bir sınıf örneği çöp toplayıcı tarafından toplanırken gerekli son temizlemeyi gerçekleştirmek için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
  
- Sonlandırıcılar structs olarak tanımlanamaz. Onlar sadece sınıflar ile kullanılır.  
  
- Bir sınıfın sadece bir finalleştiricisi olabilir.  
  
- Finalistler devralınamaz veya aşırı yüklenemez.  
  
- Sonlandırıcılar çağrılamaz. Otomatik olarak çağrılır.  
  
- Bir sonlandırıcı değiştiriciler almaz veya parametreleri var.  
  
 Örneğin, aşağıdaki `Car` sınıf için bir sonlandırıcı bildirimidir.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Bir sonlandırıcı, aşağıdaki örnekte de görüldüğü gibi, ifade gövdesi tanımı olarak da uygulanabilir.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Sonlandırıcı dolaylı olarak <xref:System.Object.Finalize%2A> nesnenin taban sınıfını çağırır. Bu nedenle, bir sonlandırıcı için bir çağrı örtülü olarak aşağıdaki koda çevrilir:  
  
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
  
 Bu, yöntemin `Finalize` devralma zincirindeki tüm örnekler için, en çok türetilmiş olandan en az türetilmiş olana kadar özyinelemeli olarak çağrıldığı anlamına gelir.  
  
> [!NOTE]
> Boş sonlandırıcılar kullanılmamalıdır. Bir sınıf bir sonlandırıcı içeriyorsa, `Finalize` sırada bir giriş oluşturulur. Sonlandırıcı çağrıldığında, sırayı işlemek için çöp toplayıcısı çağrılır. Boş bir finalize sadece performans gereksiz bir kaybına neden olur.  
  
 Bu çöp toplayıcı tarafından belirlenir, çünkü sonlandırıcı çağrıldığında programcı üzerinde hiçbir kontrole sahiptir. Çöp toplayıcı, uygulama tarafından artık kullanılmayan nesneleri denetler. Bir nesneyi sonlandırmaiçin uygun görürse, sonlandırıcıyı (varsa) çağırır ve nesneyi depolamak için kullanılan belleği geri alır.

 .NET Framework uygulamalarında (ancak .NET Core uygulamalarında değil), program çıktığında sonlandırıcılar da çağrılır.
  
 Çöp toplamayı çağırarak zorlamak <xref:System.GC.Collect%2A>mümkündür, ancak çoğu zaman performans sorunları oluşturabileceğinden bu kaçınılmalıdır.  
  
## <a name="using-finalizers-to-release-resources"></a>Kaynakları serbest bırakmak için sonlandırıcıları kullanma  
 Genel olarak, C# çöp toplama ile çalışma süresini hedeflemeyen bir dil ile geliştirdiğiniz zaman gerektiği kadar bellek yönetimi gerektirmez. Bunun nedeni, .NET Framework çöp toplayıcısının nesneleriniz için bellek tahsisini ve serbest bırakılmasını dolaylı olarak yönetmesidir. Ancak, uygulamanız windows, dosyalar ve ağ bağlantıları gibi yönetilmeyen kaynakları kapsüllediğinde, bu kaynakları serbest leştirmek için sonlandırıcılar kullanmanız gerekir. Nesne sonlandırma için uygun olduğunda, çöp `Finalize` toplayıcı nesnenin yöntemini çalıştırAr.  
  
## <a name="explicit-release-of-resources"></a>Kaynakların açık serbest bırakılması  
 Uygulamanız pahalı bir dış kaynak kullanıyorsa, çöp toplayıcı nesneyi serbest bırakmadan önce kaynağı açıkça serbest bırakmanın bir yolunu da sağlamanızı öneririz. Bunu, nesne için `Dispose` gerekli temizlemeyi gerçekleştiren <xref:System.IDisposable> arabirimden bir yöntem uygulayarak yaparsınız. Bu, uygulamanın performansını önemli ölçüde artırabilir. Kaynaklar üzerindeki bu açık denetime rağmen, `Dispose` sonlandırıcı, yönteme çağrı başarısız olursa kaynakları temizlemek için bir koruma haline gelir.  
  
 Kaynakları temizleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Yönetilmeyen Kaynakları Temizleme](../../../standard/garbage-collection/unmanaged.md)  
  
- [Dispose Yöntemi Uygulama](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [Ekstresi'ni kullanma](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir devralma zinciri oluşturan üç sınıf oluşturur. Sınıf `First` taban sınıftır, `Second` `First`türetilmiştir `Third` , ve `Second`türetilmiştir . Üçünün de finalistleri var. Içinde `Main`, en çok türetilmiş sınıfın bir örneği oluşturulur. Program çalıştığında, üç sınıfın sonlandırıcılarının otomatik olarak ve sırayla en çok türetilmiş olandan en az türetilmiş olana çağrıldığına dikkat edin.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [Yıkıcılar](~/_csharplang/spec/classes.md#destructors) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [C# Programlama Kılavuzu](../index.md)
- [Oluşturucular](./constructors.md)
- [Çöp Toplama](../../../standard/garbage-collection/index.md)

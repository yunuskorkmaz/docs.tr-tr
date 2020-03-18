---
title: C# 7.3'teki yenilikler
description: C# 7.3'teki yeni özelliklere genel bakış
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204553"
---
# <a name="whats-new-in-c-73"></a>C# 7.3'teki yenilikler

C# 7.3 sürümü için iki ana tema vardır. Bir tema, güvenli kodun güvenli olmayan kod kadar performant olmasını sağlayan özellikler sağlar. İkinci tema, varolan özellikler için artımlı iyileştirmeler sağlar. Buna ek olarak, bu sürümde yeni derleyici seçenekleri eklendi.

Aşağıdaki yeni özellikler, güvenli kod için daha iyi performans tesini destekler:

- Sabit alanlara sabitleme den erişebilirsiniz.
- Yerel değişkenleri `ref` yeniden atayabilirsiniz.
- Diziler üzerinde `stackalloc` baş harflerini kullanabilirsiniz.
- Bir deseni destekleyen herhangi bir türe sahip ifadeler kullanabilirsiniz. `fixed`
- Ek genel kısıtlamalar kullanabilirsiniz.

Aşağıdaki geliştirmeler varolan özellikler için yapılmıştır:

- Test `==` edebilirsiniz `!=` ve tuple türleri ile.
- İfade değişkenlerini daha fazla konumda kullanabilirsiniz.
- Otomatik olarak uygulanan özelliklerin destek alanına öznitelikleri ekleyebilirsiniz.
- Bağımsız değişkenler farklı `in` olduğunda yöntem çözümlemesi geliştirildi.
- Aşırı yükleme çözünürlüğü artık daha az belirsiz servis talepleri ne kadar azdır.

Yeni derleyici seçenekleri şunlardır:

- `-publicsign`derlemelerin Açık Kaynak Yazılım (OSS) imzalanmasını etkinleştirmek için.
- `-pathmap`kaynak dizinler için bir eşleme sağlamak için.

Bu makalenin geri kalanı, her bir geliştirme hakkında daha fazla bilgi edinmek için ayrıntılar ve bağlantılar sağlar. `dotnet try` Bu özellikleri ortamınızda genel aracı kullanarak keşfedebilirsiniz:

1. [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global aracını yükleyin.
1. [Dotnet/try-samples](https://github.com/dotnet/try-samples) deposunu klonla.
1. *Deneme örnekleri* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="enabling-more-efficient-safe-code"></a>Daha verimli güvenli kod etkinleştirme

C# kodunu güvenli bir şekilde yazabilmelisin. Güvenli kod arabellek taşmaları, başıboş işaretçiler ve diğer bellek erişim hataları gibi hata sınıfları önler. Bu yeni özellikler doğrulanabilir güvenli kodun yeteneklerini genişletir. Güvenli yapılar kullanarak kodunuzu daha fazla yazmak için çalışıyoruz. Bu özellikler bunu kolaylaştırır.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Dizin `fixed` oluşturma alanları sabitleme gerektirmez

Bu yapıyı göz önünde bulundurun:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

C#'ın önceki sürümlerinde, bir değişkenin parçası olan tamsayılardan birine `myFixedField`erişmek için bir değişkeni sabitlemeniz gerekiyordu. Şimdi, aşağıdaki kod ayrı `p` `fixed` bir ifade içinde değişken sabitleme olmadan derler:

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

Değişken `p` bir öğeye `myFixedField`erişer. Ayrı `int*` bir değişken bildirmeniz gerekmez. Yine de bir `unsafe` içeriğe ihtiyacınız olduğunu unutmayın. C#'ın önceki sürümlerinde, ikinci bir sabit işaretçi bildirmeniz gerekir:

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

Daha fazla bilgi için [ `fixed` deyimdeki](../language-reference/keywords/fixed-statement.md)makaleye bakın.

### <a name="ref-local-variables-may-be-reassigned"></a>`ref`yerel değişkenler yeniden atanabilir

Şimdi, `ref` yerel halk, para'ya para batandıktan sonra farklı örneklere başvurmak üzere yeniden atanabilir. Aşağıdaki kod şimdi derler:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Daha fazla bilgi [ `ref` için, döner `ref` ve yerel halklar](../programming-guide/classes-and-structs/ref-returns.md)ile ilgili makaleye ve . [`foreach`](../language-reference/keywords/foreach-in.md)

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc`diziler baş harflerini destekler

Bir dizideki öğelerin değerlerini, bir diziyi ilk olarak aranız:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Şimdi, aynı sözdizimi ile `stackalloc`bildirilen diziler için uygulanabilir:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Daha fazla bilgi için [ `stackalloc` operatör](../language-reference/operators/stackalloc.md) makalesine bakın.

### <a name="more-types-support-the-fixed-statement"></a>Diğer türler `fixed` deyimi destekler

Bildirim, `fixed` sınırlı sayıda türü destekledi. C# 7.3 ile başlayarak, `GetPinnableReference()` bir veya `ref T` `ref readonly T` olabilir döndürür bir yöntem içeren herhangi bir tür `fixed`. Bu özelliğin `fixed` eklenmesi, ilgili <xref:System.Span%601?displayProperty=nameWithType> türlerle ve ilgili türlerle kullanılabileceğini zedilen anlamına gelir.

Daha fazla bilgi [ `fixed` ](../language-reference/keywords/fixed-statement.md) için, dil başvurusundaki deyim makalesine bakın.

### <a name="enhanced-generic-constraints"></a>Geliştirilmiş genel kısıtlamalar

Artık bir tür <xref:System.Enum?displayProperty=nameWithType> parametresi için türü veya <xref:System.Delegate?displayProperty=nameWithType> taban sınıf kısıtlamaları olarak belirtebilirsiniz.

Bir tür parametrenin geçersiz olmayan `unmanaged` [yönetilmeyen](../language-reference/builtin-types/unmanaged-types.md)bir tür olması gerektiğini belirtmek için yeni kısıtlamayı da kullanabilirsiniz.

Daha fazla bilgi [ `where` için, genel kısıtlamalar](../language-reference/keywords/where-generic-type-constraint.md) ve [tür parametreleri üzerindeki kısıtlamalar hakkındaki](../programming-guide/generics/constraints-on-type-parameters.md)makalelere bakın.

Varolan türlere bu kısıtlamaları eklemek uyumsuz bir [değişikliktir.](version-update-considerations.md#incompatible-changes) Kapalı genel türleri artık bu yeni kısıtlamaları karşılamayabilir.

## <a name="make-existing-features-better"></a>Varolan özellikleri daha iyi hale getirin

İkinci tema, dildeki özellikleriçin iyileştirmeler sağlar. Bu özellikler C# yazarken üretkenliği artırır.

### <a name="tuples-support--and-"></a>Tuples `==` destek ve`!=`

C# tuple türleri `==` şimdi `!=`destek ve . Daha fazla bilgi için, [tuples](../tuples.md)makalede [eşitliği](../tuples.md#equality-and-tuples) kapsayan bölüme bakın.

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Otomatik olarak uygulanan özellikler için destek alanlarına öznitelikleri ekleme

Bu sözdizimi şimdi desteklenir:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Öznitelik `SomeThingAboutFieldAttribute` için derleyici oluşturulan destek alanına `SomeProperty`uygulanır. Daha fazla bilgi için C# programlama kılavuzundaki [özniteliklere](../programming-guide/concepts/attributes/index.md) bakın.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in`yöntem aşırı yük çözünürlüğü tiebreaker

`in` Bağımsız değişken değiştirici eklendiğinde, bu iki yöntem bir belirsizliğe neden olur:

```csharp
static void M(S arg);
static void M(in S arg);
```

Şimdi, değeri (önceki örnekte ilk) aşırı okuma yalnızca başvuru sürümü daha iyidir. Yalnızca başvuru bağımsız değişkenini içeren sürümü çağırmak `in` için, yöntemi ararken değiştiricieklemeniz gerekir.

> [!NOTE]
> Bu bir hata düzeltmesi olarak uygulandı. Bu artık dil sürümü "7.2" olarak ayarlanmış olsa bile belirsizdir.

Daha fazla bilgi için [ `in` parametre değiştirici](../language-reference/keywords/in-parameter-modifier.md)makalesine bakın.

### <a name="extend-expression-variables-in-initializers"></a>Baş harflerdeki ifade değişkenlerini genişletme

Değişken bildirimlere izin `out` vermek için C# 7.0'a eklenen sözdizimi alan başharflerini, özellik baş harflerini, oluşturucu baş harflerini ve sorgu yan tümcelerini içerecek şekilde genişletilmiştir. Aşağıdaki örnek gibi bir kod sağlar:

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a>Geliştirilmiş aşırı yükleme adayları

Her sürümde, aşırı yük çözümleme kuralları, belirsiz yöntem çağrılarının "bariz" bir seçeneği olduğu durumları ele almak için güncelleştirilir. Bu sürüm, derleyicinin bariz seçimi seçmesine yardımcı olmak için üç yeni kural ekler:

1. Bir yöntem grubu hem örnek hem de statik üye içeriyorsa, yöntem bir örnek alıcısı veya bağlam ı olmadan çağrıldıysa derleyici örnek üyeleri atar. Yöntem bir örnek alıcıile çağrıldıysa derleyici statik üyeleri atar. Alıcı olmadığında, derleyici statik bağlamda yalnızca statik üyeler içerir, aksi takdirde hem statik hem de örnek üyeler. Alıcı belirsiz bir örnek veya tür olduğunda, derleyici her ikisini de içerir. Örtük `this` bir örnek alıcının kullanılamadığı statik bağlam, statik `this` üyeler gibi tanımlanmamış üyelerin gövdesini ve `this` alan başharfleri ve yapıcı-başharfler gibi kullanılamayacak yerleri içerir.
1. Bir yöntem grubu, tür bağımsız değişkenleri kısıtlamalarını karşılamayan bazı genel yöntemler içeriyorsa, bu üyeler aday kümesinden kaldırılır.
1. Yöntem grubu dönüştürmesi için, dönüş türü temsilcinin dönüş türüyle eşleşmeyen aday yöntemler kümeden kaldırılır.

Hangi yöntemin daha iyi olduğundan emin olduğunuzda, belirsiz yöntem aşırı yüklemeleri için daha az derleyici hatası bulacağınız için bu değişikliği fark eedeceksiniz.

## <a name="new-compiler-options"></a>Yeni derleyici seçenekleri

Yeni derleyici seçenekleri, C# programları için yeni yapı ve DevOps senaryolarını destekler.

### <a name="public-or-open-source-signing"></a>Genel veya Açık Kaynak imzalama

Derleyici seçeneği derleyiciye `-publicsign` ortak bir anahtar kullanarak derlemeyi imzalamasını bildirir. Derleme imzalı olarak işaretlenir, ancak imza ortak anahtardan alınır. Bu seçenek, ortak bir anahtar kullanarak açık kaynak projelerinden imzalı derlemeler oluşturmanıza olanak tanır.

Daha fazla bilgi için [-publicsign derleyici seçeneği](../language-reference/compiler-options/publicsign-compiler-option.md) makalesine bakın.

### <a name="pathmap"></a>yol haritası

Derleyici seçeneği, `-pathmap` derleyiciye yapı ortamından gelen kaynak yollarını eşlenen kaynak yolları ile değiştirmesini bildirir. Seçenek, `-pathmap` derleyici tarafından PDB dosyalarına veya <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Daha fazla bilgi için [-pathmap derleyicisi seçeneği](../language-reference/compiler-options/pathmap-compiler-option.md) makalesine bakın.

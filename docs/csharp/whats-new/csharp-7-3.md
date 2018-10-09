---
title: C# 7.3 yenilikler nelerdir?
description: C# 7.3 içindeki yeni özelliklere genel bakış
ms.date: 05/16/2018
ms.openlocfilehash: 570da53059242c0242609ddcba5cb23f1728aa9f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873806"
---
# <a name="whats-new-in-c-73"></a>C# 7.3 yenilikler nelerdir?

C# 7.3 sürüm için iki ana temaları vardır. Bir tema güvenli kod güvenli olmayan kod olarak yüksek performanslı olmasını sağlayan özellikler sunar. İkinci temanın mevcut özelliklere yapılan artımlı iyileştirmeleri sağlar. Ayrıca, yeni derleyici seçenekleri, bu sürümde eklendi.

Aşağıdaki yeni özellikleri temayı daha iyi performans için güvenli kod desteği:

- Sabit alanlar sabitleme olmadan erişebilir.
- Yeniden atayabilirsiniz `ref` yerel değişkenler.
- Başlatıcılar kullanabileceğiniz `stackalloc` dizileri.
- Kullanabileceğiniz `fixed` ifadelerle desen destekleyen herhangi bir türü.
- Ek genel kısıtlamalara kullanabilirsiniz.

Mevcut özellikler için aşağıdaki geliştirmeler yapılmıştır:

- Test edebilirsiniz `==` ve `!=` tanımlama grubu türleri ile.
- Daha fazla konumda ifade değişkenleri kullanabilirsiniz.
- Otomatik uygulanan özellikler için destek alanı öznitelikleri iliştirebilirsiniz.
- Bağımsız değişkenleri farklı olduğunda yöntemi çözümleme `in` geliştirilmiştir.
- Aşırı yükleme çözümlemesi belirsiz daha az servis taleplerini artık sahiptir.

Yeni derleyici seçenekleri şunlardır:

- `-publicsign` Açık kaynak yazılım (OSS) derlemeleri imzalamayı etkinleştirmek için.
- `-pathmap` Kaynak dizinleri için bir eşleme sağlamak için.

Bu makalenin geri kalanında, Ayrıntılar ve her geliştirmeleri hakkında daha fazla bilgi için bağlantılar sağlar.

## <a name="enabling-more-efficient-safe-code"></a>Daha verimli bir güvenli kod etkinleştirme

Güvenli bir şekilde gerçekleştiren güvenli olmayan kod yanı sıra C# kodu yazacak olması gerekir. Güvenli kod hataları, arabellek taşmalarına parazit işaretçileri ve diğer bellek erişim hataları gibi sınıfları önler. Bu yeni özellikler doğrulanabilir bir güvenli kod yeteneklerini genişletmenizi sağlar. Daha fazla güvenli yapıları kullanarak kodunuzu yazmak çaba harcar. Bu özellikler, kolaylaştırır.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Dizin oluşturma `fixed` alanları sabitleme gerektirmez

Bu struct göz önünde bulundurun:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

Önceki sürümlerde, C#, erişim bir parçası olan bir tamsayı değişkene sabitlemek gereken `myFixedField`. Artık, aşağıdaki kod, güvenli bir bağlamda derler:

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

Değişken `p` bir öğe üzerinde erişen `myFixedField`. Ayrı bir bildirmeniz gerekmez `int*` değişkeni. Unutmayın, yine bir `unsafe` bağlamı. Önceki sürümlerde, C#, ikinci sabit bir işaretçi bildirmeniz gerekir:

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

Daha fazla bilgi için makaleye bakın [ `fixed` deyimi](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>`ref` yerel değişkenler atanabilir

Şimdi, `ref` Yereller başlatıldıktan sonra farklı örneklerine başvurmak için atanabilir. Aşağıdaki kod artık derlenmemektedir:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Daha fazla bilgi için makaleye bakın [ `ref` döndürür ve `ref` Yereller](../programming-guide/classes-and-structs/ref-returns.md)ve makale [ `foreach` ](../language-reference/keywords/foreach-in.md).

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` başlatıcılar diziler desteği

Başlattığınızda bir dizide öğe değerlerini belirtin ettirebilmeyi başardım:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Artık, aynı söz dizimi ile bildirilen diziler için uygulanabilir `stackalloc`:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Daha fazla bilgi için [ `stackalloc` deyimi](../language-reference/keywords/stackalloc.md) dil başvurusu makalesinde.

### <a name="more-types-support-the-fixed-statement"></a>Daha fazla türlerini destekleyen `fixed` deyimi

`fixed` Deyimi sınırlı sayıda türleri desteklenir. C# 7.3, içeren herhangi bir türü'ile başlayan bir `GetPinnableReference()` döndüren yöntem bir `ref T` veya `ref readonly T` olabilir `fixed`. Bu özellik ekleme anlamına `fixed` kullanılabilir <xref:System.Span%601?displayProperty=nameWithType> ve ilgili türler.

Daha fazla bilgi için [ `fixed` deyimi](../language-reference/keywords/fixed-statement.md) dil başvurusu makalesinde.

### <a name="enhanced-generic-constraints"></a>Gelişmiş genel kısıtlamalar

Türü artık belirtebilirsiniz <xref:System.Enum?displayProperty=nameWithType> veya <xref:System.Delegate?displayProperty=nameWithType> bir tür parametresi için temel sınıf kısıtlama olarak.

Ayrıca yeni kullanabilirsiniz `unmanaged` kısıtlaması, bir tür parametresi olması gerektiğini belirtmek için bir **yönetilmeyen tür**. Bir **yönetilmeyen tür** , bir başvuru türü değil ve iç içe geçme herhangi bir düzeyde herhangi bir başvuru türü içermeyen bir türdür.

Daha fazla bilgi için üzerinde makalelerine bakın. [ `where` genel kısıtlamalara](../language-reference/keywords/where-generic-type-constraint.md) ve [tür parametrelerindeki kısıtlamalar](../programming-guide/generics/constraints-on-type-parameters.md).

Bu kısıtlamaları var olan türlere ekleme bir [uyumsuz değişiklik](version-update-considerations.md#incompatible-changes). Kapalı genel türler, artık bu yeni kısıtlamalarını karşılamıyor.

## <a name="make-existing-features-better"></a>Mevcut özellikler daha iyi hale getirir

İkinci tema özelliklerinde dilde geliştirmeler sağlar. Bu özellikler, C# yazarken üretkenliği artırın.

### <a name="tuples-support--and-"></a>Diziler Destek `==` ve `!=`

C# demet türleri artık destek `==` ve `!=`. Bölüm kapsayan daha fazla bilgi için bkz. [eşitlik](../tuples.md#equality-and-tuples) makalede [diziler](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Otomatik uygulanan özellikler için yedekleme alanları öznitelikleri ekleme

Bu sözdizimi artık desteklenmektedir:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Öznitelik `SomeThingAboutFieldAttribute` derleyicinin ürettiği yedekleme alanı için uygulanan `SomeProperty`. Daha fazla bilgi için [öznitelikleri](../programming-guide/concepts/attributes/index.md) C# programlama kılavuzu.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in` yöntemi aşırı yükleme çözünürlüğü tiebreaker

Zaman `in` değiştirici bağımsız değişken eklendi, bu iki yöntem belirsizliğe neden olur:

```csharp
static void M(S arg);
static void M(in S arg);
```

Şimdi, (ilk olarak önceki örnek) değeriyle aşırı daha iyi salt okunur başvuru sürümüne göre. Sürüm salt okunur başvuru bağımsız değişkeni ile çağırmak için içermelidir `in` yöntemi çağırırken değiştiricisi.

> [!NOTE]
> Bu, bir hata düzeltmesi uygulanmıştır. Bu artık bile "7.2 için" kümesi dil sürümü ile belirsiz.

Daha fazla bilgi için makaleye bakın [ `in` parametre değiştiricisi](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Başlatıcılar içindeki ifade değişkenleri genişletme

C# izin vermek için 7.0 eklenen söz dizimi `out` değişken bildirimlerini eklemek alan başlatıcıları, özellik başlatıcılar, oluşturucu başlatıcıları sorgu yan tümceleri için genişletilmişse. Bu, aşağıdaki örnek gibi bir kod sağlar:

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

Her sürümde, aşırı yükleme çözünürlüğü kuralları belirsiz yöntem çağrılarını "açık" bir seçeneğin sahip olduğu durumlara yönelik olarak güncelleştirilir. Bu sürüm, belirgin seçim çekme derleyici yardımcı olmak için üç yeni kurallar ekler:

1. Bir yöntem grubu örneği hem statik üyeler içeriyorsa, yöntem bir örnek alıcı ya da bağlam çağrıldı, derleyici örnek üyeleri atar. Yöntemi bir örnek alıcı ile çağırdığınız derleyici statik üyeleri olarak atar. Hiç alıcı olduğunda, derleyicinin yalnızca statik üyeleri statik bir bağlamda, aksi takdirde statik içerir ve örnek üyeleri. Alıcı, muğlak örneği veya türü olduğunda, derleyici her ikisi de içerir. Bir statik içerik, örtük burada `this` örneği alıcı kullanılamaz, üyeleri gövdesi yok burada içerir `this` statik üyeleri gibi tanımlanan yanı sıra yerlerde `this` gibi alan başlatıcıları kullanılamaz ve Oluşturucu başlatıcıları.
1. Bir yöntem grubu türü bağımsız değişkenleri kendi kısıtlamaları karşılamayan bazı genel yöntemleri içeriyorsa, bu üyeler için aday kümesinden kaldırılır.
1. Bir yöntem grubu dönüştürme, türü, kümeden kaldırıldığına aday yöntemleri, dönüş türü temsilcinin ile eşleşmiyor döndürür.

Hangi daha iyi bir yöntemdir emin olduğunuzda belirsiz yöntemi aşırı yüklemeleri için daha az derleyici hataları bulabilirsiniz. çünkü bu değişiklik yalnızca fark edeceksiniz.

## <a name="new-compiler-options"></a>Yeni derleyici seçenekleri

Yeni derleme seçenekleri C# programları için yeni derleme ve DevOps senaryolarını destekler.

### <a name="public-or-open-source-signing"></a>Genel veya açık kaynak imzalama

`-publicsign` Derleyici seçeneği, bir ortak anahtar kullanarak derlemeyi imzalamak için derleyicinin bildirir. Derleme işaretli olarak işaretlenmiş, ancak imza ortak anahtardan alınır. Bu seçenek, bir ortak anahtar kullanarak, açık kaynak projelerinden imzalı derlemeler oluşturmanıza olanak sağlar.

Daha fazla bilgi için [- publicsign derleyici seçeneği](../language-reference/compiler-options/publicsign-compiler-option.md) makalesi.

### <a name="pathmap"></a>pathmap

`-pathmap` Derleyici seçeneği, yapı ortamı'ndan kaynak yolları ile eşlenen kaynak yolları değiştirmek için derleyicinin bildirir. `-pathmap` Seçeneği denetimleri veya PDB dosyaları için derleyici tarafından yazılmış kaynak yolu <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Daha fazla bilgi için [- pathmap derleyici seçeneği](../language-reference/compiler-options/pathmap-compiler-option.md) makalesi.

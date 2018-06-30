---
title: C# 7.3 içinde yenilikler nelerdir?
description: C# 7.3 içindeki yeni özelliklere genel bakış
ms.date: 05/16/2018
ms.openlocfilehash: 135351fa06a498e4aa90cb4d9372880b8119de0f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106781"
---
# <a name="whats-new-in-c-73"></a>C# 7.3 içinde yenilikler nelerdir?

C# 7.3 yayın iki ana temaları vardır. Bir tema güvenli kodunun güvenli olmayan kod olarak kullanıcı olarak olmasını sağlayan özellikler sağlar. İkinci tema artımlı iyileştirmeleri var olan özellikleri sağlar. Ayrıca, yeni derleyici seçenekleri bu sürümde eklendi.

Aşağıdaki yeni özellikleri tema daha iyi performans için güvenli kod destekler:

- Sabitleme olmadan sabit alanları erişebilir.
- Yeniden atama yapabilir `ref` yerel değişkenler.
- Başlatıcılar kullanabileceğiniz `stackalloc` dizileri.
- Kullanabileceğiniz `fixed` deyimleri ile bir deseni destekleyen herhangi bir türü.
- Ek genel kısıtlamalar kullanabilirsiniz.

Aşağıdaki geliştirmeleri için var olan özellikleri yapıldı:

- Test edebilirsiniz `==` ve `!=` tanımlama grubu türleriyle.
- Daha fazla konumlarda ifade değişkenlerini kullanabilirsiniz.
- Otomatik uygulanan özellikler yedekleme alanını için öznitelikler eklemek.
- Bağımsız değişkenler tarafından farklı olduğunda yöntemi çözümleme `in` geliştirilmiştir.
- Aşırı yükleme çözünürlüğü artık daha az belirsiz durumda olur.

Yeni derleyici seçenekleri şunlardır:

- `-publicsign` Açık kaynak yazılım (OSS) derlemelerinin imzalamayı etkinleştirmek için.
- `-pathmap` Kaynak dizin için bir eşleme sağlamak için.

Bu makalenin sonraki bölümlerinde, Ayrıntılar ve her iyileştirmeleri hakkında daha fazla bilgi için bağlantılar sağlar.

## <a name="enabling-more-performant-safe-code"></a>Daha fazla kullanıcı güvenli kod etkinleştirme

Güvenli bir şekilde yanı sıra güvenli olmayan kod gerçekleştiren C# kod yazmanız. Güvenli kod arabellek taşmaları, parazit işaretçileri ve diğer bellek erişim hataları gibi hataları sınıfları önler. Bu yeni özellikleri doğrulanabilen güvenli kod özelliklerini genişletin. Daha fazla güvenli yapıları kullanarak kodunuzu yazma konusunda da çalışmalar yapılmaktadır. Bu özellikler, kolaylaştırır.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Dizin oluşturma `fixed` alanları sabitleme gerektirmez

Bu yapı göz önünde bulundurun:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

Bir değişken parçası olan tamsayılar birine erişmek için PIN için gereken önceki sürümlerinde C#, `myFixedField`. Şimdi, aşağıdaki kodu güvenli bir bağlamda derler:

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

Değişkeni `p` bir öğedeki erişen `myFixedField`. Ayrı bir bildirmeniz gerekmez `int*` değişkeni. Hala ihtiyacınız Not bir `unsafe` bağlamı. Önceki sürümlerde, C#, ikinci bir sabit işaretçi bildirmeniz gerekir:

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

Daha fazla bilgi için üzerinde makalesine bakın. [ `fixed` deyimi](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>`ref` yerel değişkenler atanabilir

Şimdi, `ref` Yereller yeniden atandı farklı örnekleri başlatılmış sonra başvurmak için. Aşağıdaki kod artık derler:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Daha fazla bilgi için üzerinde makalesine bakın. [ `ref` döndürür ve `ref` Yereller](../programming-guide/classes-and-structs/ref-returns.md)ve makale [ `foreach` ](../language-reference/keywords/foreach-in.md).

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` diziler başlatıcıları desteği

Bunu başlattığınızda bir dizide öğeler için değerleri belirtin:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Şimdi, o aynı sözdizimi ile bildirilen diziler uygulanabilir `stackalloc`:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Daha fazla bilgi için bkz: [ `stackalloc` deyimi](../language-reference/keywords/stackalloc.md) dil başvurusu makalesinde.

### <a name="more-types-support-the-fixed-statement"></a>Daha fazla türlerini destekleyen `fixed` deyimi

`fixed` Deyimi sınırlı sayıda türleri desteklenir. C# 7.3, içeren herhangi bir türü'ile başlayan bir `GetPinnableReference()` döndüren yöntemi bir `ref T` veya `ref readonly T` olabilir `fixed`. Bu özellik ekleme anlamına `fixed` ile kullanılan <xref:System.Span%601?displayProperty=nameWithType> ve ilgili türleri.

Daha fazla bilgi için bkz: [ `fixed` deyimi](../language-reference/keywords/fixed-statement.md) dil başvurusu makalesinde.

### <a name="enhanced-generic-constraints"></a>Gelişmiş genel kısıtlamalar

Şimdi türünü belirtebilirsiniz <xref:System.Enum?displayProperty=nameWithType> veya <xref:System.Delegate?displayProperty=nameWithType> bir tür parametresi için temel sınıf kısıtlamaları olarak.

Ayrıca yeni kullanabilirsiniz `unmanaged` bir tür parametresi gerektiğini belirtmek için kısıtlaması, bir **yönetilmeyen türü**. Bir **yönetilmeyen türü** bir başvuru türü değil ve iç içe geçme herhangi bir düzeyde herhangi bir başvuru türü içermiyor. bir tür.

Daha fazla bilgi için üzerinde makalelerine bakın [ `where` genel kısıtlamalar](../language-reference/keywords/where-generic-type-constraint.md) ve [tür parametrelerindeki kısıtlamalar](../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="make-existing-features-better"></a>Var olan özellikleri daha iyi hale

İkinci tema dilde özelliklerine yönelik geliştirmelerden sağlar. Bu özellikler, C# yazarken üretkenliği artırma.

### <a name="tuples-support--and-"></a>Diziler Destek `==` ve `!=`

C# tanımlama grubu türleri şimdi destek `==` ve `!=`. Bölüm kapak daha fazla bilgi için bkz: [eşitlik](../tuples.md#equality-and-tuples) makalede [diziler](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Otomatik uygulanan özellikler için yedekleme alanların öznitelikleri ekleme

Bu sözdiziminin artık desteklenmektedir:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Öznitelik `SomeThingAboutFieldAttribute` için oluşturulan derleyici yedekleme alanına uygulanan `SomeProperty`. Daha fazla bilgi için bkz: [öznitelikleri](../programming-guide/concepts/attributes/index.md) C# programlama Kılavuzu'nda.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in` yöntemi aşırı yükleme çözümü tiebreaker

Zaman `in` bağımsız değişkeni değiştiricisi eklenen, bu iki yöntem bir belirsizlik neden olur:

```csharp
static void M(S arg);
static void M(in S arg);
```

Şimdi, (ilk olarak önceki örnek) değeriyle aşırı daha iyi salt okunur başvuru sürümüne göre. Salt okunur başvuru bağımsız değişkeni sürümüyle çağırmak için içermelidir `in` yöntemi çağrılırken değiştiricisi.

> [!NOTE]
> Bu hata düzeltmesi uygulanmıştır. Bu artık bile "7.2" kümesi dil sürümü ile belirsiz.

Daha fazla bilgi için üzerinde makalesine bakın. [ `in` parametresi değiştiricisi](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Başlatıcılar ifade değişkenlerini genişletme

C# izin vermek için 7. 0'eklenen sözdizimi `out` değişken bildirimleri genişletilmişse eklenecek alan başlatıcıları, özellik başlatıcılar, oluşturucu başlatıcıları ya da yan tümceleri sorgu. Aşağıdaki örnek gibi kodu sağlar:

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
   public D(int i) : B(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a>Geliştirilmiş aşırı adayları

Her sürümde aşırı çözümleme kurallarını belirsiz yöntem çağrılarına "açık" bir seçim sahip olduğu durumlara yönelik olarak güncelleştirilmesi. Bu sürüm bariz seçim çekme derleyici yardımcı olmak için üç yeni kurallar ekler:

1. Bir yöntem grubu örneği ve statik üyeler içeriyorsa, yöntemi bir örnek alıcı veya bağlam başlatıldı, derleyici örnek üyelerin atar. Yöntem örneği alıcı ile çağrıldı, derleyici statik üyeleri atar. Alıcı yok olduğunda Derleyici yalnızca statik üyeleri bir statik bağlamında, aksi takdirde statik içerir ve üyeleri örneği. Alıcı, muğlak örneği veya türü olduğunda, derleyicinin hem de içerir. Statik içerik örtülü burada `this` örneği alıcı kullanılamaz, Hayır burada üyeleri gövdesini içeren `this` statik üyeler gibi tanımlanmış yanı sıra yerlerde `this` alan başlatıcıları gibi kullanılamaz ve Oluşturucu başlatıcıları.
1. Bir yöntem grubu, tür bağımsız değişkenleri kendi kısıtlamalarını karşılamadığı bazı genel yöntemler içeriyorsa, bu üyeler adayı kümesinden kaldırılır.
1. Yöntemi Grup dönüştürme için türü kümeden kaldırılır, dönüş türü temsilcinin ile eşleşmeyen adayı yöntemleri döndürür.

Hangi daha iyi bir yöntemdir emin olduktan sonra daha az derleyici hataları için belirsiz yöntemi aşırı bulabilirsiniz çünkü bu değişikliği yalnızca fark edeceksiniz.

## <a name="new-compiler-options"></a>Yeni derleyici seçenekleri

Yeni derleyici seçenekleri, C# programları için yeni derleme ve DevOps senaryoları destekler.

### <a name="public-or-open-source-signing"></a>Genel veya açık kaynak imzalama

`-publicsign` Derleyici seçeneği, bir ortak anahtar kullanarak derlemeyi imzalamak için derleyici gerçekleştirilmesi talimatını verir. Derleme imzalanmış olarak işaretlenmiş, ancak imza ortak anahtarı ile alınır. Bu seçenek, ortak anahtar kullanarak açık kaynaklı projelerden imzalı derlemeler oluşturmanıza olanak sağlar.

Daha fazla bilgi için bkz: [- publicsign derleyici seçeneği](../language-reference/compiler-options/publicsign-compiler-option.md) makalesi.

### <a name="pathmap"></a>pathmap

`-pathmap` Derleyici seçeneği ile eşlenen kaynak yolları yapı ortamı'ndan kaynak yolları değiştirmek için derleyici bildirir. `-pathmap` Seçeneği denetimleri PDB dosyalarını veya için derleyici tarafından yazılan kaynak yolu <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Daha fazla bilgi için bkz: [- pathmap derleyici seçeneği](../language-reference/compiler-options/pathmap-compiler-option.md) makalesi.

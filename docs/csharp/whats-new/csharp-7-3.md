---
title: C# 7,3 ' deki yenilikler
description: C# 7,3 ' deki yeni özelliklere genel bakış
ms.date: 05/16/2018
ms.openlocfilehash: cd8f554516fb5078d9d2ed1eec787f36e8f4c7a7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174763"
---
# <a name="whats-new-in-c-73"></a>C# 7,3 ' deki yenilikler

C# 7,3 sürümünün iki ana teması vardır. Bir tema, güvenli kodun güvenli olmayan kod olarak performans sağlamak için gereken özellikler sağlar. İkinci tema, mevcut özelliklerle artımlı iyileştirmeler sağlar. Ayrıca, bu yayına yeni derleyici seçenekleri eklenmiştir.

Aşağıdaki yeni özellikler, güvenli kod için daha iyi performans temasını destekler:

- Sabitlemeden sabit alanlara erişebilirsiniz.
- `ref`Yerel değişkenleri yeniden atayabilirsiniz.
- Dizilerde başlatıcıları kullanabilirsiniz `stackalloc` .
- `fixed`Deyimlerini, bir kalıbı destekleyen herhangi bir türle birlikte kullanabilirsiniz.
- Ek genel kısıtlamalar kullanabilirsiniz.

Mevcut özelliklerde aşağıdaki geliştirmeler yapılmıştır:

- `==` `!=` Kayıt düzeni türlerini test edebilirsiniz.
- İfade değişkenlerini daha fazla konumda kullanabilirsiniz.
- Otomatik uygulanan özelliklerin yedekleme alanına öznitelikler iliştirebilirsiniz.
- Bağımsız değişkenler farklı olduğunda yöntem çözümlemesi `in` geliştirildi.
- Aşırı yükleme çözümlemesi artık daha az belirsiz durum içeriyor.

Yeni derleyici seçenekleri şunlardır:

- `-publicsign`Açık kaynak yazılım (OSS) derlemelerinin imzalanmasını etkinleştirmek için.
- `-pathmap`Kaynak dizinlere eşleme sağlamak için.

Bu makalenin geri kalanında, geliştirmelerin her biri hakkında daha fazla bilgi edinmek için Ayrıntılar ve bağlantılar sağlanmaktadır. Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz `dotnet try` :

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. Şu komutu çalıştırın: `dotnet try`.

## <a name="enabling-more-efficient-safe-code"></a>Daha verimli güvenli kod etkinleştirme

Güvenli olmayan kodun yanı sıra, güvenli bir şekilde C# kodu yazmanız gerekir. Güvenli kod, arabellek taşmaları, başıya işaretçileri ve diğer bellek erişim hataları gibi hata sınıflarını önler. Bu yeni özellikler, doğrulanabilir güvenli kod yeteneklerini genişletir. Güvenli yapılar kullanarak kodunuzun daha fazlasını yazmak için çaba harcar. Bu özellikler daha kolay hale getirir.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Dizin oluşturma `fixed` alanları sabitleme gerektirmez

Bu yapıyı göz önünde bulundurun:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

C# ' nin önceki sürümlerinde, öğesinin parçası olan tamsayıların birine erişmek için bir değişkeni sabitlemeyi gerekiyordu `myFixedField` . Şimdi, aşağıdaki kod değişkeni `p` ayrı bir ifadeye sabitlemeden derler `fixed` :

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

Değişkeni `p` içindeki bir öğeye erişir `myFixedField` . Ayrı bir değişken bildirmeniz gerekmez `int*` . Hala bir bağlam gerekeceğini unutmayın `unsafe` . C# ' nin önceki sürümlerinde ikinci bir sabit işaretçi bildirmeniz gerekir:

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

Daha fazla bilgi için, [ `fixed` deyimindeki](../language-reference/keywords/fixed-statement.md)makaleye bakın.

### <a name="ref-local-variables-may-be-reassigned"></a>`ref`Yerel değişkenler yeniden atanabilir

Şimdi `ref` Yereller, başlatıldıktan sonra farklı örneklere başvuracak şekilde yeniden atanabilir. Aşağıdaki kod artık derlenir:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Daha fazla bilgi için bkz. [ `ref` `ref` dönüşler ve yerel öğeler](../programming-guide/classes-and-structs/ref-returns.md)ve hakkındaki makale [`foreach`](../language-reference/keywords/foreach-in.md) .

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc`diziler, başlatıcıları destekler

Bir dizideki öğeler için değerleri, başlatma sırasında belirtebilirsiniz:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Artık, ile belirtilen dizilere aynı söz dizimi uygulanabilir `stackalloc` :

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Daha fazla bilgi için bkz. [ `stackalloc` operatör](../language-reference/operators/stackalloc.md) makalesi.

### <a name="more-types-support-the-fixed-statement"></a>Daha fazla tür, `fixed` ifadeyi destekler

`fixed`İfade sınırlı bir tür kümesi destekliyordu. C# 7,3 ' den başlayarak, veya döndüren bir yöntemi içeren herhangi bir tür olabilir `GetPinnableReference()` `ref T` `ref readonly T` `fixed` . Bu özelliği eklemek, `fixed` ve ilgili türlerle birlikte kullanılabilecek anlamına gelir <xref:System.Span%601?displayProperty=nameWithType> .

Daha fazla bilgi için bkz. dil başvurusu içindeki [ `fixed` ifade](../language-reference/keywords/fixed-statement.md) makalesi.

### <a name="enhanced-generic-constraints"></a>Gelişmiş genel kısıtlamalar

Artık tür <xref:System.Enum?displayProperty=nameWithType> <xref:System.Delegate?displayProperty=nameWithType> parametresi için türü veya temel sınıf kısıtlamalarını belirtebilirsiniz.

Yeni `unmanaged` kısıtlamayı, bir tür parametresinin null yapılamayan [yönetilmeyen bir tür](../language-reference/builtin-types/unmanaged-types.md)olması gerektiğini belirtmek için de kullanabilirsiniz.

Daha fazla bilgi için bkz. tür parametrelerinde [ `where` genel kısıtlamalar](../language-reference/keywords/where-generic-type-constraint.md) ve [kısıtlamalar](../programming-guide/generics/constraints-on-type-parameters.md)hakkında makaleler.

Bu kısıtlamaları var olan türlere eklemek uyumsuz bir [değişiklik](version-update-considerations.md#incompatible-changes). Kapalı genel türler artık bu yeni kısıtlamaları karşılamayabilir.

## <a name="make-existing-features-better"></a>Mevcut özellikleri daha iyi yapın

İkinci tema, dildeki özelliklere yönelik iyileştirmeler sağlar. Bu özellikler, C# yazma sırasında üretkenliği geliştirir.

### <a name="tuples-support--and-"></a>Tanımlama grubu desteği `==` ve`!=`

C# demet türleri artık ve destekler `==` `!=` . Daha fazla bilgi için [demet türleri](../language-reference/builtin-types/value-tuples.md) makalesinin [kayıt düzeni eşitlik](../language-reference/builtin-types/value-tuples.md#tuple-equality) bölümüne bakın.

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Otomatik uygulanan özellikler için yedekleme alanlarına öznitelikler iliştirme

Bu sözdizimi artık desteklenmektedir:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Özniteliği, `SomeThingAboutFieldAttribute` için derleyicinin oluşturduğu yedekleme alanına uygulanır `SomeProperty` . Daha fazla bilgi için bkz. C# programlama kılavuzundaki [öznitelikler](../programming-guide/concepts/attributes/index.md) .

### <a name="in-method-overload-resolution-tiebreaker"></a>`in`yöntem aşırı yükleme çözünürlüğü tiekesici

`in`Bağımsız değişken değiştiricisi eklendiğinde, bu iki yöntem bir belirsizliğe neden olur:

```csharp
static void M(S arg);
static void M(in S arg);
```

Artık, by değeri (önceki örnekte ilk olarak) aşırı yüklemesi, salt okunur başvuru sürümünden daha iyidir. Salt okunur başvuru bağımsız değişkeniyle sürümü çağırmak için, `in` yöntemini çağırırken değiştiricisini dahil etmeniz gerekir.

> [!NOTE]
> Bu bir hata düzeltilme olarak uygulandı. Dil sürümü "7,2" olarak ayarlanmış olsa bile bu artık belirsizdir.

Daha fazla bilgi için, [ `in` parametre değiştiricisiyle](../language-reference/keywords/in-parameter-modifier.md)ilgili makaleye bakın.

### <a name="extend-expression-variables-in-initializers"></a>Başlatıcılarda ifade değişkenlerini genişletme

Değişken bildirimlerine izin vermek için C# 7,0 ' ye eklenen söz dizimi, `out` alan başlatıcıları, özellik başlatıcıları, Oluşturucu başlatıcıları ve sorgu yan tümcelerini kapsayacak şekilde genişletilmiştir. Aşağıdaki örnek gibi kodu sunar:

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

Her sürümde, aşırı yükleme çözümleme kuralları belirsiz Yöntem etkinleştirmeleri "belirgin" bir seçeneğe sahip olduğu durumlara göre güncelleştirilir. Bu sürüm, derleyicinin açık seçimi seçmesini sağlamaya yardımcı olmak için üç yeni kural ekler:

1. Bir yöntem grubu hem örnek hem de statik üye içerdiğinde, yöntem bir örnek alıcısı veya bağlamı olmadan çağrılırsa, derleyici örnek üyelerini atar. Yöntem bir örnek alıcısıyla çağrılırsa derleyici statik üyeleri atar. Alıcı olmadığında, derleyici statik bir bağlamda yalnızca statik üyeleri ve statik ve örnek üyelerini içerir. Alıcı bir örnek veya tür ındexattributes, derleyici her ikisini de içerir. Örtük bir örnek alıcısının kullanıldığı statik bir bağlam, statik üyeler gibi, hiçbir üyenin, örneğin, `this` `this` `this` alan başlatıcıları ve Oluşturucu başlatıcıları gibi kullanılamayan yerleri de içerir.
1. Bir yöntem grubu, tür bağımsız değişkenleri kısıtlamalarını karşılamadığı bazı genel yöntemler içerdiğinde, bu üyeler aday kümesinden kaldırılır.
1. Bir yöntem grubu dönüştürmesi için, dönüş türü, temsilcinin dönüş türüyle eşleşmeyen aday Yöntemler kümeden kaldırılır.

Bu değişikliği yalnızca, hangi yöntemin daha iyi olduğundan emin olduğunuzda belirsiz yöntem aşırı yüklemeleri için daha az derleyici hatası bulacağınız için fark edeceksiniz.

## <a name="new-compiler-options"></a>Yeni derleyici seçenekleri

Yeni derleyici seçenekleri C# programları için yeni derleme ve DevOps senaryolarını destekler.

### <a name="public-or-open-source-signing"></a>Ortak veya açık kaynak imzalama

`-publicsign`Derleyici seçeneği derleyiciye ortak anahtar kullanarak derlemeyi imzalamasını söyler. Derleme imzalanmış olarak işaretlenir, ancak imza ortak anahtardan alınır. Bu seçenek, açık kaynaklı projelerden ortak anahtar kullanarak imzalı derlemeler oluşturmanıza olanak sağlar.

Daha fazla bilgi için bkz. [-publicsign derleyici seçeneği](../language-reference/compiler-options/publicsign-compiler-option.md) makalesi.

### <a name="pathmap"></a>pathmap

`-pathmap`Derleyici seçeneği, derleyicinin kaynak yollarını eşlenen kaynak yollarla derleme ortamından değiştirmesini söyler. `-pathmap`Seçeneği, derleyici tarafından pdb dosyalarına veya için yazılan kaynak yolunu denetler <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> .

Daha fazla bilgi için bkz. [-pathmap derleyici seçeneği](../language-reference/compiler-options/pathmap-compiler-option.md) makalesi.

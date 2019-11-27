---
title: C# 7,3 sürümündeki yenilikler
description: C# 7,3 sürümündeki yeni özelliklere genel bakış
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204553"
---
# <a name="whats-new-in-c-73"></a>C# 7,3 sürümündeki yenilikler

C# 7,3 sürümünün iki ana teması vardır. Bir tema, güvenli kodun güvenli olmayan kod olarak performans sağlamak için gereken özellikler sağlar. İkinci tema, mevcut özelliklerle artımlı iyileştirmeler sağlar. Ayrıca, bu yayına yeni derleyici seçenekleri eklenmiştir.

Aşağıdaki yeni özellikler, güvenli kod için daha iyi performans temasını destekler:

- Sabitlemeden sabit alanlara erişebilirsiniz.
- `ref` yerel değişkenleri yeniden atayabilirsiniz.
- `stackalloc` dizileri üzerinde başlatıcılar kullanabilirsiniz.
- `fixed` deyimlerini, bir kalıbı destekleyen herhangi bir türle birlikte kullanabilirsiniz.
- Ek genel kısıtlamalar kullanabilirsiniz.

Mevcut özelliklerde aşağıdaki geliştirmeler yapılmıştır:

- `==` ve `!=` demet türleriyle test edebilirsiniz.
- İfade değişkenlerini daha fazla konumda kullanabilirsiniz.
- Otomatik uygulanan özelliklerin yedekleme alanına öznitelikler iliştirebilirsiniz.
- `in` farklı değişkenleri farklılık gösterdiği zaman Yöntem çözümlemesi geliştirildi.
- Aşırı yükleme çözümlemesi artık daha az belirsiz durum içeriyor.

Yeni derleyici seçenekleri şunlardır:

- Açık kaynak yazılım (OSS) derlemelerinin imzalanmasını etkinleştirmek için `-publicsign`.
- Kaynak dizinler için eşleme sağlamak üzere `-pathmap`.

Bu makalenin geri kalanında, geliştirmelerin her biri hakkında daha fazla bilgi edinmek için Ayrıntılar ve bağlantılar sağlanmaktadır. Ortamınızdaki bu özellikleri, `dotnet try` genel aracını kullanarak inceleyebilirsiniz:

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try`'i çalıştırın.

## <a name="enabling-more-efficient-safe-code"></a>Daha verimli güvenli kod etkinleştirme

Güvenli olmayan kod ve güvenli kod C# yazmanız gerekir. Güvenli kod, arabellek taşmaları, başıya işaretçileri ve diğer bellek erişim hataları gibi hata sınıflarını önler. Bu yeni özellikler, doğrulanabilir güvenli kod yeteneklerini genişletir. Güvenli yapılar kullanarak kodunuzun daha fazlasını yazmak için çaba harcar. Bu özellikler daha kolay hale getirir.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Dizin oluşturma `fixed` alanları sabitleme gerektirmez

Bu yapıyı göz önünde bulundurun:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

Önceki sürümlerinde C#, `myFixedField`bir parçası olan tamsayıların birine erişmek için bir değişkeni sabitlemeyi gerekiyordu. Şimdi, aşağıdaki kod `p` değişkeni ayrı bir `fixed` ifadesinde sabitlemeden derlenir:

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

Değişken `p` `myFixedField`bir öğeye erişir. Ayrı bir `int*` değişkeni bildirmeniz gerekmez. Hala `unsafe` bir bağlam gerekeceğini unutmayın. Önceki sürümlerinde C#ikinci bir sabit işaretçi bildirmeniz gerekir:

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

Daha fazla bilgi için [`fixed` deyimindeki](../language-reference/keywords/fixed-statement.md)makaleye bakın.

### <a name="ref-local-variables-may-be-reassigned"></a>`ref` yerel değişkenler yeniden atanabilir

Şimdi, `ref` Yereller başlatıldıktan sonra farklı örneklere başvuracak şekilde yeniden atanabilir. Aşağıdaki kod artık derlenir:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Daha fazla bilgi için [`ref` geri dönüş ve `ref` Yereller](../programming-guide/classes-and-structs/ref-returns.md)ve [`foreach`](../language-reference/keywords/foreach-in.md)makalesindeki makaleye bakın.

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` dizileri başlatıcıları destekler

Bir dizideki öğeler için değerleri, başlatma sırasında belirtebilirsiniz:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Artık, aynı söz dizimi `stackalloc`ile belirtilen dizilere de uygulanabilir:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Daha fazla bilgi için [`stackalloc` operatör](../language-reference/operators/stackalloc.md) makalesine bakın.

### <a name="more-types-support-the-fixed-statement"></a>Daha fazla tür `fixed` ifadesini destekler

`fixed` bildiriminde sınırlı bir tür kümesi desteklenir. 7,3 ile C# başlayarak, bir `ref T` veya `ref readonly T` döndüren `GetPinnableReference()` yöntemi içeren herhangi bir tür `fixed`olabilir. Bu özelliğin eklenmesi, `fixed` <xref:System.Span%601?displayProperty=nameWithType> ve ilgili türlerle kullanılabileceği anlamına gelir.

Daha fazla bilgi için bkz. dil başvurusunda [`fixed` ifade](../language-reference/keywords/fixed-statement.md) makalesi.

### <a name="enhanced-generic-constraints"></a>Gelişmiş genel kısıtlamalar

Artık tür parametresi için temel sınıf kısıtlamaları olarak <xref:System.Enum?displayProperty=nameWithType> veya <xref:System.Delegate?displayProperty=nameWithType> türünü belirtebilirsiniz.

Ayrıca, bir tür parametresinin null yapılamayan [yönetilmeyen bir tür](../language-reference/builtin-types/unmanaged-types.md)olması gerektiğini belirtmek için yeni `unmanaged` kısıtlamasını de kullanabilirsiniz.

Daha fazla bilgi için bkz. [tür parametrelerinde](../programming-guide/generics/constraints-on-type-parameters.md) [genel kısıtlamalar](../language-reference/keywords/where-generic-type-constraint.md) ve kısıtlamalar`where` makaleleri.

Bu kısıtlamaları var olan türlere eklemek uyumsuz bir [değişiklik](version-update-considerations.md#incompatible-changes). Kapalı genel türler artık bu yeni kısıtlamaları karşılamayabilir.

## <a name="make-existing-features-better"></a>Mevcut özellikleri daha iyi yapın

İkinci tema, dildeki özelliklere yönelik iyileştirmeler sağlar. Bu özellikler yazarken C#üretkenliği geliştirir.

### <a name="tuples-support--and-"></a>Tanımlama grubu desteği `==` ve `!=`

C# Demet türleri artık `==` ve `!=`desteklemektedir. Daha fazla bilgi için bkz. [tanımlama](../tuples.md)bilgileri hakkındaki [makaleleri kapsayan bölüm](../tuples.md#equality-and-tuples) .

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Otomatik uygulanan özellikler için yedekleme alanlarına öznitelikler iliştirme

Bu sözdizimi artık desteklenmektedir:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

`SomeThingAboutFieldAttribute` özniteliği, `SomeProperty`için derleyicinin ürettiği yedekleme alanına uygulanır. Daha fazla bilgi için bkz [](../programming-guide/concepts/attributes/index.md) . C# programlama kılavuzundaki öznitelikler.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in` yöntemi aşırı yükleme çözünürlüğü tiekesici

`in` bağımsız değişken değiştiricisi eklendiğinde, bu iki yöntem bir belirsizliğe neden olur:

```csharp
static void M(S arg);
static void M(in S arg);
```

Artık, by değeri (önceki örnekte ilk olarak) aşırı yüklemesi, salt okunur başvuru sürümünden daha iyidir. Sürümü ReadOnly başvuru bağımsız değişkeniyle çağırmak için yöntemi çağırırken `in` değiştiricisini dahil etmeniz gerekir.

> [!NOTE]
> Bu bir hata düzeltilme olarak uygulandı. Dil sürümü "7,2" olarak ayarlanmış olsa bile bu artık belirsizdir.

Daha fazla bilgi için [`in` parametresi değiştiricisiyle](../language-reference/keywords/in-parameter-modifier.md)ilgili makaleye bakın.

### <a name="extend-expression-variables-in-initializers"></a>Başlatıcılarda ifade değişkenlerini genişletme

`out` değişken bildirimlerinin alan C# başlatıcıları, özellik başlatıcıları, Oluşturucu başlatıcıları ve sorgu yan tümcelerini kapsayacak şekilde genişletildiğine izin vermek için 7,0 'e eklenen sözdizimi. Aşağıdaki örnek gibi kodu sunar:

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

1. Bir yöntem grubu hem örnek hem de statik üye içerdiğinde, yöntem bir örnek alıcısı veya bağlamı olmadan çağrılırsa, derleyici örnek üyelerini atar. Yöntem bir örnek alıcısıyla çağrılırsa derleyici statik üyeleri atar. Alıcı olmadığında, derleyici statik bir bağlamda yalnızca statik üyeleri ve statik ve örnek üyelerini içerir. Alıcı bir örnek veya tür ındexattributes, derleyici her ikisini de içerir. Örtük bir `this` örnek alıcısının kullanılabileceği statik bir bağlam, statik üyeler gibi hiçbir `this` tanımlanmadığı üyelerin gövdesini ve alan başlatıcıları ve Oluşturucu başlatıcıları gibi `this` kullanılamayacak yerleri içerir.
1. Bir yöntem grubu, tür bağımsız değişkenleri kısıtlamalarını karşılamadığı bazı genel yöntemler içerdiğinde, bu üyeler aday kümesinden kaldırılır.
1. Bir yöntem grubu dönüştürmesi için, dönüş türü, temsilcinin dönüş türüyle eşleşmeyen aday Yöntemler kümeden kaldırılır.

Bu değişikliği yalnızca, hangi yöntemin daha iyi olduğundan emin olduğunuzda belirsiz yöntem aşırı yüklemeleri için daha az derleyici hatası bulacağınız için fark edeceksiniz.

## <a name="new-compiler-options"></a>Yeni derleyici seçenekleri

Yeni derleyici seçenekleri, programlar için C# yeni derlemeyi ve DevOps senaryolarını destekler.

### <a name="public-or-open-source-signing"></a>Ortak veya açık kaynak imzalama

`-publicsign` derleyici seçeneği derleyicinin bir ortak anahtar kullanarak derlemeyi imzalamasını ister. Derleme imzalanmış olarak işaretlenir, ancak imza ortak anahtardan alınır. Bu seçenek, açık kaynaklı projelerden ortak anahtar kullanarak imzalı derlemeler oluşturmanıza olanak sağlar.

Daha fazla bilgi için bkz. [-publicsign derleyici seçeneği](../language-reference/compiler-options/publicsign-compiler-option.md) makalesi.

### <a name="pathmap"></a>pathmap

`-pathmap` derleyici seçeneği, derleyicinin kaynak yollarını eşlenen kaynak yollarla derleme ortamından değiştirmesini söyler. `-pathmap` seçeneği, derleyici tarafından PDB dosyalarına veya <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>yönelik olarak yazılan kaynak yolunu denetler.

Daha fazla bilgi için bkz. [-pathmap derleyici seçeneği](../language-reference/compiler-options/pathmap-compiler-option.md) makalesi.

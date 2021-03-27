---
title: Boş değer atanabilir başvuru türleri
description: Bu makalede, C# 8,0 ' ye eklenen null yapılabilir başvuru türlerine ilişkin bir genel bakış sunulmaktadır. Yeni ve mevcut projeler için özelliği, null başvuru özel durumlarına karşı nasıl güvenlik sağladığını öğreneceksiniz.
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: da3b75b28d7501e8436d29c0c325c550f0a44c93
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637175"
---
# <a name="nullable-reference-types"></a>Boş değer atanabilir başvuru türleri

C# 8,0, başvuru türü değişkenlerinin özellikleri hakkında önemli deyimler etkinleştirmenizi sağlayan **null yapılabilir başvuru türlerini** ve **null yapılamayan başvuru türlerini** tanıtır:

- **Başvurunun null olması gerekir**. Değişkenlerin null olması beklenen durumlarda derleyici, bu değişkenlerin null olmadığını denetlemeden emin olmak için güvenli olduğunu sağlayan kuralları zorlar:
  - Değişken null olmayan bir değere başlatılmalıdır.
  - Değişkenine hiçbir şekilde değer atanamaz `null` .
- **Başvuru null olabilir**. Değişkenler null olabilir, derleyici null bir başvuruyu doğru bir şekilde kontrol aldığınızdan emin olmak için farklı kurallar uygular:
  - Değişken yalnızca derleyici değerin null olmadığını garanti edemediğinde başvuru yapılabilir.
  - Bu değişkenler varsayılan `null` değerle başlatılabilir ve `null` diğer koddaki değeri atanabilir.

Bu yeni özellik, tasarım amacını değişken bildiriminden belirlenemediği önceki C# sürümlerindeki başvuru değişkenlerinin işlenmesine göre önemli avantajlar sağlar. Derleyici, başvuru türleri için null başvuru özel durumlarına karşı güvenlik sağlamadı:

- **Başvuru null** olabilir. Bir başvuru türü değişkeni olarak başlatıldığında `null` veya daha sonra atandığında derleyici uyarı vermez `null` . Derleyici, null denetimleri olmadan bu değişkenlere başvurulduğunu uyarı verir.
- **Başvurunun null olmadığı varsayılır**. Başvuru türleri başvurulduğunu derleyici hiçbir uyarı vermez. Bir değişken null olabilecek bir ifadeye ayarlandıysa, derleyici uyarıları yayınlar.

Bu uyarılar derleme zamanında yayınlanır. Derleyici null denetim veya başka çalışma zamanı yapılarını Nullable bir bağlamda eklemez. Çalışma zamanında, null yapılabilir bir başvuru ve null atanamaz bir başvuru eşdeğerdir.

Null yapılabilir başvuru türleri eklenmesiyle, amacınızı daha net bir şekilde bildirebilirsiniz. `null`Değer, bir değişkenin bir değere başvurmadığından emin olmanın doğru yoludur. Bu özelliği, kodunuzun tüm değerlerini kaldırmak için kullanmayın `null` . Bunun yerine, amacınızı derleyiciye ve kodunuzu okuyan diğer geliştiricilere bildirmeniz gerekir. Amacınızı bildirerek, derleyici bu amaca tutarsız bir kod yazdığınızda size bildirir.

Null **yapılabilir bir başvuru türü** , [null yapılabilir değer türleriyle](language-reference/builtin-types/nullable-value-types.md)aynı söz dizimi kullanılarak belirtilmiştir: bir `?` değişkenin türüne eklenir. Örneğin, aşağıdaki değişken bildirimi null olabilen bir dize değişkenini temsil eder `name` :

```csharp
string? name;
```

`?`Tür adına eklenmemiş olmayan herhangi bir değişken, **null olamayan bir başvuru türüdür**. Bu özellik, bu özelliği etkinleştirdiğinizde var olan koddaki tüm başvuru türü değişkenlerini içerir.

Derleyici, null olabilen bir başvurunun boş olmayan olarak bilinmesinin bilinmediğini anlamak için statik analizi kullanır. Null olduğunda, null olabilen bir başvuruya başvuru yaptığınızda derleyici sizi uyarır. Değişken adının ardından [null-forverme işlecini](language-reference/operators/null-forgiving.md) kullanarak bu davranışı geçersiz kılabilirsiniz `!` . Örneğin, `name` değişkenin null olmadığını, ancak derleyici bir uyarı olduğunu biliyorsanız, derleyicinin analizini geçersiz kılmak için aşağıdaki kodu yazabilirsiniz:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Türlerin null olabilme sayısı

Herhangi bir başvuru türü, uyarıların ne zaman oluşturulacağını açıklayan dört adet *null* değer içerebilir:

- Null *atanabilir olmayan*: null bu türdeki değişkenlere atanamaz. Bu tür değişkenlerin, başvuru yapılmadan önce null olarak işaretli olması gerekmez.
- *Nullable*: null, bu türdeki değişkenlere atanabilir. Bu türdeki değişkenlerin başvurusunun kaldırılması, önce `null` bir uyarıya neden olup olmadığını denetler.
- *Yükümlülüğü*: zorunluluvou, pre-C # 8,0 durumundadır. Bu tür değişkenlere başvuru yapılmadan başvuru yapılabilir veya atanabilir.
- *Bilinmiyor*: bilinmiyor, genellikle kısıtlamaların tür *Nullable* veya *null değer* atanabilir olması gerektiğini bildirmeyecek tür parametreleri içindir.

Değişken bildirimindeki bir türün null olabilme değeri, değişkenin bildirildiği *null yapılabilir bağlam* tarafından denetlenir.

## <a name="nullable-contexts"></a>Null yapılabilir bağlamlar

Null yapılabilir bağlamlar, derleyicinin başvuru türü değişkenlerini nasıl yorumlayacağını öğrenmek için ayrıntılı denetimi etkinleştirir. Belirli bir kaynak çizginin **null yapılabilir ek açıklama bağlamı** etkin veya devre dışı. Önceden C # 8,0 derleyicisini, tüm kodunuzu devre dışı bırakılmış bir null yapılabilir bağlamda derleme olarak düşünebilirsiniz: herhangi bir başvuru türü null olabilir. **Null yapılabilir uyarılar bağlamı** da etkinleştirilebilir veya devre dışı bırakılabilir. Null yapılabilir uyarılar bağlamı, akış analizini kullanarak derleyici tarafından oluşturulan uyarıları belirtir.

`Nullable` *. Csproj* dosyanızdaki öğesi kullanılarak bir proje için Nullable ek açıklama bağlamı ve null yapılabilir uyarı bağlamı ayarlanabilir. Bu öğe, derleyicinin türlerin null olduğunu ve hangi uyarıların oluşturulduğunu nasıl yorumlayacağını yapılandırır. Geçerli ayarlar şunlardır:

- `enable`: Null yapılabilir ek açıklama bağlamı **etkin**. Null yapılabilir uyarı bağlamı **etkin**.
  - Bir başvuru türü değişkenleri, `string` Örneğin, null değer atanamaz.  Tüm null değer alabilirlik uyarıları etkin.
- `warnings`: Nullable ek açıklama bağlamı **devre dışı bırakıldı**. Null yapılabilir uyarı bağlamı **etkin**.
  - Bir başvuru türü değişkenleri, zorunluluvou. Tüm null değer alabilirlik uyarıları etkin.
- `annotations`: Null yapılabilir ek açıklama bağlamı **etkin**. Null yapılabilir uyarı bağlamı **devre dışı**.
  - Bir başvuru türü değişkenleri, örneğin dizesi null değer atanamaz. Tüm null değer alabilirlik uyarıları devre dışı bırakıldı.
- `disable`: Nullable ek açıklama bağlamı **devre dışı bırakıldı**. Null yapılabilir uyarı bağlamı **devre dışı**.
  - Bir başvuru türü değişkenleri, C# ' ın önceki sürümlerinde olduğu gibi, zorunluluvou 'lardır. Tüm null değer alabilirlik uyarıları devre dışı bırakıldı.

**Örnek**:

```xml
<Nullable>enable</Nullable>
```

Ayrıca, aynı bağlamlarını projenizde her yerde ayarlamak için yönergeleri de kullanabilirsiniz:

- `#nullable enable`: Null yapılabilir ek açıklama bağlamını ve null yapılabilir uyarı bağlamını **etkin** olarak ayarlar.
- `#nullable disable`: Nullable ek açıklama bağlamını ve null yapılabilir uyarı bağlamını **devre dışı** olarak ayarlar.
- `#nullable restore`: Null yapılabilir ek açıklama bağlamını ve null yapılabilir uyarı bağlamını proje ayarlarına geri yükler.
- `#nullable disable warnings`: Nullable uyarı bağlamını **devre dışı** olarak ayarlayın.
- `#nullable enable warnings`: Null yapılabilir uyarı bağlamını **etkin** olarak ayarlayın.
- `#nullable restore warnings`: Proje ayarlarına Nullable uyarı bağlamını geri yükler.
- `#nullable disable annotations`: Nullable ek açıklama bağlamını **devre dışı** olarak ayarlayın.
- `#nullable enable annotations`: Null yapılabilir ek açıklama bağlamını **etkin** olarak ayarlayın.
- `#nullable restore annotations`: Ek açıklama uyarı bağlamını proje ayarlarına geri yükler.

> [!IMPORTANT]
> Global null yapılabilir bağlam, oluşturulan kod dosyaları için uygulanmaz. Her iki strateji kapsamında, null yapılabilir bağlam, üretilen olarak işaretlenen tüm kaynak dosyaları için *devre dışıdır* . Bu, oluşturulan dosyalardaki tüm API 'Lerin açıklanmadığını gösterir. Bir dosyanın oluşturulduğu şekilde işaretlenmiş dört yolu vardır:
>
> 1. . Editorconfig dosyasında, `generated_code = true` Bu dosya için geçerli olan bir bölümde belirtin.
> 1. `<auto-generated>` `<auto-generated/>` Dosyanın üst kısmına bir açıklama koyun. Bu, açıklama içindeki herhangi bir satırda olabilir, ancak açıklama bloğu dosyadaki ilk öğe olmalıdır.
> 1. Dosya adını *TemporaryGeneratedFile_* başlatın
> 1. Dosya adını *. Designer. cs*, *. generated. cs*, *. g. cs* veya *. g. ı. cs* ile sonlandırın.
>
> Oluşturucular, Önişlemci yönergesini kullanarak kabul edebilir [`#nullable`](language-reference/preprocessor-directives.md#nullable-context) .

Varsayılan olarak, null yapılabilir ek açıklama ve uyarı bağlamları yeni projeler dahil **devre dışıdır**. Bu, mevcut kodunuzun değişiklik yapılmadan ve yeni bir uyarı oluşturmadan derlendiğini gösterir.

Bu seçenekler, [mevcut bir kod temelinin](nullable-migration-strategies.md) Nullable başvuru türlerini kullanmak için iki ayrı strateji sağlar.

## <a name="nullable-annotation-context"></a>Null yapılabilir ek açıklama bağlamı

Derleyici, devre dışı bırakılmış bir null yapılabilir ek açıklama bağlamında aşağıdaki kuralları kullanır:

- Etkin olamayan başvuruları devre dışı bir bağlamda bildiremezsiniz.
- Tüm başvuru değişkenlerine null değeri atanabilir.
- Başvuru türü değişkenine başvurulduğunu bir uyarı oluşturulmaz.
- Null-forverme işleci devre dışı bir bağlamda kullanılamaz.

Davranış, C# ' nin önceki sürümleriyle aynıdır.

Derleyici, etkinleştirilmiş bir null yapılabilir ek açıklama bağlamında aşağıdaki kuralları kullanır:

- Başvuru türündeki herhangi bir değişken **null atanamaz bir başvurudur**.
- Null olamayan herhangi bir başvuruya, güvenli bir şekilde başvurulmalıdır.
- Herhangi bir Nullable başvuru türü ( `?` değişken bildiriminde bulunan tür öğesinden sonra belirtilen) null olabilir. Statik analiz, başvurunun başvurulduğunu bir değerin null olarak bilinmeyeceğini belirler. Aksi takdirde, derleyici sizi uyarır.
- Null yapılabilir bir başvurunun null olmadığını bildirmek için null-forverme işlecini kullanabilirsiniz.

Etkin bir null yapılabilir ek açıklama bağlamında, `?` başvuru türüne eklenen karakter **null yapılabilir bir başvuru türü** bildirir. İfadenin null olmadığını bildirmek için **null-forverme işleci** `!` bir ifadeye eklenebilir.

## <a name="nullable-warning-context"></a>Null yapılabilir uyarı bağlamı

Null yapılabilir uyarı bağlamı null yapılabilir ek açıklama bağlamından farklıdır. Yeni ek açıklamalar devre dışı bırakıldığında bile uyarılar etkinleştirilebilir. Derleyici, herhangi bir başvurunun **null durumunu** belirlemede statik akış analizini kullanır. Null *yapılabilir uyarı bağlamı* **devre dışı bırakılmadıysa** null durumu **null** ya da null **olabilir** . Derleyici **null** olduğunu tespit ettiğinizde bir başvuruya başvuru yaparsanız, derleyici sizi uyarır. Derleyici iki koşuldan birini belirleyemediği takdirde başvurunun durumu **null olabilir** :

1. Değişkene kesinlikle null olmayan bir değer atandı.
1. Değişken veya ifade, kendisine başvurulmadan önce null değere karşı denetlendi.

Derleyici, null olabilen bir uyarı bağlamında **null** olabilecek bir değişkene veya ifadeye başvuru yaptığınızda uyarı oluşturur. Ayrıca, null olamayan bir başvuru türü değişkenine **null** olabilen bir değişken ya da ifade atandığında, bu da derleyici uyarı oluşturur.

## <a name="attributes-describe-apis"></a>Öznitelikler API 'Leri tanımlıyor

API 'lere, bağımsız değişkenlerin veya dönüş değerlerinin null olması veya ne zaman null olamaz hakkında daha fazla bilgi sağlayan öznitelikler eklersiniz. Bu öznitelikler hakkında daha fazla bilgiyi [null yapılabilir öznitelikleri](language-reference/attributes/nullable-analysis.md)kapsayan dil başvurusunda bulabilirsiniz. Bu öznitelikler geçerli ve gelecek sürümler üzerinden .NET kitaplıklarına ekleniyor. En yaygın kullanılan API 'Ler ilk olarak güncelleştiriliyor.

## <a name="known-pitfalls"></a>Bilinen Süde

Başvuru türleri içeren diziler ve yapılar, null yapılabilir başvuru türleri özelliği olarak bilinir.

### <a name="structs"></a>Yapılar

Null yapılamayan başvuru türleri içeren bir struct, `default` herhangi bir uyarı olmadan bu için atamaya izin verir. Aşağıdaki örneği inceleyin:

```csharp
using System;

#nullable enable

public struct Student
{
    public string FirstName;
    public string? MiddleName;
    public string LastName;
}

public static class Program
{
    public static void PrintStudent(Student student)
    {
        Console.WriteLine($"First name: {student.FirstName.ToUpper()}");
        Console.WriteLine($"Middle name: {student.MiddleName.ToUpper()}");
        Console.WriteLine($"Last name: {student.LastName.ToUpper()}");
    }

    public static void Main() => PrintStudent(default);
}
```

Yukarıdaki örnekte, null `PrintStudent(default)` olamayan başvuru türleri sırasında hiçbir uyarı yoktur `FirstName` ve `LastName` null olur.

Diğer bir daha yaygın durum, genel yapılar ile ilgilenirken olur. Aşağıdaki örneği inceleyin:

```csharp
#nullable enable

public struct Foo<T>
{
    public T Bar { get; set; }
}

public static class Program
{
    public static void Main()
    {
        string s = default(Foo<string>).Bar;
    }
}
```

Önceki örnekte, özelliği `Bar` `null` çalışma zamanında olacak ve herhangi bir uyarı olmadan null yapılamayan dizeye atanır.

### <a name="arrays"></a>Diziler

Diziler aynı zamanda null yapılabilir başvuru türlerinde bilinen bir Süde bulunur. Uyarı üretmeyen aşağıdaki örneği göz önünde bulundurun:

```csharp
using System;

#nullable enable

public static class Program
{
    public static void Main()
    {
        string[] values = new string[10];
        string s = values[0];
        Console.WriteLine(s.ToUpper());
    }
}
```

Önceki örnekte, dizinin bildirimi null yapılamayan dizeler olduğunu gösterirken, öğeleri tamamen null olarak başlatılır. Sonra, değişkenine `s` null değer atanır (dizinin ilk öğesi). Son olarak, değişken başvurusu `s` bir çalışma zamanı özel durumuna neden olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Taslak Nullable başvuru türleri belirtimi](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)
- [Null yapılabilir başvurular öğreticisine giriş](whats-new/tutorials/nullable-reference-types.md)
- [Var olan bir kod temelinin Nullable başvurulara geçirilmesi](whats-new/tutorials/upgrade-to-nullable-references.md)
- [**Nullable** (C# derleyici seçeneği)](language-reference/compiler-options/language.md#nullable)

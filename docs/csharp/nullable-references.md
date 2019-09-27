---
title: Boş değer atanabilir başvuru türleri
description: Bu makalede, 8 ' C# e eklenen Nullable başvuru türlerine genel bir bakış sağlanır. Yeni ve mevcut projeler için özelliği, null başvuru özel durumlarına karşı nasıl güvenlik sağladığını öğreneceksiniz.
ms.date: 02/19/2019
ms.openlocfilehash: 05a8e14a7c51df685b3ffdf16aab997da0a8036f
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332367"
---
# <a name="nullable-reference-types"></a>Boş değer atanabilir başvuru türleri

C#8,0, başvuru türü değişkenlerinin özellikleri hakkında önemli deyimler etkinleştirmenizi sağlayan **null yapılabilir başvuru türleri** ve **null yapılamayan başvuru türleri** tanıtır:

- **Başvurunun null olması gerekir**. Değişkenlerin null olması beklenen durumlarda derleyici, bu değişkenlerin null olmadığını denetlemeden önce bu değişkenlere başvurmasının güvenli olmasını sağlayan kuralları zorlar:
  - Değişken null olmayan bir değere başlatılmalıdır.
  - Değişkenine hiçbir şekilde değer `null`atanamaz.
- **Başvuru null olabilir**. Değişkenler null olabilir, derleyici null bir başvuruyu doğru bir şekilde kontrol aldığınızdan emin olmak için farklı kurallar uygular:
  - Değişken yalnızca derleyici değerin null olmadığını garanti edemediğinde başvuru yapılabilir.
  - Bu değişkenler varsayılan `null` değerle başlatılabilir ve diğer koddaki değeri `null` atanabilir.

Bu yeni özellik, tasarım amacını değişken bildiriminden belirlenemediği önceki sürümlerde C# başvuru değişkenlerinin işlenmesine göre önemli avantajlar sağlar. Derleyici, başvuru türleri için null başvuru özel durumlarına karşı güvenlik sağlamadı:

- **Başvuru null**olabilir. Bir başvuru türü null olarak başlatıldığında veya daha sonra null değeri atandığında hiçbir uyarı verilmez.
- **Başvurunun null olmadığı varsayılır**. Başvuru türleri başvurulduğunu derleyici hiçbir uyarı vermez. (Null olabilen başvurular sayesinde, null olabilen bir değişkene başvuru yaptığınızda Derleyici uyarıları yayınlar).

Null yapılabilir başvuru türleri eklenmesiyle, amacınızı daha net bir şekilde bildirebilirsiniz. `null` Değer, bir değişkenin bir değere başvurmadığından emin olmanın doğru yoludur. Bu özelliği, kodunuzun tüm `null` değerlerini kaldırmak için kullanmayın. Bunun yerine, amacınızı derleyiciye ve kodunuzu okuyan diğer geliştiricilere bildirmeniz gerekir. Amacınızı bildirerek, derleyici bu amaca tutarsız bir kod yazdığınızda size bildirir.

Null **yapılabilir bir başvuru türü** , [null yapılabilir değer türleriyle](programming-guide/nullable-types/index.md)aynı söz dizimi kullanılarak belirtilmiştir: `?` bir değişkenin türüne eklenir. Örneğin, aşağıdaki değişken bildirimi null olabilen bir dize değişkenini `name`temsil eder:

```csharp
string? name;
```

Tür adına eklenmemiş olan `?` herhangi bir değişken **null yapılamayan bir başvuru türüdür**. Bu özellik, bu özelliği etkinleştirdiğinizde var olan koddaki tüm başvuru türü değişkenlerini içerir.

Derleyici, null olabilen bir başvurunun boş olmayan olarak bilinmesinin bilinmediğini anlamak için statik analizi kullanır. Null olduğunda, null olabilen bir başvuruya başvuru yaptığınızda derleyici sizi uyarır. Değişken adının ardından **null-forverme işlecini** `!` kullanarak bu davranışı geçersiz kılabilirsiniz. Örneğin, `name` değişkenin null olmadığını, ancak derleyici bir uyarı olduğunu biliyorsanız, derleyicinin analizini geçersiz kılmak için aşağıdaki kodu yazabilirsiniz:

```csharp
name!.Length;
```

Bu işleç hakkındaki ayrıntıları GitHub 'da [null yapılabilir başvuru türleri](../../_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) belirtim teklifinde okuyabilirsiniz.

## <a name="nullability-of-types"></a>Türlerin null olabilme sayısı

Herhangi bir başvuru türü, uyarıların ne zaman oluşturulacağını açıklayan dört adet *null*değer içerebilir:

- *Null atanabilir olmayan*: Bu türdeki değişkenlere null atanamaz. Bu tür değişkenlerin, başvuru yapılmadan önce null olarak işaretli olması gerekmez.
- *Null yapılabilir*: Bu türdeki değişkenlere null atanabilir. Bu türdeki değişkenlerin başvurusunun kaldırılması, önce bir uyarıya `null` neden olup olmadığını denetler.
- *Zorunluluvou*: Bu, öncedenC# 8 durumundadır. Bu tür değişkenlere başvuru yapılmadan başvuru yapılabilir veya atanabilir.
- *Bilinmiyor*: Bu, genellikle kısıtlamaların tür *Nullable* veya *null değer*atanamaz olması gerektiğini derleyiciye bildirmeyecek tür parametrelerine yöneliktir.

Değişken bildirimindeki bir türün null olabilme değeri, değişkenin bildirildiği *null yapılabilir bağlam* tarafından denetlenir.

## <a name="nullable-contexts"></a>Null yapılabilir bağlamlar

Null yapılabilir bağlamlar, derleyicinin başvuru türü değişkenlerini nasıl yorumlayacağını öğrenmek için ayrıntılı denetimi etkinleştirir. Herhangi bir kaynak satırının **Nullable ek açıklama bağlamı** veya `disabled`' `enabled` dir. Tüm kodunuzu null yapılabilir birC# `disabled` bağlamda derlemek için önceden 8 derleyicisini düşünebilirsiniz: Herhangi bir başvuru türü null olabilir. **Null olabilir uyarılar bağlamı** veya `enabled` `disabled`olarak ayarlanabilir. Null yapılabilir uyarılar bağlamı, akış analizini kullanarak derleyici tarafından oluşturulan uyarıları belirtir.

`Nullable` *. Csproj* dosyanızdaki öğesi kullanılarak bir proje için Nullable ek açıklama bağlamı ve null yapılabilir uyarı bağlamı ayarlanabilir. Bu öğe, derleyicinin türlerin null olduğunu ve hangi uyarıların oluşturulduğunu nasıl yorumlayacağını yapılandırır. Geçerli ayarlar şunlardır:

- `enable`: Null yapılabilir ek açıklama bağlamı **etkindir**. Null yapılabilir uyarı bağlamı **etkin**.
  - Bir başvuru türü değişkenleri, `string` Örneğin, null değer atanamaz.  Tüm null değer alabilirlik uyarıları etkin.
- `warnings`: Null yapılabilir ek açıklama bağlamı **devre dışı**. Null yapılabilir uyarı bağlamı **etkin**.
  - Bir başvuru türü değişkenleri, zorunluluvou. Tüm null değer alabilirlik uyarıları etkin.
- `annotations`: Null yapılabilir ek açıklama bağlamı **etkindir**. Null yapılabilir uyarı bağlamı **devre dışı**.
  - Bir başvuru türü değişkenleri, zorunluluvou. Tüm null değer alabilirlik uyarıları etkin.
- `disable`: Null yapılabilir ek açıklama bağlamı **devre dışı**. Null yapılabilir uyarı bağlamı **devre dışı**.
  - Başvuru türündeki değişkenler, daha önceki sürümlerinde olduğu gibi, zorunluluvou 'lardır C#. Tüm null değer alabilirlik uyarıları devre dışı bırakıldı.

Ayrıca, aynı bağlamlarını projenizde her yerde ayarlamak için yönergeleri de kullanabilirsiniz:

- `#nullable enable`: Null yapılabilir ek açıklama bağlamını ve null yapılabilir uyarı bağlamını **etkin**olarak ayarlar.
- `#nullable disable`: Nullable ek açıklama bağlamını ve null yapılabilir uyarı bağlamını **devre dışı**olarak ayarlar.
- `#nullable restore`: Null yapılabilir ek açıklama bağlamını ve null yapılabilir uyarı bağlamını proje ayarlarına geri yükler.
- `#nullable disable warnings`: Null yapılabilir uyarı bağlamını **devre dışı**olarak ayarlayın.
- `#nullable enable warnings`: Null yapılabilir uyarı bağlamını **etkin**olarak ayarlayın.
- `#nullable restore warnings`: Null yapılabilir uyarı bağlamını proje ayarlarına geri yükler.
- `#nullable disable annotations`: Null yapılabilir ek açıklama bağlamını **devre dışı**olarak ayarlayın.
- `#nullable enable annotations`: Null yapılabilir ek açıklama bağlamını **etkin**olarak ayarlayın.
- `#nullable restore annotations`: Ek açıklama uyarı bağlamını proje ayarlarına geri yükler.

Varsayılan null atanabilir ek açıklaması ve uyarı bağlamları `disabled`şunlardır. Bu karar, mevcut kodunuzun değişiklik yapılmadan ve yeni bir uyarı oluşturmadan derlendiğini gösterir.

## <a name="nullable-annotation-context"></a>Null yapılabilir ek açıklama bağlamı

Derleyici, devre dışı bırakılmış bir null yapılabilir ek açıklama bağlamında aşağıdaki kuralları kullanır:

- Etkin olamayan başvuruları devre dışı bir bağlamda bildiremezsiniz.
- Tüm başvuru değişkenleri null 'a atanabilir.
- Başvuru türü değişkenine başvurulduğunu bir uyarı oluşturulmaz.
- Null-forverme işleci devre dışı bir bağlamda kullanılamaz.

Davranışı önceki sürümleriyle aynıdır C#.

Derleyici, etkinleştirilmiş bir null yapılabilir ek açıklama bağlamında aşağıdaki kuralları kullanır:

- Başvuru türündeki herhangi bir değişken **null atanamaz bir başvurudur**.
- Null olamayan herhangi bir başvuruya, güvenli bir şekilde başvurulmalıdır.
- Herhangi bir Nullable başvuru türü (değişken `?` bildiriminde bulunan tür öğesinden sonra belirtilen) null olabilir. Statik analiz, başvurunun başvurulduğunu null dışında bir değer olarak bilinmeyeceğini belirler. Aksi takdirde, derleyici sizi uyarır.
- Null yapılabilir bir başvurunun null olmadığını bildirmek için null-forverme işlecini kullanabilirsiniz.

Etkin bir null yapılabilir ek açıklama bağlamında, `?` başvuru türüne eklenen karakter **null yapılabilir bir başvuru türü**bildirir. İfadenin null olmadığını bildirmek için **null-forverme işleci** `!` bir ifadeye eklenebilir.

## <a name="nullable-warning-context"></a>Null yapılabilir uyarı bağlamı

Null yapılabilir uyarı bağlamı null yapılabilir ek açıklama bağlamından farklıdır. Yeni ek açıklamalar devre dışı bırakıldığında bile uyarılar etkinleştirilebilir. Derleyici, herhangi bir başvurunun **null durumunu** belirlemede statik akış analizini kullanır. Null *yapılabilir uyarı bağlamı* **devre dışı bırakılmadıysa**null durumu **null** ya da null **olabilir** . Derleyici **null**olduğunu tespit ettiğinizde bir başvuruya başvuru yaparsanız, derleyici sizi uyarır. Derleyici iki koşuldan birini belirleyemediği takdirde başvurunun durumu **null olabilir** :

1. Değişken, null olmayan bir değere kesin olarak atandı.
1. Değişken veya ifade, kendisine başvurulmadan önce null değere karşı denetlendi.

Derleyici, **null** yapılabilir uyarı bağlamı `enabled`olduğunda bir değişkene veya ifadeye, belki de null bir durumda her başvuru yaptığınızda uyarı oluşturur. Ayrıca, **null** olabilen ek açıklama bağlamı `enabled`olduğunda, null olamayan bir başvuruya veya ifadeye null olmayan bir başvuru türüne atandığında uyarılar üretilir.

## <a name="learn-more"></a>Daha fazla bilgi edinin

- [Taslak Nullable başvuru belirtimi](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Null yapılabilir başvurular öğreticisine giriş](tutorials/nullable-reference-types.md)
- [Var olan bir kod temelinin Nullable başvurulara geçirilmesi](tutorials/upgrade-to-nullable-references.md)

---
title: Boş değer atanabilir başvuru türleri
description: Bu makalede, 8,0 ' C# ye eklenen null yapılabilir başvuru türlerine genel bir bakış sunulmaktadır. Yeni ve mevcut projeler için özelliği, null başvuru özel durumlarına karşı nasıl güvenlik sağladığını öğreneceksiniz.
ms.technology: csharp-null-safety
ms.date: 02/19/2019
ms.openlocfilehash: ded7234ecb746ba03ba59505b7189272886f1cbf
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737828"
---
# <a name="nullable-reference-types"></a>Boş değer atanabilir başvuru türleri

C#8,0, başvuru türü değişkenlerinin özellikleri hakkında önemli deyimler etkinleştirmenizi sağlayan **null yapılabilir başvuru türleri** ve **null yapılamayan başvuru türleri** tanıtır:

- **Başvurunun null olması gerekir**. Değişkenlerin null olması beklenen durumlarda derleyici, bu değişkenlerin null olmadığını denetlemeden önce bu değişkenlere başvurmasının güvenli olmasını sağlayan kuralları zorlar:
  - Değişken null olmayan bir değere başlatılmalıdır.
  - Değişkene hiçbir şekilde `null` değeri atanamaz.
- **Başvuru null olabilir**. Değişkenler null olabilir, derleyici null bir başvuruyu doğru bir şekilde kontrol aldığınızdan emin olmak için farklı kurallar uygular:
  - Değişken yalnızca derleyici değerin null olmadığını garanti edemediğinde başvuru yapılabilir.
  - Bu değişkenler varsayılan `null` değeri ile başlatılabilir ve diğer kodda `null` değeri atanabilir.

Bu yeni özellik, tasarım amacını değişken bildiriminden belirlenemediği önceki sürümlerde C# başvuru değişkenlerinin işlenmesine göre önemli avantajlar sağlar. Derleyici, başvuru türleri için null başvuru özel durumlarına karşı güvenlik sağlamadı:

- **Başvuru null**olabilir. Bir başvuru türü null olarak başlatıldığında veya daha sonra null değeri atandığında hiçbir uyarı verilmez.
- **Başvurunun null olmadığı varsayılır**. Başvuru türleri başvurulduğunu derleyici hiçbir uyarı vermez. (Null olabilen başvurular sayesinde, null olabilen bir değişkene başvuru yaptığınızda Derleyici uyarıları yayınlar).

Null yapılabilir başvuru türleri eklenmesiyle, amacınızı daha net bir şekilde bildirebilirsiniz. `null` değeri, bir değişkenin bir değere başvurmadığından emin olmanın doğru yoludur. Bu özelliği, tüm `null` değerlerini kodınızdan kaldırmak için kullanmayın. Bunun yerine, amacınızı derleyiciye ve kodunuzu okuyan diğer geliştiricilere bildirmeniz gerekir. Amacınızı bildirerek, derleyici bu amaca tutarsız bir kod yazdığınızda size bildirir.

Null **yapılabilir bir başvuru türü** , [null yapılabilir değer türleriyle](language-reference/builtin-types/nullable-value-types.md)aynı söz dizimi kullanılarak belirtilmiştir: değişkenin türüne bir `?` eklenir. Örneğin, aşağıdaki değişken bildirimi null olabilen bir dize değişkenini temsil eder, `name`:

```csharp
string? name;
```

`?` tür adına eklenmemiş olan herhangi bir değişken **null yapılamayan bir başvuru türüdür**. Bu özellik, bu özelliği etkinleştirdiğinizde var olan koddaki tüm başvuru türü değişkenlerini içerir.

Derleyici, null olabilen bir başvurunun boş olmayan olarak bilinmesinin bilinmediğini anlamak için statik analizi kullanır. Null olduğunda, null olabilen bir başvuruya başvuru yaptığınızda derleyici sizi uyarır. Bir değişken adından sonra, `!` [null-forverme işlecini](language-reference/operators/null-forgiving.md) kullanarak bu davranışı geçersiz kılabilirsiniz. Örneğin, `name` değişkeni null olmadığını, ancak derleyici bir uyarı verir, derleyicinin analizini geçersiz kılmak için aşağıdaki kodu yazabilirsiniz:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Türlerin null olabilme sayısı

Herhangi bir başvuru türü, uyarıların ne zaman oluşturulacağını açıklayan dört adet *null*değer içerebilir:

- Null *atanabilir olmayan*: null bu türdeki değişkenlere atanamaz. Bu tür değişkenlerin, başvuru yapılmadan önce null olarak işaretli olması gerekmez.
- *Nullable*: null, bu türdeki değişkenlere atanabilir. Bu türdeki değişkenlerin başvurusunun kaldırılması, önce `null` denetlenmeksizin bir uyarıya neden olur.
- *Zorunluluvou*: bu,C# 8,0 öncesi durumundadır. Bu tür değişkenlere başvuru yapılmadan başvuru yapılabilir veya atanabilir.
- *Bilinmiyor*: Bu, genellikle kısıtlamaların, türün *null yapılabilir* veya *null değer*atanabilir olması gerektiğini bildirmeyecek tür parametreleri içindir.

Değişken bildirimindeki bir türün null olabilme değeri, değişkenin bildirildiği *null yapılabilir bağlam* tarafından denetlenir.

## <a name="nullable-contexts"></a>Null yapılabilir bağlamlar

Null yapılabilir bağlamlar, derleyicinin başvuru türü değişkenlerini nasıl yorumlayacağını öğrenmek için ayrıntılı denetimi etkinleştirir. Belirli bir kaynak çizginin **null yapılabilir ek açıklama bağlamı** etkin veya devre dışı. ÖncedenC# 8,0 derleyicisini, tüm kodunuzu devre dışı bırakılmış bir null yapılabilir bağlamda derleme olarak düşünebilirsiniz: herhangi bir başvuru türü null olabilir. **Null yapılabilir uyarılar bağlamı** da etkinleştirilebilir veya devre dışı bırakılabilir. Null yapılabilir uyarılar bağlamı, akış analizini kullanarak derleyici tarafından oluşturulan uyarıları belirtir.

*. Csproj* dosyanızdaki `Nullable` öğesi kullanılarak bir proje için Nullable ek açıklama bağlamı ve null yapılabilir uyarı bağlamı ayarlanabilir. Bu öğe, derleyicinin türlerin null olduğunu ve hangi uyarıların oluşturulduğunu nasıl yorumlayacağını yapılandırır. Geçerli ayarlar şunlardır:

- `enable`: null yapılabilir ek açıklama bağlamı **etkindir**. Null yapılabilir uyarı bağlamı **etkin**.
  - Örneğin, `string` olan bir başvuru türü değişkenleri null değer atanamaz.  Tüm null değer alabilirlik uyarıları etkin.
- `warnings`: Nullable ek açıklama bağlamı **devre dışı**. Null yapılabilir uyarı bağlamı **etkin**.
  - Bir başvuru türü değişkenleri, zorunluluvou. Tüm null değer alabilirlik uyarıları etkin.
- `annotations`: null yapılabilir ek açıklama bağlamı **etkindir**. Null yapılabilir uyarı bağlamı **devre dışı**.
  - Bir başvuru türü değişkenleri, örneğin dizesi null değer atanamaz. Tüm null değer alabilirlik uyarıları devre dışı bırakıldı.
- `disable`: Nullable ek açıklama bağlamı **devre dışı**. Null yapılabilir uyarı bağlamı **devre dışı**.
  - Başvuru türündeki değişkenler, daha önceki sürümlerinde olduğu gibi, zorunluluvou 'lardır C#. Tüm null değer alabilirlik uyarıları devre dışı bırakıldı.

**Örnek**:

```xml
<Nullable>enable</Nullable>
```

Ayrıca, aynı bağlamlarını projenizde her yerde ayarlamak için yönergeleri de kullanabilirsiniz:

- `#nullable enable`: null yapılabilir ek açıklama bağlamını ve null yapılabilir uyarı bağlamını **etkin**olarak ayarlar.
- `#nullable disable`: null yapılabilir ek açıklama bağlamını ve null yapılabilir uyarı bağlamını **devre dışı**olarak ayarlar.
- `#nullable restore`: null yapılabilir ek açıklama bağlamını ve null yapılabilir uyarı bağlamını proje ayarlarına geri yükler.
- `#nullable disable warnings`: null yapılabilir uyarı bağlamını **devre dışı**olarak ayarlayın.
- `#nullable enable warnings`: null yapılabilir uyarı bağlamını **etkin**olarak ayarlayın.
- `#nullable restore warnings`: proje ayarlarına Nullable uyarı bağlamını geri yükler.
- `#nullable disable annotations`: null yapılabilir ek açıklama bağlamını **devre dışı**olarak ayarlayın.
- `#nullable enable annotations`: null yapılabilir ek açıklama bağlamını **etkin**olarak ayarlayın.
- `#nullable restore annotations`: ek açıklama uyarı bağlamını proje ayarlarına geri yükler.

Varsayılan olarak, null yapılabilir ek açıklama ve uyarı bağlamları **devre dışıdır**. Bu, mevcut kodunuzun değişiklik yapılmadan ve yeni bir uyarı oluşturmadan derlendiğini gösterir.

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
- Herhangi bir null yapılabilir başvuru türü (değişken bildiriminde bulunan türden sonra `?` tarafından belirtilen) null olabilir. Statik analiz, başvurunun başvurulduğunu null dışında bir değer olarak bilinmeyeceğini belirler. Aksi takdirde, derleyici sizi uyarır.
- Null yapılabilir bir başvurunun null olmadığını bildirmek için null-forverme işlecini kullanabilirsiniz.

Etkin bir null yapılabilir ek açıklama bağlamında, bir başvuru türüne eklenen `?` karakteri **null olabilen bir başvuru türü**bildirir. İfadenin null olmadığını bildirmek için `!` **null-forverme işleci** bir ifadeye eklenebilir.

## <a name="nullable-warning-context"></a>Null yapılabilir uyarı bağlamı

Null yapılabilir uyarı bağlamı null yapılabilir ek açıklama bağlamından farklıdır. Yeni ek açıklamalar devre dışı bırakıldığında bile uyarılar etkinleştirilebilir. Derleyici, herhangi bir başvurunun **null durumunu** belirlemede statik akış analizini kullanır. Null *yapılabilir uyarı bağlamı* **devre dışı bırakılmadıysa**null durumu **null** ya da null **olabilir** . Derleyici **null**olduğunu tespit ettiğinizde bir başvuruya başvuru yaparsanız, derleyici sizi uyarır. Derleyici iki koşuldan birini belirleyemediği takdirde başvurunun durumu **null olabilir** :

1. Değişken, null olmayan bir değere kesin olarak atandı.
1. Değişken veya ifade, kendisine başvurulmadan önce null değere karşı denetlendi.

Null yapılabilir uyarı bağlamı etkin olduğunda, derleyici bir değişken veya ifadeye, **belki de null** bir durumda her başvuru yaptığınızda uyarılar oluşturur. Ayrıca, **null** olabilen bir tür veya ifade, etkin bir Nullable ek açıklama bağlamında null yapılamayan bir başvuru türüne atandığında uyarılar oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Taslak Nullable başvuru türleri belirtimi](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Null yapılabilir başvurular öğreticisine giriş](tutorials/nullable-reference-types.md)
- [Var olan bir kod temelinin Nullable başvurulara geçirilmesi](tutorials/upgrade-to-nullable-references.md)

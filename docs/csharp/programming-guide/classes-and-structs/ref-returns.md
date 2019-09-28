---
title: Ref dönüş değerleri ve ref YerellerC# (kılavuz)
description: Ref return ve ref yerel değerlerini tanımlama ve kullanma hakkında bilgi edinin
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: e23007deffea0f542d623be918cd1c61496d1362
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353891"
---
# <a name="ref-returns-and-ref-locals"></a>Ref dönüşler ve ref yerel ayarlar

7,0 ile C# başlayarak, C# başvuru dönüş değerlerini (Ref dönüşler) destekler. Bir başvuru dönüş değeri, bir yöntemin bir değer yerine bir değişkene geri dönmesi için bir başvuru döndürmesini sağlar. Çağıran, döndürülen değişkeni değere veya başvuruya göre döndürülmüş gibi kabul edebilir. Çağıran, başvuru yerel olarak adlandırılan döndürülen değere bir başvuru olan yeni bir değişken oluşturabilir.

## <a name="what-is-a-reference-return-value"></a>Başvuru dönüş değeri nedir?

Çoğu geliştirici, bir bağımsız değişkeni *başvuruya göre*çağrılan bir yönteme geçirmeyi öğrenmektir. Çağrılan yöntemin bağımsız değişken listesi, başvuruya göre geçirilmiş bir değişken içerir. Çağrılan yönteme göre değerinde yapılan tüm değişiklikler arayan tarafından izlenir. Bir *Başvuru dönüş değeri* , bir yöntemin bazı değişkene bir *başvuru* (veya diğer ad) döndürdüğü anlamına gelir. Bu değişkenin kapsamı yöntemi içermelidir. Bu değişkenin yaşam süresi yöntemin geri dönüşlerinin ötesinde genişlemelidir. Metodun dönüş değerindeki çağıran tarafından yapılan değişiklikler, yöntemi tarafından döndürülen değişkene yapılır.

Bir yöntemin bir *Başvuru dönüş değeri* döndürdüğünü bildirmek, yöntemin bir değişkene bir diğer ad döndürdüğünü gösterir. Tasarım amacı, genellikle çağıran kodun, diğer ad üzerinden bu değişkene, değiştirmek de dahil olmak üzere erişim sahibi olması gerekir. Başvuruya göre döndüren yöntemlerin dönüş türü `void` olamaz.

İfadede bir yöntemin başvuru dönüş değeri olarak döndürebilen bazı kısıtlamalar vardır. Sınırlamalar şunları içerir:

- Dönüş değeri, yönteminin yürütülmesini aşan bir yaşam süresine sahip olmalıdır. Diğer bir deyişle, bu, döndüren yöntemde yerel bir değişken olamaz. Bir sınıfın örneği veya statik alanı olabilir veya yöntemine geçirilen bir bağımsız değişken olabilir. Yerel bir değişken döndürme girişimi, "yerel ' obj" bir ref yerel olmadığından, "yerel ' obj ' başvuru ile döndürülemiyor."

- Dönüş değeri `null` sabit değeri olamaz. @No__t-0 döndüren derleyici hatası CS8156, "başvuruya göre döndürülmeyebilir çünkü bu bağlamda bir ifade kullanılamaz."

   Ref Return içeren bir yöntem, değeri şu anda null (örneklenmiş) değeri olan bir değişkene veya bir değer türü için null [yapılabilir değer türüne](../nullable-types/index.md) sahip bir diğer ad döndürebilir.

- Dönüş değeri bir sabit, bir numaralandırma üyesi, bir özellikten değere göre dönüş değeri veya `class` veya `struct` yöntemi olamaz. Bu kuralın ihlal edildiğinde derleyici hatası CS8156, "bir ifade başvuru ile döndürülmeyebilir çünkü bu bağlamda kullanılamaz."

Buna ek olarak, zaman uyumsuz metotlarda başvuru dönüş değerlerine izin verilmez. Zaman uyumsuz bir yöntem yürütmeyi bitmeden önce dönebilir, ancak dönüş değeri hala bilinmez.

## <a name="defining-a-ref-return-value"></a>Başvuru dönüş değeri tanımlama

*Başvuru dönüş değeri* döndüren bir yöntem aşağıdaki iki koşulu karşılamalıdır:

- Yöntem imzası, dönüş türünün önünde [ref](../../language-reference/keywords/ref.md) anahtar sözcüğünü içerir.
- Yöntem gövdesindeki her [dönüş](../../language-reference/keywords/return.md) ifadesinde, döndürülen örnek adının önünde [başvuru](../../language-reference/keywords/ref.md) anahtar sözcüğü bulunur.

Aşağıdaki örnek, bu koşulları karşılayan bir yöntemi gösterir ve `p` adlı `Person` nesnesine bir başvuru döndürür:

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Ref dönüş değeri kullanma

Ref dönüş değeri, çağrılan metodun kapsamındaki başka bir değişken için diğer addır. Ref Return öğesinin herhangi bir kullanımını, diğer ad olan değişkeni kullanarak yorumlayabilir.

- Değerini atadığınızda, diğer ad olan değişkene bir değer atarsınız.
- Değerini okurken, diğer adı değişkenin değerini Okuyorda olursunuz.
- *Başvuruya göre*geri döndürülürken, aynı değişkene bir diğer ad döndürürler.
- *Başvuruya göre*başka bir yönteme geçirirseniz, diğer ad olan değişkene bir başvuru geçirolursunuz.
- Bir [ref yerel](#ref-locals) diğer adı yaptığınızda aynı değişkene yeni bir diğer ad yaparsınız.

## <a name="ref-locals"></a>Başvuru yerelleri

@No__t-0 yönteminin bir ref Return olarak bildirildiği varsayılır:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Değere göre atama bir değişkenin değerini okur ve bunu yeni bir değişkene atar:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Yukarıdaki atama `p` ' i yerel bir değişken olarak bildirir. İlk değeri `GetContactInformation` tarafından döndürülen değerin okunmasından kopyalanır. @No__t-0 ' a yönelik sonraki atamalar `GetContactInformation` tarafından döndürülen değişkenin değerini değiştirmez. @No__t-0 değişkeni artık döndürülen değişken için bir diğer ad değil.

Diğer adı özgün değerine kopyalamak için bir *ref yerel* değişkeni bildirirsiniz. Aşağıdaki atamada, `p` `GetContactInformation` ' den döndürülen değişkenin diğer adıdır.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

@No__t-0 ' ın sonraki kullanımı, bu değişken için `p` bir diğer ad olduğundan, `GetContactInformation` tarafından döndürülen değişkeni kullanmakla aynıdır. @No__t-0 ' da yapılan değişiklikler ayrıca `GetContactInformation` ' den döndürülen değişkeni de değiştirir.

@No__t-0 anahtar sözcüğü, hem yerel değişken bildiriminden önce *hem* de yöntem çağrısından önce kullanılır. 

Başvuruya göre bir değere aynı şekilde erişebilirsiniz. Bazı durumlarda, başvuruya göre değere erişmek, potansiyel olarak pahalı bir kopyalama işlemini önleyerek performansı artırır. Örneğin, aşağıdaki ifade bir değere başvurmak için kullanılan bir başvuru yerel değerini nasıl tanımlayacağınızı gösterir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

@No__t-0 anahtar sözcüğü, hem yerel *değişken bildiriminden önce hem de* ikinci örnekteki değerden önce kullanılır. Değişken bildiriminde hem `ref` anahtar kelimelerin hem de atamanın dahil edilmemesi, "derleyici hatası CS8172," bir değere sahip bir başvuruya göre değişkeni başlatamıyor. " 

C# 7,3 ' den önce, ref yerel değişkenleri, başlatıldıktan sonra farklı depolamaya başvuracak şekilde yeniden atanamadı. Bu kısıtlama kaldırılmıştır. Aşağıdaki örnekte bir yeniden atama gösterilmektedir:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Ref yerel değişkenlerinin, bildirildiği zaman yine de başlatılmış olması gerekir.

## <a name="ref-returns-and-ref-locals-an-example"></a>Ref, ve ref yerelleri: bir örnek

Aşağıdaki örnek, bir tamsayı değerleri dizisini depolayan `NumberStore` sınıfını tanımlar. @No__t-0 yöntemi, bir bağımsız değişken olarak geçirilen sayıdan daha büyük veya ona eşit olan ilk sayı başvuruya göre döndürülür. Bir sayı bağımsız değişkenden büyük veya ona eşit değilse, yöntem 0 dizininden sayı döndürür. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Aşağıdaki örnek, 16 ' dan büyük veya buna eşit ilk değeri almak için `NumberStore.FindNumber` yöntemini çağırır. Çağıran, yöntemi tarafından döndürülen değeri iki katına çıkarır. Örneğin çıktısı, `NumberStore` örneğinin dizi öğelerinin değerinde yansıtılan değişikliği gösterir.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Başvuru dönüş değerleri için destek olmadan, bu tür bir işlem, dizi öğesinin dizinini değeriyle birlikte döndürerek gerçekleştirilir. Çağıran, bu dizini kullanarak değeri ayrı bir yöntem çağrısında değiştirebilir. Bununla birlikte, çağıran dizine erişim için de değişiklik yapabilir ve muhtemelen diğer dizi değerlerini değiştirebilir.  

Aşağıdaki örnek, `FindNumber` yönteminin, ref yerel yeniden atamasını kullanmak üzere C# 7,3 sonrasında nasıl yeniden yazılabilir olduğunu gösterir:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Bu ikinci sürüm, aranan sayının dizinin sonuna yakın olduğu senaryolarda daha uzun dizileriyle daha etkilidir.

## <a name="see-also"></a>Ayrıca bkz.

- [ref anahtar sözcüğü](../../language-reference/keywords/ref.md)
- [Güvenli verimli kod yazma](../../write-safe-efficient-code.md)

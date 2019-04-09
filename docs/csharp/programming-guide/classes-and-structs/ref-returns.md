---
title: Başvuru dönüş değerleri ve ref yerel ayarlar (C# Kılavuzu)
description: Başvuru dönüş ve ref yerel değerlerine tanımlanacağını ve kullanılacağını öğrenin
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: fcac162f63438b6cbe54908383467d4b0f227c39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081856"
---
# <a name="ref-returns-and-ref-locals"></a>Ref dönüşler ve ref yerel ayarlar

C# 7.0 ile başlayarak, C# (ref döndürür) başvuru dönüş değerleri destekler. Başvuru dönüş değeri bir değer yerine bir değişken bir başvuru arayana geri döndürmek bir yöntem sağlar. Çağırana döndürülen değişkeni değere veya başvuruya göre döndürülmedi yokmuş gibi kabul seçebilirsiniz. Arayan, döndürülen değer, bir ref yerel olarak adlandırılan bir başvuru kendisi yeni bir değişken oluşturabilirsiniz.

## <a name="what-is-a-reference-return-value"></a>Başvuru dönüş değeri nedir?

Çoğu geliştirici için çağrılan bir yöntem bağımsız değişken geçirme ile ilgili bilgi sahibi olduğunuz *başvuruya göre*. Çağrılan yöntemin bağımsız değişken listesinin bir değişken başvuruyla geçirildi içerir. Tarafından çağrılan yöntem değerine yapılan tüm değişiklikler arayan tarafından gözlenmiştir. A *başvuru dönüş değeri* döndüren bir yöntemi gösterir bir *başvuru* (veya diğer ad) bazı değişken. Bu değişkenin kapsamı yöntemi eklemeniz gerekir. Değişkenin ömrü yöntemi iadesini genişletmeniz gerekir. Yöntem tarafından döndürülen değişkeni yöntemin dönüş değeri çağıran tarafından yapılan değişiklikler yapılır.

Döndüren bir yöntemi bildirmek bir *başvuru dönüş değeri* yöntemi bir değişkene bir diğer ad verdiğini gösterir. Tasarım amacı genellikle çağıran kod değişken değiştirmek için de dahil olmak üzere diğer ad üzerinden erişim gerektiğidir. Yöntemleri başvuruya göre dönüş türü olamaz takip eden `void`.

Başvuru dönüş değeri olarak bir yöntem döndüren bir ifade üzerinde bazı kısıtlamalar vardır. Kısıtlamaları şunlardır:

- Dönüş değeri, yöntemin yürütülmesi genişletir bir yaşam süresi olması gerekir. Diğer bir deyişle, bu yöntemin döndürdüğü yerel bir değişkende olamaz. Bu yönteme geçirilen bağımsız değişken olabilir veya bir örnek veya bir sınıfın statik alanı olabilir. Derleyici Hatası CS8168, yerel bir değişken oluşturur dönüş çalışılırken "döndüremiyor yerel 'obj' başvuruya göre bir ref yerel öğesi olmadığından."

- Dönüş değeri, değişmez değer olamaz `null`. Döndüren `null` CS8156 "bir ifade başvuru ile döndürülemez olduğundan bu bağlamda kullanılamaz.", derleyici hatası oluşturur

   Bir yöntem dönüş ref ile bir diğer ad değeri şu anda null (örneklenmemiş) değeri bir değişkene döndürebilir veya [boş değer atanabilir tür](../nullable-types/index.md) için bir değer türü.
 
- Dönüş değeri bir sabit bir numaralandırma üyesine olamaz, değer tarafından dönen değer bir özelliği veya yöntemi bir `class` veya `struct`. Derleyici Hatası CS8156 "bir ifade başvuru ile döndürülemez olduğundan bu bağlamda kullanılamaz.", bu kuralın ihlali oluşturur

Ayrıca, başvuru döndürmek zaman uyumsuz yöntemlerde değerlere izin verilmez. Zaman uyumsuz bir yöntemin dönüş değerini hala bilinmiyor ancak yürütme bitmeden önce döndürebilir.
 
## <a name="defining-a-ref-return-value"></a>Başvuru dönüş değeri tanımlama

Döndüren bir yöntem bir *başvuru dönüş değeri* aşağıdaki iki koşulları karşılaması gerekir:

- Yöntem imzası içerir [ref](../../language-reference/keywords/ref.md) önünde dönüş türü anahtar sözcüğü.
- Her [dönüş](../../language-reference/keywords/return.md) deyimi yöntemin gövdesinde [ref](../../language-reference/keywords/ref.md) döndürülen örneğinin adını önünde anahtar sözcüğü.

Aşağıdaki örnek, bir başvuru döndürür ve koşullarını bu karşılayan bir yöntemi gösterir. bir `Person` adlı nesne `p`:

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Başvuru dönüş değeri kullanma

Başvuru dönüş değeri çağrılan yöntemin kapsamında başka bir değişkene bir diğer ad:. Yorumlaması için tüm dönüş başvurusuna sahip değişkeni kullanarak, diğer adları kullanın:

- Değişkene bir değer atadığınız değeri atadığınızda, bu diğer adları.
- Değerlerini okumak, değişkenin değerini okuyorsanız, diğer adları.
- Bu dönüş yaparsa *başvuruya göre*, bir diğer ad, aynı değişkene döndürüyor.
- Başka bir yönteme geçirdiğinizde *başvuruya göre*, bir değişken başvurusu'nu geçirme, diğer adları.
- Yaptığınızda bir [ref yerel](#ref-locals) aynı değişkene yeni bir diğer ad yaptığınız diğer ad.

## <a name="ref-locals"></a>Ref yerel ayarlar

Varsayar `GetContactInformation` yöntemi bildirilen bir başvuru dönüş:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Bir değere göre ataması, bir değişkenin değerini okur ve yeni bir değişkene atar:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Yukarıdaki atamanın bildirir `p` yerel bir değişken olarak. İlk değeri tarafından döndürülen değer okumasını kopyalanır `GetContactInformation`. Gelecekteki atamaların `p` tarafından döndürülen değişkenin değerini değiştirmez `GetContactInformation`. Değişken `p` artık döndürülen değişkenine diğer ad değil.

Bildirdiğiniz bir *ref yerel* değişken özgün değere diğer kopyalamak için. Aşağıdaki atama `p` döndürüldüğü değişkeni için bir diğer addır `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Sonraki kullanımını `p` tarafından döndürülen değişkenini kullanarak aynı `GetContactInformation` çünkü `p` Bu değişken için bir diğer addır. Değişikliklerini `p` döndürüldüğü değişkeni de değiştirmeniz `GetContactInformation`.

`ref` Anahtar sözcüğü kullanılır yerel değişken bildiriminde önce her ikisini de *ve* yöntemi çağırmadan önce. 

Başvuruya göre bir değer aynı şekilde erişebilirsiniz. Bazı durumlarda, bir değere Başvuruya göre erişmeden performansı büyük olasılıkla pahalı kopyalama işlemi tarafından artırır. Örneğin, aşağıdaki ifade bir değer başvurmak için kullanılan bir ref yerel değer nasıl tanımlayabilirsiniz gösterir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

`ref` Anahtar sözcüğü kullanılır yerel değişken bildiriminde önce her ikisini de *ve* değerinden ikinci örnekte önce. Her ikisi de içerecek şekilde hatası `ref` değişken bildirimi anahtar sözcükleri ve derleyici hatası CS8172, her iki örnek sonucu atama "başlatamıyor bir başvuruya göre değişken değeri." 

C# 7.3 önce ref yerel değişkenleri başlatıldıktan sonra farklı bir depolama alanına başvurmak için başkasına alınamadı. Bu kısıtlama kaldırıldı. Aşağıdaki örnek, bir yeniden atama gösterir:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Bunlar bildirildiğinde ref yerel değişkenleri hala başlatılması gerekir.

## <a name="ref-returns-and-ref-locals-an-example"></a>Ref dönüşler ve ref yerel ayarlar: örneği

Aşağıdaki örnekte tanımlayan bir `NumberStore` tamsayı değerleri dizisi depolayan sınıf. `FindNumber` Yöntemi başvuruya göre büyük veya ona eşit bir bağımsız değişken olarak geçirilen ilk sayı döndürür. Büyüktür veya eşittir bağımsız değişken numarası yok ise, yöntem dizin 0 döndürür. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Aşağıdaki örnek çağrıları `NumberStore.FindNumber` büyüktür veya eşittir 16 ilk değerini almak için yöntemi. Çağıran yöntemi tarafından döndürülen değer ardından iki katına çıkar. Değişikliğin dizi öğelerinin değerinde yansıtıldığını örneğin çıktısında gösterildiği `NumberStore` örneği.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Başvuru dönüş değerleri için desteği olmadan değerini birlikte dizi öğenin dizinini döndüren ve bu tür bir işlem gerçekleştirilir. Çağıran, ayrı yöntem çağrısında değerini değiştirmek için bu dizini sonra kullanabilirsiniz. Ancak, çağırana erişmek ve büyük olasılıkla diğer dizi değerlerini değiştirmek için dizini değiştirebilirsiniz.  

Aşağıdaki örnekte gösterildiği nasıl `FindNumber` yöntemi C# ref yerel yeniden atama kullanılacak 7.3 sonra yeniden:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Bu ikinci sürüm numarasını Aranan dizinin sonuna yakın olduğu senaryolarda uzun dizileri ile daha verimli olur.

## <a name="see-also"></a>Ayrıca bkz.

- [ref anahtar sözcüğü](../../language-reference/keywords/ref.md)
- [Güvenli verimli kod yazma](../../write-safe-efficient-code.md)

---
title: Ref iade değerleri ve ref yerlileri (C# Guide)
description: Ref return ve ref local değerlerini nasıl tanımlayıp kullanacağınızı öğrenin
ms.date: 04/04/2018
ms.openlocfilehash: 87a9538db60d69062f0fb48ed9683a9d4f972b91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170079"
---
# <a name="ref-returns-and-ref-locals"></a>Ref dönüşler ve ref yerel ayarlar

C# 7.0 ile başlayarak, C# referans iade değerlerini (ref döner) destekler. Başvuru iade değeri, bir yöntemin bir başvurucuzun bir değer yerine bir değişkene geri dönmesini sağlar. Arayan daha sonra döndürülen değişkeni değer veya başvuru yla döndürülmüş gibi ele almayı seçebilir. Arayan, döndürülen değere bir başvuru olan ve ref yerel olarak adlandırılan yeni bir değişken oluşturabilir.

## <a name="what-is-a-reference-return-value"></a>Referans iade değeri nedir?

Çoğu geliştirici, bir bağımsız değişkeni *başvuru yla*çağrılan yönteme geçirmeye aşinadır. Çağrılan yöntemin bağımsız değişken listesi, başvuru tarafından geçirilen bir değişken içerir. Çağrılan yöntemle değerinde yapılan değişiklikler arayan tarafından gözlenir. *Başvuru iade değeri,* yöntemin bazı değişkenlere *bir başvuru* (veya diğer ad) döndürdüğü anlamına gelir. Bu değişkenin kapsamı yöntemi içermelidir. Bu değişkenin ömrü yöntemin geri dönüşünden öteye uzanmalıdır. Arayanın yöntemin geri dönüş değerinde yaptığı değişiklikler, yöntem tarafından döndürülen değişkene yapılır.

Bir yöntemin bir *başvuru iade değeri* döndürüğünün beyan ı, yöntemin bir diğer adı bir değişkene döndürüğünu gösterir. Tasarım amacı genellikle arama kodunun bu değişkene diğer ad aracılığıyla erişmesi gerektiğidir. Başvuruyla dönen yöntemlerin return türüne `void`sahip olamamayacağı izsini izler.

Bir yöntemin başvuru iade değeri olarak döndürülebileceği ifadeüzerinde bazı kısıtlamalar vardır. Kısıtlamalar şunlardır:

- İade değerinin, yöntemin yürütülmesinin ötesine uzanan bir ömrü olmalıdır. Başka bir deyişle, döndüren yöntemde yerel bir değişken olamaz. Bir sınıfın örnek veya statik alanı olabilir veya yönteme geçirilen bir bağımsız değişken olabilir. Yerel bir değişkeni döndürmeye çalışırken derleyici hatası CS8168 oluşturur, "Ref local olmadığı için başvuru yla yerel 'obj' döndüremez."

- İade değeri gerçek `null`olamaz. Returning `null` derleyici hatası CS8156 oluşturur, "Bir ifade başvuru yla döndürülemeyebilir, çünkü bu bağlamda kullanılamaz."

   Ref iadesi olan bir yöntem, değeri şu anda null (instantiated) değeri olan bir değişkene veya bir değer türü için [nullable değer türüne](../../language-reference/builtin-types/nullable-value-types.md) bir diğer ad döndürebilir.

- İade değeri sabit, numaralandırma üyesi, bir özellikten gelen yan değer dönüş değeri veya `class` bir `struct`veya . Bu kuralı ihlal etmek derleyici hatası CS8156 oluşturur, "Bir ifade başvuruyla döndürülemeyebilir, çünkü bu bağlamda kullanılamaz."

Buna ek olarak, async yöntemleri referans dönüş değerleri izin verilmez. Adsız bir yöntem yürütme tamamlanmadan önce dönebilir, ancak geri dönüş değeri hala bilinmiyor.

## <a name="defining-a-ref-return-value"></a>Ref iade değerinin tanımlanması

*Başvuru iade değerini* döndüren bir yöntem aşağıdaki iki koşulu karşılamalıdır:

- Yöntem imzası, iade türünün önündeki [ref](../../language-reference/keywords/ref.md) anahtar sözcüğüiçerir.
- Yöntem gövdesindeki her [iade](../../language-reference/keywords/return.md) deyimi, döndürülen örneğin adının önündeki [ref](../../language-reference/keywords/ref.md) anahtar sözcüğüiçerir.

Aşağıdaki örnek, bu koşulları karşılayan ve bir başvuruyu adlı `Person` `p`nesneye döndüren bir yöntem gösterir:

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Ref iade değerini tüketme

Ref dönüş değeri, çağrılan yöntemin kapsamındaki başka bir değişkenin diğer adıdır. Ref iadesinin herhangi bir kullanımını diğer adlar değişkenini kullanarak yorumlayabilirsiniz:

- Değerini atadığınızda, diğer adlarına bir değer atarsınız.
- Değerini okuduğunuzda, diğer adlarının değişkeninin değerini okuyorsunuz.
- *Başvuruyla*döndürerseniz, aynı değişkene bir diğer ad döndürebilirsin.
- *Başvuru yla*başka bir yönteme geçerseniz, diğer adlarına bir başvuru aktarırsınız.
- Bir ref [yerel](#ref-locals) takma ad yaptığınızda, aynı değişkene yeni bir takma ad yaparsınız.

## <a name="ref-locals"></a>Ref yerlileri

Yöntemin `GetContactInformation` ref iadesi olarak beyan edildiği varsayalım:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Bir yan değer ataması bir değişkenin değerini okur ve onu yeni bir değişkene atar:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Önceki atama yerel `p` değişken olarak bildirir. İlk değeri, döndürülen değerin okunmasından `GetContactInformation`kopyalanır. Gelecekteki atamalar `p` tarafından döndürülen değişkenin değerini `GetContactInformation`değiştirmez. Değişken `p` artık döndürülen değişkenin diğer adı değildir.

Diğer adı özgün değere kopyalamak için *ref yerel* değişkeni beyan esiniz. Aşağıdaki atamada, `p` 'den `GetContactInformation`döndürülen değişkenin diğer adıdır.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Sonraki `p` kullanım, bu değişkenin diğer `GetContactInformation` adı `p` olduğu için döndürülen değişkeni kullanmakla aynıdır. Döndürülen `p` değişkeni değiştirmek `GetContactInformation`için yapılan değişiklikler.

`ref` Anahtar kelime hem yerel değişken bildiriminden önce *hem* de yöntem çağrısından önce kullanılır.

Bir değere aynı şekilde başvuru yla erişebilirsiniz. Bazı durumlarda, bir değere referans la erişmek, pahalı olabilecek bir kopyalama işleminden kaçınarak performansı artırır. Örneğin, aşağıdaki deyim, bir değere başvurmak için kullanılan bir ref yerel değerini nasıl tanımlayabileceğini gösterir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

`ref` Anahtar kelime hem yerel değişken bildiriminden önce *hem* de ikinci örnekteki değerden önce kullanılır. Değişken bildirimi `ref` ve atama her iki örnekte her iki anahtar kelime dahil edilmemesi derleyici hatası CS8172 sonuçlanır, "Bir değer ile bir by-referans değişken başlatılması olamaz."

C# 7.3'ten önce, ref yerel değişkenleri baş harfe batandıktan sonra farklı depolama alanına başvurmak üzere yeniden atanamadı. Bu kısıtlama kaldırıldı. Aşağıdaki örnekte yeniden atama gösterilmektedir:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Ref yerel değişkenler, beyan edildiklerinde hala başharfe alınmalıdır.

## <a name="ref-returns-and-ref-locals-an-example"></a>Ref döner ve ref yerliler: bir örnek

Aşağıdaki örnek, bir `NumberStore` tamsayı değerleri dizisini depolayan bir sınıf tanımlar. Yöntem, `FindNumber` bağımsız değişken olarak geçirilen sayıdan daha büyük veya eşit olan ilk sayıyı referans la döndürür. Hiçbir sayı bağımsız değişkenden büyük veya eşit değilse, yöntem dizin 0'daki sayıyı döndürür.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Aşağıdaki örnek, `NumberStore.FindNumber` 16'dan büyük veya eşit olan ilk değeri almak için yöntemi çağırır. Arayan daha sonra yöntem tarafından döndürülen değeri iki katına çıkar. Örnekteki çıktı, `NumberStore` örneğin dizi öğelerinin değerine yansıyan değişikliği gösterir.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Referans döndürücü değerler desteği olmadan, bu tür bir işlem değeri ile birlikte dizi öğesidizini döndürülerek gerçekleştirilir. Arayan daha sonra ayrı bir yöntem çağrısında değeri değiştirmek için bu dizini kullanabilirsiniz. Ancak, arayan dizin erişmek ve büyük olasılıkla diğer dizi değerlerini değiştirmek için de değiştirebilirsiniz.  

Aşağıdaki örnek, yöntemin `FindNumber` ref yerel yeniden atamasını kullanmak için C# 7.3'ten sonra nasıl yeniden yazılabileceğini gösterir:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Bu ikinci sürüm, aranan sayının dizinin sonuna daha yakın olduğu senaryolarda daha uzun dizilerle daha verimlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [ref anahtar kelime](../../language-reference/keywords/ref.md)
- [Güvenli verimli kod yazın](../../write-safe-efficient-code.md)

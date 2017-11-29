---
title: "Ref dönüş değerleri ve ref Yereller (C# Kılavuzu)"
description: "Ref dönüş ve ref yerel değerleri tanımlayın ve nasıl kullanılacağını öğrenin"
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 18cf7a4b-29f0-4b14-85b8-80af754aabd8
ms.openlocfilehash: 1d8fb092b578602b5d4f791a3fd14f47dfae1ba6
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="ref-returns-and-ref-locals"></a>Ref döndürür ve ref Yereller

C# 7 ile başlayan, C# başvurusu dönüş değerleri (başvuru dönüşleri) destekler. Bir başvuru dönüş değeri bir değer yerine bir nesne başvurusu bir çağırana geri dönmek tek bir yöntem sağlar. Arayan değere veya başvuruya göre döndürülmedi gibi döndürülen döndürülen nesne kabul seçebilirsiniz. Yerine yerel bir ref değerdir çağıran bir başvuru olarak işleme başvuruya göre bir değer döndürdü.

## <a name="what-is-a-reference-return-value"></a>Bir başvuru dönüş değeri nedir?

Çoğu geliştirici çağrılan yöntemi için bağımsız değişken geçirme ile bilginiz *başvuruya göre*. Çağrılan yöntemin bağımsız değişken listesi başvuruya göre geçirilen bir değer ve değerine çağrılan yöntemi tarafından yapılan değişiklikleri içerir çağırana döndürülen. A *başvuru dönüş değeri* tersidir:

- Çağrılan yöntemin dönüş değeri, bağımsız değişken kendisine geçirilen yerine başvurusudur.

- Çağrılan yöntemin yerine çağıran yöntemi tarafından döndürülen değer değiştirebilirsiniz.

- Nesne durumda üzerinde çağıran yansıtılır değişikliklerin yerine bağımsız değişkenin, yöntemin dönüş değeri çağıran tarafından yapılan değişiklikler, yöntemi çağrıldı nesne durumda yansıtılır.

Başvuru dönüş değerleri daha küçük kod üretmek yanı çağırana ilgi yalnızca tek tek veri öğeleri, bir dizi öğesi gibi göstermek bir nesne izin. Bu, çağıran nesnenin durumu yanlışlıkla değiştirecek olasılığını azaltır.

Bir yöntem başvuru dönüş değeri olarak döndürebilir değeri bazı kısıtlamalar vardır. Bu güncelleştirmeler şunlardır:

- Dönüş değeri olamaz `void`. Bir yöntemi tanımlamak çalışan bir `void` başvuru dönüş değeri derleyici hatası CS1547 oluşturur, "Anahtar sözcüğü 'void' Bu bağlamda kullanılamaz."
 
- Dönüş değeri döndürdüğü yöntemi yerel bir değişkende olamaz; döndürdüğü yöntemi dışında bir kapsamı olmalıdır. Bu yönteme geçirilen bağımsız değişken olabilir veya bir örneği veya sınıfının statik alanı olabilir. Derleyici Hatası CS8168, yerel bir değişken oluşturur dönüş çalışılırken "döndüremiyor yerel 'obj' başvuruya göre yerel bir ref olmadığından."

- Dönüş değeri olamaz bir `null`. Döndürülecek çalışırken `null` derleyici hatası "bir ifade başvuruya göre döndürülemez olduğundan bu bağlamda kullanılamaz." CS8156 oluşturur

   Ref dönüş yöntemiyle bir null değer döndürmesi gerekiyorsa, bir başvuru türü null (örneklendirilmemiş) değerini ya da döndürebilir ya da bir [boş değer atanabilir tür](../nullable-types/index.md) değer türü.
 
- Dönüş değeri bir sabit, bir numaralandırma üyesi veya bir özelliği olamaz bir `class` veya `struct`. Derleyici Hatası CS8156 "bir ifade başvuruya göre döndürülemez olduğundan bu bağlamda kullanılamaz.", bunlar döndürülecek çalışırken oluşturur

Dönüş değerini bilinmeyen hala durumdayken yürütme bitmeden önce zaman uyumsuz bir yöntem döndürebilir olduğundan, ayrıca, başvuru dönüş değerleri zaman uyumsuz yöntemleri izin verilmez.
 
## <a name="defining-a-ref-return-value"></a>Ref dönüş değeri tanımlama

Ref dönüş değeri ekleyerek tanımlarsınız [ref](../../language-reference/keywords/ref.md) yöntem imzası dönüş türü için anahtar sözcüğü. Örneğin, aşağıdaki imzası belirten `GetContactInformation` özelliği bir başvuru döndürür bir `Person` çağıran nesneye:

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

Ayrıca, nesnenin adını döndürülen her tarafından [dönmek](../../language-reference/keywords/return.md) yöntem gövdesi deyiminde öncesinde, tarafından [ref](../../language-reference/keywords/ref.md) anahtar sözcüğü. Örneğin, aşağıdaki `return` deyiminin döndüreceği bir `Person` adlı nesne `p` başvuruya göre:

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>Ref dönüş değeri kullanma

Çağıran bir ref dönüş değeri iki yoldan biriyle işleyebilir:

- Değere göre bir yönteminden döndürülen sıradan bir değer. Çağıran, dönüş değeri bir başvuru dönüş değeri olduğunu göz ardı etmeyi seçebilir. Bu durumda, yöntem çağrısı tarafından döndürülen değer yapılan değişiklikler çağrılan türü durumda yansıtılmaz. Döndürülen değeri bir değer türü ise, yöntem çağrısı tarafından döndürülen değer yapılan değişiklikler çağrılan türü durumda yansıtılmaz.

- Bir başvuru olarak değerini döndürür. Arayan için başvuru dönüş değeri olarak atanır değişkeni tanımlamanız gerekir bir [ref yerel](#ref-local), ve yöntem çağrısı tarafından döndürülen değer değişiklikleri çağrılan türü durumda yansıtılır. 

## <a name="ref-locals"></a>Ref Yereller

Başvuru dönüş değeri bir başvuru olarak işlemek için arayan bir değere bildirmelidir bir *ref yerel* kullanarak `ref` anahtar sözcüğü. Örneğin tarafından döndürülen değer, `Person.GetContactInfomation` yöntemi bir değer yerine bir başvuru olarak kullanılması, yöntem çağrısı gibi görünür:

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Unutmayın `ref` anahtar sözcüğü kullanılır hem yerel değişken bildirimi önce *ve* yöntemi çağırmadan önce. Her ikisi de dahil etmek için hata `ref` Değişken bildiriminde anahtar sözcükleri ve atama sonuçları derleyici hatası CS8172, "başlatamıyor bir başvuru tarafından değere sahip bir değişken." 
 
Sonraki değişiklikler `Person` yöntemi tarafından döndürülen nesne yansıtılır `contacts` nesnesi.

Varsa `p` ref yerel kullanarak tanımlı değil `ref` anahtar sözcüğü, yapılan değişiklikleri `p` çağıran tarafından yansıtılmaz `contacts` nesnesi.
 
## <a name="ref-returns-and-ref-locals-an-example"></a>Ref döndürür ve ref Yereller: örneği

Aşağıdaki örnek tanımlayan bir `NumberStore` tamsayı değerleri dizisi depolayan sınıf. `FindNumber` Yöntemi büyük veya eşit bir bağımsız değişken olarak geçirilen ilk sayı başvuruya göre döndürür. Büyük veya ona eşit bağımsız değişkeni için herhangi bir sayı ise, yöntem dizin 0 döndürür. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

Aşağıdaki örnek çağrıları `NumberStore.FindNumber` 16 eşit veya daha büyük olan ilk değer alma yöntemi. Arayan yöntemi tarafından döndürülen değer sonra iki katına çıkar. Örneğin çıktısını gösterildiği gibi bu değişikliği dizi öğelerinin değeri yansıtılır `NumberStore` örneği.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

Başvuru dönüş değerleri desteği, böyle bir işlem dizin değerini birlikte dizi öğesinin döndürerek genellikle gerçekleştirilir. Çağıran, ayrı bir yöntem çağrısı değeri değiştirmek için bu dizini sonra kullanabilirsiniz. Ancak, çağıran erişmek ve büyük olasılıkla diğer dizi değerlerini değiştirmek için dizini de değiştirebilirsiniz.  
 
## <a name="see-also"></a>Ayrıca bkz.

[ref anahtar sözcüğü](../../language-reference/keywords/ref.md)

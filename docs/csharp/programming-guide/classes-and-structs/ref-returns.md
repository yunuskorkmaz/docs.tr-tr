---
title: Ref dönüş değerleri ve ref Yereller (C# Kılavuzu)
description: Ref dönüş ve ref yerel değerleri tanımlayın ve nasıl kullanılacağını öğrenin
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: e749b9c9309a4b1a737a0c1d0b5e1cfe5748114a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ref-returns-and-ref-locals"></a>Ref döndürür ve ref Yereller

C# 7. 0'dan başlayarak, C# başvurusu dönüş değerleri (başvuru dönüşleri) destekler. Bir başvuru dönüş değeri bir değer yerine bir değişken başvurusu çağırana geri dönmek tek bir yöntem sağlar. Çağıran, daha sonra döndürülen değişkeni değere veya başvuruya göre döndürülmedi sanki işlemek seçebilirsiniz. Çağıran bir ref yerel olarak adlandırılan döndürülen değer, başvuru kendisi yeni bir değişken oluşturabilirsiniz.

## <a name="what-is-a-reference-return-value"></a>Bir başvuru dönüş değeri nedir?

Çoğu geliştirici çağrılan yöntemi için bağımsız değişken geçirme ile bilginiz *başvuruya göre*. Çağrılan yöntemin bağımsız değişken listesi başvuruya göre geçirilen bir değişken içerir. Çağrılan yöntemi tarafından değerine yapılan değişiklikler, çağıran tarafından uyulması gereken. A *başvuru dönüş değeri* yöntemi döndürür anlamına gelir bir *başvuru* (veya diğer ad) bazı değişkenine. Bu değişkenin kapsamı yöntemi eklemeniz gerekir. Bu değişkenin ömrü yöntemin dönüş genişletmeniz gerekir. Yöntemin dönüş değeri çağıran tarafından yapılan değişiklikler yöntemi tarafından döndürülen değişkeni yapılır.

Bir yöntem döndüren bildirme bir *başvuru dönüş değeri* yöntemi bir değişkene bir diğer ad döndürdüğünü gösterir. Tasarım hedefi çağıran kodu değişken değiştirmek için de dahil olmak üzere diğer ad üzerinden erişimi olması gerektiğini görülür. Başvuruya göre döndüren yöntemler dönüş türüne sahip olamaz izleyen `void`.

Bir yöntem başvuru dönüş değeri olarak döndürebilir ifade bazı kısıtlamalar vardır. Sınırlamaları içerir:

- Dönüş değeri yönteminin yürütülmesi genişleten bir yaşam süresi olması gerekir. Diğer bir deyişle, onu döndüren yöntemi yerel bir değişkende olamaz. Bu yönteme geçirilen bağımsız değişken olabilir veya bir örneği veya sınıfının statik alanı olabilir. Derleyici Hatası CS8168, yerel bir değişken oluşturur dönüş çalışılırken "döndüremiyor yerel 'obj' başvuruya göre yerel bir ref olmadığından."

- Dönüş değeri sabit olamaz `null`. Döndürme `null` derleyici hatası "bir ifade başvuruya göre döndürülemez olduğundan bu bağlamda kullanılamaz." CS8156 oluşturur

   Ref dönüş yöntemiyle bir diğer ad değeri şu anda null (örneklendirilmemiş) değeri bir değişkene döndürebilir ya da bir [boş değer atanabilir tür](../nullable-types/index.md) değer türü.
 
- Dönüş değeri bir sabit bir numaralandırma üyesi olamaz, değer tarafından dönüş değeri bir özelliği veya yöntemi bir `class` veya `struct`. Derleyici Hatası CS8156 "bir ifade başvuruya göre döndürülemez olduğundan bu bağlamda kullanılamaz.", bu kural ihlal oluşturur

Ayrıca, başvuru döndürmek zaman uyumsuz yöntemleri değerlere izin verilmiyor. Dönüş değerini bilinmeyen hala durumdayken yürütme bitmeden önce zaman uyumsuz bir yöntem döndürebilir.
 
## <a name="defining-a-ref-return-value"></a>Ref dönüş değeri tanımlama

Ref dönüş değeri ekleyerek tanımlarsınız [ref](../../language-reference/keywords/ref.md) yöntem imzası dönüş türü için anahtar sözcüğü. Örneğin, aşağıdaki imzası belirten `GetContactInformation` özelliği bir başvuru döndürür bir `Person` çağıran nesneye:

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

Ayrıca, nesnenin adını döndürülen her tarafından [dönmek](../../language-reference/keywords/return.md) yöntem gövdesi deyiminde öncesinde, tarafından [ref](../../language-reference/keywords/ref.md) anahtar sözcüğü. Örneğin, aşağıdaki `return` deyimi bir başvuru döndürür bir `Person` adlı nesne `p`:

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>Ref dönüş değeri kullanma

Ref dönüş değeri: çağrılan yöntemin kapsamında başka bir değişken için bir diğer ad. Yorumlaması için herhangi dönüş ref, değişkeni kullanarak, diğer adlar kullanın:

- Değerini atadığınızda, değişkene bir değer atadığınız bu diğer adları.
- Değerini okurken değişkenin değerini okumakta olduğunuz bu diğer adları.
- Bunu dönerseniz *başvuruya göre*, bu aynı değişkenine bir diğer ad döndürüyor.
- Başka bir yönteme geçirirseniz *başvuruya göre*, değişkeni bir başvuru geçtiğiniz bu diğer adları.
- Yaptığınızda bir [ref yerel](#ref-local) aynı değişken için yeni bir diğer ad yaptığınız diğer ad.


## <a name="ref-locals"></a>Ref Yereller

Varsayın `GetContactInformation` yöntemi bildirilen bir başvuru dönüş:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Bir değer tarafından ataması bir değişkenin değeri olarak okur ve yeni bir değişkene atar:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Önceki atama bildirir `p` yerel değişken olarak. İlk değeri tarafından döndürülen değer okuma kopyalanır `GetContactInformation`. Gelecekteki tüm atamaları `p` tarafından döndürülen değişkenin değerini değiştirmez `GetContactInformation`. Değişkeni `p` artık döndürülen değişkenine bir diğer ad değil.

Bildirdiğiniz bir *ref yerel* diğer özgün değerine kopyalamak için değişkeni. Aşağıdaki atamasında `p` döndürülen değişkenine bir diğer adı `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Sonraki kullanımını `p` tarafından döndürülen değişkenini kullanarak aynı `GetContactInformation` çünkü `p` Bu değişken için bir diğer ad değil. Değişikliklerini `p` döndürülen değişkeni aynı zamanda değiştirmeniz `GetContactInformation`.

`ref` Anahtar sözcüğü kullanılır hem yerel değişken bildirimi önce *ve* yöntemi çağırmadan önce. 

Başvuruya göre bir değer aynı şekilde erişebilirsiniz. Bazı durumlarda, bir değer başvuruya göre erişme, performans'potansiyel olarak pahalı kopyalama işlemi kaçınarak artırır. Örneğin, aşağıdaki deyim bir değer başvurmak için kullanılan bir ref yerel değerin nasıl tanımlayabilirsiniz gösterir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

`ref` Anahtar sözcüğü kullanılır hem yerel değişken bildirimi önce *ve* değerin ikinci örnekte önce. Her ikisi de dahil etmek için hata `ref` Değişken bildiriminde anahtar sözcükleri ve atama derleyici hatası CS8172, her iki örnekler sonucu "başlatamıyor bir başvuru tarafından değere sahip bir değişken." 

Farklı depolama birimine başlatılmış sonra başvurmak için C# 7.3 önce ref yerel değişkenler atanmasını uygulanamadı. Bu kısıtlama kaldırılmıştır. Aşağıdaki örnek, bir yeniden atama gösterir:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Bunlar bildirirken ref yerel değişkenler hala başlatılması gerekir.

## <a name="ref-returns-and-ref-locals-an-example"></a>Ref döndürür ve ref Yereller: örneği

Aşağıdaki örnek tanımlayan bir `NumberStore` tamsayı değerleri dizisi depolayan sınıf. `FindNumber` Yöntemi büyük veya eşit bir bağımsız değişken olarak geçirilen ilk sayı başvuruya göre döndürür. Büyük veya ona eşit bağımsız değişkeni için herhangi bir sayı ise, yöntem dizin 0 döndürür. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Aşağıdaki örnek çağrıları `NumberStore.FindNumber` 16 eşit veya daha büyük olan ilk değer alma yöntemi. Arayan yöntemi tarafından döndürülen değer sonra iki katına çıkar. Dizi öğelerinin değeri yansıtılan değişiklik örnek çıktısını gösterir `NumberStore` örneği.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Başvuru dönüş değerleri için desteği olmadan, dizin değerini birlikte dizi öğesinin döndürerek böyle bir işlem gerçekleştirilir. Çağıran, ayrı bir yöntem çağrısı değeri değiştirmek için bu dizini sonra kullanabilirsiniz. Ancak, çağıran erişmek ve büyük olasılıkla diğer dizi değerlerini değiştirmek için dizini de değiştirebilirsiniz.  

Aşağıdaki örnekte gösterildiği nasıl `FindNumber` yöntemi C# ref yerel yeniden atama kullanılacak 7.3 sonra yeniden:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Bu ikinci sürümü Aranan numarası dizinin sonuna daha yakın olduğu senaryolarda uzun serileri ile daha verimli olur.

## <a name="see-also"></a>Ayrıca bkz.

[ref anahtar sözcüğü](../../language-reference/keywords/ref.md)  
[Başvuru semantiği ile değer türleri](../../../csharp/reference-semantics-with-value-types.md)

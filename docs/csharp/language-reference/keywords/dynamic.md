---
title: dynamic (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: de54b3ea663738f5b7af9e6100e0b69571d4caf9
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948403"
---
# <a name="dynamic-c-reference"></a>dynamic (C# Başvurusu)

`dynamic` Türü içinde gerçekleşir derleme zamanı tür denetimi atlayacak işlemleri etkinleştirir. Bunun yerine, bu işlemlerin çalışma zamanında çözümlenir. `dynamic` Türü Office Automation API'leri gibi COM API'leri ve ayrıca IronPython kitaplıklarına gibi dinamik API'lere ve erişim HTML belge nesne modeli (DOM) basitleştirir.

Tür `dynamic` türü gibi davranır `object` çoğu durumda. Ancak, türünde ifadeler içeren operations `dynamic` değil çözülen veya derleyici tarafından teslim türü. Çalışma zamanı derleyici paketleri işlemi birlikte bilgilerini ve bu bilgileri daha sonra işlemi tekrar değerlendirmek için kullanılır. Türündeki değişkenler işleminin bir parçası olarak `dynamic` türündeki değişkenler derlenmiş `object`. Bu nedenle, yazın `dynamic` yalnızca derleme zamanında değil çalışma zamanında bulunmaktadır.

Aşağıdaki örnek türünde bir değişken karşılaştırır `dynamic` türünde bir değişken için `object`. Derleme zamanında her bir değişken türünü doğrulamak için üzerine fare işaretçisini getirin `dyn` veya `obj` içinde `WriteLine` deyimleri. IntelliSense gösterir **dinamik** için `dyn` ve **nesne** için `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

`WriteLine` Deyimlerini görüntülemek çalışma zamanı tür `dyn` ve `obj`. Bu noktada, her ikisi de aynı türe sahip tamsayı. Şu çıktı üretilir:

`System.Int32`

`System.Int32`

Arasındaki farkı görmek için `dyn` ve `obj` derleme zamanında bildirimler arasında aşağıdaki iki satırı ekleyin ve `WriteLine` deyimleri önceki örnekte.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Derleyici Hatası bir tamsayı ve bir nesne ifadesinde denenen eklenmesi için bildirilen `obj + 3`. Ancak, herhangi bir hata için bildirilen `dyn + 3`. İçeren ifade `dyn` derleme zamanında çünkü işaretlenmediği türünü `dyn` olan `dynamic`.

## <a name="context"></a>Bağlam

`dynamic` Anahtar sözcüğü, doğrudan veya bir bileşen aşağıdaki durumlarda yapılandırılmış bir tür olarak görünebilir:

- Bir özellik, alan, dizin oluşturucu, parametre türü olarak bildirimlerden dönüş değeri, yerel değişken veya kısıtlama yazın. Aşağıdaki sınıf tanımı kullanır `dynamic` birkaç farklı bildirimlerden.

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- Açık tür dönüşümleri içinde bir dönüştürme hedef türü.

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- Burada türleri hizmet değerler olarak gibi sağ tarafında bağlamında bir `is` işleci veya bir `as` işleci veya bağımsız değişken olarak `typeof` oluşturulan türü bir parçası olarak. Örneğin, `dynamic` aşağıdaki ifadelerde kullanılabilir.

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a>Örnek

Aşağıdaki örnek kullanır `dynamic` birkaç bildirimlerden. `Main` Yöntemi de derleme zamanı tür denetimi çalışma zamanı tür denetimi ile karşılaştırır.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

Daha fazla bilgi ve örnekler için bkz: [türünü kullanarak dinamik](../../../csharp/programming-guide/types/using-type-dynamic.md).

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
<xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
[Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
[object](../../../csharp/language-reference/keywords/object.md)  
[is](../../../csharp/language-reference/keywords/is.md)  
[as](../../../csharp/language-reference/keywords/as.md)  
[typeof](../../../csharp/language-reference/keywords/typeof.md)  
[Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)  
[İzlenecek yol: Oluşturma ve dinamik nesneler kullanma](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)

---
title: "dynamic (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e3bf51ab62e195f7a5d1f0641f62380977c731ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dynamic-c-reference"></a>dynamic (C# Başvurusu)
`dynamic` Türü içinde gerçekleşir derleme zamanı tür denetimi atlayacak işlemleri etkinleştirir. Bunun yerine, bu işlemlerin çalışma zamanında çözümlenir. `dynamic` Türü Office Automation API'leri gibi COM API'leri ve ayrıca IronPython kitaplıklarına gibi dinamik API'lere ve erişim HTML belge nesne modeli (DOM) basitleştirir.  
  
 Tür `dynamic` türü gibi davranır `object` çoğu durumda. Ancak, türünde ifadeler içeren operations `dynamic` değil çözülen veya derleyici tarafından teslim türü. Çalışma zamanı derleyici paketleri işlemi birlikte bilgilerini ve bu bilgileri daha sonra işlemi tekrar değerlendirmek için kullanılır. Türündeki değişkenler işleminin bir parçası olarak `dynamic` türündeki değişkenler derlenmiş `object`. Bu nedenle, yazın `dynamic` yalnızca derleme zamanında değil çalışma zamanında bulunmaktadır.  
  
 Aşağıdaki örnek türünde bir değişken karşılaştırır `dynamic` türünde bir değişken için `object`. Derleme zamanında her bir değişken türünü doğrulamak için üzerine fare işaretçisini getirin `dyn` veya `obj` içinde `WriteLine` deyimleri. IntelliSense gösterir **dinamik** için `dyn` ve **nesne** için `obj`.  
  
 [!code-csharp[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
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
  
-   Bir özellik, alan, dizin oluşturucu, parametre türü olarak bildirimlerden dönüş değeri, yerel değişken veya kısıtlama yazın. Aşağıdaki sınıf tanımı kullanır `dynamic` birkaç farklı bildirimlerden.  
  
     [!code-csharp[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   Açık tür dönüşümleri içinde bir dönüştürme hedef türü.  
  
     [!code-csharp[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   Burada türleri hizmet değerler olarak gibi sağ tarafında bağlamında bir `is` işleci veya bir `as` işleci veya bağımsız değişken olarak `typeof` oluşturulan türü bir parçası olarak. Örneğin, `dynamic` aşağıdaki ifadelerde kullanılabilir.  
  
     [!code-csharp[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `dynamic` birkaç bildirimlerden. `Main` Yöntemi de derleme zamanı tür denetimi çalışma zamanı tür denetimi ile karşılaştırır.  
  
 [!code-csharp[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 Daha fazla bilgi ve örnekler için bkz: [türünü kullanarak dinamik](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Nesne](../../../csharp/language-reference/keywords/object.md)  
 [değil](../../../csharp/language-reference/keywords/is.md)  
 [olarak](../../../csharp/language-reference/keywords/as.md)  
 [typeof](../../../csharp/language-reference/keywords/typeof.md)  
 [Nasıl yapılır: is işleçlerini ve olarak kullanarak güvenli bir şekilde atama](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)  
 [İzlenecek yol: Oluşturma ve dinamik nesneler kullanma](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)

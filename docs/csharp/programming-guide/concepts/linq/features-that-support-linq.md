---
title: LINQ'i Destekleyen C# Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: c617b2d7b56618867fe92cbe1d9ee04aa4c3ab64
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45653206"
---
# <a name="c-features-that-support-linq"></a>LINQ'i Destekleyen C# Özellikleri
Aşağıdaki bölümde, C# 3.0 sürümünde sunulan yeni dil yapıları sunar. Bu yeni özelliklerin tümünü bir dereceye kullanılsa [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular olmadıkları için sınırlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ve burada, bunları kullanışlı her bağlamda kullanılabilir.  
  
## <a name="query-expressions"></a>Sorgu İfadeleri  
 Sorgu ifadeleri IEnumerable koleksiyonları sorgulamak için SQL veya XQuery benzer bir tanımlayıcı sözdizimi kullanın. Derleme zamanı sorgu sözdizimi yöntem çağrıları için dönüştürülür bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcısının uygulaması standart sorgu işleci genişletme yöntemleri. Uygulama Denetim uygun ad belirterek kapsamındaki standart sorgu işleçleri bir `using` yönergesi. Aşağıdaki sorgu ifadesi dizisini alır, bunları dizedeki ilk karakter göre gruplandırır ve grupları sıralar.  
  
```csharp  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 Daha fazla bilgi için [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="implicitly-typed-variables-var"></a>Örtük olarak yazılan değişkenler (var)  
 Kullanabileceğiniz bildirme ve bir değişkeni başlatarak, açıkça bir tür belirtmek yerine, [var](../../../../csharp/language-reference/keywords/var.md) çıkarır ve atamak için burada gösterildiği gibi derleyicisinin değiştiricisi:  
  
```csharp  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 Olarak bildirilen değişkenler `var` yalnızca olarak türünü açıkça belirtmeniz değişkenleri olarak kesin olan. Kullanımını `var` anonim türler, ancak oluşturmak mümkün kullanılabileceği için yalnızca yerel değişkenler yapar. Diziler de örtülü yazma ile bildirilebilir.  
  
 Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="object-and-collection-initializers"></a>Nesne ve Koleksiyon Başlatıcıları  
 Nesne ve koleksiyon başlatıcıları nesne için açıkça bir oluşturucu çağırmaya gerek kalmadan nesneleri başlatmak mümkün kılar. Bunlar kaynak verileri yeni bir veri türüne projenizin başlatıcılar genellikle sorgu ifadelerinde kullanılır. Adlı bir sınıf varsayılarak `Customer` ortak `Name` ve `Phone` nesne Başlatıcı özellikleri, aşağıdaki kodda gösterildiği gibi kullanılabilir:  
  
```csharp  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 Daha fazla bilgi için [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="anonymous-types"></a>Anonim Türler  
 Anonim bir tür derleyici tarafından oluşturulmuş olan ve yalnızca tür adı derleyici için kullanılabilir. Anonim türler bir sorgu sonucu özelliklerinde geçici olarak bir dizi türü adlı ayrı bir tanımlamak zorunda kalmadan gruplandırmak için kullanışlı bir yol sağlar. Anonim türler, burada gösterildiği gibi bir new ifadesi ve bir nesne Başlatıcı ile başlatılır:  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 Daha fazla bilgi için [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="extension-methods"></a>Uzantı Metotları  
 Böylece türünde bir örnek yöntemi gibi çağrılabilen bir genişletme yöntemi, bir tür ile ilişkilendirilebilir bir statik yöntemidir. Bu özellik, aslında "yeni yöntemler varolan türleri için bunları gerçekten değiştirmeden eklemek," sağlar. Standart sorgu işleçleri sağlayan genişletme yöntemleri kümesidir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işlevselliğini uygulayan herhangi bir türü için sorgu <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Daha fazla bilgi için [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Bir lambda ifadesi = kullanan bir satır içi işlevdir > işleci ayırmak için giriş parametreleri işlevi gövdesinden ve derleme zamanında bir temsilci veya ifade ağacı dönüştürülebilir. İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standart sorgu işleçleri için doğrudan yöntem çağrıları yaptığınızda programlama, lambda ifadeleri karşılaşırsınız.  
  
 Daha fazla bilgi için bkz.:  
  
-   [Anonim İşlevler](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Lambda İfadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a>Otomatik Uygulanan Özellikler  
 Otomatik uygulanan özellikler özellik bildirimini daha kısa yapın. Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici özellik alıcı ve ayarlayıcı erişilemeyen dışında özel, anonim destek alanı oluşturacaksınız.  
  
```csharp  
public string Name {get; set;}  
```  
  
 Daha fazla bilgi için [Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)

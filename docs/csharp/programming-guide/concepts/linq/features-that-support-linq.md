---
title: LINQ'i Destekleyen C# Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: f1c045ffe311dfad851c7cace37966d8d42a22cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="c-features-that-support-linq"></a>LINQ'i Destekleyen C# Özellikleri
Aşağıdaki bölümde, C# 3.0 sürümünde sunulan yeni dil yapıları tanıtır. Bu yeni özellikleri tüm ile bir dereceye kullanılsa [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları, bunlar için sınırlı değildir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ve bunları yararlı bulabileceğiniz bir bağlamda kullanılabilir.  
  
## <a name="query-expressions"></a>Sorgu İfadeleri  
 Sorgu ifadeleri sorguya SQL ya da XQuery benzer bir tanımlayıcı sözdizimi IEnumerable koleksiyonları kullanın. Derleme zamanı sorgu sözdizimi yöntem çağrılarını dönüştürülür bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standart sorgu işleci genişletme yöntemleri sağlayıcının uygulamasıdır. Uygulamaları denetim uygun ad belirterek kapsamındaki standart sorgu işleçleri bir `using` yönergesi. Aşağıdaki sorgu ifadesi dizisini alır, bunları dizedeki ilk karakter göre gruplandırır ve grupları sıralar.  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 Daha fazla bilgi için bkz: [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="implicitly-typed-variables-var"></a>Örtük olarak yazılan değişkenler (var)  
 Kullanabileceğiniz bildirme ve bir değişkeni başlatma zaman açıkça bir tür belirtmek yerine, [var](../../../../csharp/language-reference/keywords/var.md) Infer ve türünü atamak için aşağıda gösterildiği gibi görevlendirin değiştiricisi:  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 Olarak bildirilen değişkenlerin `var` yalnızca olarak kesin türü türünü açıkça belirtmek değişkenleri olarak belirtilmiş olan. Kullanımını `var` anonim türler, ancak oluşturmak mümkün kullanılabilir herhangi bir yerel değişken için yapar. Diziler de örtülü yazma ile bildirilebilir.  
  
 Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="object-and-collection-initializers"></a>Nesne ve Koleksiyon Başlatıcıları  
 Nesne ve koleksiyon başlatıcıları nesne için açıkça bir oluşturucu çağırmadan nesneleri başlatmak mümkün kılar. Bunlar veri kaynağını yeni bir veri türüne projenizin başlatıcıları genellikle sorgu ifadelerinde kullanılır. Adlı bir sınıf varsayılarak `Customer` ortak `Name` ve `Phone` özellikleri, nesne Başlatıcı olduğu gibi aşağıdaki kodu kullanılabilir:  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 Daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="anonymous-types"></a>Anonim Türler  
 Anonim bir tür derleyici tarafından oluşturulan ve tür adı yalnızca derleyiciye kullanılabilir. Anonim türler türü adlı ayrı bir tanımlamak zorunda kalmadan sorgu sonucu geçici olarak özelliklerinde kümesini gruplamak için kolay bir yol sağlamak. Anonim türler, aşağıda gösterildiği gibi yeni bir ifade ve nesne Başlatıcı başlatılır:  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 Daha fazla bilgi için bkz: [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="extension-methods"></a>Uzantı Metotları  
 Bir genişletme yöntemi türü ile ilişkilendirilebilir bir statik yöntem, böylelikle türü üzerinde örnek yöntemi değilmiş gibi çağrılabilir. Bu özellik, etkin, "yeni yöntemi var olan türlere bunları gerçekte değiştirmeden eklemek," sağlar. Standart sorgu işleçleri sağlamak genişletme yöntemleri kümesidir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işlevselliği uygulayan herhangi bir türü için sorgu <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Lambda ifadesi = kullanan bir satır içi işlevidir > ayırmak için işleci giriş parametreleri işlevi gövdesinden ve temsilci ya da bir ifade ağacına derleme zamanında dönüştürülebilir. İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] doğrudan yöntem çağrılarını standart sorgu işleçleri için yaptığınızda programlama, lambda ifadeleri karşılaşırsınız.  
  
 Daha fazla bilgi için bkz.:  
  
-   [Anonim İşlevler](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Lambda İfadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a>Otomatik Uygulanan Özellikler  
 Otomatik uygulanan özellikler özellik bildirimi daha kısa hale getirir. Aşağıdaki örnekte gösterildiği gibi bir özelliği bildirme, derleyici özellik Set'yordamı erişilemez dışında bir özel, anonim yedekleme alanını oluşturun.  
  
```  
public string Name {get; set;}  
```  
  
 Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)

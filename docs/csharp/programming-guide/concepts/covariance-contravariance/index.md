---
title: Covariance ve Contravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 80b4d703bb88d0bf1f7f48236c21b7698017e7f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169876"
---
# <a name="covariance-and-contravariance-c"></a>Covariance ve Contravariance (C#)
C#'da, tutarlılık ve kontravariance, dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için örtük başvuru dönüştürmesini sağlar. Covariance atama uyumluluğunu korur ve kontravariance bunu tersine çevirir.  
  
 Aşağıdaki kod atama uyumluluğu, tutarlılık ve kontravariance arasındaki farkı gösterir.  
  
```csharp  
// Assignment compatibility.
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.
object obj = str;  
  
// Covariance.
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument
// is assigned to an object instantiated with a less derived type argument.
// Assignment compatibility is preserved.
IEnumerable<object> objects = strings;  
  
// Contravariance.
// Assume that the following method is in the class:
// static void SetObject(object o) { }
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument
// is assigned to an object instantiated with a more derived type argument.
// Assignment compatibility is reversed.
Action<string> actString = actObject;  
```  
  
 Diziler için tutarlılık, daha türetilmiş bir tür dizisinin daha az türetilmiş bir türe örtük olarak dönüştürülmesini sağlar. Ancak bu işlem, aşağıdaki kod örneğinde gösterildiği gibi güvenli bir tür değildir.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Yöntem grupları için tutarlılık ve kontravarlık desteği, yöntem imzalarının temsilci türleri ile eşleştirilmesine olanak tanır. Bu, yalnızca eşleşen imzalara sahip yöntemleri değil, aynı zamanda daha fazla türemiş türleri (covariance) döndüren veya temsilci türü tarafından belirtilenden daha az türemiş türleri (kontravariance) olan parametreleri kabul eden yöntemleri de temsilcilere atamanızı sağlar. Daha fazla bilgi için, [Temsilcilerdeki Varyans (C#)](./variance-in-delegates.md) ve [Temsilcilerdeki Varyans Kullanma (C#) 'ye](./using-variance-in-delegates.md)bakın.  
  
 Aşağıdaki kod örneği, yöntem grupları için tutarlılık ve kontravarlık desteğini gösterir.  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 .NET Framework 4 veya yeni C# olarak genel arabirimlerde ve temsilcilerde tutarlılık ve kontratürle desteklenir ve genel tür parametrelerinin örtülü olarak dönüştürülmesine olanak tanır. Daha fazla bilgi için [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md) ve [Temsilcilerdeki Varyans (C#) 'ye](./variance-in-delegates.md)bakın.  
  
 Aşağıdaki kod örneği, genel arabirimler için örtülü başvuru dönüştürmesini gösterir.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Genel parametreleri eşdeğişken veya karşıt değişken olarak bildirilirse, genel arabirim veya temsilci *varyant* olarak adlandırılır. C# kendi varyant arabirimlerinizi ve temsilcilerinizi oluşturmanıza olanak tanır. Daha fazla bilgi için bkz: [Varyant Genel Arabirimleri Oluşturma (C#)](./creating-variant-generic-interfaces.md) ve [Varyans Temsilciler (C#).](./variance-in-delegates.md)  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md)|Genel arabirimlerdeki tutarlılık ve kontradastanlığı tartışır ve .NET Framework'de varyant genel arabirimlerinin bir listesini sağlar.|  
|[Varyant Genel Arabirimler Oluşturma (C#)](./creating-variant-generic-interfaces.md)|Özel varyant arabirimlerinin nasıl oluşturulurolduğunu gösterir.|  
|[Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md)|Ve <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IComparable%601> arabirimlerdeki tutarlılık ve kontravariance desteğinin kodu yeniden kullanmanıza nasıl yardımcı olabileceğini gösterir.|  
|[Temsilcilerde Varyans (C#)](./variance-in-delegates.md)|Genel ve genel olmayan temsilcilerdeki tutarlılık ve kontradastanlığı tartışır ve .NET Framework'de varyant genel temsilcilerinin listesini sağlar.|  
|[Varyans'ı Temsilcilerde Kullanma (C#)](./using-variance-in-delegates.md)|Yöntem imzalarını temsilci türleri ile eşleştirmek için genel olmayan temsilcilerde covariance ve contravariance desteğinin nasıl kullanılacağını gösterir.|  
|[Func ve Action Generic Delegeler için Varyans Kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md)|Ve `Action` temsilcilerdeki tutarlılık ve kontravaryans `Func` desteğinin kodu yeniden kullanmanıza nasıl yardımcı olabileceğini gösterir.|

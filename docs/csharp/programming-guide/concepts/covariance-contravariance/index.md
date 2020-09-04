---
title: Kovaryans ve değişken varyans (C#)
description: Kovaryans ve değişken varyans hakkında bilgi edinin ve bunların atama uyumluluğunu nasıl etkilediğini öğrenin. Aralarındaki farkları gösteren bir kod örneğine bakın.
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: ad4b2a7d7925d7893eb5a8e1d2d7c9ee3dcbd527
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465669"
---
# <a name="covariance-and-contravariance-c"></a>Kovaryans ve değişken varyans (C#)
C# ' de, Kovaryans ve değişken varyans dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için örtük başvuru dönüştürmeyi etkinleştirir. Kovaryans, atama uyumluluğunu korur ve değişken varyans onu tersine çevirir.  
  
 Aşağıdaki kod, atama uyumluluğu, Kovaryans ve değişken varyans arasındaki farkı gösterir.  
  
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
  
 Diziler için Kovaryans, daha önce türetilmiş bir türün dizisinin daha az türetilmiş bir tür dizisine örtük olarak dönüştürülmesini sağlar. Ancak, aşağıdaki kod örneğinde gösterildiği gibi bu işlem tür kullanımı güvenli değildir.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Yöntem grupları için Kovaryans ve değişken varyans desteği, temsilci türleriyle eşleşen Yöntem imzalarına izin verir. Bu, yalnızca eşleşen imzalara sahip yöntemlerin değil, aynı zamanda daha fazla türetilmiş tür (Kovaryans) döndüren veya temsilci türü tarafından belirtilenden daha az türetilmiş türler (değişken varyans) döndüren parametreleri kabul eden yöntemlere atama yapmanızı sağlar. Daha fazla bilgi için bkz. [Temsilcilerde varyans (c#)](./variance-in-delegates.md) ve [Temsilcilerde varyans (c#)](./using-variance-in-delegates.md).  
  
 Aşağıdaki kod örneği, yöntem grupları için Kovaryans ve değişken varyans desteğini gösterir.  
  
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
  
 .NET Framework 4 ve sonraki sürümlerde C#, Genel arabirimlerde ve temsilcilerde kovaryans ve değişken varyansı destekler ve genel tür parametrelerinin örtük dönüştürmelerine izin verir. Daha fazla bilgi için bkz. [Genel Arabirimlerde Varyans (c#)](./variance-in-generic-interfaces.md) ve [Temsilcilerde varyans (c#)](./variance-in-delegates.md).  
  
 Aşağıdaki kod örneğinde genel arabirimler için örtük başvuru dönüştürmesi gösterilmektedir.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Genel bir arabirim veya temsilci, genel parametreleri birlikte değişken veya değişken karşıtı olarak bildirilirse *değişken* olarak adlandırılır. C# kendi değişken arabirimlerinizi ve temsilcilerinizi oluşturmanızı sağlar. Daha fazla bilgi için bkz. [değişken genel arabirimler (C#) oluşturma](./creating-variant-generic-interfaces.md) ve [Temsilcilerde varyans (c#)](./variance-in-delegates.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md)|Genel arabirimlerde Kovaryans ve değişken varyansı açıklar ve .NET 'te VARIANT genel arabirimlerin bir listesini sağlar.|  
|[VARIANT genel arabirimleri oluşturma (C#)](./creating-variant-generic-interfaces.md)|Özel değişken arabirimlerinin nasıl oluşturulacağını gösterir.|  
|[Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md)|Ve arabirimlerinde Kovaryans ve değişken varyans desteğinin <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IComparable%601> kodu yeniden kullanmanıza nasıl yardımcı olduğunu gösterir.|  
|[Temsilcilerde varyans (C#)](./variance-in-delegates.md)|Genel ve genel olmayan temsilcilerde kovaryans ve değişken varyansı açıklar ve .NET 'te VARIANT genel temsilcilerin bir listesini sağlar.|  
|[Temsilcilerde varyans kullanma (C#)](./using-variance-in-delegates.md)|Temsilci türleriyle Yöntem imzalarını eşleştirmek için genel olmayan temsilcilerde kovaryans ve değişken varyans desteğinin nasıl kullanılacağını gösterir.|  
|[Func ve eylem genel temsilcileri için varyans kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md)|Ve temsilcilerde kovaryans ve değişken varyans desteğinin `Func` `Action` kodu yeniden kullanmanıza nasıl yardımcı olduğunu gösterir.|

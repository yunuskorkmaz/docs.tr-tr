---
title: Kovaryans ve kontravaryans (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: bfd78b1a32b9d4fe11b1dce129c24ceb5aca6754
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="covariance-and-contravariance-c"></a>Kovaryans ve kontravaryans (C#)
C# ' ta Kovaryans ve kontravaryans dolaylı başvuru dönüştürme dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için etkinleştirin. Kovaryans atama uyumluluğu korur ve değişken karşıtı tersine çevirir.  
  
 Aşağıdaki kod atama uyumluluğu, Kovaryans ve kontravaryans arasındaki farkı gösterir.  
  
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
  
 Kovaryans diziler için daha az türetilmiş bir tür bir dizi bir dizi daha türetilmiş bir tür örtük dönüştürme sağlar. Ancak bu işlem güvenli, aşağıdaki kod örneğinde gösterildiği gibi türünde değil.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Yöntem imzaları temsilci türleri ile eşleşen yöntem grupları Kovaryans ve kontravaryans desteği verir. Bu etkinleştirir, temsilcileri yalnızca imzalar, aynı zamanda türleri (kovaryans) ya da daha fazla türetilmiş döndüren yöntemler eşleşen yöntemleri atamak için temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul eder. Daha fazla bilgi için bkz: [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Temsilcilerde varyans (C#) kullanarak](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Aşağıdaki kod örneğinde Kovaryans ve kontravaryans yöntemini grupları için destek gösterir.  
  
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
  
 .NET Framework 4 veya daha yeni C# Kovaryans ve kontravaryans genel arabirimler ve temsilciler destekler ve genel tür parametreleri örtük dönüştürme için verir. Daha fazla bilgi için bkz: [genel arabirimler (C#) varyans](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Aşağıdaki kod örneğinde dolaylı başvuru dönüştürme genel arabirimler için gösterir.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Genel arabirim veya temsilci adlı *değişken* genel parametreleri eşdeğişken bildirilir varsa veya karşıtı. C#, kendi değişken arabirimler ve temsilciler oluşturmanıza olanak sağlar. Daha fazla bilgi için bkz: [değişken genel arabirimler oluşturma (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) ve [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Genel arabirimler (C#) varyans](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Kovaryans ve kontravaryans genel arabirimler açıklanır ve .NET Framework değişken genel arabirimler listesini sağlar.|  
|[Değişken genel arabirimler oluşturma (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Özel değişken arabirimler oluşturulacağını gösterir.|  
|[Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Nasıl Kovaryans ve kontravaryans desteklemek gösterir <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601> arabirimleri, kodu yeniden kullanmanıza yardımcı olabilir.|  
|[Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Kovaryans ve kontravaryans genel ve genel olmayan temsilciler açıklanır ve .NET Framework değişken genel temsilciler listesini sağlar.|  
|[Temsilcilerde varyans (C#) kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Kovaryans ve kontravaryans Destek genel olmayan temsilcileri yöntem imzaları temsilci türleri ile eşleşmesi için nasıl kullanılacağını gösterir.|  
|[İşlev ve eylem genel temsilciler (C#) için varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Nasıl Kovaryans ve kontravaryans desteklemek gösterir `Func` ve `Action` Temsilciler, kodu yeniden kullanmanıza yardımcı olabilir.|

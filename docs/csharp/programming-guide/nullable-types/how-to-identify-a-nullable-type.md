---
title: 'Nasıl yapılır: Boş Değer Atanabilir bir Tür Belirleme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: f3ac4ebd77fc92a133eb326919d5ba55264ced97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Nasıl yapılır: Boş Değer Atanabilir bir Tür Belirleme (C# Programlama Kılavuzu)
C# kullanabilirsiniz [typeof](../../../csharp/language-reference/keywords/typeof.md) oluşturmak için işleç bir <xref:System.Type> null atanabilir bir tür temsil eden nesnesi:  
  
```  
System.Type type = typeof(int?);  
```  
  
 Sınıflar ve yöntemler birini de kullanabilirsiniz <xref:System.Reflection> oluşturmak için ad alanı <xref:System.Type> boş değer atanabilir türleri temsil eden nesne. Ancak, kullanarak boş değer atanabilir değişkenlerden çalışma zamanında tür bilgilerini edinmek için deneyin <xref:System.Object.GetType%2A> yöntemi veya `is` işleç sonucu olan bir <xref:System.Type> temel alınan türü, null atanabilir olmayan temsil eden nesnesi kendisini yazın.  
  
 Çağırma `GetType` üzerinde null atanabilir tür türü örtük olarak dönüştürülür olduğunda gerçekleştirilecek kutulama işlemi neden <xref:System.Object>. Bu nedenle <xref:System.Object.GetType%2A> her zaman döndüren bir <xref:System.Type> temel alınan türü, boş değer atanabilir tür temsil eden nesne.  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 C# [olan](../../../csharp/language-reference/keywords/is.md) işleci null atanabilir'ın temel alınan tür üzerinde de çalışır. Bu nedenle kullanamazsınız `is` bir değişken null atanabilir bir tür olup olmadığını belirlemek için. Aşağıdaki örnekte gösterilir `is` işleci değerlendirir bir null atanabilir\<int > bir tamsayı olarak değişken  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a>Örnek  
 Belirlemek için aşağıdaki kodu kullanmak isteyip bir <xref:System.Type> nesnesi, null atanabilir bir tür temsil eder. Bu kodu yanlış olmadığını her zaman döndürdüğünü unutmayın `Type` çağrısından döndürülen nesne <xref:System.Object.GetType%2A>, bu konunun önceki kısımlarında açıklandığı gibi.  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Boş Değer Atanabilir Tipler](../../../csharp/programming-guide/nullable-types/index.md)  
 [Boş Değer Atanabilir Tipleri Kutulama](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)

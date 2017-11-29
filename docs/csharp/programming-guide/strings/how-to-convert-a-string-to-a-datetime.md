---
title: "Nasıl yapılır: Bir Dizeyi DateTime Olarak Dönüştürme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b459f245f0090fff16918bceb12a0082f6944331
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a>Nasıl yapılır: Bir Dizeyi DateTime Olarak Dönüştürme (C# Programlama Kılavuzu)
Programların tarihleri dize değerleri olarak girmek kullanıcıların sağlamak yaygın bir durumdur. Bir dize tabanlı tarihi dönüştürmek için bir <xref:System.DateTime?displayProperty=nameWithType> nesne kullanabileceğiniz <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType> yöntemi veya <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi statik yöntemi.  
  
 **Kültür**.  Dünyadaki farklı kültürler farklı şekillerde tarih dizeleri yazma.  Örneğin, ABD'de 20/01/2008 20 Ocak 2008 ' dir.  İçinde Fransa bu bir InvalidFormatException atar. Fransa tarih saatler gün/ay/yıl olarak okur ve isteğe bağlı olarak ABD'de gün/ay/yıl olduğundan budur.  
  
 Sonuç olarak, 20/01/2008 gibi bir dize 20 Ocak 2008 Fransa, ayrıştırma ve bir InvalidFormatException ABD throw.  
  
 Geçerli kültür ayarları belirlemek için System.Globalization.CultureInfo.CurrentCulture kullanabilirsiniz.  
  
 Aşağıdaki örnekte, bir dizeyi dateTime olarak dönüştürme basit bir örnek için bkz.  
  
 Daha fazla tarih dizeleri örnekleri için bkz: <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType>.  
  
```csharp  
string dateTime = "01/08/2008 14:50:50.42";  
            DateTime dt = Convert.ToDateTime(dateTime);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond);  
            // Specify exactly how to interpret the string.  
            IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true);  
  
            // Alternate choice: If the string has been input by an end user, you might    
            // want to format it according to the current culture:   
            // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture;  
            DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond  
/* Output (assuming first culture is en-US and second is fr-FR):  
    Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Press any key to continue . . .  
 */  
```  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dizeleri](../../../csharp/programming-guide/strings/index.md)

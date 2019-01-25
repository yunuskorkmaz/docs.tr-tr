---
title: Özel durumlar ve performans
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: KrzysztofCwalina
ms.openlocfilehash: f9fe3045d8bd8b4d625c5cd49bc18574ebb740de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707732"
---
# <a name="exceptions-and-performance"></a>Özel durumlar ve performans
Özel durumlar için ilgili bir sık karşılaşılan özel durumlar için düzenli olarak başarısız kodu kullandıysanız, uygulama performansını kabul edilemez olduğunu konusudur. Bu geçerli bir konudur. Üye bir özel durum oluşturduğunda, kendi performans kat daha yavaş olabilir. Ancak, hata kodlarını kullanarak izin vermeyin. özel durum yönergeleri kesinlikle bağlılığı sırasında iyi performans elde etmek mümkündür. Bu bölümde açıklanan iki deseni, bunu yapmak için yöntemler önerir.  
  
 **X DO NOT** özel durumlar performansı olumsuz etkileyebilir sorunları nedeniyle hata kodları kullanın.  
  
 Performansı artırmak için test edici Doer desen veya deneyin-Parse sonraki iki bölümde açıklanan düzeni kullanmak da mümkündür.  
  
## <a name="tester-doer-pattern"></a>Test edici Doer düzeni  
 Bazen bir özel durum atma üye performansını üye ikiye bölerek geliştirilebilir. Bakalım <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemi <xref:System.Collections.Generic.ICollection%601> arabirimi.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 Yöntem `Add` koleksiyonu salt okunur ise oluşturur. Bu yöntem çağrısında burada sık sık başarısız beklenmektedir senaryolarda bir performans sorunu olabilir. Sorunu azaltmak için yollarla değer eklemek denemeden önce koleksiyona yazılabilir olup olmadığını sınamak için biridir.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 Bizim örneğimizde, özellik koşulunu test etmek için kullanılan bir üye `IsReadOnly`, test edici adlandırılır. Olası oluşturma bir işlemi gerçekleştirmek için kullanılan bir üye `Add` yöntemi örneğimizde doer adlandırılır.  
  
 **✓ CONSIDER** Tester Doer düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.  
  
## <a name="try-parse-pattern"></a>Try-ayrıştırma desenindeki  
 Son derece performans açısından duyarlı API'leri için önceki bölümde açıklanan test edici Doer düzeni daha daha hızlı bir desen kullanılması gerekir. Desen, bir üye semantiği parçası case iyi tanımlanmış bir test yapmak için üye adı ayarlamak için çağırır. Örneğin, <xref:System.DateTime> tanımlayan bir <xref:System.DateTime.Parse%2A> yöntemi bir dizeyi ayrıştırma başarısız olursa, bir özel durum oluşturur. Ayrıca, karşılık gelen tanımlar <xref:System.DateTime.TryParse%2A> ayrıştırmak için çalışır yöntemi ancak false döndürürse ayrıştırma başarısız ve başarılı ayrıştırma kullanarak bir sonuç döndürür bir `out` parametresi.  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 Bu model kullanılırken, try işlevi katı koşullarını tanımlamak önemlidir. Üye, iyi tanımlanmış try dışındaki herhangi bir nedenle başarısız olursa, üye karşılık gelen bir özel durum throw gerekir.  
  
 **✓ CONSIDER** deneyin ayrıştırma düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.  
  
 **✓ DO** bu düzeni uygulama yöntemleri için "Deneme" ve Boolean dönüş türü önekini kullanın.  
  
 **✓ DO** deneyin ayrıştırma desenini kullanarak her üyesi için bir özel durum atma üye sağlayın.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)

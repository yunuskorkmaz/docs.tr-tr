---
title: Özel durumları ve performans
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7972cf7d63ee22e791d46046f30c9be467cc758e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="exceptions-and-performance"></a>Özel durumları ve performans
Özel durumlar için ilgili bir ortak özel durumlar için düzenli olarak başarısız kodu kullandıysanız, uygulama performansını kabul edilemez olduğunu konusudur. Bu geçerli bir konudur. Üye bir özel durum oluşturduğunda, kendi performansını büyüklük yavaş olabilir. Ancak, kesinlikle hata kodlarını kullanarak izin vermeyecek özel durum yönergelerine uymak sırasında iyi performans elde etmek mümkündür. Bu bölümde açıklanan iki desenleri Bunu yapmak için yöntemler önerir.  
  
 **X yok** özel durumlar performansı olumsuz etkileyebilir sorunları nedeniyle hata kodları kullanın.  
  
 Performansı artırmak için Tester Doer desen veya deneyin ayrıştırma sonraki iki bölümde açıklanan düzeni kullanmak da mümkündür.  
  
## <a name="tester-doer-pattern"></a>Tester Doer düzeni  
 Bazen bir özel durum atma üye performansını üye ikiye bölerek geliştirilebilir. Bakalım <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemi <xref:System.Collections.Generic.ICollection%601> arabirimi.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 Yöntem `Add` koleksiyon salt okunur ise oluşturur. Bu yöntem çağrısının sık sık başarısız olmasına beklenirken senaryolarda bir performans sorunu olabilir. Sorunu çözmek için yollardan değer eklemek denemeden önce koleksiyona yazılabilir olup olmadığını sınamak için biridir.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 Özelliği, örneğimizde bir koşulu test etmek için kullanılan üye `IsReadOnly`, tester adlandırılır. Olası oluşturma işlemi gerçekleştirmek için kullanılan üye `Add` örneğimizde yöntemi doer adlandırılır.  
  
 **✓ DÜŞÜNÜN** Tester Doer düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.  
  
## <a name="try-parse-pattern"></a>Try-ayrıştırma düzeni  
 Son derece performans duyarlı API'ler, önceki bölümde açıklanan Tester Doer düzeni daha daha hızlı bir desen kullanılması gerekir. Üye semantiğini parçası durumda iyi tanımlanmış bir test yapmak için üye adı ayarlamak için desen çağırır. Örneğin, <xref:System.DateTime> tanımlayan bir <xref:System.DateTime.Parse%2A> yöntemi dizesi ayrıştırma başarısız olursa, bir özel durum oluşturur. Ayrıca bir karşılık gelen tanımlar <xref:System.DateTime.TryParse%2A> ayrıştırmak için çalışır yöntemi ancak yanlış döndürür ayrıştırma başarısız olur ve bir başarılı ayrıştırma kullanmanın sonucu döndürürse bir `out` parametresi.  
  
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
  
 Bu deseni kullanılırken deneyin işlevselliği katı koşullarını tanımlamak önemlidir. Üye iyi tanımlanmış deneyin dışındaki herhangi bir nedenle başarısız olursa, üye karşılık gelen bir özel durum gerekir.  
  
 **✓ DÜŞÜNÜN** deneyin ayrıştırma düzeni özel durumlar oluşturma üyeleri için özel durumlar ortak senaryolar performans sorunlarını önlemek için ilgili.  
  
 **✓ YAPMAK** bu düzeni uygulama yöntemleri için "Deneme" ve Boolean dönüş türü önekini kullanın.  
  
 **✓ YAPMAK** deneyin ayrıştırma desenini kullanarak her üyesi için bir özel durum atma üye sağlayın.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)

---
title: Standart özel durum türlerini kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ea4a61be3a76c30c564cbf98ba3318fc6c3e7d4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591205"
---
# <a name="using-standard-exception-types"></a>Standart özel durum türlerini kullanma
Bu bölümde, Framework ve bunların kullanım ayrıntılarını tarafından sağlanan standart özel durumlar açıklanmaktadır. Listede olmadığı göre Hayır hepsine yer. Lütfen .NET Framework başvuru diğer Framework özel durum türlerinin kullanımı için belgelerine bakın.  
  
## <a name="exception-and-systemexception"></a>Özel durum ve SystemException  
 **X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> veya <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` veya `System.SystemException` framework kodunda yeniden oluşturulması düşünmüyorsanız.  
  
 **X AVOID** yakalama `System.Exception` veya `System.SystemException`, üst düzey özel durum işleyicileri dışındaki.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** throw veya öğesinden türetilen <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** throw bir <xref:System.InvalidOperationException> nesne uygunsuz bir durumda ise.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException ArgumentNullException ve üretiliyor  
 **✓ DO** throw <xref:System.ArgumentException> ya da hatalı değişkenler üye aktarılırsa, alt türlerinden birini. En çok türetilen özel durum türü varsa tercih eder.  
  
 **✓ DO** ayarlamak `ParamName` sınıfları birini atarken özelliği `ArgumentException`.  
  
 Bu özellik, özel durum oluşturulmasına neden olan parametrenin adını temsil eder. Özellik oluşturucu aşırı yüklemeleri birini kullanarak ayarlanabilir unutmayın.  
  
 **✓ DO** kullanmak `value` özellik ayarlayıcıları örtük değeri parametrenin adı.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException ve IndexOutOfRangeException AccessViolationException  
 **X DO NOT** açıkça veya örtük throw herkese açık şekilde çağrılabilir izin vermek <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, veya <xref:System.IndexOutOfRangeException>. Bu özel durumlar ayrılmış ve yürütme altyapısı tarafından oluşturulur ve buna genellikle bir hata gösterir.  
  
 Bağımsız değişken bu özel durumları atma önlemek için denetimi yapın. Bu özel durumları atma zaman içinde değişebileceğini yönteminizi uygulama ayrıntılarını gösterir.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** açıkça throw <xref:System.StackOverflowException>. Özel durum CLR tarafından yalnızca açıkça durum.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 Rastgele yığını taşmaları saklanacaktır tutarlılığın yönetilen kod yazmak neredeyse imkansızdır. CLR yönetilmeyen bölümlerini, iyi tanımlanmış basamağa yığın taşmaları taşımak araştırmalarını kullanan yerine rastgele yığını taşmaları yedekleme göre tutarlı kalır.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** açıkça throw <xref:System.OutOfMemoryException>. Bu durum CLR altyapısı tarafından yalnızca durum sağlamaktır.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException SEHException ve ExecutionEngineException  
 **X DO NOT** açıkça throw <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, ve <xref:System.Runtime.InteropServices.SEHException>. Bu özel durumların CLR altyapısı tarafından yalnızca durum üzeresiniz.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)

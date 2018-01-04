---
title: "Standart özel durum türleri kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5098db5131c2e47c0b73efaac51477ef3b107761
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="using-standard-exception-types"></a>Standart özel durum türleri kullanma
Bu bölümde Framework ve bunların kullanım ayrıntılarını tarafından sağlanan standart özel durumlar açıklanmaktadır. Halinde kapsamlı listesidir. Lütfen .NET Framework başvuru diğer Framework özel durum türleri kullanım için belgelerine bakın.  
  
## <a name="exception-and-systemexception"></a>Özel durum ve SystemException  
 **X yok** throw <xref:System.Exception?displayProperty=nameWithType> veya <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X yok** catch `System.Exception` veya `System.SystemException` framework kodunda yeniden oluşturulması düşünmüyorsanız.  
  
 **KAÇININ x** yakalama `System.Exception` veya `System.SystemException`, üst düzey özel durum işleyicileri dışındaki.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X yok** throw veya öğesinden türetilen <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ YAPMAK** throw bir <xref:System.InvalidOperationException> nesne uygunsuz bir durumda ise.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException ve ArgumentOutOfRangeException  
 **✓ YAPMAK** throw <xref:System.ArgumentException> ya da hatalı değişkenler üye aktarılırsa, alt türlerinden birini. En çok türetilen özel durum türü varsa tercih eder.  
  
 **✓ YAPMAK** ayarlamak `ParamName` sınıfları birini atarken özelliği `ArgumentException`.  
  
 Bu özellik, özel durum oluşturulmasına neden parametre adını temsil eder. Özelliği Oluşturucusu aşırı birini kullanarak ayarlanabilir unutmayın.  
  
 **✓ YAPMAK** kullanmak `value` özellik ayarlayıcıları örtük değeri parametrenin adı.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException ve AccessViolationException  
 **X yok** açıkça veya örtük throw herkese açık şekilde çağrılabilir izin vermek <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, veya <xref:System.IndexOutOfRangeException>. Bu özel durumlar ayrılmış ve yürütme altyapısı tarafından oluşturulur ve buna genellikle bir hata gösterir.  
  
 Bu özel durumları atma önlemek için denetimi bağımsız değişkeni yapın. Bu özel durumları atma zaman içinde değişebilir yönteminizi uygulama ayrıntılarını gösterir.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X yok** açıkça throw <xref:System.StackOverflowException>. Özel yalnızca CLR tarafından açıkça durum.  
  
 **X yok** catch `StackOverflowException`.  
  
 Rastgele yığını taşmaları varlığında tutarlılığın yönetilen kod yazmaya neredeyse mümkün değildir. CLR yönetilmeyen bölümlerini araştırmalar yığını iyi tanımlanmış basamağa taşar taşımak için yerine kullanarak rasgele yığını taşmaları yedekleme tutarlı kalır.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X yok** açıkça throw <xref:System.OutOfMemoryException>. Bu durum yalnızca CLR altyapısı tarafından oluşturulan olmaktır.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, SEHException ve ExecutionEngineException  
 **X yok** açıkça throw <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, ve <xref:System.Runtime.InteropServices.SEHException>. Bu özel durumlar, yalnızca CLR altyapısı tarafından oluşturulan üzeresiniz.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)

---
title: Standart Özel Durum Türlerini Kullanma
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 6b202d618d9d2216c8998181303250081de6781c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708990"
---
# <a name="using-standard-exception-types"></a>Standart Özel Durum Türlerini Kullanma
Bu bölümde, çerçevesi tarafından sunulan standart özel durumlar ve kullanımlarının ayrıntıları açıklanmaktadır. Liste, ayrıntılı anlamına gelir. Diğer Framework özel durum türlerinin kullanımı için lütfen .NET Framework başvuru belgelerine bakın.  
  
## <a name="exception-and-systemexception"></a>Özel durum ve SystemException  
 **X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> veya <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` veya `System.SystemException` framework kodunda yeniden oluşturulması düşünmüyorsanız.  
  
 **X AVOID** yakalama `System.Exception` veya `System.SystemException`, üst düzey özel durum işleyicileri dışındaki.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** throw veya öğesinden türetilen <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** throw bir <xref:System.InvalidOperationException> nesne uygunsuz bir durumda ise.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException ve ArgumentOutOfRangeException  
 **✓ DO** throw <xref:System.ArgumentException> ya da hatalı değişkenler üye aktarılırsa, alt türlerinden birini. Varsa, en çok türetilmiş özel durum türünü tercih edin.  
  
 **✓ DO** ayarlamak `ParamName` sınıfları birini atarken özelliği `ArgumentException`.  
  
 Bu özellik, özel durumun oluşturulmasına neden olan parametrenin adını temsil eder. Özelliğin, Oluşturucu aşırı yüklerinden biri kullanılarak ayarlankullanılamayacağını unutmayın.  
  
 **✓ DO** kullanmak `value` özellik ayarlayıcıları örtük değeri parametrenin adı.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException ve AccessViolationException  
 **X DO NOT** açıkça veya örtük throw herkese açık şekilde çağrılabilir izin vermek <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, veya <xref:System.IndexOutOfRangeException>. Bu özel durumlar, yürütme altyapısı tarafından ayrılmıştır ve oluşturulur ve çoğu durumda bir hata olduğunu gösterir.  
  
 Bağımsız değişken denetimini, bu özel durumların üretilmesini önlemek için yapın. Bu özel durumları oluşturmak, zaman içinde değişebilir yönteminizin uygulama ayrıntılarını sunar.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** açıkça throw <xref:System.StackOverflowException>. Özel durum yalnızca CLR tarafından açıkça oluşturulmalıdır.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 Rastgele yığın taşlarına sahip olan yönetilen kodu yazmak neredeyse imkansızdır. CLR 'nin yönetilmeyen parçaları, yığın dışına çıkmaları, rastgele yığın taşlarından yedeklenmek yerine iyi tanımlanmış konumlara taşımak için yoklamalar kullanılarak tutarlı kalır.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** açıkça throw <xref:System.OutOfMemoryException>. Bu özel durum yalnızca CLR altyapısı tarafından oluşturulmalıdır.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, şehir özel durumu ve ExecutionEngineException  
 **X DO NOT** açıkça throw <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, ve <xref:System.Runtime.InteropServices.SEHException>. Bu özel durumlar yalnızca CLR altyapısı tarafından atılır.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)

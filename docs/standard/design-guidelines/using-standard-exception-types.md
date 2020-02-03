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
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743546"
---
# <a name="using-standard-exception-types"></a>Standart Özel Durum Türlerini Kullanma
Bu bölümde, çerçevesi tarafından sunulan standart özel durumlar ve kullanımlarının ayrıntıları açıklanmaktadır. Liste, ayrıntılı anlamına gelir. Diğer Framework özel durum türlerinin kullanımı için lütfen .NET Framework başvuru belgelerine bakın.

## <a name="exception-and-systemexception"></a>Özel durum ve SystemException
 ❌ <xref:System.Exception?displayProperty=nameWithType> veya <xref:System.SystemException?displayProperty=nameWithType>oluşturmaz.

 ❌, yeniden oluşturma amacını belirtmedikçe Framework kodunda `System.Exception` veya `System.SystemException` yakalamayın.

 ❌, üst düzey özel durum işleyicileri dışında `System.Exception` veya `System.SystemException`yakalanmaktan kaçının.

## <a name="applicationexception"></a>ApplicationException
 ❌ <xref:System.ApplicationException>oluşturmaz veya türemeyin.

## <a name="invalidoperationexception"></a>InvalidOperationException
 ✔️, nesne uygunsuz bir durumdaysa <xref:System.InvalidOperationException> oluşturur.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException ve ArgumentOutOfRangeException
 bir üyeye hatalı bağımsız değişkenler geçirilirse ✔️ <xref:System.ArgumentException> veya alt türlerinden birini oluşturun. Varsa, en çok türetilmiş özel durum türünü tercih edin.

 ✔️ `ArgumentException`alt sınıflarından birini oluştururken `ParamName` özelliğini ayarlayın.

 Bu özellik, özel durumun oluşturulmasına neden olan parametrenin adını temsil eder. Özelliğin, Oluşturucu aşırı yüklerinden biri kullanılarak ayarlankullanılamayacağını unutmayın.

 ✔️ Özellik ayarlayıcılarının örtük değer parametresinin adı için `value` kullanın.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException ve AccessViolationException
 ❌, genel olarak çağrılabilir API 'Lerin <xref:System.NullReferenceException>, <xref:System.AccessViolationException>veya <xref:System.IndexOutOfRangeException>açıkça veya örtük olarak throw yapmasına izin vermez. Bu özel durumlar, yürütme altyapısı tarafından ayrılmıştır ve oluşturulur ve çoğu durumda bir hata olduğunu gösterir.

 Bağımsız değişken denetimini, bu özel durumların üretilmesini önlemek için yapın. Bu özel durumları oluşturmak, zaman içinde değişebilir yönteminizin uygulama ayrıntılarını sunar.

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌ açıkça <xref:System.StackOverflowException>oluşturmaz. Özel durum yalnızca CLR tarafından açıkça oluşturulmalıdır.

 ❌ `StackOverflowException`yakalamayın.

 Rastgele yığın taşlarına sahip olan yönetilen kodu yazmak neredeyse imkansızdır. CLR 'nin yönetilmeyen parçaları, yığın dışına çıkmaları, rastgele yığın taşlarından yedeklenmek yerine iyi tanımlanmış konumlara taşımak için yoklamalar kullanılarak tutarlı kalır.

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌ açıkça <xref:System.OutOfMemoryException>oluşturmaz. Bu özel durum yalnızca CLR altyapısı tarafından oluşturulmalıdır.

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, şehir özel durumu ve ExecutionEngineException
 ❌ açıkça <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>ve <xref:System.Runtime.InteropServices.SEHException>oluşturmaz. Bu özel durumlar yalnızca CLR altyapısı tarafından atılır.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)

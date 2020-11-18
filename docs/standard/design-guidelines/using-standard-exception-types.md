---
title: Standart Özel Durum Türlerini Kullanma
description: .NET 'teki standart özel durum türleri hakkında bilgi edinin. SystemException, ApplicationException, ArgumentException, ComException ve daha fazlasını öğrenin.
ms.date: 10/22/2008
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: d8e75f7104b755476f255563c9c1f7ece14f67db
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828471"
---
# <a name="using-standard-exception-types"></a>Standart Özel Durum Türlerini Kullanma
Bu bölümde, çerçevesi tarafından sunulan standart özel durumlar ve kullanımlarının ayrıntıları açıklanmaktadır. Liste, ayrıntılı anlamına gelir. Diğer Framework özel durum türlerinin kullanımı için lütfen .NET Framework başvuru belgelerine bakın.

## <a name="exception-and-systemexception"></a>Özel durum ve SystemException
 ❌<xref:System.Exception?displayProperty=nameWithType>Veya oluşturun <xref:System.SystemException?displayProperty=nameWithType> .

 ❌`System.Exception` `System.SystemException` Yeniden oluşturma amacını taşımadığınız müddetçe, çerçeve kodunu yakalamayın.

 ❌`System.Exception` `System.SystemException` En üst düzey özel durum işleyicileri dışında, yakalanmaktan kaçının.

## <a name="applicationexception"></a>ApplicationException
 ❌ ' İ throw veya türemeyin <xref:System.ApplicationException> .

## <a name="invalidoperationexception"></a>InvalidOperationException
 <xref:System.InvalidOperationException>nesne uygunsuz bir durumdaysa ✔️ oluşturun.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException ve ArgumentOutOfRangeException
 <xref:System.ArgumentException>bir üyeye hatalı bağımsız değişkenler geçirilmezse, ✔️ veya alt türlerinden birini oluşturun. Varsa, en çok türetilmiş özel durum türünü tercih edin.

 ✔️, alt `ParamName` sınıflarından birini oluştururken özelliğini ayarlayın `ArgumentException` .

 Bu özellik, özel durumun oluşturulmasına neden olan parametrenin adını temsil eder. Özelliğin, Oluşturucu aşırı yüklerinden biri kullanılarak ayarlankullanılamayacağını unutmayın.

 `value`özellik ayarlayıcılarının örtük değer parametresinin adı için ✔️ kullanın.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException ve AccessViolationException
 ❌ Genel olarak çağrılabilir API 'Lerin açıkça veya örtük olarak,, veya olarak throw yapmasına izin vermeyin <xref:System.NullReferenceException> <xref:System.AccessViolationException> <xref:System.IndexOutOfRangeException> . Bu özel durumlar, yürütme altyapısı tarafından ayrılmıştır ve oluşturulur ve çoğu durumda bir hata olduğunu gösterir.

 Bağımsız değişken denetimini, bu özel durumların üretilmesini önlemek için yapın. Bu özel durumları oluşturmak, zaman içinde değişebilir yönteminizin uygulama ayrıntılarını sunar.

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌ Açık olarak throw <xref:System.StackOverflowException> . Özel durum yalnızca CLR tarafından açıkça oluşturulmalıdır.

 ❌ Yakalamayın `StackOverflowException` .

 Rastgele yığın taşlarına sahip olan yönetilen kodu yazmak neredeyse imkansızdır. CLR 'nin yönetilmeyen parçaları, yığın dışına çıkmaları, rastgele yığın taşlarından yedeklenmek yerine iyi tanımlanmış konumlara taşımak için yoklamalar kullanılarak tutarlı kalır.

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌ Açık olarak throw <xref:System.OutOfMemoryException> . Bu özel durum yalnızca CLR altyapısı tarafından oluşturulmalıdır.

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, şehir özel durumu ve ExecutionEngineException
 ❌ Açık olarak <xref:System.Runtime.InteropServices.COMException> ,  <xref:System.ExecutionEngineException> , ve oluşturun <xref:System.Runtime.InteropServices.SEHException> . Bu özel durumlar yalnızca CLR altyapısı tarafından atılır.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Özel Durumlar için Tasarım Yönergeleri](exceptions.md)

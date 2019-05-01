---
title: Saat dilimlerini kaydetme ve geri yükleme
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d783f9e0d098e472dcf67aea394804d6eef2662
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026529"
---
# <a name="saving-and-restoring-time-zones"></a>Saat dilimlerini kaydetme ve geri yükleme

<xref:System.TimeZoneInfo> Önceden tanımlanmış saat dilimi veri almak için kayıt defteri sınıfını kullanır. Ancak, kayıt defteri dinamik bir yapıdır. Ayrıca, kayıt içeren bir saat dilimi bilgilerini, öncelikle geçerli yıl için saat ayarlamaları ve dönüştürmeleri işlemek için işletim sistemi tarafından kullanılır. Bu, doğru saat dilimi verilere dayanan uygulamalar için iki ana olası etkilere sahiptir:

* Bir uygulama tarafından istenen bir saat dilimi kayıt defterinde tanımlanmış olmayabilir veya bunu yeniden adlandırılmış veya olabilir kayıt defterinden kaldırılacağını.

* Kayıt defterinde tanımlanan bir saat dilimi geçmiş saat dilimi dönüşümleri için gerekli olan belirli ayarlama kuralları hakkında bilgi olmayabilir.

<xref:System.TimeZoneInfo> Sınıfı (kaydetme) serileştirme ve seri durumundan çıkarma (saat dilimi veri geri yükleme) için kendi destek aracılığıyla bu sınırlamalar yöneliktir.

## <a name="time-zone-serialization-and-deserialization"></a>Saat dilimi serileştirme ve seri durumundan çıkarma

Kaydetme ve seri hale getirme ve saat dilimi verileri seri durumdan çıkarılırken bir saat dilimi geri yükleme yalnızca iki yöntem çağrılarını içerir:

* Seri hale getirmek bir <xref:System.TimeZoneInfo> nesnenin çağırarak <xref:System.TimeZoneInfo.ToSerializedString%2A> yöntemi. Yöntem parametre almayan ve saat dilimi bilgilerini içeren bir dize döndürür.

* Seri durumdan çıkarabiliyorsa bir <xref:System.TimeZoneInfo> nesne seri hale getirilmiş bir dizeden Bu dize olarak geçirerek `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> yöntemi.

## <a name="serialization-and-deserialization-scenarios"></a>Serileştirme ve seri durumundan çıkarma senaryoları

Kaydet (veya seri) olanağı bir <xref:System.TimeZoneInfo> bir dizeye ve geri yükleme (veya seri durumdan) bu nesnenin daha sonra kullanmak için yardımcı program hem esnekliğini artırır <xref:System.TimeZoneInfo> sınıfı. Bu bölümde bazı serileştirme ve seri durumundan çıkarma en faydalı olduğu durumları inceler.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Serileştirme ve seri kaldırma uygulamanın verileri saat dilimi

Gerektiğinde bir dizeden seri hale getirilmiş bir saat dilimi geri yüklenebilir. Kayıt defterinden alınan saat dilimi doğru bir tarih ve saat belirli bir tarih aralığı içinde dönüştüremedi ise uygulamanın bunu yapabilirsiniz. Örneğin, Windows Vista kayıt defterinde genellikle tanımlanan saat dilimlerini yaklaşık iki ayarlama kuralları bilgi sunarken saat dilimi veri Windows XP kayıt defterindeki bir tek ayarlama kuralı destekler. Başka bir deyişle, geçmiş saat dönüşümleri yanlış olabilir. Bu sınırlama, serileştirme ve seri durumundan çıkarma saat dilimi veri işleyebilir.

Aşağıdaki örnekte, özel bir <xref:System.TimeZoneInfo> ABD temsil etmek için tanımlanmış ayarlama kuralları yok sınıfı Amerika Birleşik Devletleri'nde Yaz Saati giriş önce bir 1917 1883 bölgeye Doğu Standart Saati. Özel saat dilimi genel kapsama sahip bir değişkende seri hale getirilir. Saat dilimi dönüştürme yöntemi `ConvertUtcTime`, Eşgüdümlü Evrensel Saat (UTC) zamanları dönüştürme geçirilir. Tarih ve saat ortaya çıkarsa 1917 veya önceki sürümleri, özel Doğu Standart saat dilimi seri hale getirilmiş bir dizeden geri ve kayıt defterinden alınan saat dilimini değiştirir.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Saat dilimi özel durumları işleme

Kayıt defteri dinamik yapısı olduğundan, içeriği tabi yanlışlıkla veya kasıtlı değişikliği var. Başka bir deyişle, kayıt defterinde tanımlanması gerekir ve bir uygulamayı başarılı bir şekilde yürütmek gerekli olan bir saat dilimi mevcut olmayabilir. Saat dilimi serileştirme ve seri durumundan çıkarma için desteği olmadan, tanıtıcı elde edilen ancak az seçeneğiniz <xref:System.TimeZoneNotFoundException> sonlandırarak uygulama. Ancak, saat dilimi serileştirme ve seri durumundan çıkarma kullanarak, beklenmeyen bir işleyebilirsiniz <xref:System.TimeZoneNotFoundException> döndürerek gerekli saat dilimini seri hale getirilmiş bir dize ve uygulama çalışmaya devam eder.

Aşağıdaki örnek, oluşturur ve özel bir merkezi standart saat dilimi serileştirir. Ardından kayıt defterinden merkezi standart saat dilimi almaya çalışır. Alma işlemi ya da oluşturursa bir <xref:System.TimeZoneNotFoundException> veya <xref:System.InvalidTimeZoneException>, özel durum işleyicisi saat dilimini seri durumdan çıkarır.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Seri hale getirilmiş bir dize depolamak ve ihtiyaç olunması durumunda geri yükleme

Önceki örneklerde, bir dize değişkeni saat dilimi bilgilerini depolanan ve gerektiğinde geri. Ancak, uygulama veya kayıt defterinde seri hale getirilmiş saat dilimi bilgileri kendisini harici bir dosyaya, bir kaynak dosyası gibi bazı depolama ortamına depolanabilir içeren dizeyi katıştırılmış. (Özel saat dilimleri hakkında bilgi sistemin saat dilimi kayıt defteri anahtarlarında dışında depolanması gereken unutmayın.)

Bu şekilde bir seri hale getirilmiş saat dilimi dize depolamak de saat dilimi oluşturma yordamı uygulamadan ayırır. Örneğin, bir saat dilimi oluşturma yordamını yürütün ve kullanılabilir geçmiş saat dilimi bilgilerini içeren bir veri dosyası oluşturun. Veri dosyası olabilir daha sonra uygulama ile birlikte yüklü olması ve açılmadan ve uygulama bunları gerektirdiğinde bir veya daha fazla zaman bölgelerinden seri durumdan çıkarılabiliyorsa.

Seri hale getirilmiş saat dilimi veri depolamak için katıştırılmış bir kaynağı kullanan bir örnek için bkz: [nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)

---
title: "Kaydetme ve saat dilimlerini geri yükleme"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9451b1b0ff41f32c31ef3574b5684ae5a02e252
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="saving-and-restoring-time-zones"></a>Kaydetme ve saat dilimlerini geri yükleme

<xref:System.TimeZoneInfo> Sınıfı önceden tanımlanmış saat dilimi veri almak için kayıt defterini kullanır. Ancak, kayıt defteri dinamik bir yapıdır. Ayrıca, kayıt defteri içeriyor saat dilimi bilgilerini saat ayarlamaları ve dönüşümleri geçerli yıl için öncelikle işlemek için işletim sistemi tarafından kullanılır. Bu doğru saat dilimi verilere dayanan uygulamalar için iki ana etkilere sahiptir:

* Bir uygulama tarafından istenen bir saat dilimi kayıt defterinde tanımlanmış olmayabilir veya bunu yeniden adlandırılmış veya olabilir kayıt defterinden kaldırılacağını.

* Kayıt defterinde tanımlanan bir saat dilimi geçmiş saat dilimi dönüştürmeleri için gerekli olan belirli ayarlama kuralları hakkında bilgi olmayabilir.

<xref:System.TimeZoneInfo> Sınıfı (kaydetme) serileştirme ve seri durumundan çıkarma (saat dilimi verilerini geri yükleme) için desteğini aracılığıyla bu sınırlamalara adresleri.

## <a name="time-zone-serialization-and-deserialization"></a>Saat dilimi seri hale getirme ve seri durumdan çıkarma

Kaydetme ve seri hale getirme ve saat dilimi verileri seri durumdan çıkarılırken bir saat dilimi geri yükleme yalnızca iki yöntem çağrılarını içerir:

* Seri hale getirebilir bir <xref:System.TimeZoneInfo> o nesnenin çağırarak nesne <xref:System.TimeZoneInfo.ToSerializedString%2A> yöntemi. Bu yöntem parametre almayan ve saat dilimi bilgilerini içeren bir dize döndürür.

* Seri durumdan çıkarabiliyorsa bir <xref:System.TimeZoneInfo> nesne seri hale getirilmiş bir dizeden Bu dizeye geçirerek `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> yöntemi.

## <a name="serialization-and-deserialization-scenarios"></a>Serileştirme ve seri durumdan çıkarma senaryoları

Kaydet (veya seri) olanağı bir <xref:System.TimeZoneInfo> bir dizeye ve geri yükleme (veya seri durumdan çıkarmak için) nesnesi daha sonra kullanmak için yardımcı program ve esnekliğini artırır <xref:System.TimeZoneInfo> sınıfı. Bu bölümde bazı seri hale getirme ve seri durumdan çıkarma en yararlı durumlarda inceler.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Seri hale getirme ve bir uygulamada saat dilimi verileri seri durumdan çıkarılıyor

Gerektiğinde bir dizeden seri hale getirilmiş bir saat dilimi geri yüklenebilir. Kayıt defterinden alınan saat dilimi doğru bir tarih ve saat belirli bir tarih aralığındaki dönüştüremedi ise, bir uygulamanın bunu yapabilirsiniz. Örneğin, Windows Vista kayıt defterinde genellikle tanımlanmış saat dilimleri hakkında iki ayarlama kuralları bilgi sunarken saat dilimi verilerini Windows XP kayıt defterindeki tek ayarlama kuralı destekler. Başka bir deyişle, geçmiş saat dönüşümleri yanlış olabilir. Bu sınırlama, seri hale getirme ve seri durumdan çıkarma saat dilimi veri işleyebilir.

Aşağıdaki örnekte, özel bir <xref:System.TimeZoneInfo> ABD temsil etmek için tanımlanmış ayarlama kuralları yok sınıfı Amerika Birleşik Devletleri'nde Yaz Saati giriş önce 1917 1883 bölgeye Doğu Standart Saati. Özel saat dilimi genel kapsama sahip bir değişkende serileştirilir. Saat dilimi dönüştürme yöntemi `ConvertUtcTime`, Eşgüdümlü Evrensel Saat (UTC) kez dönüştürmek için geçirilir. Tarih ve saat meydana gelirse 1917 veya önceki sürümleri, özel Doğu Standart saat dilimi seri hale getirilmiş bir dizeden geri ve kayıt defterinden alınan saat dilimini değiştirir.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Saat dilimi özel durumları işleme

Kayıt defteri dinamik bir yapı olduğundan, içeriği yanlışlıkla veya kasıtlı değişiklik tabi ' dir. Başka bir deyişle, kayıt defterinde tanımlanması gerekir ve bir uygulamanın başarıyla yürütmek için gerekli bir saat dilimi mevcut olmayabilir. Saat dilimi serileştirme ve seri durumundan çıkarma için desteği olmadan, elde edilen tanıtıcı ancak az seçeneğiniz <xref:System.TimeZoneNotFoundException> sonlandırarak uygulama. Ancak, saat dilimi serileştirme ve seri durumdan çıkarma kullanarak, bir beklenmeyen işleyebilir <xref:System.TimeZoneNotFoundException> geri yükleyerek gerekli saat dilimi seri hale getirilmiş bir dize ve uygulama çalışmaya devam eder.

Aşağıdaki örnek, oluşturur ve özel bir merkezi standart saat dilimi serileştirir. Ardından kayıt defterinden merkezi standart saat dilimi almaya çalışır. Alma işlemi ya da oluşturursa bir <xref:System.TimeZoneNotFoundException> veya bir <xref:System.InvalidTimeZoneException>, özel durum işleyici saat dilimi seri durumdan çıkarır.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Seri hale getirilmiş bir dize depolamak ve gerektiğinde geri

Önceki örneklerde, saat dilimi bilgilerini dize değişkenine depolanır ve gerektiğinde geri. Ancak, uygulama veya kayıt defterinde serileştirilmiş saat dilimi bilgilerini kendisini dış dosyası, bir kaynak dosyası gibi bazı depolama ortamına depolanabilir içeren dize katıştırılmış. (Özel saat dilimleri hakkında bilgi sistemin saat dilimi kayıt defteri anahtarlarında dışında depolanması gereken unutmayın.)

Bu şekilde bir seri hale getirilmiş saat dilimi dize depolamak ayrıca saat dilimi oluşturma yordamı uygulamadan ayırır. Örneğin, bir saat dilimi oluşturma yordamı yürütün ve bir uygulamanın kullanabileceği geçmiş saat dilimi bilgilerini içeren bir veri dosyası oluşturun. Veri dosyası olabilir sonra uygulama ile yüklenmesi ve açılamadı ve uygulama bunları gerektiğinde bir veya daha fazla zaman bölgelerinden seri durumdan çıkarılabiliyorsa.

Katıştırılmış bir kaynağı serileştirilmiş saat dilimi verileri depolamak için kullandığı bir örnek için bkz: [nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Ayrıca bkz.

[Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)

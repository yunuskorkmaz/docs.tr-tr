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
ms.openlocfilehash: 8da26988d2e141ac704f0d3756cd8a50602cb3fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281056"
---
# <a name="saving-and-restoring-time-zones"></a>Saat dilimlerini kaydetme ve geri yükleme

<xref:System.TimeZoneInfo>Sınıfı, önceden tanımlı saat dilimi verilerini almak için kayıt defterine bağımlıdır. Ancak, kayıt defteri dinamik bir yapıdır. Ayrıca, kayıt defterinin içerdiği saat dilimi bilgileri, işletim sistemi tarafından, birincil olarak geçerli yıl için zaman ayarlamalarını ve dönüştürmeleri işlemek için kullanılır. Bu, doğru saat dilimi verilerine bağımlı uygulamalar için iki önemli etkilere sahiptir:

- Bir uygulama için gerekli olan bir saat dilimi kayıt defterinde tanımlanamaz veya yeniden adlandırılmış veya kayıt defterinden kaldırılmış olabilir.

- Kayıt defterinde tanımlı bir saat dilimi, geçmiş saat dilimi dönüştürmeleri için gerekli olan belirli ayarlama kuralları hakkında bilgi içermeyebilir.

<xref:System.TimeZoneInfo>Sınıfı, zaman dilimi verilerinin serileştirme (kaydetme) ve serisini kaldırma (geri yükleme) desteğiyle bu sınırlamalara yöneliktir.

## <a name="time-zone-serialization-and-deserialization"></a>Saat dilimi serileştirme ve serisini kaldırma

Saat dilimi verilerini serileştirerek ve serisini kaldırarak saat dilimini kaydetmek ve geri yüklemek yalnızca iki yöntem çağrısı içerir:

- Nesne metodunu çağırarak bir nesneyi seri hale getirebilirsiniz <xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.ToSerializedString%2A> . Yöntem hiçbir parametre alır ve saat dilimi bilgilerini içeren bir dize döndürür.

- <xref:System.TimeZoneInfo>Bu dizeyi `static` ( `Shared` Visual Basic) yöntemine geçirerek seri hale getirilen bir dizeden bir nesnenin serisini kaldırabilirsiniz <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> .

## <a name="serialization-and-deserialization-scenarios"></a>Serileştirme ve seri kaldırma senaryoları

Bir nesneyi bir dizeye kaydetme (veya serileştirme) <xref:System.TimeZoneInfo> ve daha sonra kullanılmak üzere geri yükleme (veya serisini kaldırma) özelliği, hem yardımcı programını hem de sınıfının esnekliğini artırır <xref:System.TimeZoneInfo> . Bu bölümde, serileştirme ve seri durumundan çıkarma konusunda en yararlı olan bazı durumlar incelenir.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Bir uygulamadaki saat dilimi verilerini serileştirme ve serisini kaldırma

Seri hale getirilmiş bir saat dilimi, gerektiğinde bir dizeden geri yüklenebilir. Bir uygulama, kayıt defterinden alınan saat dilimi belirli bir tarih aralığındaki tarih ve saati doğru bir şekilde dönüştüremeyebilir bu işlemi yapabilirsiniz. Örneğin, Windows XP kayıt defterindeki saat dilimi verileri tek bir ayarlama kuralını destekleirken, Windows Vista kayıt defterinde tanımlanan saat dilimleri genellikle iki ayarlama kuralı hakkında bilgi sağlar. Bu, geçmiş zaman dönüştürmelerin yanlış olabileceği anlamına gelir. Saat dilimi verilerinin serileştirilmesi ve serisini kaldırmak bu sınırlamayı işleyebilir.

Aşağıdaki örnekte, ayarlama kuralları olmayan özel bir <xref:System.TimeZoneInfo> sınıf, Birleşik Devletler gün ışığından yararlanma saatine giriş yapmadan önce 1883 ile 1917 arasında ABD Doğu Standart saat dilimini temsil edecek şekilde tanımlanmıştır. Özel saat dilimi, genel kapsama sahip bir değişkende serileştirilir. Saat dilimi dönüştürme yöntemi, `ConvertUtcTime` dönüştürme Için Eşgüdümlü Evrensel Saat (UTC) zamanlarını geçti. Tarih ve saat 1917 veya daha önceki bir sürümde gerçekleşirse, özel Doğu Standart saat dilimi serileştirilmiş bir dizeden geri yüklenir ve kayıt defterinden alınan saat dilimini değiştirir.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Saat dilimi özel durumlarını işleme

Kayıt defteri dinamik bir yapı olduğundan, içeriği yanlışlıkla veya bilinçli değişikliğine tabidir. Bu, kayıt defterinde tanımlanması gereken ve bir uygulamanın başarıyla yürütülmesi için gerekli olan bir zaman diliminin eksik olması anlamına gelir. Saat dilimi serileştirme ve seri durumundan çıkarma desteği olmadan, uygulamayı sonlandırarak ortaya çıkan, ancak sonucu işlemek için çok az seçeneğiniz vardır <xref:System.TimeZoneNotFoundException> . Ancak, saat dilimi serileştirme ve serisini kaldırma kullanarak, <xref:System.TimeZoneNotFoundException> istenen saat dilimini seri hale getirilmiş bir dizeden geri yükleyerek beklenmedik bir şekilde işleyebilir ve uygulama çalışmaya devam eder.

Aşağıdaki örnek, özel bir merkezi standart saat dilimini oluşturur ve seri hale getirir. Daha sonra merkezi standart saat dilimini kayıt defterinden almaya çalışır. Alma işlemi bir <xref:System.TimeZoneNotFoundException> veya bir oluşturursa <xref:System.InvalidTimeZoneException> , özel durum işleyicisi saat dilimini seri hale getirir.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Seri hale getirilmiş bir dizeyi depolama ve gerektiğinde geri yükleme

Önceki örneklerde saat dilimi bilgileri bir dize değişkenine depolanmalı ve gerektiğinde geri yüklenir. Ancak, seri hale getirilmiş saat dilimi bilgilerini içeren dize, bir dış dosya, uygulamaya eklenmiş bir kaynak dosyası ya da kayıt defteri gibi bazı depolama ortamında depolanabilir. (Özel Saat dilimleriyle ilgili bilgilerin, kayıt defterindeki sistemin saat dilimi anahtarlarından ayrı depolanması gerektiğini unutmayın.)

Seri hale getirilmiş saat dilimi dizesinin bu şekilde depolanması, uygulamanın kendisinden saat dilimi oluşturma yordamını da ayırır. Örneğin, bir saat dilimi oluşturma yordamı, bir uygulamanın kullanabileceği geçmiş saat dilimi bilgilerini içeren bir veri dosyası yürütebilir ve oluşturabilir. Veri dosyası daha sonra uygulamayla birlikte yüklenebilir ve açılabilir ve uygulama için gerektiğinde bir veya daha fazla saat dilimi seri durumdan çıkarılamaz.

Seri hale getirilmiş saat dilimi verilerini depolamak için gömülü bir kaynak kullanan bir örnek için bkz. [nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme](save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: zaman dilimlerini gömülü bir kaynaktan geri yükleme](restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)

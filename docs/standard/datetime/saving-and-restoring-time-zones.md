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
ms.openlocfilehash: ea44b29eaa0273baadbf02093108bc4da912a3e5
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106740"
---
# <a name="saving-and-restoring-time-zones"></a>Saat dilimlerini kaydetme ve geri yükleme

<xref:System.TimeZoneInfo> Sınıfı, önceden tanımlı saat dilimi verilerini almak için kayıt defterine bağımlıdır. Ancak, kayıt defteri dinamik bir yapıdır. Ayrıca, kayıt defterinin içerdiği saat dilimi bilgileri, işletim sistemi tarafından, birincil olarak geçerli yıl için zaman ayarlamalarını ve dönüştürmeleri işlemek için kullanılır. Bu, doğru saat dilimi verilerine bağımlı uygulamalar için iki önemli etkilere sahiptir:

- Bir uygulama için gerekli olan bir saat dilimi kayıt defterinde tanımlanamaz veya yeniden adlandırılmış veya kayıt defterinden kaldırılmış olabilir.

- Kayıt defterinde tanımlı bir saat dilimi, geçmiş saat dilimi dönüştürmeleri için gerekli olan belirli ayarlama kuralları hakkında bilgi içermeyebilir.

Sınıfı <xref:System.TimeZoneInfo> , zaman dilimi verilerinin serileştirme (kaydetme) ve serisini kaldırma (geri yükleme) desteğiyle bu sınırlamalara yöneliktir.

## <a name="time-zone-serialization-and-deserialization"></a>Saat dilimi serileştirme ve serisini kaldırma

Saat dilimi verilerini serileştirerek ve serisini kaldırarak saat dilimini kaydetmek ve geri yüklemek yalnızca iki yöntem çağrısı içerir:

- Nesne <xref:System.TimeZoneInfo.ToSerializedString%2A> metodunu çağırarak bir <xref:System.TimeZoneInfo> nesneyi seri hale getirebilirsiniz. Yöntem hiçbir parametre alır ve saat dilimi bilgilerini içeren bir dize döndürür.

- <xref:System.TimeZoneInfo> Bu dizeyi `static` (VisualBasic`Shared` ) yönteminegeçirerekserihalegetirilenbirdizedenbir<xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> nesnenin serisini kaldırabilirsiniz.

## <a name="serialization-and-deserialization-scenarios"></a>Serileştirme ve seri kaldırma senaryoları

Bir <xref:System.TimeZoneInfo> nesneyi bir dizeye kaydetme (veya serileştirme) ve daha sonra kullanılmak üzere geri yükleme (veya serisini kaldırma) özelliği, hem yardımcı programını hem de <xref:System.TimeZoneInfo> sınıfının esnekliğini artırır. Bu bölümde, serileştirme ve seri durumundan çıkarma konusunda en yararlı olan bazı durumlar incelenir.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Bir uygulamadaki saat dilimi verilerini serileştirme ve serisini kaldırma

Seri hale getirilmiş bir saat dilimi, gerektiğinde bir dizeden geri yüklenebilir. Bir uygulama, kayıt defterinden alınan saat dilimi belirli bir tarih aralığındaki tarih ve saati doğru bir şekilde dönüştüremeyebilir bu işlemi yapabilirsiniz. Örneğin, Windows XP kayıt defterindeki saat dilimi verileri tek bir ayarlama kuralını destekleirken, Windows Vista kayıt defterinde tanımlanan saat dilimleri genellikle iki ayarlama kuralı hakkında bilgi sağlar. Bu, geçmiş zaman dönüştürmelerin yanlış olabileceği anlamına gelir. Saat dilimi verilerinin serileştirilmesi ve serisini kaldırmak bu sınırlamayı işleyebilir.

Aşağıdaki örnekte, ABD 'yi temsil eden <xref:System.TimeZoneInfo> ayarlama kuralları olmayan özel bir sınıf tanımlanmıştır Birleşik Devletler gün ışığından yararlanma saatine giriş yapmadan önce 1883 ile 1917 arasındaki Doğu Standart saat dilimi. Özel saat dilimi, genel kapsama sahip bir değişkende serileştirilir. Saat dilimi dönüştürme yöntemi `ConvertUtcTime`, dönüştürme için Eşgüdümlü Evrensel Saat (UTC) zamanlarını geçti. Tarih ve saat 1917 veya daha önceki bir sürümde gerçekleşirse, özel Doğu Standart saat dilimi serileştirilmiş bir dizeden geri yüklenir ve kayıt defterinden alınan saat dilimini değiştirir.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Saat dilimi özel durumlarını işleme

Kayıt defteri dinamik bir yapı olduğundan, içeriği yanlışlıkla veya bilinçli değişikliğine tabidir. Bu, kayıt defterinde tanımlanması gereken ve bir uygulamanın başarıyla yürütülmesi için gerekli olan bir zaman diliminin eksik olması anlamına gelir. Saat dilimi serileştirme ve seri durumundan çıkarma desteği olmadan, uygulamayı sonlandırarak ortaya çıkan, ancak sonucu <xref:System.TimeZoneNotFoundException> işlemek için çok az seçeneğiniz vardır. Ancak, saat dilimi serileştirme ve serisini kaldırma kullanarak, istenen saat dilimini seri hale <xref:System.TimeZoneNotFoundException> getirilmiş bir dizeden geri yükleyerek beklenmedik bir şekilde işleyebilir ve uygulama çalışmaya devam eder.

Aşağıdaki örnek, özel bir merkezi standart saat dilimini oluşturur ve seri hale getirir. Daha sonra merkezi standart saat dilimini kayıt defterinden almaya çalışır. Alma işlemi bir <xref:System.TimeZoneNotFoundException> veya bir <xref:System.InvalidTimeZoneException>oluşturursa, özel durum işleyicisi saat dilimini seri hale getirir.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Seri hale getirilmiş bir dizeyi depolama ve gerektiğinde geri yükleme

Önceki örneklerde saat dilimi bilgileri bir dize değişkenine depolanmalı ve gerektiğinde geri yüklenir. Ancak, seri hale getirilmiş saat dilimi bilgilerini içeren dize, bir dış dosya, uygulamaya eklenmiş bir kaynak dosyası ya da kayıt defteri gibi bazı depolama ortamında depolanabilir. (Özel Saat dilimleriyle ilgili bilgilerin, kayıt defterindeki sistemin saat dilimi anahtarlarından ayrı depolanması gerektiğini unutmayın.)

Seri hale getirilmiş saat dilimi dizesinin bu şekilde depolanması, uygulamanın kendisinden saat dilimi oluşturma yordamını da ayırır. Örneğin, bir saat dilimi oluşturma yordamı, bir uygulamanın kullanabileceği geçmiş saat dilimi bilgilerini içeren bir veri dosyası yürütebilir ve oluşturabilir. Veri dosyası daha sonra uygulamayla birlikte yüklenebilir ve açılabilir ve uygulama için gerektiğinde bir veya daha fazla saat dilimi seri durumdan çıkarılamaz.

Seri hale getirilmiş saat dilimi verilerini depolamak için gömülü bir kaynak kullanan bir örnek için bkz [. nasıl yapılır: Zaman dilimlerini gömülü bir kaynağa](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) kaydedin ve [şunları yapın: Katıştırılmış bir kaynaktan](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)saat dilimlerini geri yükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)

---
title: 'Nasıl yapılır: Saat dilimlerini eklenmiş kaynağa kaydetme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67a97193d186275e6a788f6b18bbc17c535f367
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912710"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Nasıl yapılır: Saat dilimlerini eklenmiş kaynağa kaydetme

Genellikle saat dilimiyle uyumlu bir uygulama belirli bir saat dilimini gerektirir. Ancak, çünkü tek kullanılabilirliğini <xref:System.TimeZoneInfo> yerel sisteminin kayıt defterinde depolanan bilgileri bağımlı nesneler, Alışıldığı bile kullanılabilir saat dilimi yok. Ayrıca, özel saat dilimleri hakkında bilgi örneği kullanarak <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi ile diğer saat dilimi bilgileri kayıt depolanmaz. Gerektiğinde bu saat dilimlerini kullanılabilir olmasını sağlamak için seri hale getirme tarafından kaydedin ve daha sonra seri durumdan çıkarılırken tarafından geri yükleyebilirsiniz.

Genellikle, seri hale getirilirken bir <xref:System.TimeZoneInfo> nesne saat dilimiyle uyumlu uygulama dışında gerçekleşir. Seri hale getirilmiş tutmak için kullanılan veri deposu bağlı olarak <xref:System.TimeZoneInfo> nesneler, saat dilimi veri seri hale getirilemiyor bir kurulum veya yükleme yordamı (örneğin, veriler bir uygulama kayıt defteri anahtarında depolanır) bir parçası olarak ya da çalışan bir yardımcı programı yordamının parçası olarak son uygulama (örneğin, serileştirilmiş veriler .NET XML kaynak (.resx) dosyası depolandığında) derlenmeden önce.

Uygulama ile derlenmiş olan bir kaynak dosyasına ek olarak, çeşitli veri depoları için saat dilimi bilgileri kullanılabilir. Bunlar aşağıdakileri içerir:

* Kayıt defteri. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time bölgeleri anahtarlarını kullanmak yerine özel saat dilimi veri depolamak için bir uygulama anahtarlarını kendi uygulama anahtarı kullanması gerektiğini unutmayın.

* Yapılandırma dosyaları.

* Diğer sistem dosyaları.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Bir .resx dosyasına serileştirmek tarafından bir saat dilimi kaydetmek için

1. Var olan bir saat dilimi almak veya yeni bir saat dilimi oluşturun.

   Var olan bir saat dilimi almak için bkz: [nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](../../../docs/standard/datetime/access-utc-and-local.md) ve [nasıl yapılır: Bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).

   Yeni bir saat dilimi oluşturmak amacıyla bir aşırı yüklemelerinden birini çağırın <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi. Daha fazla bilgi için [nasıl yapılır: Ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

2. Çağrı <xref:System.TimeZoneInfo.ToSerializedString%2A> saat diliminin veri içeren bir dize oluşturmak için yöntemi.

3. Örneği bir <xref:System.IO.StreamWriter> nesne adı ve isteğe bağlı olarak için .resx dosyasının yolunu sağlayarak <xref:System.IO.StreamWriter> sınıf oluşturucusu.

4. Örneği bir <xref:System.Resources.ResXResourceWriter> geçirerek nesne <xref:System.IO.StreamWriter> nesnesini <xref:System.Resources.ResXResourceWriter> sınıf oluşturucusu.

5. Geçişi saat dilimine ait dize olarak serileştirilmiş <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemi.

6. Çağrı <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi.

7. Çağrı <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemi.

8. Kapat <xref:System.IO.StreamWriter> çağırarak kendi <xref:System.IO.StreamWriter.Close%2A> yöntemi.

9. Oluşturulan bir .resx dosyası, uygulamanın Visual Studio projenize ekleyin.

10. Kullanarak **özellikleri** Visual Studio penceresinde emin olun, .resx dosyasının **derleme eylemi** özelliği **gömülü kaynak**.

## <a name="example"></a>Örnek

Aşağıdaki örnek serileştiren bir <xref:System.TimeZoneInfo> Orta Standart Saati temsil eden nesne ve <xref:System.TimeZoneInfo> SerializedTimeZones.resx adlı bir .NET XML kaynak dosyası Palmer istasyonu, Antarktika zamanı temsil eden nesne. Orta Standart Saati, genellikle kayıt defterinde tanımlanır; PALMER istasyonu, Antarktika, özel bir zaman dilimi olur.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Bu örnekte serileştiren <xref:System.TimeZoneInfo> bunlar bir kaynak dosyasında derleme zamanında kullanılabilir olacak şekilde nesneleri.

Çünkü <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi .NET XML kaynak dosyası için tam başlık bilgilerini ekler, kaynakları var olan bir dosyaya eklemek için kullanılamaz. Örnek için SerializedTimeZones.resx dosyasını denetleyerek bu işler ve, varsa, tüm kaynaklarını dışında depolama iki saat dilimleri için genel serileştirilmiş <xref:System.Collections.Generic.Dictionary%602> nesne. Var olan dosyayı ardından silinir ve mevcut kaynakları yeni SerializedTimeZones.resx dosyasına eklenir. Seri hale getirilmiş saat dilimi veri bu dosyaya da eklenir.

Anahtar (veya **adı**) kaynakları alanlarının gömülü boşluklar içermemelidir. <xref:System.String.Replace%28System.String%2CSystem.String%29> Yöntemi, kaynak dosyasına atanmadan önce tüm gömülü boşluklar saat dilimi tanımlayıcıları kaldırmak için çağrılır.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Projeye bir başvuru System.Windows.Forms.dll ve System.Core.dll eklenmesi gerektiğini.

* Şu ad alanlarından alınan olduğunu:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
- [Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)

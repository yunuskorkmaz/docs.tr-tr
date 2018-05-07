---
title: 'Nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme'
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
ms.openlocfilehash: 4dd7e6db78b76d737cb4646c2fad79d96fb60aee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme

Saat dilimi algılayan uygulama genelde belirli bir saat dilimi gerektirir. Ancak, çünkü tek kullanılabilirliğini <xref:System.TimeZoneInfo> yerel sistemin kayıt defterinde depolanan bilgileri bağımlı nesneler, geleneksel olarak bile kullanılabilir saat dilimi yok. Ayrıca, özel saat dilimleri hakkında bilgi örneği kullanarak <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi, kayıt defterinde diğer saat dilimi bilgileri ile depolanmaz. Gerektiğinde bu saat dilimleri kullanılabilir olduğundan emin olmak için seri hale getirme tarafından kaydedebilir ve daha sonra bunları seri durumdan çıkarılırken tarafından geri yükleyin.

Genellikle, seri hale getirilirken bir <xref:System.TimeZoneInfo> nesne dışında saat dilimi algılayan uygulama oluşur. Serileştirilmiş tutmak için kullanılan veri deposu bağlı olarak <xref:System.TimeZoneInfo> nesneleri, saat dilimi veri serileştirilmiş Kurulum veya yükleme yordamı (örneğin, bir uygulama kayıt defteri anahtarında veri depolandığında) bir parçası olarak ya da çalışan bir yardımcı programı yordamının parçası olarak son uygulama (örneğin, serileştirilmiş veriler bir .NET XML kaynak (.resx) dosyasında depolandığında) derlenmiş önce.

Uygulama ile derlenen bir kaynak dosyasına ek olarak, diğer birkaç veri depoları için saat dilimi bilgilerini kullanılabilir. Bunlar aşağıdakileri içerir:

* Kayıt defteri. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones alt anahtarları kullanmak yerine özel saat dilimi veri depolamak için uygulamanın kendi uygulama anahtarı alt anahtarları kullanması gerektiğini unutmayın.

* Yapılandırma dosyaları.

* Diğer sistem dosyalarını.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Bir saat dilimi .resx dosyasına serileştirme tarafından kaydetmek için

1. Varolan bir saat dilimi almak veya yeni bir saat dilimi oluşturun.

   Varolan bir saat dilimi almak için bkz: [nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md) ve [nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).

   Yeni bir saat dilimi oluşturmak için aşırı birini çağırın <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

2. Çağrı <xref:System.TimeZoneInfo.ToSerializedString%2A> saat diliminin veri içeren bir dize oluşturmak için yöntemi.

3. Örneği bir <xref:System.IO.StreamWriter> ad ve isteğe bağlı olarak için .resx dosyasının yolunu sağlayarak nesne <xref:System.IO.StreamWriter> sınıfı oluşturucusu.

4. Örneği bir <xref:System.Resources.ResXResourceWriter> geçirerek nesne <xref:System.IO.StreamWriter> nesnesine <xref:System.Resources.ResXResourceWriter> sınıfı oluşturucusu.

5. Geçişi saat dilimi 's dize olarak serileştirilmiş <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemi.

6. Çağrı <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi.

7. Çağrı <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemi.

8. Kapat <xref:System.IO.StreamWriter> çağırarak nesne kendi <xref:System.IO.StreamWriter.Close%2A> yöntemi.

9. Oluşturulan .resx dosyası uygulamanın Visual Studio projeye ekleyin.

10. Kullanarak **özellikleri** Visual Studio'da pencere emin olun .resx dosyanın **yapı eylemi** özelliği ayarlanmış **katıştırılmış kaynak**.

## <a name="example"></a>Örnek

Aşağıdaki örnek serileştiren bir <xref:System.TimeZoneInfo> Orta Standart Saati temsil eden nesnesi ve <xref:System.TimeZoneInfo> SerializedTimeZones.resx adlı bir .NET XML kaynak dosyası Palmer istasyon, Antarktika saati temsil eden nesne. Orta Standart Saati kayıt defterinde tanımlanır; PALMER istasyon, Antarktika özel bir saat dilimi olur.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Bu örnek serileştiren <xref:System.TimeZoneInfo> böylece bunlar kaynak dosyası derleme zamanında kullanılabilir nesneleri.

Çünkü <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi, bir .NET XML kaynak dosyasına tam üst bilgileri ekler, kaynaklar için varolan bir dosyayı eklemek için kullanılamaz. Örnek için SerializedTimeZones.resx dosyasını denetleyerek bu işler ve, varsa, kaynaklarının tümü dışında depolama iki saat dilimleri için genel seri <xref:System.Collections.Generic.Dictionary%602> nesnesi. Var olan dosyayı ardından silinir ve var olan kaynaklar için yeni bir SerializedTimeZones.resx dosyası eklenir. Serileştirilmiş saat dilimi verilerini de bu dosyaya eklenir.

Anahtar (veya **adı**) kaynakları alanlarının katıştırılmış boşluklar içeremez. <xref:System.String.Replace%28System.String%2CSystem.String%29> Yöntemi kaynak dosyasına atanan önce tüm katıştırılmış boşluklar saat dilimi tanımlayıcıları kaldırmak için çağrılır.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Bir başvuru System.Windows.Forms.dll ve System.Core.dll projeye eklenmesini.

* Şu ad alanlarından alınan olduğunu:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
[nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)

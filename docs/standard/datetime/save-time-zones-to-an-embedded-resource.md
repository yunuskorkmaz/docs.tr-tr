---
title: 'Nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme'
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
ms.openlocfilehash: aaee4e82d09e8b604d06dadb5a5eefe8d2e1f307
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123769"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme

Saat dilimi ile uyumlu bir uygulama genellikle belirli bir saat dilimi varlığını gerektirir. Ancak, bireysel <xref:System.TimeZoneInfo> nesnelerinin kullanılabilirliği yerel sistemin kayıt defterinde depolanan bilgilere bağlı olduğundan, geleneksel kullanılabilir saat dilimleri de bulunmayabilir. Ayrıca, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kullanılarak oluşturulan özel Saat dilimleriyle ilgili bilgiler, kayıt defterindeki diğer saat dilimi bilgileriyle depolanmaz. Bu saat dilimlerinin gerekli olmaları durumunda kullanılabilir olmasını sağlamak için bunları serileştirerek kaydedebilir ve daha sonra bunları seri durumdan kaldırarak geri yükleyebilirsiniz.

Genellikle, bir <xref:System.TimeZoneInfo> nesnesini seri hale getirme zaman dilimi kullanan uygulamadan ayrı olur. Seri hale getirilmiş <xref:System.TimeZoneInfo> nesnelerini tutmak için kullanılan veri deposuna bağlı olarak, saat dilimi verileri bir kurulum veya yükleme yordamının parçası olarak (örneğin, verilerin kayıt defterinin bir uygulama anahtarında depolanması) veya daha önce çalışan bir yardımcı program yordamının bir parçası olarak seri hale getirilebilir. son uygulama derlenir (örneğin, serileştirilmiş veriler bir .NET XML kaynak (. resx) dosyasında depolandığında).

Uygulamayla derlenen bir kaynak dosyasına ek olarak, saat dilimi bilgileri için diğer birçok veri deposu kullanılabilir. Bunlar aşağıdakileri içerir:

- Kayıt defteri. Bir uygulamanın, özel saat dilimi verilerini depolamak için, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time bölgelerinin alt anahtarlarını kullanmak yerine kendi uygulama anahtarının alt anahtarlarını kullanması gerektiğini unutmayın.

- Yapılandırma dosyaları.

- Diğer sistem dosyaları.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Bir saat dilimini bir. resx dosyasına serileştirerek kaydetmek için

1. Mevcut bir saat dilimini alın veya yeni bir saat dilimi oluşturun.

   Mevcut bir saat dilimini almak için bkz. [nasıl yapılır: önceden TANıMLANMıŞ UTC ve yerel saat dilimi nesnelerine erişme](../../../docs/standard/datetime/access-utc-and-local.md) ve [nasıl yapılır: bir TimeZoneInfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).

   Yeni bir saat dilimi oluşturmak için <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yönteminin aşırı yüklemelerinin birini çağırın. Daha fazla bilgi için bkz. [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları Ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

2. Saat diliminin verilerini içeren bir dize oluşturmak için <xref:System.TimeZoneInfo.ToSerializedString%2A> yöntemini çağırın.

3. Adı ve isteğe bağlı olarak. resx dosyasının yolunu <xref:System.IO.StreamWriter> sınıf oluşturucusuna girerek bir <xref:System.IO.StreamWriter> nesnesi örneği oluşturun.

4. <xref:System.IO.StreamWriter> nesnesini <xref:System.Resources.ResXResourceWriter> sınıf oluşturucusuna geçirerek bir <xref:System.Resources.ResXResourceWriter> nesnesi örneği oluşturun.

5. Saat dilimini serileştirilmiş dizeyi <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metoduna geçirin.

6. <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemini çağırın.

7. <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemini çağırın.

8. <xref:System.IO.StreamWriter> nesnesini <xref:System.IO.StreamWriter.Close%2A> yöntemini çağırarak kapatın.

9. Oluşturulan. resx dosyasını uygulamanın Visual Studio projesine ekleyin.

10. Visual Studio 'da **Özellikler** penceresini kullanarak,. resx dosyasının **derleme eylemi** özelliğinin **gömülü kaynak**olarak ayarlandığından emin olun.

## <a name="example"></a>Örnek

Aşağıdaki örnek, SerializedTimeZones. resx adlı bir .NET XML kaynak dosyasına Antarktika zamanını temsil eden merkezi standart saatini ve bir <xref:System.TimeZoneInfo> nesnesini temsil eden bir <xref:System.TimeZoneInfo> nesnesini seri hale getirir. Merkezi Standart saat genellikle kayıt defterinde tanımlanır; Palmer Istasyonu, Antarktika özel bir saat dilimsidir.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Bu örnek, derleme zamanında bir kaynak dosyasında kullanılabilmesi için nesneleri <xref:System.TimeZoneInfo> seri hale getirir.

<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi bir .NET XML kaynak dosyasına tüm başlık bilgilerini eklediğinden, mevcut bir dosyaya kaynak eklemek için kullanılamaz. Örnek, SerializedTimeZones. resx dosyasını denetleyerek ve varsa, iki seri hale getirilmiş zaman dilimi dışındaki tüm kaynaklarını genel bir <xref:System.Collections.Generic.Dictionary%602> nesnesine depolayarak bunu gerçekleştirir. Varolan dosya daha sonra silinir ve var olan kaynaklar yeni bir SerializedTimeZones. resx dosyasına eklenir. Seri hale getirilmiş saat dilimi verileri de bu dosyaya eklenir.

Kaynakların anahtar (veya **ad**) alanları, gömülü boşluklar içermemelidir. <xref:System.String.Replace%28System.String%2CSystem.String%29> yöntemi, kaynak dosyasına atanmadan önce saat dilimi tanımlayıcılarında tüm gömülü boşlukları kaldırmak için çağrılır.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- System. Windows. Forms. dll ve System. Core. dll ' ye bir başvuru projeye eklenir.

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
- [Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)

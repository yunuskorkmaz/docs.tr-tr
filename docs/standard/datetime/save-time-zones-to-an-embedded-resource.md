---
title: 'Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme'
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
ms.openlocfilehash: c8084cb8edff64b9d598f4fd0a62a362491c7aa7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281251"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme

Saat dilimi ile uyumlu bir uygulama genellikle belirli bir saat dilimi varlığını gerektirir. Ancak, tek tek <xref:System.TimeZoneInfo> nesnelerin kullanılabilirliği yerel sistemin kayıt defterinde depolanan bilgilere bağlı olduğundan, geleneksel kullanılabilir saat dilimleri de bulunmayabilir. Ayrıca, yöntemi kullanılarak oluşturulan özel Saat dilimleriyle ilgili bilgiler, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> kayıt defterindeki diğer saat dilimi bilgileriyle depolanmaz. Bu saat dilimlerinin gerekli olmaları durumunda kullanılabilir olmasını sağlamak için bunları serileştirerek kaydedebilir ve daha sonra bunları seri durumdan kaldırarak geri yükleyebilirsiniz.

Genellikle, bir nesneyi seri hale getirme <xref:System.TimeZoneInfo> zaman dilimi kullanan uygulamadan ayrı olarak meydana gelir. Seri hale getirilmiş nesneleri tutmak için kullanılan veri deposuna bağlı olarak <xref:System.TimeZoneInfo> , saat dilimi verileri bir kurulum veya yükleme yordamının parçası olarak (örneğin, veriler kayıt defteri 'nin bir uygulama anahtarında depolandığında) veya son uygulama derlenmesinden önce çalışan bir yardımcı program yordamının parçası olarak (örneğin, serileştirilmiş veriler bir .NET XML kaynak (. resx) dosyasında depolandığında) seri hale getirilebilir.

Uygulamayla derlenen bir kaynak dosyasına ek olarak, saat dilimi bilgileri için diğer birçok veri deposu kullanılabilir. Bunlar aşağıdakileri içerir:

- Kayıt defteri. Bir uygulamanın, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time bölgelerinin alt anahtarlarını kullanmak yerine özel saat dilimi verilerini depolamak için kendi uygulama anahtarının alt anahtarlarını kullanması gerektiğini unutmayın.

- Yapılandırma dosyaları.

- Diğer sistem dosyaları.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Bir saat dilimini bir. resx dosyasına serileştirerek kaydetmek için

1. Mevcut bir saat dilimini alın veya yeni bir saat dilimi oluşturun.

   Mevcut bir saat dilimini almak için bkz. [nasıl yapılır: önceden TANıMLANMıŞ UTC ve yerel saat dilimi nesnelerine erişme](access-utc-and-local.md) ve [nasıl yapılır: bir TimeZoneInfo nesnesinin örneğini oluşturma](instantiate-time-zone-info.md).

   Yeni bir saat dilimi oluşturmak için, yönteminin aşırı yüklemelerinin birini çağırın <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları Ile saat dilimleri oluşturma](create-time-zones-with-adjustment-rules.md).

2. <xref:System.TimeZoneInfo.ToSerializedString%2A>Saat diliminin verilerini içeren bir dize oluşturmak için yöntemini çağırın.

3. <xref:System.IO.StreamWriter>Ad ve isteğe bağlı olarak. resx dosyasının yolunu, sınıf oluşturucusuna ekleyerek bir nesne oluşturun <xref:System.IO.StreamWriter> .

4. <xref:System.Resources.ResXResourceWriter> <xref:System.IO.StreamWriter> Nesneyi sınıf oluşturucusuna geçirerek bir nesne oluşturun <xref:System.Resources.ResXResourceWriter> .

5. Saat diliminin serileştirilmiş dizesini <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemine geçirin.

6. Yöntemini çağırın <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> .

7. Yöntemini çağırın <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> .

8. <xref:System.IO.StreamWriter>Yöntemini çağırarak nesneyi kapatın <xref:System.IO.StreamWriter.Close%2A> .

9. Oluşturulan. resx dosyasını uygulamanın Visual Studio projesine ekleyin.

10. Visual Studio 'da **Özellikler** penceresini kullanarak,. resx dosyasının **derleme eylemi** özelliğinin **gömülü kaynak**olarak ayarlandığından emin olun.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.TimeZoneInfo> merkezi standart saati ve <xref:System.TimeZoneInfo> Palmer istasyonunu temsil eden bir nesneyi, Antarktika zaman SerializedTimeZones. resx adlı BIR .NET XML kaynak dosyasına temsil eden bir nesneyi seri hale getirir. Merkezi Standart saat genellikle kayıt defterinde tanımlanır; Palmer Istasyonu, Antarktika özel bir saat dilimsidir.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Bu örnek <xref:System.TimeZoneInfo> , derleme zamanında bir kaynak dosyasında kullanılabilmesi için nesneleri seri hale getirir.

<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>Yöntemi bir .NET XML kaynak dosyasına tüm başlık bilgilerini eklediğinden, mevcut bir dosyaya kaynak eklemek için kullanılamaz. Bu örnek, SerializedTimeZones. resx dosyasını denetleyerek ve varsa, iki serileştirilmiş zaman dilimi dışındaki tüm kaynaklarını genel bir nesneye depolayarak bunu gerçekleştirir <xref:System.Collections.Generic.Dictionary%602> . Varolan dosya daha sonra silinir ve var olan kaynaklar yeni bir SerializedTimeZones. resx dosyasına eklenir. Seri hale getirilmiş saat dilimi verileri de bu dosyaya eklenir.

Kaynakların anahtar (veya **ad**) alanları, gömülü boşluklar içermemelidir. <xref:System.String.Replace%28System.String%2CSystem.String%29>Yöntemi, kaynak dosyasına atanmadan önce saat dilimi tanımlayıcılarında tüm gömülü boşlukları kaldırmak için çağrılır.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- System. Windows. Forms. dll ve System. Core. dll ' ye bir başvuru projeye eklenir.

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Saat dilimine genel bakış](time-zone-overview.md)
- [Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](restore-time-zones-from-an-embedded-resource.md)

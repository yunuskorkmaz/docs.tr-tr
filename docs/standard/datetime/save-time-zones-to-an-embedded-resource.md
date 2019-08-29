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
ms.openlocfilehash: 9ca39d989cc7bc16ec2678ba5fa53710899f3ac4
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107152"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Nasıl yapılır: Saat dilimlerini eklenmiş kaynağa kaydetme

Saat dilimi ile uyumlu bir uygulama genellikle belirli bir saat dilimi varlığını gerektirir. Ancak, tek tek <xref:System.TimeZoneInfo> nesnelerin kullanılabilirliği yerel sistemin kayıt defterinde depolanan bilgilere bağlı olduğundan, geleneksel kullanılabilir saat dilimleri de bulunmayabilir. Ayrıca, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kullanılarak oluşturulan özel Saat dilimleriyle ilgili bilgiler, kayıt defterindeki diğer saat dilimi bilgileriyle depolanmaz. Bu saat dilimlerinin gerekli olmaları durumunda kullanılabilir olmasını sağlamak için bunları serileştirerek kaydedebilir ve daha sonra bunları seri durumdan kaldırarak geri yükleyebilirsiniz.

Genellikle, bir <xref:System.TimeZoneInfo> nesneyi seri hale getirme zaman dilimi kullanan uygulamadan ayrı olarak meydana gelir. Seri hale getirilmiş <xref:System.TimeZoneInfo> nesneleri tutmak için kullanılan veri deposuna bağlı olarak, saat dilimi verileri bir kurulum veya yükleme yordamının parçası olarak (örneğin, verilerin kayıt defterinin bir uygulama anahtarında depolanması) veya çalışan bir yardımcı program yordamının bir parçası olarak serileştirilmeyebilir. son uygulama derlenmesinden önce (örneğin, serileştirilmiş veriler bir .NET XML kaynak (. resx) dosyasında depolandığında).

Uygulamayla derlenen bir kaynak dosyasına ek olarak, saat dilimi bilgileri için diğer birçok veri deposu kullanılabilir. Bunlar aşağıdakileri içerir:

- Kayıt defteri. Bir uygulamanın, özel saat dilimi verilerini depolamak için, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time bölgelerinin alt anahtarlarını kullanmak yerine kendi uygulama anahtarının alt anahtarlarını kullanması gerektiğini unutmayın.

- Yapılandırma dosyaları.

- Diğer sistem dosyaları.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Bir saat dilimini bir. resx dosyasına serileştirerek kaydetmek için

1. Mevcut bir saat dilimini alın veya yeni bir saat dilimi oluşturun.

   Mevcut bir saat dilimini almak için bkz [. nasıl yapılır: Önceden tanımlanmış UTC ve yerel saat dilimi nesnelerine](../../../docs/standard/datetime/access-utc-and-local.md) erişin ve [şunları yapın: Bir TimeZoneInfo nesnesi](../../../docs/standard/datetime/instantiate-time-zone-info.md)örneği oluşturun.

   Yeni bir saat dilimi oluşturmak için, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yönteminin aşırı yüklemelerinin birini çağırın. Daha fazla bilgi için [nasıl yapılır: Ayarlama kuralları](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) olmadan saat dilimleri oluşturun ve [şunları yapın: Ayarlama kuralları](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)ile saat dilimleri oluşturun.

2. Saat diliminin verilerini içeren bir dize oluşturmak için yönteminiçağırın.<xref:System.TimeZoneInfo.ToSerializedString%2A>

3. Ad ve <xref:System.IO.StreamWriter> isteğe bağlı olarak. resx dosyasının <xref:System.IO.StreamWriter> yolunu, sınıf oluşturucusuna ekleyerek bir nesne oluşturun.

4. <xref:System.IO.StreamWriter> <xref:System.Resources.ResXResourceWriter> Nesneyi<xref:System.Resources.ResXResourceWriter> sınıf oluşturucusuna geçirerek bir nesne oluşturun.

5. Saat diliminin serileştirilmiş dizesini <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemine geçirin.

6. Çağrı <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi.

7. Çağrı <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemi.

8. Yöntemini çağırarak nesneyi kapatın. <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Close%2A>

9. Oluşturulan. resx dosyasını uygulamanın Visual Studio projesine ekleyin.

10. Visual Studio 'da **Özellikler** penceresini kullanarak,. resx dosyasının **derleme eylemi** özelliğinin **gömülü kaynak**olarak ayarlandığından emin olun.

## <a name="example"></a>Örnek

Aşağıdaki örnek, merkezi standart saati <xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo> ve Palmer istasyonunu temsil eden bir nesneyi, Antarktika zaman SerializedTimeZones. resx adlı bir .NET XML kaynak dosyasına temsil eden bir nesneyi seri hale getirir. Merkezi Standart saat genellikle kayıt defterinde tanımlanır; Palmer Istasyonu, Antarktika özel bir saat dilimsidir.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Bu örnek, derleme <xref:System.TimeZoneInfo> zamanında bir kaynak dosyasında kullanılabilmesi için nesneleri seri hale getirir.

<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> Yöntemi bir .NET XML kaynak dosyasına tüm başlık bilgilerini eklediğinden, mevcut bir dosyaya kaynak eklemek için kullanılamaz. Bu örnek, SerializedTimeZones. resx dosyasını denetleyerek ve varsa, iki serileştirilmiş zaman dilimi dışındaki tüm kaynaklarını genel <xref:System.Collections.Generic.Dictionary%602> bir nesneye depolayarak bunu gerçekleştirir. Varolan dosya daha sonra silinir ve var olan kaynaklar yeni bir SerializedTimeZones. resx dosyasına eklenir. Seri hale getirilmiş saat dilimi verileri de bu dosyaya eklenir.

Kaynakların anahtar (veya **ad**) alanları, gömülü boşluklar içermemelidir. <xref:System.String.Replace%28System.String%2CSystem.String%29> Yöntemi, kaynak dosyasına atanmadan önce saat dilimi tanımlayıcılarında tüm gömülü boşlukları kaldırmak için çağrılır.

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

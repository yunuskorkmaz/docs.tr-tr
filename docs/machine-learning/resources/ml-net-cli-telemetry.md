---
title: ML.NET CLI tarafından Telemetri koleksiyonu
description: Analiz için kullanım bilgilerini toplayan, hangi verilerin toplandığı ve nasıl devre dışı kalınan CLI telemetri özellikleri ML.NET hakkında bilgi edinin. Ayrıca, .NET lisans sözleşmesine bağlantılar ve Microsoft GDPR uyumluluğu hakkındaki bilgileri bulun.
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 99e11acba343cc689c3219ca9316144fc62cd618
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849750"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>ML.NET CLI tarafından Telemetri koleksiyonu

[CLI ML.NET,](https://aka.ms/mlnet-cli) Microsoft tarafından kullanılmak üzere toplanan anonim kullanım verilerini toplayan bir telemetri özelliği içerir.

## <a name="how-microsoft-uses-the-data"></a>Microsoft verileri nasıl kullanır?

Ürün ekibi, araçları nasıl geliştireceğini anlamama yardımcı olmak için ML.NET CLI telemetri verilerini kullanır. Örneğin, müşteriler belirli bir makine öğrenimi görevini seyrek olarak kullanıyorsa, ürün ekibi neden olduğunu araştırır ve özellik geliştirmeye öncelik vermek için bulguları kullanır. ML.NET CLI telemetri de çöker ve kod anomalileri gibi sorunların hata ayıklama ile yardımcı olur.

Ürün ekibi bu öngörüyü takdir etse de, herkesin bu verileri göndermek istemediğini de biliyoruz. [Telemetriyi nasıl devre dışı dışı katabileceğinizi öğrenin.](#opt-out-of-data-collection)

## <a name="scope"></a>Kapsam

Komut `mlnet` CLI ML.NET başlatıyor, ancak komutun kendisi telemetri toplamaz.

`mlnet` Komutu başka bir komut eklenmeden çalıştırdığınızda telemetri *etkinleştirilmez.* Örnek:

- `mlnet`
- `mlnet --help`

Telemetri, [cli komutu gibi bir](../reference/ml-net-cli-reference.md)ML.NET `mlnet auto-train`çalıştırdığınızda *etkinleştirilir.*

## <a name="opt-out-of-data-collection"></a>Veri toplamayı devre dışı bırakma

cli telemetri özelliğiML.NET varsayılan olarak etkinleştirilir.

Ortam değişkenini `MLDOTNET_CLI_TELEMETRY_OPTOUT` `1` `true`ayarlayarak telemetri özelliğini devre dışı bırakma Bu ortam değişkeni, ML.NET CLI aracı için genel olarak geçerlidir.

## <a name="data-points-collected"></a>Toplanan veri noktaları

Özellik aşağıdaki verileri toplar:

- Hangi komut çağrıldı, örneğin`auto-train`
- Kullanılan komut satırı parametre adları (diğer bir şey, "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")
- Hashed MAC adresi: bir makine için şifreleme (SHA256) anonim ve benzersiz bir kimlik
- Bir çağırmanın zaman damgası
- Yalnızca coğrafi konumu belirlemek için kullanılan üç sekizli IP adresi (tam IP adresi değil)
- Kullanılan tüm bağımsız değişkenlerin/parametrelerin adı. Dizeleri gibi müşterinin değerleri değil
- Hashed dataset dosya adı
- Dataset dosya boyutunda kova
- İşletim sistemi ve sürüm
- --görev parametresi değeri: `regression`Kategorik değerler, `binary-classification`, , ve`multiclass-classification`
- ML.NET CLI sürümü (yani, 0.3.27703.4)

Veriler, sınırlı erişim altında tutulan ve güvenli [Azure Depolama](https://azure.microsoft.com/services/storage/) sistemlerinden gelen sıkı güvenlik denetimleri altında kullanılan [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) teknolojisini kullanarak Microsoft sunucularına güvenli bir şekilde gönderilir.

### <a name="data-points-not-collected"></a>Toplanmayan veri noktaları

Telemetri özelliği şunları *toplamaz:*

- kullanıcı adları gibi kişisel veriler
- dataset dosya adları
- dataset dosyalarından gelen veriler

CLI telemetrisinin ML.NET hassas verileri topladığından veya verilerin güvensiz veya uygunsuz şekilde işlendiğini sanıyorsanız, ML.NET [deposunda](https://github.com/dotnet/machinelearning) bir sorun dosyalayarak inceleme için bir sorun bulun.

## <a name="license"></a>Lisans

CLI'ML.NET Microsoft dağıtımı Microsoft Yazılım Lisans Koşulları ile [lisanslanmıştır: Microsoft .NET Kitaplığı.](https://aka.ms/dotnet-core-eula) Veri toplama ve işleme ile ilgili ayrıntılar için "Veri" başlıklı bölüme bakın.

## <a name="disclosure"></a>Açıklama

CLI ML.NET aracı gibi `mlnet auto-train`bir ML.NET [CLI komutunu](../reference/ml-net-cli-reference.md) ilk çalıştırdığınızda, telemetriyi nasıl devre dışı bırakmanız gerektiğini belirten açıklama metni görüntülenir. Metin, çalıştırdığınız CLI sürümüne bağlı olarak biraz değişiklik gösterebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLI başvurusu](../reference/ml-net-cli-reference.md)
- [Microsoft Yazılım Lisans Koşulları: Microsoft .NET Kitaplığı](https://aka.ms/dotnet-core-eula)
- [Microsoft'ta gizlilik](https://www.microsoft.com/trustcenter/privacy/)
- [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement)

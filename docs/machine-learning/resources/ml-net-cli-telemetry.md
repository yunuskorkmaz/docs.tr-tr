---
title: ML.NET CLı tarafından telemetri toplama
description: Analiz için kullanım bilgilerini toplayan, hangi verilerin toplandığı ve devre dışı bırakılacağı ML.NET CLı telemetri özellikleri hakkında bilgi edinin. Ayrıca, .NET lisans sözleşmesinin bağlantılarını ve Microsoft GDPR uyumluluğu hakkındaki bilgileri bulabilirsiniz.
ms.topic: conceptual
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 753361abdac5a2e979873003f419232a069b2015
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546438"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>ML.NET CLı tarafından telemetri toplama

[Ml.net CLI](../automate-training-with-cli.md) , Microsoft tarafından kullanılmak üzere toplanan anonim kullanım verilerini toplayan bir telemetri özelliği içerir.

## <a name="how-microsoft-uses-the-data"></a>Microsoft verileri nasıl kullanır?

Ürün ekibi, araçların nasıl geliştirilmesine yardımcı olmak için ML.NET CLı telemetri verilerini kullanır. Örneğin, müşteriler belirli bir makine öğrenimi görevini sık sık kullanıyorsa, ürün ekibi, özellik geliştirmeyi önceliklendirmek için neden ve bulguları araştırır kullanır. ML.NET CLı telemetrisi, çökmeler ve kod bozuklukları gibi sorunların hatalarını ayıklamanıza de yardımcı olur.

Ürün ekibi bu öngörüleri öğrenirken, herkesin bu verileri göndermek istediğini da biliyoruz. [Telemetriyi devre dışı bırakmayı öğrenin.](#opt-out-of-data-collection)

## <a name="scope"></a>Kapsam

`mlnet`Komut ml.net CLI 'yi başlatır, ancak komut telemetri toplamaz.

Komutu başka bir komut ekli olmadan çalıştırdığınızda telemetri *etkin değildir* `mlnet` . Örnek:

- `mlnet`
- `mlnet --help`

Telemetri, gibi bir [ml.net CLI komutu](../reference/ml-net-cli-reference.md)çalıştırdığınızda *etkinleştirilir* `mlnet classification` .

## <a name="opt-out-of-data-collection"></a>Veri toplamayı geri çevirme

ML.NET CLı telemetri özelliği varsayılan olarak etkindir.

`MLDOTNET_CLI_TELEMETRY_OPTOUT`Ortam değişkenini veya olarak ayarlayarak telemetri özelliğini geri çevirin `1` `true` . Bu ortam değişkeni, ML.NET CLı aracına Global olarak uygulanır.

## <a name="data-points-collected"></a>Toplanan veri noktaları

Bu özellik aşağıdaki verileri toplar:

- Çağrılan komut `classification`
- Kullanılan komut satırı parametre adları (yani, "DataSet, Label-Col, Output-Path, tren-Time, ayrıntı")
- Karma hale getirilmiş MAC adresi: bir makine için bir şifreleme (SHA256) anonim ve benzersiz KIMLIĞI
- Bir çağrının zaman damgası
- Yalnızca coğrafi konumu belirlemede kullanılan üç sekizli IP adresi (tam IP adresi değil)
- Kullanılan tüm bağımsız değişkenlerin/parametrelerin adı. Müşterinin değerleri değil (dizeler gibi)
- Karma veri kümesi dosya adı
- Veri kümesi dosya boyutu demeti
- İşletim sistemi ve sürümü
- ML görev komutlarının değeri:,, ve gibi kategorik değerler `regression` `classification``recommendation`
- ML.NET CLı sürümü (yani, 0.3.27703.4)

Veriler, [azure Application Insights](https://azure.microsoft.com/services/application-insights/) teknolojisi kullanılarak Microsoft sunucularına güvenli bir şekilde gönderilir, kısıtlı erişim altında tutulur ve güvenli [Azure depolama](https://azure.microsoft.com/services/storage/) sistemlerinden katı güvenlik denetimleri altında kullanılır.

### <a name="data-points-not-collected"></a>Veri noktaları toplanmadı

Telemetri *özelliği toplanmaz* :

- Kullanıcı adları gibi kişisel veriler
- veri kümesi dosya adları
- veri kümesi dosyalarından veriler

ML.NET CLı telemetrinin hassas verileri toplamasını veya verilerin güvenli veya uygun şekilde işlenmekte olduğunu kuşkulanıyorsanız, araştırma için [ml.net](https://github.com/dotnet/machinelearning) deposunda bir sorun verin.

## <a name="license"></a>Lisans

ML.NET CLı 'nin Microsoft dağıtımı, [Microsoft yazılım lisans koşulları: Microsoft .NET kitaplığı](https://aka.ms/dotnet-core-eula)ile lisanslanır. Veri toplama ve işleme hakkında daha fazla bilgi için "veri" başlıklı bölüme bakın.

## <a name="disclosure"></a>Savunmasız

Gibi bir [ml.net CLI komutunu](../reference/ml-net-cli-reference.md) ilk kez çalıştırdığınızda `mlnet classification` , ml.net CLI aracı Telemetriyi nasıl kabul eteceklerini belirten açıklama metnini görüntüler. Metin, çalıştırdığınız CLı sürümüne bağlı olarak biraz farklılık gösterebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLı başvurusu](../reference/ml-net-cli-reference.md)
- [Microsoft yazılımı lisans koşulları: Microsoft .NET kitaplığı](https://aka.ms/dotnet-core-eula)
- [Microsoft 'ta Gizlilik](https://www.microsoft.com/trustcenter/privacy/)
- [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement)

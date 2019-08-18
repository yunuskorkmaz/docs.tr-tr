---
title: ML.NET CLı tarafından telemetri toplama
description: Analiz için kullanım bilgilerini toplayan, hangi verilerin toplandığı ve devre dışı bırakılacağı ML.NET CLı telemetri özellikleri hakkında bilgi edinin. Ayrıca, .NET lisans sözleşmesinin bağlantılarını ve Microsoft GDPR uyumluluğu hakkındaki bilgileri bulabilirsiniz.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: b9f6ccf7ff76f0cf4ce806f39909b7607a20b9f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567497"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>ML.NET CLı tarafından telemetri toplama

[Ml.net CLI](https://aka.ms/mlnet-cli) , Microsoft tarafından kullanılmak üzere toplanan anonim kullanım verilerini toplayan bir telemetri özelliği içerir.

## <a name="how-microsoft-uses-the-data"></a>Microsoft verileri nasıl kullanır?

Ürün ekibi, araçların nasıl geliştirilmesine yardımcı olmak için ML.NET CLı telemetri verilerini kullanır. Örneğin, müşteriler belirli bir makine öğrenimi görevini sık sık kullanıyorsa, ürün ekibi, özellik geliştirmeyi önceliklendirmek için neden ve bulguları araştırır kullanır. ML.NET CLı telemetrisi, çökmeler ve kod bozuklukları gibi sorunların hatalarını ayıklamanıza de yardımcı olur. 

Ürün ekibi bu öngörüleri öğrenirken, herkesin bu verileri göndermek istediğini da biliyoruz. [Telemetriyi devre dışı bırakmayı öğrenin.](#opt-out-of-data-collection)

## <a name="scope"></a>Kapsam

`mlnet` Komut ml.net CLI 'yi başlatır, ancak komut telemetri toplamaz.

`mlnet` Komutu başka bir komut ekli olmadan çalıştırdığınızda telemetri *etkin değildir* . Örneğin:

- `mlnet`
- `mlnet --help`

Telemetri`mlnet auto-train`, gıbı bir [ml.net CLI komutu](../reference/ml-net-cli-reference.md)çalıştırdığınızda *etkinleştirilir* .

## <a name="opt-out-of-data-collection"></a>Veri toplamayı geri çevirme

ML.NET CLı telemetri özelliği varsayılan olarak etkindir.

`MLDOTNET_CLI_TELEMETRY_OPTOUT` Ortam değişkenini `1` veya`true`olarak ayarlayarak telemetri özelliğini geri çevirin. Bu ortam değişkeni, .NET CLı aracı için global olarak geçerlidir.

## <a name="data-points-collected"></a>Toplanan veri noktaları

Bu özellik aşağıdaki verileri toplar:

- Çağrılan komut`auto-train`
- Kullanılan komut satırı parametre adları (örneğin, "DataSet-Name, Label-Column-Name, ml-Task, Output-Path, Max-araştırma zamanı, ayrıntı")
- Karma hale getirilmiş MAC adresi: bir makine için bir şifreleme (SHA256) anonim ve benzersiz KIMLIĞI
- Bir çağrının zaman damgası
- Yalnızca coğrafi konumu belirlemede kullanılan üç sekizli IP adresi (tam IP adresi değil)
- Kullanılan tüm bağımsız değişkenlerin/parametrelerin adı. Müşterinin değerleri değil (dizeler gibi)
- Karma veri kümesi dosya adı
- Veri kümesi dosya boyutu demeti
- İşletim sistemi ve sürümü
- --Görev parametresi değeri: , Ve gibi kategorik değerler `regression` `binary-classification``multiclass-classification`
- ML.NET CLı sürümü (ör. 0.3.27703.4)

Veriler, [azure Application Insights](https://azure.microsoft.com/services/application-insights/) teknolojisi kullanılarak Microsoft sunucularına güvenli bir şekilde gönderilir, kısıtlı erişim altında tutulur ve güvenli [Azure depolama](https://azure.microsoft.com/services/storage/) sistemlerinden katı güvenlik denetimleri altında kullanılır.

### <a name="data-points-not-collected"></a>Veri noktaları toplanmadı
Telemetri özelliği toplanmaz :
- Kullanıcı adları gibi kişisel veriler
- veri kümesi dosya adları
- veri kümesi dosyalarından veriler

ML.NET CLı telemetrinin hassas verileri toplamasını veya verilerin güvenli veya uygun şekilde işlenmekte olduğunu kuşkulanıyorsanız, araştırma için [ml.net](https://github.com/dotnet/machinelearning) deposunda bir sorun verin.

## <a name="license"></a>Lisans

ML.net CLI 'nin Microsoft dağıtımı, [Microsoft yazılımı lisans koşulları ile lisanslanır: Microsoft .NET kitaplığı](https://aka.ms/dotnet-core-eula). Veri toplama ve işleme hakkında daha fazla bilgi için "veri" başlıklı bölüme bakın.

## <a name="disclosure"></a>Savunmasız

Gibi bir [ml.net CLI komutunu](../reference/ml-net-cli-reference.md) `mlnet auto-train`ilk kez çalıştırdığınızda, ml.net CLI aracı Telemetriyi nasıl kabul eteceklerini belirten açıklama metnini görüntüler. Metin, çalıştırdığınız CLı sürümüne bağlı olarak biraz farklılık gösterebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [ML.NET CLı başvurusu](../reference/ml-net-cli-reference.md)
- [Microsoft yazılımı lisans koşulları: Microsoft .NET kitaplığı](https://aka.ms/dotnet-core-eula)
- [Microsoft 'ta Gizlilik](https://www.microsoft.com/trustcenter/privacy/)
- [Microsoft gizlilik bildirimi](https://privacy.microsoft.com/privacystatement)

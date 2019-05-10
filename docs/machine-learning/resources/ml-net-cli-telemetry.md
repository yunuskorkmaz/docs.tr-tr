---
title: ML.NET CLI tarafından telemetri toplama
description: Analiz için bilgileri, hangi verileri toplanır ve bunu devre dışı bırakma, kullanım verileri toplayan ML.NET CLI telemetri özellikler hakkında bilgi edinin. Ayrıca .NET lisans sözleşmesi ve Microsoft GDPR uyumluluğu hakkında bilgi için bağlantılar öğrenin.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: 49ebd6c9e1b77c85d891b8c9fb8cbd5c66b478a9
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066159"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>ML.NET CLI tarafından telemetri toplama

[ML.NET CLI](http://aka.ms/mlnet-cli) kullanmak için Microsoft tarafından toplanan anonim kullanım verileri toplayan telemetri özelliğini içerir.

## <a name="how-microsoft-uses-the-data"></a>Microsoft verileri nasıl kullanır

Ürün ekibine araçları geliştirmek nasıl anlamanıza yardımcı olması için ML.NET CLI telemetri verilerini kullanır. Örneğin, müşteriler seyrek belirli bir makine öğrenimi görevi kullanıyorsa, ürün ekibine neden araştırır ve bulguları özellik geliştirme önceliğini belirlemek için kullanır. ML.NET CLI telemetri Kilitlenmeler ve kod anormallikleri gibi sorunların hatalarını ayıklamaya yardımcı olur. 

Ürün ekibine bu öngörüleri appreciates olsa da herkes bu verileri göndermek istiyor da biliyoruz. [Telemetri devre dışı bırakmak öğrenin.](#opt-out-of-data-collection)

## <a name="scope"></a>Kapsam

`mlnet` ML.NET CLI komutu çalıştırır, ancak komut telemetri toplamaz.

Telemetri *etkin değilse* çalıştırdığınızda `mlnet` bağlı herhangi bir komut ile komutu. Örneğin:

- `mlnet`
- `mlnet --help`

Telemetri *etkin* çalıştırdığınızda bir [ML.NET CLI komutunu](../reference/ml-net-cli-reference.md), gibi `mlnet auto-train`.

## <a name="opt-out-of-data-collection"></a>Veri toplama işlemini iptal

ML.NET CLI telemetri özellik varsayılan olarak etkindir.

Ayarlayarak telemetri özelliği iyileştirilmiş `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenine `1` veya `true`. Bu ortam değişkeni, genel .NET CLI aracı için geçerlidir.

## <a name="data-points-collected"></a>Toplanan veri noktaları

Bu özellik aşağıdaki verileri toplar:

- Hangi komutları gibi çağırılır `auto-train`
- Karma MAC adresi: bir şifreleme açısından (SHA256) anonim ve benzersiz bir kimliği bir makine için
- Zaman damgası bir çağırma
- Yalnızca coğrafi konumunu belirlemek için kullanılan üç sekizli IP adresi
- Kullanılan tüm bağımsız değişkenler/parametreler adı. Dizeleri gibi müşteri'nin değerlerini değil
- İşletim sistemi ve sürümü
- --Ml görev parametresinin değeri: Gibi kategorik değerler `regression`, `binary-classification`, ve `multiclass-classification`
- [Logaritmik yuvarlanır](https://en.wikipedia.org/wiki/Rounding#Rounding_to_a_specified_power) dataset dosya boyutu (en yakın 2 power)
- `ExitCode` komutu

Veriler güvenli bir şekilde kullanarak Microsoft sunucularına gönderilir [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) kısıtlı erişim'in altında tutulması ve katı güvenlik denetimleri güvenli altında kullanılan teknoloji [Azure depolama](https://azure.microsoft.com/services/storage/) sistemler.

### <a name="data-points-not-collected"></a>Veri noktaları toplanmadı
Telemetri özellik *değil* toplayın:
- kullanıcı adları gibi kişisel veriler
- veri kümesi dosya adları
- veri kümesi dosyalardan alınan veriler

ML.NET CLI telemetri hassas veriler ya da toplama şüpheleniyorsanız veri endpoınt yapılıyor veya uygunsuz bir şekilde ele, sorunu bildirin [ML.NET](https://github.com/dotnet/machinelearning) araştırma için depo.

## <a name="license"></a>Lisans

Microsoft Dağıtım ML.NET CLI ile lisanslı [Microsoft Yazılımı Lisans koşulları: Microsoft .NET kitaplığı](https://aka.ms/dotnet-core-eula). Veri toplama ve işleme hakkında daha fazla bilgi için "Veri" başlıklı bölüme bakın.

## <a name="disclosure"></a>Açığa çıkması

İlk kez çalıştırdığınızda bir [ML.NET CLI komutunu](../reference/ml-net-cli-reference.md) gibi `mlnet auto-train`, ML.NET CLI araç telemetri dışında nasıl söyler açığa metin görüntüler. Metin, çalıştırmakta olduğunuz CLI sürümüne bağlı olarak biraz değişebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [ML.NET CLI başvurusu](../reference/ml-net-cli-reference.md)
- [Microsoft Yazılımı Lisans koşulları: Microsoft .NET kitaplığı](https://aka.ms/dotnet-core-eula)
- [Microsoft gizlilik](https://www.microsoft.com/en-us/trustcenter/privacy/)
- [Microsoft gizlilik bildirimi](https://privacy.microsoft.com/en-us/privacystatement)

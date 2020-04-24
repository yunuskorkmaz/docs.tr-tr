---
title: Azure Işlevleri-sunucusuz uygulamalar
description: Azure işlevleri, olay odaklı anında ölçeklendirme kodu sağlamak için birden çok dilde (C#, JavaScript, Java) ve platformlarda sunucusuz yetenekler sağlar.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 2dee60e3635be94a55ee26a7f04942bc59cb8dec
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135730"
---
# <a name="azure-functions"></a>Azure İşlevleri

Azure işlevleri, sunucusuz bir işlem deneyimi sağlar. Bir işlev bir *tetikleyici* tarafından çağrılır (bir HTTP uç noktasına veya bir zamanlayıcıya erişim gibi) ve bir kod bloğu veya iş mantığı yürütür. İşlevler ayrıca depolama ve kuyruklar gibi kaynaklara bağlanan özelleştirilmiş *bağlamaları* destekler.

![Azure işlevleri logosu](./media/azure-functions-logo.png)

Geçerli çalışma zamanı sürüm 3,0, platformlar arası .NET Core 3,1 uygulamalarını destekler. JavaScript, F # ve Java gibi ek diller de desteklenir. Portalda oluşturulan işlevler, zengin bir betik sözdizimi sağlar. Tek başına projeler olarak oluşturulan işlevler, tam platform desteği ve özellikleri ile dağıtılabilir.

Daha fazla bilgi için bkz. [Azure işlevleri belgeleri](https://docs.microsoft.com/azure/azure-functions).

## <a name="programming-language-support"></a>Programlama dili desteği

Aşağıdaki dillerin tümü genel kullanılabilirlik (GA) içinde desteklenir.

|Dil      |Desteklenen çalışma zamanları|
|--------------|------------------|
|**C#**        |.NET Core 3,1     |
|**JavaScript**|Düğüm 10 & 12      |
|**F#**        |.NET Core 3,1     |
|**Java**      |Java 8            |
|**Python**    |Python 3,6, 3,7, & 3,8|
|**TypeScript**|Düğüm 10 & 12 (JavaScript aracılığıyla)|
|**PowerShell**|PowerShell Core 6|

Daha fazla bilgi için bkz. [Desteklenen diller](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>App Service planları

İşlevler bir *App Service planı*tarafından desteklenir. Plan, işlevler uygulaması tarafından kullanılan kaynakları tanımlar. Bir bölgeye planlar atayabilir, kullanılacak sanal makinelerin boyutunu ve sayısını belirleyebilir ve bir fiyatlandırma katmanı seçebilirsiniz. Doğru sunucusuz bir yaklaşım için işlev uygulamaları **Tüketim** planını kullanabilir. Tüketim planı, yük temelinde arka ucu otomatik olarak ölçeklendirecektir.

İşlev uygulamaları için başka bir barındırma seçeneği de [Premium plandır](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan). Bu plan, soğuk başlangıçtan kaçınmak için "Always On" örneği sağlar, VNet bağlantısı gibi gelişmiş özellikleri destekler ve Premium donanımda çalışır.

Daha fazla bilgi için bkz. [App Service planları](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>İlk uygulamanızı oluşturma

İşlev uygulamaları oluşturabileceğiniz üç yaygın yol vardır.

- Portalda betik işlevleri.
- Azure CLı kullanarak gereken kaynakları oluşturun.
- En sevdiğiniz IDE 'yi kullanarak işlevleri yerel olarak derleyin ve Azure 'da yayımlayın.

Portalda betikleştirilmiş bir işlev oluşturma hakkında daha fazla bilgi için, [Azure Portal ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)bölümüne bakın.

Azure CLı 'dan derlemek için bkz. [Azure CLI kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Visual Studio 'dan bir işlev oluşturmak için bkz. [Visual Studio kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Tetikleyicileri ve bağlamaları anlama

İşlevler bir *tetikleyici* tarafından çağrılır ve tam olarak bir tane olabilir. İşlevi çağırmaya ek olarak, bazı Tetikleyiciler de bağlamalar olarak görev yapar. Ayrıca, tetikleyicisine ek olarak birden çok bağlama de tanımlayabilirsiniz. *Bağlamalar* , verileri kodunuza bağlamanın bildirim temelli bir yolunu sağlar. Bunlar (giriş) veya veri alabilir (çıktı). Tetikleyiciler ve bağlamalar işlevleri ile çalışmayı kolay hale getirir. Bağlamalar, veritabanı veya dosya sistemi bağlantılarını el ile oluşturma ek yükünü ortadan kaldırır. Bağlamalar için gereken tüm bilgiler, betikler için özel bir *Functions. JSON* dosyasında bulunur veya koddaki özniteliklerle birlikte bildirilmiştir.

Bazı ortak Tetikleyiciler şunları içerir:

- BLOB depolama: bir dosya veya klasör bir depolama alanında karşıya yüklenirken veya değiştirildiğinde işlevinizi çağırın.
- HTTP: işlevinizi REST API gibi çağırın.
- Queue: bir kuyrukta öğeler mevcutsa işlevinizi çağırın.
- Süreölçer: işlevinizi düzenli bir temposunda çağırma.

Bağlama örnekleri şunları içerir:

- CosmosDB: dosyaları yüklemek veya kaydetmek için kolayca veritabanına bağlanın.
- Tablo Depolama: işlev uygulamanızdan anahtar/değer depolama ile çalışma.
- Kuyruk depolama: bir kuyruktan kolayca öğe alın veya yeni öğeleri kuyruğa yerleştirin.

Aşağıdaki örnek *Functions. JSON* dosyası bir tetikleyiciyi ve bağlamayı tanımlar:

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

Bu örnekte, işlev, `images` kapsayıcıda blob depolamaya yapılan bir değişiklik tarafından tetiklenir. Dosya ile ilgili bilgiler geçirilir, bu nedenle tetikleyici de bir bağlama işlevi görür. Adlı `images`bir kuyruğa bilgi koymak için başka bir bağlama var.

İşlevin C# betiği aşağıdadır:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

Örnek, değiştirilen veya blob depolamaya yüklenen dosyanın adını alan ve daha sonra işlenmek üzere bir kuyruğa yerleştirtiren basit bir işlevdir.

Tetikleyiciler ve bağlamaların tam listesi için bkz. [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

>[!div class="step-by-step"]
>[Önceki](azure-serverless-platform.md)
>[İleri](application-insights.md)

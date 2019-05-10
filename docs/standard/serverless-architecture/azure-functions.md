---
title: Azure işlevleri - sunucusuz uygulamalar
description: Azure işlevleri, sunucusuz özellikler birden çok dil arasında (C#, JavaScript, Java) sağlar ve olay odaklı anında sağlamak için Platform kodu ölçeklendirin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754225"
---
# <a name="azure-functions"></a>Azure İşlevleri

Azure işlevleri, sunucusuz işlem deneyimi sağlar. Bir işlev tarafından çağrılan bir *tetikleyici* (örneğin, bir HTTP uç noktası veya bir zamanlayıcı erişim) ve kod veya iş mantığı bloğunu yürütür. Ayrıca destek özel işlevler *bağlamaları* depolama ve kuyruk gibi kaynaklara bağlanın.

![Azure işlevleri logosu](./media/azure-functions-logo.png)

Azure işlevleri framework'ün iki sürümü vardır. Eski sürüm tam .NET Framework ve .NET Core uygulamaları platformlar arası yeni çalışma zamanı destekler. İlave diller yanı sıra C# JavaScript gibi F#, ve Java desteklenir. Portalda oluşturulan işlevleri, zengin bir betik söz dizimi sağlar. Tek başına projeleri oluşturulan işlevleri tam bir platform desteği ve özellikleri ile dağıtılabilir.

Daha fazla bilgi için [Azure işlevleri belgelerinde](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>İşlevler v1 ve v2 karşılaştırması

Azure işlevleri çalışma zamanı iki sürümü vardır: 1.x ve 2.x'i. Sürüm 1.x olan genel kullanıma (GA). .NET geliştirme portalı veya Windows makineleri destekler ve .NET Framework'ü kullanır. 1.x destekler C#, JavaScript ve F#, Python, PHP, TypeScript, Batch, Bash ve PowerShell için Deneysel desteği.

[Sürüm 2.x de genel kullanıma sunulan artık](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). .NET Core yararlanır ve Windows, macOS ve Linux makinelerini platformlar arası geliştirmeyi destekler. 2.x Java için birinci sınıf destek ekler, ancak henüz doğrudan Deneysel dillerden herhangi birini desteklemiyor. Sürüm 2.x üçüncü taraf uzantıları bağımsız sürüm oluşturma işlemlerini bağlamaları platforma sağlayan yeni bir bağlama genişletilebilirlik modeli kullanır ve daha rahat bir yürütme ortamı.

> **1.x ile içinde bilinen bir sorun var. [bağlama yeniden yönlendirme desteği](https://github.com/Azure/azure-functions-host/issues/992).** Sorun için .NET geliştirme özeldir. Kitaplıkların çalışma zamanı'nda bulunan farklı bir sürüm kitaplıkları bağımlı olan projeler etkilenir. İşlevleri ekibi, sorunu somut ilerleme kaydediyor için kaydoldu. Genel kullanıma geçmeden önce takım 2.x bağlama yeniden yönlendirmelerini ele alınacaktır. Önerilen düzeltmeler ve geçici çözümler resmi takım deyimiyle buradan kullanılabilir: [Azure işlevleri'nde derleme çözümlemesine](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Daha fazla bilgi için [1.x ve 2.x'i karşılaştırma](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Programlama dili desteği

Aşağıdaki dillerde desteklenmektedir ya da genel kullanıma (GA) Önizleme, veya Deneysel.

|Dil      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |GA          |Önizleme  |
|**JavaScript**|GA          |Önizleme  |
|**F#**        |GA          |         |
|**Java**      |            |Önizleme  |
|**Python**    |Deneysel|         |
|**PHP**       |Deneysel|         |
|**TypeScript**|Deneysel|         |
|**Batch**     |Deneysel|         |
|**Bash**      |Deneysel|         |
|**PowerShell**|Deneysel|         |

Daha fazla bilgi için [desteklenen diller](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>App service planları

İşlevleri tarafından desteklenen bir *app service planı*. Plan, İşlevler uygulama tarafından kullanılan kaynakları tanımlar. Planları bir bölgeye atama, kullanılacak ve fiyatlandırma katmanı seçme sanal makinelerin sayısını ve boyutunu belirler. İşlev uygulamaları için doğru bir sunucusuz yaklaşım, kullanabilir **tüketim** planı. Tüketim planı otomatik olarak yüküne göre arka uç ölçeklenir.

Daha fazla bilgi için [App service planları](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>İlk işlevinizi oluşturma

İşlev uygulamaları oluşturabileceğiniz üç yaygın yolları vardır.

* Portalda betik işlevleri.
* Azure komut satırı arabirimi (CLI) kullanarak gerekli kaynakları oluşturur.
* Sık kullandığınız IDE'yi kullanarak yerel olarak işlevler oluşturun ve bunları Azure'a yayımlayın.

Portalda komut dosyalı bir işlev oluşturma hakkında daha fazla bilgi için bkz. [Azure portalında ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Azure CLI üzerinden oluşturmak için bkz: [Azure CLI kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Visual Studio'dan bir işlev oluşturmak için bkz [Visual Studio kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Tetikleyiciler ve bağlamalar anlama

İşlevler tarafından çağrılır bir *tetikleyici* ve tam olarak bir olabilir. İşlev çağırma yanı sıra belirli Tetikleyicileri bağlamaları Ayrıca hizmet. Ayrıca, tetikleyici yanı sıra birden çok bağlamaları tanımlayabilir. *Bağlamaları* kodunuza veri bağlanmak için bildirim temelli bir yöntemini sağlar. Bunlar, (giriş) geçirilebilir veya verileri (çıktı) alırsınız. İşlevleri Tetikleyicileri ve bağlamaları ile çalışmak kolaylaştırır. Veritabanı veya dosya sistemi bağlantıları el ile oluşturma ek yükü bağlamaları kaldırın. Özel bir barındırılan tüm bağlamaları için gereken bilgileri *functions.json* için komut dosyası veya kod öznitelikleri ile bildirilen.

Bazı sık kullanılan Tetikleyicileri şunlardır:

* BLOB Depolama: dosya veya klasör karşıya veya depolama alanında değiştirildi, işlevinizi çağırır.
* HTTP:, işlev bir REST API gibi çağırın.
* Kuyruk:, kuyrukta öğeleri mevcut olduğunda, işlev çağırın.
* Zamanlayıcı: normal temposu üzerinde işlevinizi çağırır.

Bağlamaları örnekleri şunlardır:

* Cosmos DB: kolayca yüklemek veya dosyaları kaydetmek için veritabanına bağlanın.
* Tablo depolaması: işlev uygulamanızı depolamadan anahtar/değer çalışın.
* Kuyruk Depolama: kolayca öğeleri kuyruktan almak veya yeni öğeleri sıraya koyun.

Aşağıdaki örnek *functions.json* dosyası, bir tetikleyici ve bağlama tanımlar:

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

Bu örnekte, bir blob depolama alanında değişiklik işlevi tetiklenir `images` kapsayıcı. Tetikleyici olarak bir bağlama ayrıca çalışır. Bu nedenle, dosya bilgilerini geçirilir. Bilgi adlı bir sıra üstüne koymak için başka bir bağlamanın mevcut `images`.

C# betik işlevi için şu şekildedir:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

Dosyanın adı almayan basit bir işlevi değiştirildi veya BLOB depolamaya yüklediğiniz ve daha sonra işlemek için bir kuyruk yerleştirir örnektir.

Tetikleyiciler ve bağlamalar tam listesi için bkz [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Proxy'ler

Proxy'leri, uygulamanızın yeniden yönlendirme işlevselliği sağlar. Proxy'leri, bir uç noktanın kullanıma ve başka bir kaynak için uç noktanın eşleyin. Proxy ile şunları yapabilirsiniz:

* Başka bir uç nokta gelen bir isteği yeniden yönlendirebilir.
* Gelen istek boyunca geçirilmeden önce değiştirin.
* Değiştirmek veya bir yanıt verin.

Proxy'leri gibi senaryolar için kullanılır:

* Basitleştirme, kısaltmayı veya URL değiştirme.
* Birden fazla arka uç Hizmetleri için tutarlı bir API öneki sağlama.
* Geliştirilmekte olan bir uç nokta için bir yanıt sahte işlem.
* İyi bilinen bir uç nokta için statik bir yanıt sağlama.
* Arka uç taşınmış veya geçiş yaparken bir API uç noktası tutarlı kalmasını sağlar.

Proxy'leri JSON tanımları depolanır. Aşağıda bir örnek verilmiştir:

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

`Domain Redirect` Proxy kısaltılmış bir yol alır ve uzun işlevi kaynağa eşler. Dönüştürme şu şekilde görünür:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

`Root` Proxy kök URL'ye gönderilen her şeyi alır (`https://--shorturl--/`) ve belge sitesine yönlendirir.

Proxy'leri kullanma örneği, videoda gösterilen [Azure: Sunucusuz Azure işlevleri ile bulut uygulamanızı taşıyın](https://channel9.msdn.com/events/Connect/2017/E102). Gerçek zamanlı olarak yerel SQL Server üzerinde çalışan bir ASP.NET Core uygulaması Azure buluta geçirilir. Proxy işlevleri kullanmak için geleneksel bir Web API projesi yeniden düzenleme yardımcı olmak için kullanılır.

Proxy hakkında daha fazla bilgi için bkz: [iş ile Azure işlevleri proxy'leri](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Önceki](azure-serverless-platform.md)
>[İleri](application-insights.md)

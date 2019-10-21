---
title: Azure Işlevleri-sunucusuz uygulamalar
description: Azure işlevleri, olay odaklı anında ölçeklendirme kodu sağlamak içinC#birden çok dilde (, JavaScript, Java) ve platformlarda sunucusuz yetenekler sağlar.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5e8187b3752a0f0d0bcf8e15f2ce440dc5a64e45
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522871"
---
# <a name="azure-functions"></a>Azure İşlevleri

Azure işlevleri, sunucusuz bir işlem deneyimi sağlar. Bir işlev bir *tetikleyici* tarafından çağrılır (bir HTTP uç noktasına veya bir zamanlayıcıya erişim gibi) ve bir kod bloğu veya iş mantığı yürütür. İşlevler ayrıca depolama ve kuyruklar gibi kaynaklara bağlanan özelleştirilmiş *bağlamaları* destekler.

![Azure işlevleri logosu](./media/azure-functions-logo.png)

Azure Işlevleri çerçevesinin iki sürümü vardır. Eski sürüm, tam .NET Framework destekler ve yeni çalışma zamanı platformlar arası .NET Core uygulamalarını destekler. JavaScript, F#ve C# Java gibi ek diller de desteklenir. Portalda oluşturulan işlevler, zengin bir betik sözdizimi sağlar. Tek başına projeler olarak oluşturulan işlevler, tam platform desteği ve özellikleri ile dağıtılabilir.

Daha fazla bilgi için bkz. [Azure işlevleri belgeleri](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>İşlevler v1 ve v2

Azure Işlevleri çalışma zamanının iki sürümü vardır: 1. x ve 2. x. Sürüm 1. x genel kullanıma sunuldu (GA). Portal veya Windows makinelerinden .NET geliştirmesini destekler ve .NET Framework kullanır. 1. x, C#Python, php, F#TypeScript, Batch, bash ve PowerShell için deneysel destekle birlikte desteklenir, JavaScript ve.

[Sürüm 2. x artık genel olarak kullanılabilir](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). .NET Core 'u kullanır ve Windows, macOS ve Linux makinelerinde platformlar arası geliştirmeyi destekler. 2. x, Java için birinci sınıf destek ekler ancak deneysel dillerin hiçbirini henüz doğrudan desteklemez. Sürüm 2. x, platforma üçüncü taraf uzantılar, bağlamaların bağımsız sürümü ve daha kolay bir yürütme ortamı sağlayan yeni bir bağlama genişletilebilirlik modeli kullanır.

> **[Bağlama yeniden yönlendirme desteğiyle](https://github.com/Azure/azure-functions-host/issues/992)1. x içinde bilinen bir sorun var.** Bu sorun .NET geliştirmeye özgüdür. Çalışma zamanına dahil olan kitaplıkların farklı bir sürümü olan kitaplıklarda bağımlılıklar içeren projeler etkilenir. Takım işlevleri, sorun üzerinde somut ilerleme durumu yapmayı taahhüt etti. Takım, genel kullanıma geçmeden önce 2. x içindeki bağlama yeniden yönlendirmelerini ele alacak. Önerilen düzeltmeler ve geçici çözümler içeren resmi takım bildirimine buradan ulaşabilirsiniz: [Azure işlevleri 'Nde derleme çözümlemesi](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Daha fazla bilgi için bkz. [Compare 1. x ve 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Programlama dili desteği

Aşağıdaki diller genel kullanılabilirlik (GA), önizleme veya deneysel olarak desteklenir.

|Dil      |'in         |2.x      |
|--------------|------------|---------|
|**C#**        |GA          |Önizleme  |
|**JavaScript**|GA          |Önizleme  |
|**F#**        |GA          |         |
|**Java**      |            |Önizleme  |
|**Python**    |Deneysel|         |
|**PHP**       |Deneysel|         |
|**TypeScript**|Deneysel|         |
|**İşlemini**     |Deneysel|         |
|**Bash**      |Deneysel|         |
|**PowerShell**|Deneysel|         |

Daha fazla bilgi için bkz. [desteklenen diller](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>App Service planları

İşlevler bir *App Service planı*tarafından desteklenir. Plan, işlevler uygulaması tarafından kullanılan kaynakları tanımlar. Bir bölgeye planlar atayabilir, kullanılacak sanal makinelerin boyutunu ve sayısını belirleyebilir ve bir fiyatlandırma katmanı seçebilirsiniz. Doğru sunucusuz bir yaklaşım için işlev uygulamaları **Tüketim** planını kullanabilir. Tüketim planı, yük temelinde arka ucu otomatik olarak ölçeklendirecektir.

Daha fazla bilgi için bkz. [App Service planları](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>İlk işlevinizi oluşturma

İşlev uygulamaları oluşturabileceğiniz üç yaygın yol vardır.

- Portalda betik işlevleri.
- Azure komut satırı arabirimi 'ni (CLı) kullanarak gerekli kaynakları oluşturun.
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

Bu örnekte, işlevi `images` kapsayıcısındaki blob depolamada yapılan bir değişiklik tarafından tetiklenir. Dosya ile ilgili bilgiler geçirilir, bu nedenle tetikleyici de bir bağlama işlevi görür. @No__t_0 adlı bir kuyruğa bilgi koymak için başka bir bağlama var.

İşlevin C# betiği şöyledir:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

Örnek, değiştirilen veya blob depolamaya yüklenen dosyanın adını alan ve daha sonra işlenmek üzere bir kuyruğa yerleştirtiren basit bir işlevdir.

Tetikleyiciler ve bağlamaların tam listesi için bkz. [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Kullanıldığı

Proxy 'ler, uygulamanız için yeniden yönlendirme işlevi sağlar. Proxy 'ler bir uç noktayı kullanıma sunar ve bu uç noktayı başka bir kaynakla eşler. Proxy 'ler ile şunları yapabilirsiniz:

- Gelen isteği başka bir uç noktaya yeniden yönlendir.
- Gelen isteği geçirilmeden önce değiştirin.
- Bir yanıtı değiştirin veya bir yanıt verin.

Proxy 'ler gibi senaryolar için kullanılır:

- URL 'YI basitleştirecek, kısaltaştırın veya değiştirmeyi kolaylaştırın.
- Birden fazla arka uç hizmetine tutarlı bir API öneki sağlama.
- Geliştirmekte olan bir uç noktaya yanıt verme.
- İyi bilinen bir uç noktaya statik yanıt sağlama.
- Arka uç taşındığında veya geçirildiğinde bir API uç noktasının tutarlı tutulması.

Proxy 'ler JSON tanımları olarak depolanır. Aşağıda bir örnek verilmiştir:

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

@No__t_0 proxy, kısaltılmış bir yol alır ve daha uzun işlev kaynağıyla eşlenir. Dönüştürme şöyle görünür:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

@No__t_0 proxy, kök URL 'ye gönderilen her şeyi alır (`https://--shorturl--/`) ve belge sitesine yönlendirir.

Azure 'da ara sunucu kullanımıyla ilgili bir örnek gösterilir [: sunucusuz Azure işlevleri ile Uygulamanızı buluta taşıyın](https://channel9.msdn.com/events/Connect/2017/E102). Gerçek zamanlı olarak, yerel SQL Server üzerinde çalışan bir ASP.NET Core uygulaması Azure bulutuna geçirilir. Proxy 'ler, işlevleri kullanmak üzere geleneksel bir Web API projesini yeniden düzenleme konusunda yardımcı olmak için kullanılır.

Proxy 'Ler hakkında daha fazla bilgi için bkz. [Azure işlev proxy'leri Ile çalışma](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Önceki](azure-serverless-platform.md)
>[İleri](application-insights.md)

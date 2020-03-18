---
title: Azure Fonksiyonları - Sunucusuz uygulamalar
description: Azure işlevleri, olay odaklı anlık ölçek kodu sağlamak için birden çok dilde (C#, JavaScript, Java) ve platformlarda sunucusuz özellikler sağlar.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401615"
---
# <a name="azure-functions"></a>Azure İşlevleri

Azure işlevleri sunucusuz bir bilgi işlem deneyimi sağlar. Bir işlev bir *tetikleyici* tarafından çağrılır (örneğin, bir HTTP bitiş noktası veya zamanlayıcıya erişim) ve bir kod bloğu veya iş mantığı yürütür. İşlevler, depolama ve kuyruklar gibi kaynaklara bağlanan özel *bağlamaları* da destekler.

![Azure işlevleri logosu](./media/azure-functions-logo.png)

Azure İşlevler çerçevesinin iki sürümü vardır. Eski sürüm tam .NET Framework'u destekler ve yeni çalışma süresi çapraz platform .NET Core uygulamalarını destekler. JavaScript, F#ve Java gibi C# ek dilleri desteklenir. Portalda oluşturulan işlevler zengin bir komut dosyası sözdizimi sağlar. Bağımsız projeler olarak oluşturulan işlevler tam platform desteği ve yetenekleri ile dağıtılabilir.

Daha fazla bilgi için Azure [İşlevleri belgelerine](https://docs.microsoft.com/azure/azure-functions)bakın.

## <a name="functions-v1-vs-v2"></a>Fonksiyonlar v1 vs. v2

Azure İşlevleri çalışma zamanının iki sürümü vardır: 1.x ve 2.x. Sürüm 1.x genellikle kullanılabilir (GA). Portal veya Windows makinelerinden .NET geliştirmeyi destekler ve .NET Framework'i kullanır. 1.x, Python, PHP, TypeScript, Batch, Bash ve PowerShell için deneysel destekle C#, JavaScript ve F#'ı destekler.

[Sürüm 2.x de genel olarak şimdi kullanılabilir](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). .NET Core'dan yararlanır ve Windows, macOS ve Linux makinelerinde platformlar arası geliştirmeyi destekler. 2.x Java için birinci sınıf destek ekler, ancak henüz deneysel dillerin hiçbirini doğrudan desteklemez. Sürüm 2.x, platforma üçüncü taraf uzantıları, bağlamaların bağımsız sürümü ve daha kolay bir yürütme ortamı sağlayan yeni bir bağlayıcı genişletilebilirlik modeli kullanır.

> **[Bağlayıcı yönlendirme desteği](https://github.com/Azure/azure-functions-host/issues/992)ile 1.x bilinen bir sorun vardır.** Sorun .NET geliştirmeye özgüdür. Çalışma zamanında dahil edilen kitaplıklardan farklı bir sürüme sahip kitaplıklara bağımlılık ları olan projeler etkilenir. Fonksiyonlar ekibi, sorun üzerinde somut ilerleme kaydetmeyi taahhüt etmiştir. Takım, genel kullanılabilirliğe geçmeden önce 2.x'te bağlama yönlendirmelerini ele alacaktır. Önerilen düzeltmeler ve geçici çözümleriçeren resmi ekip bildirimine buradan ulaşabilirsiniz: [Azure İşyerlerinde Derleme çözümü.](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)

Daha fazla bilgi için bkz: [1.x ve 2.x karşılaştırın.](https://docs.microsoft.com/azure/azure-functions/functions-versions)

## <a name="programming-language-support"></a>Programlama dili desteği

Aşağıdaki diller genel kullanılabilirlik (GA), önizleme veya deneysel olarak desteklenir.

|Dil      |1.x         |2.x      |
|--------------|------------|---------|
|**C #**        |GA          |Önizleme  |
|**Javascript**|GA          |Önizleme  |
|**F#**        |GA          |         |
|**Java**      |            |Önizleme  |
|**Python**    |Deneysel|         |
|**PHP**       |Deneysel|         |
|**TypeScript**|Deneysel|         |
|**Toplu iş**     |Deneysel|         |
|**Bash**      |Deneysel|         |
|**Powershell**|Deneysel|         |

Daha fazla bilgi için bkz. [Desteklenen diller](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Uygulama hizmeti planları

İşlevler bir *uygulama hizmet planı*tarafından yedeklenir. Plan, işlevler uygulaması tarafından kullanılan kaynakları tanımlar. Bir bölgeye planlar atayabilir, kullanılacak sanal makinelerin boyutunu ve sayısını belirleyebilir ve bir fiyatlandırma katmanı seçebilirsiniz. Gerçek bir sunucusuz yaklaşım için işlev uygulamaları **tüketim** planını kullanabilir. Tüketim planı, arka ucunu yüke göre otomatik olarak ölçeklendirecektir.

Daha fazla bilgi için [Uygulama hizmet planlarına](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)bakın.

## <a name="create-your-first-function"></a>İlk uygulamanızı oluşturma

İşlev uygulamaları oluşturmanın üç yaygın yolu vardır.

- Portaldaki komut dosyası işlevleri.
- Azure CLI'yi kullanarak gerekli kaynakları oluşturun.
- En sevdiğiniz IDE'yi kullanarak işlevleri yerel olarak oluşturun ve Bunları Azure'da yayınlayın.

Portalda komut dosyası işlevi oluşturma hakkında daha fazla bilgi için azure [portalında ilk işlevinizi oluştur'a](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)bakın.

Azure CLI'den oluşturmak için [bkz.](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)

Visual Studio'dan bir işlev oluşturmak için visual [studio'u kullanarak ilk işlevinizi oluşturun'e](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)bakın.

## <a name="understand-triggers-and-bindings"></a>Tetikleyicileri ve bağlamaları anlama

Fonksiyonlar bir *tetikleyici* tarafından çağrılır ve tam olarak bir tane olabilir. İşlev çağırmak için ek olarak, bazı tetikleyiciler de bağlama olarak hizmet vermektedir. Tetikleyiciye ek olarak birden çok bağlama da tanımlayabilirsiniz. *Bağlamalar,* verileri kodunuza bağlamak için bildirimsel bir yol sağlar. Bunlar (giriş) geçirilebilir veya veri (çıktı) alabilir. Tetikleyiciler ve bağlamalar işlevlerin çalışmasını kolaylaştırır. Bağlamalar, veritabanı veya dosya sistemi bağlantılarının el ile oluşturma ek yükü kaldırılır. Bağlamalar için gereken tüm bilgiler, komut dosyaları için özel bir *functions.json* dosyasında bulunur veya koddaki özniteliklerle birlikte bildirilir.

Bazı yaygın tetikleyiciler şunlardır:

- Blob Depolama: Bir dosya veya klasör depolama alanına yüklendiğinde veya değiştirildiğinde işlevinizi çağırın.
- HTTP: REST API gibi işlevinizi çağırın.
- Sıra: Öğeler kuyrukta olduğunda işlevinizi çağırın.
- Zamanlayıcı: düzenli bir cadence üzerinde işlevinizi çağırmak.

Bağlamalara örnek olarak şunlar verilebilir:

- CosmosDB: dosyaları yüklemek veya kaydetmek için veritabanına kolayca bağlanın.
- Tablo Depolama: fonksiyon uygulamanızdan anahtar/değer depolama ile çalışın.
- Sıra Depolama: öğeleri kuyruktan kolayca alın veya kuyruğa yeni öğeler yerleştirin.

Aşağıdaki örnek *functions.json* dosyası bir tetikleyici ve bağlama tanımlar:

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

Bu örnekte, işlev `images` kapsayıcıda blob depolama bir değişiklik tarafından tetiklenir. Dosyaiçin bilgiler geçirilir, bu nedenle tetikleyici de bağlayıcı olarak hareket eder. Başka bir bağlama adlı `images`bir kuyruğa bilgi koymak için var.

Burada işlev için C# komut dosyası:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

Örnek, değiştirilen veya blob depolamasına yüklenen dosyanın adını alan ve daha sonra işleme için sıraya koyan basit bir işlevdir.

Tetikleyicilerin ve bağlamaların tam listesi için Azure [İşlevleri tetikleyicileri ve bağlama kavramlarını](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)görün.

## <a name="proxies"></a>Proxy 'leri

Ek severler, uygulamanız için yeniden yönlendirme işlevselliği sağlar. Ekseksiler, bitiş noktasını başka bir kaynağa gösterir ve haritayı gösterir. Vekillerile şunları yapabilirsiniz:

- Gelen isteği başka bir bitiş noktasına yeniden yönlendirin.
- Gelen isteği geçirilmeden önce değiştirin.
- Değiştirin veya yanıt sağlayın.

Ekseksitler gibi senaryolar için kullanılır:

- URL'yi basitleştirme, kısaltma veya değiştirme.
- Birden çok arka uç hizmetine tutarlı bir API öneki sağlar.
- Geliştirilen bir uç noktaya verilen yanıtla alay etmek.
- Bilinen bir bitiş noktasına statik yanıt sağlar.
- Arka uç taşınırken veya geçirilirken API bitiş noktasını tutarlı tutmak.

Yakınlıklar JSON tanımları olarak depolanır. Örnek aşağıda verilmiştir:

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

Proxy `Domain Redirect` kısaltılmış bir rota alır ve daha uzun işlev kaynağıyla eşler. Dönüşüm gibi görünüyor:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

Proxy, kök URL'ye `Root` gönderilen`https://--shorturl--/`bir şeyi alır ( ) ve belgeleme sitesine yönlendirir.

Ekseksi kullanmanın bir örneği Azure videosunda [gösterilir: Sunucusuz Azure İşlevleri ile uygulamanızı buluta getirin.](https://channel9.msdn.com/events/Connect/2017/E102) Gerçek zamanlı olarak, yerel SQL Server'da çalışan bir ASP.NET Core uygulaması Azure Bulutu'na geçirilir. Ekseksiler, işlevleri kullanmak için geleneksel bir Web API projesini yeniden düzenlemeye yardımcı olmak için kullanılır.

Proxies hakkında daha fazla bilgi için Azure [İşleriyle Çalışma'ya](https://docs.microsoft.com/azure/azure-functions/functions-proxies)bakın.

>[!div class="step-by-step"]
>[Önceki](azure-serverless-platform.md)
>[Sonraki](application-insights.md)
